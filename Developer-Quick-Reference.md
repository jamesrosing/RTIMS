# Developer Quick Reference Guide
## Starbucks Real-Time Inventory Management System (RTIMS)

---

## 1. Local Development Setup

### Prerequisites
- Docker Desktop 4.0+
- Java 17
- Python 3.11
- Node.js 18+
- kubectl
- AWS CLI configured

### Quick Start
```bash
# Clone repository
git clone https://github.com/starbucks/rtims.git
cd rtims

# Start local infrastructure
docker-compose up -d

# Install dependencies
./scripts/install-deps.sh

# Run database migrations
./gradlew flywayMigrate

# Start services
./scripts/start-local.sh
```

---

## 2. API Examples

### Scan Item (POS Integration)
```bash
curl -X POST https://localhost:8080/api/v1/inventory/items/track \
  -H "Authorization: Bearer $TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "itemId": "550e8400-e29b-41d4-a716-446655440000",
    "action": "SOLD",
    "location": {
      "type": "STORE",
      "id": "STR-001"
    },
    "timestamp": "2025-05-26T10:30:00Z"
  }'
```

### Get Store Inventory
```bash
curl -X GET https://localhost:8080/api/v1/inventory/stores/STR-001 \
  -H "Authorization: Bearer $TOKEN"
```

### Trigger ML Prediction
```bash
curl -X GET https://localhost:8080/api/v1/analytics/predictions/STR-001?timeframe=7d \
  -H "Authorization: Bearer $TOKEN"
```
---

## 3. Common Development Tasks

### Running Tests
```bash
# Unit tests
./gradlew test

# Integration tests
./gradlew integrationTest

# End-to-end tests
npm run test:e2e

# Performance tests
artillery run tests/performance/load-test.yml
```

### Database Operations
```bash
# Generate new migration
./gradlew flywayMigrate -Pflyway.target=empty
./gradlew flywayGenerate -Pflyway.description="add_new_table"

# Reset local database
docker-compose down -v
docker-compose up -d postgres
./gradlew flywayMigrate
```

### Debugging
```bash
# Enable debug logging
export LOG_LEVEL=DEBUG

# Remote debugging (port 5005)
java -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=*:5005 -jar app.jar

# View container logs
docker-compose logs -f inventory-service

# Access service mesh dashboard
istioctl dashboard kiali
```

---

## 4. Code Standards

### Java Service Example
```java
@RestController
@RequestMapping("/api/v1/inventory")
@RequiredArgsConstructor
@Slf4j
public class InventoryController {
    
    private final InventoryService inventoryService;
    private final MetricService metricService;
    
    @PostMapping("/items/track")
    @Transactional
    public ResponseEntity<TrackingResponse> trackItem(
            @Valid @RequestBody TrackingRequest request) {
        
        log.debug("Tracking item: {}", request.getItemId());
        
        // Record metric
        metricService.recordItemScan(request.getStoreId());
        
        // Process tracking
        TrackingResponse response = inventoryService.trackItem(request);
        
        return ResponseEntity.status(HttpStatus.CREATED).body(response);
    }
}
```
### Python ML Service Example
```python
from fastapi import FastAPI, HTTPException
from typing import List, Dict
import numpy as np
from models import DemandForecastModel

app = FastAPI()
model = DemandForecastModel()

@app.post("/api/v1/ml/predict/demand")
async def predict_demand(
    store_id: str,
    sku: str,
    features: Dict[str, float]
) -> Dict[str, float]:
    try:
        # Prepare features
        feature_vector = np.array([
            features.get('avg_sales_7d', 0),
            features.get('seasonality_index', 1.0),
            features.get('weather_impact', 0),
            features.get('event_proximity', 0)
        ])
        
        # Generate prediction
        prediction = model.predict(feature_vector)
        confidence = model.predict_proba(feature_vector).max()
        
        return {
            "predicted_demand": float(prediction),
            "confidence": float(confidence),
            "model_version": model.version
        }
    except Exception as e:
        raise HTTPException(status_code=500, detail=str(e))
```

---

## 5. Troubleshooting

### Common Issues

**Issue: Service fails to start**
```bash
# Check logs
kubectl logs -n rtims-dev deployment/inventory-service

# Check resource limits
kubectl describe pod -n rtims-dev -l app=inventory-service

# Verify secrets
kubectl get secrets -n rtims-dev
```

**Issue: Database connection errors**
```bash
# Test connection
psql -h localhost -U rtims -d inventory

# Check connection pool
curl http://localhost:8080/actuator/metrics/hikaricp.connections.active
```

**Issue: Kafka consumer lag**
```bash
# Check consumer groups
kafka-consumer-groups --bootstrap-server localhost:9092 --list

# Check lag
kafka-consumer-groups --bootstrap-server localhost:9092 \
  --group inventory-consumer --describe
```

---

## 6. Useful Resources

- **Documentation:** https://wiki.starbucks.com/rtims
- **API Docs:** https://api-docs.rtims.starbucks.com
- **Monitoring:** https://grafana.rtims.starbucks.com
- **Support Slack:** #rtims-support

---

*End of Developer Guide*