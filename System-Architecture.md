# System Architecture Document
## Starbucks Real-Time Inventory Management System (RTIMS)

---

## 1. High-Level Architecture Overview

### 1.1 System Components

```mermaid
graph TB
    subgraph "External Systems"
        EXT1[Weather APIs]
        EXT2[Events APIs]
        EXT3[SAP System]
        EXT4[POS Systems]
    end
    
    subgraph "Integration Layer"
        GW[API Gateway<br/>Kong]
        MQ[Message Queue<br/>Kafka]
        AD[Adapter Services]
    end
    
    subgraph "Application Services"
        SVC1[Inventory Service<br/>Java/Spring]
        SVC2[ML/AI Service<br/>Python/FastAPI]
        SVC3[Blockchain Service<br/>Go/Hyperledger]
        SVC4[Analytics Service<br/>Python/Spark]
    end
    
    subgraph "Service Mesh"
        MESH[Istio Service Mesh]
    end
    
    subgraph "Data Layer"
        DB1[(PostgreSQL<br/>Primary)]
        DB2[(InfluxDB<br/>Metrics)]
        DB3[(MongoDB<br/>Features)]
        DB4[(Redis<br/>Cache)]
    end
    
    EXT1 & EXT2 & EXT3 & EXT4 --> GW
    GW --> MQ
    MQ --> AD
    AD --> MESH
    MESH --> SVC1 & SVC2 & SVC3 & SVC4
    SVC1 --> DB1 & DB4
    SVC2 --> DB2 & DB3
    SVC3 --> DB1
    SVC4 --> DB2
    
    style GW fill:#00704A,color:#fff
    style MESH fill:#1976d2,color:#fff
    style SVC1 fill:#fff59d
    style SVC2 fill:#e8f5e9
    style SVC3 fill:#e3f2fd
    style SVC4 fill:#ffe0b2
```

### 1.2 Deployment Architecture

```mermaid
graph TB
    subgraph "AWS Multi-Region"
        subgraph "US-East-1 (Primary)"
            subgraph "EKS Cluster"
                P1[App Pods]
                P2[Service Mesh]
                P3[Monitoring]
            end
            subgraph "Data Tier"
                RDS1[(RDS Multi-AZ<br/>PostgreSQL)]
                EC1[(ElastiCache<br/>Redis)]
            end
        end
        
        subgraph "US-West-2 (DR)"
            subgraph "EKS Standby"
                S1[App Pods]
                S2[Service Mesh]
            end
            subgraph "Replicas"
                RDS2[(RDS Read<br/>Replica)]
                EC2[(ElastiCache<br/>Replica)]
            end
        end
        
        subgraph "Global Services"
            CF[CloudFront CDN]
            R53[Route 53]
            S3[S3 Storage]
        end
    end
    
    R53 --> CF
    CF --> P1
    RDS1 -.->|Replication| RDS2
    EC1 -.->|Sync| EC2
    
    style P1 fill:#4caf50,color:#fff
    style S1 fill:#ff9800,color:#fff
    style CF fill:#00704A,color:#fff
```

---

## 2. Microservices Architecture

### 2.1 Service Interaction Map

```mermaid
graph LR
    subgraph "Frontend Services"
        UI[UI Layer]
    end
    
    subgraph "Core Services"
        INV[Inventory Service]
        ML[ML Service]
        BC[Blockchain Service]
        AN[Analytics Service]
    end
    
    subgraph "Infrastructure"
        KAFKA[Kafka]
        CACHE[Redis]
    end
    
    UI -->|REST| INV
    UI -->|GraphQL| AN
    
    INV -->|gRPC| ML
    INV -->|Events| KAFKA
    ML -->|Predictions| KAFKA
    BC -->|Events| KAFKA
    
    KAFKA -->|Subscribe| AN
    KAFKA -->|Subscribe| INV
    
    INV <-->|Cache| CACHE
    ML <-->|Cache| CACHE
    
    style INV fill:#fff59d
    style ML fill:#e8f5e9
    style BC fill:#e3f2fd
    style KAFKA fill:#00704A,color:#fff
```

### 2.2 Service Details

```mermaid
flowchart TD
    subgraph "Inventory Service"
        IS1[REST API]
        IS2[Business Logic]
        IS3[Data Access]
        IS4[Event Publisher]
        
        IS1 --> IS2
        IS2 --> IS3
        IS2 --> IS4
    end
    
    subgraph "ML/AI Service"
        ML1[Prediction API]
        ML2[Model Server]
        ML3[Feature Pipeline]
        ML4[Training Pipeline]
        
        ML1 --> ML2
        ML3 --> ML2
        ML3 --> ML4
    end
    
    subgraph "Blockchain Service"
        BC1[Transaction API]
        BC2[Smart Contracts]
        BC3[Consensus]
        BC4[Ledger]
        
        BC1 --> BC2
        BC2 --> BC3
        BC3 --> BC4
    end
```

---

## 3. Security Architecture

### 3.1 Security Layers

```mermaid
flowchart TB
    subgraph "Edge Security"
        WAF[WAF<br/>CloudFlare]
        DDOS[DDoS Protection]
        IDS[IDS/IPS<br/>AWS GuardDuty]
    end
    
    subgraph "API Security"
        APIGW[API Gateway]
        RL[Rate Limiting]
        AUTH[OAuth 2.0]
        VAL[Request Validation]
    end
    
    subgraph "Service Security"
        MESH[Service Mesh]
        MTLS[mTLS]
        RBAC[RBAC Policies]
        ENC[Traffic Encryption]
    end
    
    subgraph "Data Security"
        DAR[Encryption at Rest<br/>AES-256]
        DIT[Encryption in Transit<br/>TLS 1.3]
        KMS[Key Management<br/>AWS KMS]
        TDE[Database TDE]
    end
    
    WAF --> DDOS --> IDS --> APIGW
    APIGW --> RL --> AUTH --> VAL
    VAL --> MESH
    MESH --> MTLS --> RBAC --> ENC
    ENC --> DAR & DIT
    KMS --> DAR & DIT & TDE
    
    style WAF fill:#ff5252,color:#fff
    style APIGW fill:#00704A,color:#fff
    style MESH fill:#1976d2,color:#fff
    style KMS fill:#673ab7,color:#fff
```

### 3.2 Authentication Flow

```mermaid
sequenceDiagram
    participant User
    participant App
    participant Gateway
    participant Auth as Auth Service
    participant Okta
    participant Service
    
    User->>App: Login Request
    App->>Gateway: Auth Request
    Gateway->>Auth: Validate Credentials
    Auth->>Okta: SSO Check
    Okta-->>Auth: User Valid
    Auth->>Auth: Generate JWT
    Auth-->>Gateway: JWT Token
    Gateway-->>App: Access Token
    
    App->>Gateway: API Request + JWT
    Gateway->>Gateway: Validate JWT
    Gateway->>Service: Forward Request
    Service-->>Gateway: Response
    Gateway-->>App: API Response
    
    Note over Gateway,Service: All internal communication uses mTLS
```

---

## 4. Data Architecture

### 4.1 Data Flow Architecture

```mermaid
flowchart LR
    subgraph "Data Sources"
        POS[POS Transactions]
        IOT[IoT Sensors]
        EXT[External APIs]
    end
    
    subgraph "Stream Processing"
        KAFKA[Kafka Streams]
        FLINK[Apache Flink]
    end
    
    subgraph "Storage"
        subgraph "Operational"
            PG[(PostgreSQL)]
            REDIS[(Redis)]
        end
        
        subgraph "Analytical"
            INFLUX[(InfluxDB)]
            MONGO[(MongoDB)]
        end
        
        subgraph "Archive"
            S3[(S3 Data Lake)]
        end
    end
    
    subgraph "Analytics"
        SPARK[Spark Jobs]
        ML[ML Training]
        BI[BI Dashboards]
    end
    
    POS & IOT & EXT --> KAFKA
    KAFKA --> FLINK
    FLINK --> PG & INFLUX
    PG --> REDIS
    INFLUX --> MONGO
    PG & INFLUX --> S3
    S3 --> SPARK
    SPARK --> ML & BI
    
    style KAFKA fill:#00704A,color:#fff
    style PG fill:#336791,color:#fff
    style S3 fill:#ff9800,color:#fff
```

### 4.2 Database Partitioning Strategy

```mermaid
graph TD
    subgraph "PostgreSQL Partitioning"
        MAIN[Items Table<br/>Parent]
        P1[items_2025_01<br/>January]
        P2[items_2025_02<br/>February]
        P3[items_2025_03<br/>March]
        PN[items_2025_NN<br/>...]
        
        MAIN --> P1 & P2 & P3 & PN
    end
    
    subgraph "Sharding Strategy"
        SHARD[Store Inventory]
        S1[Region West<br/>Stores 1-5000]
        S2[Region Central<br/>Stores 5001-10000]
        S3[Region East<br/>Stores 10001-17000]
        
        SHARD --> S1 & S2 & S3
    end
    
    style MAIN fill:#336791,color:#fff
    style SHARD fill:#00704A,color:#fff
```

---

## 5. Performance Architecture

### 5.1 Caching Strategy

```mermaid
flowchart TD
    subgraph "Cache Layers"
        CDN[CDN Cache<br/>Static Assets<br/>24hr TTL]
        L1[L1 Cache<br/>Redis<br/>5min TTL]
        L2[L2 Cache<br/>DB Query Cache<br/>1hr TTL]
    end
    
    subgraph "Cache Patterns"
        CP1[Cache Aside]
        CP2[Write Through]
        CP3[Write Behind]
    end
    
    REQ[Request] --> CDN
    CDN -->|Miss| L1
    L1 -->|Miss| L2
    L2 -->|Miss| DB[(Database)]
    
    DB --> CP1 & CP2 & CP3
    CP1 & CP2 & CP3 --> L1
    
    style CDN fill:#00704A,color:#fff
    style L1 fill:#dc382d,color:#fff
```

### 5.2 Load Balancing Architecture

```mermaid
graph TB
    subgraph "Global Load Balancing"
        R53[Route 53<br/>Geo Routing]
    end
    
    subgraph "Regional Load Balancing"
        ALB1[ALB US-East]
        ALB2[ALB US-West]
    end
    
    subgraph "Service Load Balancing"
        ISTIO1[Istio East<br/>Circuit Breaker]
        ISTIO2[Istio West<br/>Circuit Breaker]
    end
    
    subgraph "Database Load Balancing"
        PGB1[PgBouncer<br/>Connection Pool]
        PGB2[PgBouncer<br/>Connection Pool]
    end
    
    R53 --> ALB1 & ALB2
    ALB1 --> ISTIO1
    ALB2 --> ISTIO2
    ISTIO1 --> PGB1
    ISTIO2 --> PGB2
    
    style R53 fill:#ff9800,color:#fff
    style ISTIO1 fill:#1976d2,color:#fff
    style ISTIO2 fill:#1976d2,color:#fff
```

---

## 6. Monitoring and Observability

### 6.1 Monitoring Stack

```mermaid
flowchart LR
    subgraph "Data Collection"
        APP[Applications]
        SYS[System Metrics]
        LOG[Logs]
        TRACE[Traces]
    end
    
    subgraph "Processing"
        PROM[Prometheus]
        FLUENT[Fluentd]
        JAEGER[Jaeger]
    end
    
    subgraph "Storage"
        ELASTIC[Elasticsearch]
        INFLUX[InfluxDB]
    end
    
    subgraph "Visualization"
        GRAF[Grafana]
        KIB[Kibana]
        CUSTOM[Custom Dashboards]
    end
    
    APP & SYS --> PROM
    LOG --> FLUENT
    TRACE --> JAEGER
    
    PROM --> INFLUX
    FLUENT --> ELASTIC
    JAEGER --> ELASTIC
    
    INFLUX --> GRAF
    ELASTIC --> KIB
    INFLUX & ELASTIC --> CUSTOM
    
    style PROM fill:#e6522c,color:#fff
    style GRAF fill:#f46800,color:#fff
    style ELASTIC fill:#005571,color:#fff
```

### 6.2 Alert Flow

```mermaid
stateDiagram-v2
    [*] --> MetricCollection: Collect Metrics
    
    MetricCollection --> ThresholdCheck: Evaluate Rules
    
    ThresholdCheck --> Normal: Within Limits
    ThresholdCheck --> Warning: Approaching Limit
    ThresholdCheck --> Critical: Limit Exceeded
    
    Normal --> [*]
    
    Warning --> AlertManager: Send Warning
    Critical --> AlertManager: Send Alert
    
    AlertManager --> Routing: Route Alert
    
    Routing --> Email: Low Priority
    Routing --> Slack: Medium Priority
    Routing --> PagerDuty: High Priority
    
    PagerDuty --> OnCall: Page Engineer
    OnCall --> Investigate: Acknowledge
    Investigate --> Resolve: Fix Issue
    Resolve --> [*]
    
    Email --> [*]
    Slack --> [*]
```

---

## 7. Disaster Recovery Architecture

### 7.1 Backup Strategy

```mermaid
flowchart TD
    subgraph "Production Data"
        PROD_DB[(Production DB)]
        PROD_FILES[File Storage]
        PROD_CONFIG[Configurations]
    end
    
    subgraph "Backup Types"
        FULL[Full Backup<br/>Weekly]
        INCR[Incremental<br/>Daily]
        SNAP[Snapshots<br/>Hourly]
    end
    
    subgraph "Storage Locations"
        S3_SAME[S3 Same Region]
        S3_CROSS[S3 Cross Region]
        GLACIER[Glacier<br/>Long Term]
    end
    
    PROD_DB --> FULL & INCR & SNAP
    PROD_FILES --> FULL & INCR
    PROD_CONFIG --> SNAP
    
    FULL --> S3_SAME --> S3_CROSS --> GLACIER
    INCR --> S3_SAME --> S3_CROSS
    SNAP --> S3_SAME
    
    style FULL fill:#4caf50,color:#fff
    style S3_CROSS fill:#00704A,color:#fff
    style GLACIER fill:#1976d2,color:#fff
```

### 7.2 Failover Process

```mermaid
sequenceDiagram
    participant Monitor
    participant Health
    participant DNS
    participant Primary
    participant DR
    participant Users
    
    Monitor->>Health: Check Primary Health
    Health->>Primary: Health Check
    Primary--xHealth: No Response
    
    Health->>Monitor: Primary Down
    Monitor->>Monitor: Confirm Failure (3 checks)
    Monitor->>DNS: Initiate Failover
    
    DNS->>DNS: Update Records
    DNS->>DR: Route Traffic
    
    DR->>DR: Activate Services
    DR->>DR: Verify Data Sync
    
    Users->>DNS: Request
    DNS->>DR: Route to DR
    DR-->>Users: Service Response
    
    Note over Primary,DR: RTO: 15 minutes, RPO: 5 minutes
```

---

*End of System Architecture Document*