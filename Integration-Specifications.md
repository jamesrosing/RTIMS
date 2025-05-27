# Integration Specifications
## Starbucks Real-Time Inventory Management System (RTIMS)

---

## 1. POS System Integration

### 1.1 Real-Time Transaction Interface

**Protocol:** REST API with WebSocket fallback  
**Format:** JSON with Avro schema validation  
**Authentication:** OAuth 2.0 with rotating API keys

#### Transaction Event Structure
```json
{
  "eventType": "SALE",
  "timestamp": "2025-05-26T10:30:45.123Z",
  "storeId": "STR-001",
  "registerId": "REG-003",
  "transactionId": "TRX-123456789",
  "items": [
    {
      "itemId": "550e8400-e29b-41d4-a716-446655440000",
      "sku": "FOOD-CROIS-001",
      "quantity": 1,
      "price": 4.95,
      "discounts": []
    }
  ],
  "payment": {
    "method": "CREDIT_CARD",
    "amount": 4.95,
    "status": "APPROVED"
  }
}
```

#### Integration Flow
1. POS scans item QR code
2. Validates item against RTIMS
3. Processes payment
4. Sends transaction event
5. Receives acknowledgment with blockchain hash

### 1.2 Legacy POS Adapter

**Purpose:** Support 72-hour batch systems during transition  
**Architecture:** Message queue with transformation layer

```
Legacy POS → XML Batch → Adapter Service → JSON Events → RTIMS
```

**Transformation Rules:**
- XML to JSON conversion
- Batch to real-time event streaming
- Historical data backfill capability
- Duplicate detection and handling
---

## 2. SAP Financial System Integration

### 2.1 Real-Time Interface

**Protocol:** SAP PI/PO middleware  
**Format:** IDoc and RFC  
**Sync Frequency:** Real-time for critical, batch for reconciliation

#### Integration Points

**Inventory Valuation Sync**
```
RTIMS → SAP PI → SAP ECC
- Material movements (MB51)
- Inventory valuation (MB5B)
- Cost center updates
```

**Financial Posting Structure**
```xml
<FinancialPosting>
  <Header>
    <PostingDate>2025-05-26</PostingDate>
    <DocumentType>WA</DocumentType>
    <CompanyCode>SBUX</CompanyCode>
  </Header>
  <Items>
    <Item>
      <MaterialNumber>FOOD-CROIS-001</MaterialNumber>
      <Quantity>100</Quantity>
      <Amount>250.00</Amount>
      <CostCenter>CC-STR-001</CostCenter>
      <GLAccount>500100</GLAccount>
    </Item>
  </Items>
</FinancialPosting>
```

### 2.2 Reconciliation Process

**Daily Reconciliation Job**
- Runs at 2 AM local time
- Compares RTIMS totals with SAP
- Generates discrepancy reports
- Auto-corrects minor differences (<$100)
- Flags major discrepancies for review
---

## 3. External API Integrations

### 3.1 Weather API Integration

**Provider:** NOAA Weather Service API  
**Backup Provider:** Weather.com API  
**Update Frequency:** Every 4 hours  
**Data Points:**
- Current temperature
- 7-day forecast
- Precipitation probability
- Severe weather alerts

```python
# Weather API Request Example
GET https://api.weather.gov/gridpoints/SEW/124,67/forecast
Authorization: Bearer {api_key}

# Transform for ML Pipeline
{
  "store_id": "STR-001",
  "weather_data": {
    "current_temp": 72,
    "forecast_7d": [
      {"date": "2025-05-27", "high": 75, "low": 60, "precipitation": 0.1}
    ],
    "weather_impact_score": 0.15
  }
}
```

### 3.2 Events API Integration

**Primary Provider:** Ticketmaster API  
**Secondary Providers:** Local event calendars  
**Update Frequency:** Daily  
**Radius:** 5 miles from store

```python
# Events API Request
GET https://app.ticketmaster.com/discovery/v2/events
?apikey={api_key}
&latlong=47.6062,-122.3321
&radius=5
&unit=miles
&startDateTime=2025-05-26T00:00:00Z

# Event Impact Calculation
event_impact = (expected_attendance / 1000) * (1 / distance_miles) * category_weight
```
---

## 4. Blockchain Network Integration

### 4.1 Hyperledger Fabric Configuration

**Network Topology:**
- 3 Organization setup (Stores, DCs, Corporate)
- 2 Peers per organization
- 3 Orderer nodes (Raft consensus)
- 1 Channel for supply chain

**Smart Contract Functions:**
```javascript
// Record inventory transaction
async recordTransaction(ctx, itemId, transactionType, quantity, location) {
  const transaction = {
    itemId,
    transactionType,
    quantity,
    location,
    timestamp: new Date().toISOString(),
    transactionId: ctx.stub.getTxID()
  };
  
  await ctx.stub.putState(itemId, Buffer.from(JSON.stringify(transaction)));
  return transaction;
}

// Query item history
async queryItemHistory(ctx, itemId) {
  const iterator = await ctx.stub.getHistoryForKey(itemId);
  const history = [];
  
  while (true) {
    const result = await iterator.next();
    if (result.done) break;
    history.push(JSON.parse(result.value.toString()));
  }
  
  return history;
}
```

### 4.2 Integration Security

**Key Management:**
- Hardware Security Modules (HSM) for private keys
- Key rotation every 90 days
- Separate keys per organization

**Access Control:**
- Certificate-based authentication
- Role-based channel access
- Transaction endorsement policies