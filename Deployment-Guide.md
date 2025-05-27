# Deployment and CI/CD Guide
## Starbucks Real-Time Inventory Management System (RTIMS)

---

## 1. CI/CD Pipeline Architecture

### 1.1 Pipeline Overview

```
┌───────────┐     ┌───────────┐     ┌───────────┐     ┌───────────┐
│   Code    │     │   Build   │     │   Test    │     │  Deploy   │
│  Commit   ├────►│   Stage   ├────►│   Stage   ├────►│   Stage   │
└───────────┘     └───────────┘     └───────────┘     └───────────┘
     │                  │                  │                  │
     ▼                  ▼                  ▼                  ▼
  GitHub           Jenkins/           Test Envs          Kubernetes
              GitLab CI/GitHub                          (Progressive)
                 Actions

Environments: Dev → QA → Staging → Production
```

### 1.2 Build Pipeline Configuration

**GitHub Actions Workflow**
```yaml
name: RTIMS Build and Deploy

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

env:
  AWS_REGION: us-east-1
  ECR_REPOSITORY: rtims
  EKS_CLUSTER: rtims-prod

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - name: Set up JDK 17
        uses: actions/setup-java@v3
        with:
          java-version: '17'
          
      - name: Run Unit Tests
        run: ./gradlew test
        
      - name: Run Integration Tests
        run: ./gradlew integrationTest
        
      - name: SonarQube Analysis
        env:
          SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}
        run: ./gradlew sonarqube
        
      - name: Security Scan
        run: |
          docker run --rm -v $(pwd):/src \
            aquasec/trivy:latest filesystem /src
  build:
    needs: test
    runs-on: ubuntu-latest
    if: github.ref == 'refs/heads/main' || github.ref == 'refs/heads/develop'
    
    steps:
      - uses: actions/checkout@v3
      
      - name: Configure AWS credentials
        uses: aws-actions/configure-aws-credentials@v2
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          aws-region: ${{ env.AWS_REGION }}
          
      - name: Build Docker Image
        run: |
          docker build -t $ECR_REPOSITORY:$GITHUB_SHA .
          docker tag $ECR_REPOSITORY:$GITHUB_SHA $ECR_REPOSITORY:latest
          
      - name: Push to ECR
        run: |
          aws ecr get-login-password | docker login --username AWS --password-stdin $ECR_REGISTRY
          docker push $ECR_REGISTRY/$ECR_REPOSITORY:$GITHUB_SHA
          docker push $ECR_REGISTRY/$ECR_REPOSITORY:latest

  deploy:
    needs: build
    runs-on: ubuntu-latest
    
    steps:
      - name: Deploy to Kubernetes
        run: |
          aws eks update-kubeconfig --name $EKS_CLUSTER
          kubectl set image deployment/rtims-api rtims-api=$ECR_REGISTRY/$ECR_REPOSITORY:$GITHUB_SHA
          kubectl rollout status deployment/rtims-api
```

---

## 2. Kubernetes Deployment

### 2.1 Deployment Configuration

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: rtims-inventory-service
  namespace: rtims-prod
spec:
  replicas: 5
  selector:
    matchLabels:
      app: inventory-service
  template:
    metadata:
      labels:
        app: inventory-service
    spec:
      containers:
      - name: inventory-service
        image: rtims/inventory-service:latest
        ports:
        - containerPort: 8080
        env:
        - name: SPRING_PROFILES_ACTIVE
          value: "production"
        - name: DB_PASSWORD
          valueFrom:
            secretKeyRef:
              name: rtims-secrets
              key: db-password        resources:
          requests:
            memory: "2Gi"
            cpu: "1000m"
          limits:
            memory: "4Gi"
            cpu: "2000m"
        livenessProbe:
          httpGet:
            path: /actuator/health
            port: 8080
          initialDelaySeconds: 90
          periodSeconds: 10
        readinessProbe:
          httpGet:
            path: /actuator/health/readiness
            port: 8080
          initialDelaySeconds: 60
          periodSeconds: 5
```

### 2.2 Service Configuration

```yaml
apiVersion: v1
kind: Service
metadata:
  name: inventory-service
  namespace: rtims-prod
spec:
  selector:
    app: inventory-service
  ports:
    - protocol: TCP
      port: 80
      targetPort: 8080
  type: ClusterIP
---
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: inventory-service-hpa
  namespace: rtims-prod
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: rtims-inventory-service
  minReplicas: 5
  maxReplicas: 50
  metrics:
  - type: Resource
    resource:
      name: cpu
      target:
        type: Utilization
        averageUtilization: 70
  - type: Resource
    resource:
      name: memory
      target:
        type: Utilization
        averageUtilization: 80
```
---

## 3. Deployment Strategies

### 3.1 Progressive Rollout Strategy

**Phase 1: Mock Store Testing (Month 1)**
```bash
# Deploy to mock environment
kubectl apply -f k8s/mock-env/ -n rtims-mock

# Run synthetic load tests
artillery run load-tests/mock-store.yml

# Validate metrics
./scripts/validate-metrics.sh mock
```

**Phase 2: Pilot Store (Month 2)**
```bash
# Deploy with feature flags
helm upgrade rtims ./charts/rtims \
  --set featureFlags.pilotStores="STR-001,STR-002,STR-003" \
  --set replicaCount=3 \
  -n rtims-pilot
```

**Phase 3: Regional Rollout (Months 3-6)**
```bash
# Progressive rollout by region
for region in northwest southwest midwest northeast southeast; do
  helm upgrade rtims-$region ./charts/rtims \
    --set region=$region \
    --set rollout.percentage=10 \
    -n rtims-prod
    
  # Monitor for 24 hours before proceeding
  ./scripts/monitor-rollout.sh $region 24h
done
```

### 3.2 Blue-Green Deployment

```yaml
# Blue environment (current)
apiVersion: v1
kind: Service
metadata:
  name: rtims-active
spec:
  selector:
    app: rtims
    version: blue
---
# Green environment (new)
apiVersion: apps/v1
kind: Deployment
metadata:
  name: rtims-green
spec:
  replicas: 5
  selector:
    matchLabels:
      app: rtims
      version: green
```

**Cutover Process:**
```bash
# 1. Deploy green version
kubectl apply -f deployments/green.yaml

# 2. Run smoke tests
./tests/smoke-test.sh green

# 3. Switch traffic
kubectl patch service rtims-active \
  -p '{"spec":{"selector":{"version":"green"}}}'

# 4. Monitor metrics
./scripts/monitor-cutover.sh 30m

# 5. Cleanup old version after validation
kubectl delete deployment rtims-blue
```
---

## 4. Rollback Procedures

### 4.1 Automated Rollback

```yaml
# Flagger configuration for automated rollback
apiVersion: flagger.app/v1beta1
kind: Canary
metadata:
  name: rtims-inventory
spec:
  targetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: rtims-inventory
  progressDeadlineSeconds: 300
  service:
    port: 80
  analysis:
    interval: 30s
    threshold: 5
    maxWeight: 50
    stepWeight: 10
    metrics:
    - name: request-success-rate
      thresholdRange:
        min: 99
      interval: 1m
    - name: request-duration
      thresholdRange:
        max: 500
      interval: 1m
    webhooks:
    - name: load-test
      url: http://flagger-loadtester.test/
      timeout: 5s
```

### 4.2 Manual Rollback Process

```bash
#!/bin/bash
# rollback.sh - Emergency rollback script

DEPLOYMENT=$1
NAMESPACE=${2:-rtims-prod}

# Get previous revision
PREVIOUS_REVISION=$(kubectl rollout history deployment/$DEPLOYMENT -n $NAMESPACE | tail -2 | head -1 | awk '{print $1}')

# Rollback to previous version
kubectl rollout undo deployment/$DEPLOYMENT --to-revision=$PREVIOUS_REVISION -n $NAMESPACE

# Wait for rollback to complete
kubectl rollout status deployment/$DEPLOYMENT -n $NAMESPACE

# Verify health
./scripts/health-check.sh $DEPLOYMENT $NAMESPACE
```

---

## 5. Monitoring and Alerts

### 5.1 Deployment Monitoring

```yaml
# Prometheus alerts for deployment issues
groups:
- name: deployment_alerts
  rules:
  - alert: DeploymentReplicasNotReady
    expr: |
      kube_deployment_status_replicas_ready{namespace="rtims-prod"}
      < kube_deployment_spec_replicas{namespace="rtims-prod"}
    for: 5m
    annotations:
      summary: "Deployment {{ $labels.deployment }} has unhealthy replicas"
      
  - alert: HighErrorRate
    expr: |
      rate(http_requests_total{status=~"5.."}[5m]) > 0.05
    for: 5m
    annotations:
      summary: "High error rate detected post-deployment"
```

---

*End of Deployment Guide*