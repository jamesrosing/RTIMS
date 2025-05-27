# Database Schema Documentation
## Starbucks Real-Time Inventory Management System (RTIMS)

---

## 1. PostgreSQL Main Database Schema

### items
Primary table for tracking individual food items

```sql
CREATE TABLE items (
    item_id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    sku VARCHAR(50) NOT NULL,
    name VARCHAR(200) NOT NULL,
    category VARCHAR(50) NOT NULL,
    production_date TIMESTAMP NOT NULL,
    expiration_date TIMESTAMP NOT NULL,
    current_location_type VARCHAR(20) CHECK (current_location_type IN ('STORE', 'DC', 'TRANSIT')),
    current_location_id VARCHAR(50) NOT NULL,
    status VARCHAR(20) CHECK (status IN ('PRODUCED', 'IN_TRANSIT', 'IN_STORE', 'SOLD', 'WASTED')),
    blockchain_tx_hash VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    
    INDEX idx_sku (sku),
    INDEX idx_location (current_location_type, current_location_id),
    INDEX idx_status (status),
    INDEX idx_expiration (expiration_date)
);

-- Partitioned by month for scalability
CREATE TABLE items_2025_05 PARTITION OF items
    FOR VALUES FROM ('2025-05-01') TO ('2025-06-01');
```

### stores
Store information and configuration

```sql
CREATE TABLE stores (
    store_id VARCHAR(50) PRIMARY KEY,
    store_name VARCHAR(200) NOT NULL,
    address TEXT NOT NULL,
    timezone VARCHAR(50) NOT NULL,
    latitude DECIMAL(10, 8),
    longitude DECIMAL(11, 8),
    district_id VARCHAR(50),
    dc_id VARCHAR(50),
    operating_hours JSONB,
    capacity_limits JSONB,
    active BOOLEAN DEFAULT true,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```
### inventory_levels
Current inventory snapshot by store and SKU

```sql
CREATE TABLE inventory_levels (
    store_id VARCHAR(50),
    sku VARCHAR(50),
    current_quantity INTEGER NOT NULL DEFAULT 0,
    threshold_min INTEGER NOT NULL,
    threshold_optimal INTEGER NOT NULL,
    threshold_max INTEGER NOT NULL,
    threshold_confidence DECIMAL(3, 2),
    last_restocked TIMESTAMP,
    last_stockout TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    
    PRIMARY KEY (store_id, sku),
    FOREIGN KEY (store_id) REFERENCES stores(store_id)
);

-- Create materialized view for faster queries
CREATE MATERIALIZED VIEW inventory_summary AS
SELECT 
    store_id,
    COUNT(DISTINCT sku) as total_skus,
    SUM(CASE WHEN current_quantity < threshold_min THEN 1 ELSE 0 END) as low_stock_items,
    SUM(CASE WHEN current_quantity = 0 THEN 1 ELSE 0 END) as out_of_stock_items,
    MAX(updated_at) as last_update
FROM inventory_levels
GROUP BY store_id;

CREATE UNIQUE INDEX ON inventory_summary (store_id);
```

### transactions
Track all inventory transactions

```sql
CREATE TABLE transactions (
    transaction_id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    item_id UUID NOT NULL,
    transaction_type VARCHAR(20) NOT NULL CHECK (transaction_type IN ('SALE', 'RESTOCK', 'WASTE', 'TRANSFER')),
    store_id VARCHAR(50),
    quantity INTEGER NOT NULL,
    unit_price DECIMAL(10, 2),
    total_value DECIMAL(10, 2),
    pos_transaction_id VARCHAR(100),
    user_id VARCHAR(50),
    blockchain_tx_hash VARCHAR(100),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    
    FOREIGN KEY (item_id) REFERENCES items(item_id),
    INDEX idx_store_date (store_id, created_at),
    INDEX idx_type (transaction_type)
) PARTITION BY RANGE (created_at);
```
### orders
Supply chain orders

```sql
CREATE TABLE orders (
    order_id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    store_id VARCHAR(50) NOT NULL,
    dc_id VARCHAR(50) NOT NULL,
    order_type VARCHAR(20) CHECK (order_type IN ('AUTOMATIC', 'MANUAL', 'EMERGENCY')),
    status VARCHAR(20) CHECK (status IN ('PENDING', 'CONFIRMED', 'IN_TRANSIT', 'DELIVERED', 'CANCELLED')),
    created_by VARCHAR(50),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    confirmed_at TIMESTAMP,
    shipped_at TIMESTAMP,
    delivered_at TIMESTAMP,
    estimated_delivery TIMESTAMP,
    total_items INTEGER,
    total_value DECIMAL(10, 2),
    
    FOREIGN KEY (store_id) REFERENCES stores(store_id),
    INDEX idx_status (status),
    INDEX idx_store_created (store_id, created_at)
);
```

---

## 2. Time-Series Database (InfluxDB) Schema

### inventory_metrics
Real-time inventory metrics

```
measurement: inventory_metrics
tags:
  - store_id
  - sku
  - category
fields:
  - quantity (integer)
  - sales_velocity (float)
  - waste_rate (float)
  - stockout_duration (integer)
  - temperature (float)
  - humidity (float)
time: timestamp
```

### ml_predictions
ML model predictions

```
measurement: ml_predictions
tags:
  - store_id
  - sku
  - model_version
  - prediction_type (demand|waste|threshold)
fields:
  - predicted_value (float)
  - confidence (float)
  - actual_value (float)
  - error_rate (float)
time: timestamp
```
---

## 3. MongoDB Document Store Schema

### ml_features
Feature store for ML models

```javascript
{
  _id: ObjectId,
  store_id: String,
  sku: String,
  timestamp: ISODate,
  features: {
    historical: {
      avg_daily_sales_7d: Number,
      avg_daily_sales_30d: Number,
      avg_daily_sales_90d: Number,
      seasonality_index: Number,
      trend_coefficient: Number
    },
    external: {
      weather_forecast: {
        temperature: Number,
        precipitation: Number,
        conditions: String
      },
      local_events: [{
        event_name: String,
        distance_miles: Number,
        expected_attendance: Number,
        impact_score: Number
      }]
    },
    patterns: {
      day_of_week: [Number], // 7 values
      hour_of_day: [Number], // 24 values
      holiday_impact: Number
    }
  }
}
```

### audit_logs
Comprehensive audit trail

```javascript
{
  _id: ObjectId,
  timestamp: ISODate,
  user_id: String,
  action: String,
  entity_type: String,
  entity_id: String,
  changes: {
    before: Object,
    after: Object
  },
  metadata: {
    ip_address: String,
    user_agent: String,
    store_id: String,
    request_id: String
  }
}
```

---

## 4. Redis Cache Schema

### Keys Pattern

```
# Inventory levels
inventory:{store_id}:{sku} -> JSON object with current quantity and thresholds

# User sessions
session:{token} -> User session data

# ML predictions cache
prediction:{store_id}:{sku}:{type} -> Cached prediction with TTL

# Real-time alerts
alert:{store_id} -> List of active alerts

# Rate limiting
rate_limit:{user_id}:{endpoint} -> Request count
```