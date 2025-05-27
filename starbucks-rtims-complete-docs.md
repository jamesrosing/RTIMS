# Starbucks Real-Time Inventory Management System (RTIMS)
## Complete Technical Documentation Suite

**Version:** 1.0  
**Date:** May 26, 2025  
**Document Type:** Unified Technical Documentation

---

# Table of Contents

1. [Product Requirements Document (PRD)](#1-product-requirements-document-prd)
2. [API Specifications](#2-api-specifications)
3. [Data Flow Diagrams](#3-data-flow-diagrams)
4. [Database Schema Documentation](#4-database-schema-documentation)
5. [Integration Specifications](#5-integration-specifications)
6. [System Architecture Document](#6-system-architecture-document)
7. [Deployment and CI/CD Guide](#7-deployment-and-cicd-guide)
8. [Developer Quick Reference](#8-developer-quick-reference)

---

# 1. Product Requirements Document (PRD)

## Executive Summary

The Starbucks Real-Time Inventory Management System (RTIMS) represents a transformative leap in supply chain management, addressing critical inefficiencies that currently cost Starbucks an estimated $50-75 million annually in lost revenue. This proprietary, blockchain-enabled, AI-driven platform will fundamentally reimagine how Starbucks tracks, manages, and optimizes its food inventory across all 17,000 stores globally.

### The Current Challenge

Today's inventory system operates on a 72-hour reporting cycle that creates dangerous blind spots in our supply chain. When a store sells out of croissants at 10 AM on Monday, the system doesn't register this stockout until Thursday. During this three-day window, the store reports zero sales of croissants—not because customers don't want them, but because they're simply unavailable. This delayed visibility creates a cascade of problems:

- **Lost Revenue**: Customers who can't find their preferred food items often leave without making any purchase, impacting both food and beverage sales
- **Customer Dissatisfaction**: Regular customers change their routines when their favorite items are consistently unavailable
- **Operational Inefficiency**: Store managers resort to over-ordering to prevent stockouts, leading to increased waste
- **Data Corruption**: The 72-hour delay corrupts demand signals, making accurate forecasting nearly impossible

### The RTIMS Solution

RTIMS eliminates these blind spots through real-time, item-level tracking powered by cutting-edge technology:

1. **Zero-Latency Architecture**: Every food item receives a unique QR code identifier that updates our central system within 1 second of sale
2. **AI-Driven Intelligence**: Machine learning models analyze 15+ data sources to predict demand with >85% accuracy
3. **Blockchain Transparency**: Immutable ledger technology ensures complete supply chain visibility and trust
4. **Automated Response**: Dynamic thresholds trigger automatic reordering before stockouts occur

### Quantifiable Business Impact

**Key Value Propositions with Detailed Financial Impact:**

**1. Elimination of 48-72 Hour Stockout Blind Spots**
- **Current State**: Average store experiences 15-20 stockout events monthly, each lasting 2.5 days
- **Future State**: Real-time visibility reduces stockout duration to <4 hours
- **Financial Impact**: $50-75M annual revenue recovery from prevented lost sales
- **Customer Impact**: 95% reduction in "item not available" customer experiences

**2. AI-Driven Dynamic Threshold Management**
- **Current State**: Static reorder points based on historical averages, 65% accuracy
- **Future State**: ML models adjust thresholds every 15 minutes based on 15+ variables
- **Financial Impact**: $30-40M savings from optimized inventory levels
- **Operational Impact**: 60% reduction in manual inventory management time

**3. Complete Supply Chain Transparency via Blockchain**
- **Current State**: Limited visibility into product journey, manual reconciliation
- **Future State**: End-to-end tracking from production to sale with immutable audit trail
- **Financial Impact**: $10-15M savings from reduced shrinkage and improved accountability
- **Compliance Impact**: 100% traceability for food safety regulations

**4. 15-20% Reduction in Food Waste**
- **Current State**: 8-10% of food products expire or are damaged before sale
- **Future State**: Predictive algorithms optimize inventory levels and rotation
- **Financial Impact**: $25-35M annual savings from reduced waste
- **Sustainability Impact**: 5,000 tons less food waste, supporting ESG goals

**5. 8-12% Increase in Food Sales Revenue**
- **Current State**: Food represents 20% of total revenue with significant untapped potential
- **Future State**: Consistent availability drives increased attach rates and customer satisfaction
- **Financial Impact**: $400-600M additional annual revenue
- **Strategic Impact**: Positions Starbucks as a legitimate food destination

### Implementation Strategy

The system will be deployed through a carefully orchestrated 18-month rollout:
- **Months 1-3**: Foundation and pilot testing with mock stores
- **Months 4-6**: AI/ML integration with 50 store pilot
- **Months 7-9**: Blockchain implementation across 200 stores
- **Months 10-12**: Regional expansion to 1,000 stores
- **Months 13-18**: National rollout to all 17,000 stores

### Technology Innovation

RTIMS leverages best-in-class technologies while maintaining cost efficiency:
- **QR Codes over RFID**: 95% cost savings ($0.02 vs $0.50 per tag) without sacrificing reliability
- **Cloud-Native Architecture**: Auto-scaling reduces infrastructure costs by 40% during off-peak hours
- **Open-Source Foundation**: Strategic use of proven technologies reduces licensing costs by $2M annually

### Risk Mitigation

The phased approach minimizes implementation risk:
- **Progressive Rollout**: Each phase validates technology and processes before expansion
- **Backward Compatibility**: Legacy POS systems continue functioning during transition
- **Human Oversight**: AI recommendations can be overridden by experienced managers
- **Proven Technologies**: No bleeding-edge dependencies that could jeopardize stability

### Success Metrics

Clear, measurable objectives ensure accountability:
- **Technical**: 99.9% inventory accuracy, <5 second update latency
- **Business**: 90% stockout reduction, 15% waste reduction
- **Financial**: ROI within 18 months, $500M+ total economic benefit
- **Customer**: 4.5+ star satisfaction rating for food availability

### Competitive Advantage

RTIMS positions Starbucks as the industry leader in supply chain innovation:
- **First-Mover**: No competitor has real-time, item-level tracking at this scale
- **Data Moat**: AI models trained on Starbucks-specific data create insurmountable advantage
- **Platform Potential**: Technology could be licensed to other retailers for additional revenue
- **Talent Attraction**: Cutting-edge technology attracts top engineering talent

This investment in RTIMS is not merely an operational upgrade—it's a strategic transformation that will redefine what customers expect from quick-service restaurants and position Starbucks for the next decade of growth.

## Product Overview and Objectives

### Problem Statement
Current POS systems update inventory data in 72-hour windows, causing stores that sell out of food items to show zero sales for 2-3 days while awaiting restocking. This results in:
- Lost revenue (estimated $50-75M annually across 17,000 stores)
- Poor customer experience
- Inefficient distribution center operations
- Excessive food waste from overstocking as compensation

### Solution Overview
A real-time, AI-powered inventory management system with:
- Zero-latency tracking of individual food items
- Predictive analytics for demand forecasting
- Blockchain-secured supply chain transparency
- Automated restock triggering with dynamic thresholds
- Progressive rollout capability with POS backward compatibility

### Success Criteria
- 99.9% inventory accuracy
- <5 second latency from sale to system update
- 90% reduction in stockout duration
- 15% reduction in food waste
- ROI within 18 months

## Target Users and Stakeholders

### Primary Users

**Store Managers (17,000 users)**
- Access: Web dashboard + mobile app
- Key functions: Real-time inventory visibility, manual order override, waste tracking
- Success metric: 80% daily active usage

**Distribution Center Staff (500 users)**
- Access: Web dashboard + mobile app + warehouse terminals
- Key functions: Pick list optimization, delivery scheduling, quality control
- Success metric: 25% efficiency improvement

**Supply Chain Engineers/Analysts (100 users)**
- Access: Advanced web dashboard
- Key functions: Analytics, ML model tuning, system optimization
- Success metric: Predictive accuracy >85%

**C-Level Executives (20 users)**
- Access: Strategic dashboards (web + mobile)
- Key functions: KPI monitoring, ROI tracking, strategic decision support
- Success metric: Weekly engagement

## Core Features and Functionality

### Real-Time Inventory Tracking
**Description:** Track every food item with unique identifiers from production to sale

**Technical Requirements:**
- Unique identifier generation system (QR codes recommended)
- POS integration for zero-latency updates
- Event streaming architecture (Apache Kafka or AWS Kinesis)
- In-memory data processing for sub-second response

**Acceptance Criteria:**
- Each food item has scannable unique identifier
- Sale events transmitted within 1 second
- System handles 700 transactions/store/day (12M total)
- 99.99% uptime during business hours

### AI-Powered Dynamic Thresholds
**Description:** Machine learning models that automatically adjust reorder points based on multiple factors

**Technical Requirements:**
- Historical sales data ingestion (minimum 2 years)
- Real-time feature engineering pipeline
- ML model serving infrastructure (TensorFlow Serving or AWS SageMaker)
- A/B testing framework for model improvements

**Features to Include:**
- Weather-based demand forecasting
- Local event detection and adjustment
- Seasonal pattern recognition
- Day-of-week and time-of-day optimization
- Shelf life consideration

**Acceptance Criteria:**
- Models retrain daily with latest data
- Threshold recommendations achieve >85% accuracy
- Manual override capability preserved
- Explainable AI dashboard for threshold reasoning

### Blockchain Supply Chain Transparency
**Description:** Immutable ledger tracking all inventory movements and transactions

**Technical Requirements:**
- Permissioned blockchain (Hyperledger Fabric recommended)
- Smart contracts for automated processes
- Integration with existing financial systems
- Secure key management infrastructure

**Blockchain Data Model:**
```
Block Structure:
- Block Header
  - Previous block hash
  - Timestamp
  - Merkle root
- Transaction Data
  - Item ID
  - Location (store/DC)
  - Transaction type (produced/shipped/received/sold/wasted)
  - Quantity
  - Quality metrics
  - Digital signatures
```

**Acceptance Criteria:**
- All supply chain participants have blockchain nodes
- Transaction finality within 3 seconds
- Complete audit trail for every item
- Compliance with SOC 2 and food safety standards

### Predictive Analytics Suite
**Description:** Advanced analytics for waste reduction and demand optimization

**Core Algorithms:**
- Demand Forecasting: LSTM neural networks with attention mechanisms
- Waste Prediction: Gradient boosting with shelf-life features
- Route Optimization: Modified VRP with time windows
- Quality Prediction: Random forest with sensor data integration

**Acceptance Criteria:**
- Forecast accuracy within 10% margin of error
- Waste predictions 24-48 hours in advance
- Route optimization reduces delivery time by 15%
- Dashboard updates every 15 minutes

### Multi-Platform User Interfaces
**Description:** Responsive web and native mobile applications

**Technical Specifications:**
- Frontend: React 18+ with TypeScript
- Mobile: React Native for iOS/Android
- State Management: Redux Toolkit with RTK Query
- UI Component Library: Custom design system
- Real-time updates: WebSocket connections

**Key Screens:**
- Real-time inventory dashboard
- Predictive analytics view
- Order management interface
- Alert and notification center
- Historical reporting tools

## Technical Architecture and Stack

### Recommended Technology Stack

**Backend Services:**
- Language: Java 17+ (Spring Boot 3.x) for core services
- Python 3.11+ for ML/AI services
- Message Queue: Apache Kafka
- Cache: Redis Cluster
- Search: Elasticsearch

**Databases:**
- Primary: PostgreSQL 15+ with partitioning
- Time-series: InfluxDB for metrics
- Document Store: MongoDB for unstructured data
- Blockchain: Hyperledger Fabric 2.5+

**Infrastructure:**
- Cloud: AWS (primary) with multi-region deployment
- Container Orchestration: Kubernetes (EKS)
- Service Mesh: Istio
- API Gateway: Kong or AWS API Gateway

**Security Stack:**
- Identity Provider: Okta or Auth0
- Secrets Management: HashiCorp Vault
- Encryption: AES-256 for data at rest, TLS 1.3 for transit

### System Architecture Diagram
```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│   Store POS     │     │  Mobile Apps    │     │  Web Dashboard  │
└────────┬────────┘     └────────┬────────┘     └────────┬────────┘
         │                       │                         │
         └───────────────────────┴─────────────────────────┘
                                 │
                        ┌────────▼────────┐
                        │  API Gateway    │
                        └────────┬────────┘
                                 │
        ┌────────────────────────┼────────────────────────┐
        │                        │                        │
┌───────▼────────┐     ┌─────────▼────────┐     ┌────────▼────────┐
│ Core Services  │     │  ML/AI Services  │     │ Blockchain Node │
└───────┬────────┘     └─────────┬────────┘     └────────┬────────┘
        │                        │                         │
        └────────────────────────┴─────────────────────────┘
                                 │
                        ┌────────▼────────┐
                        │  Message Queue  │
                        └────────┬────────┘
                                 │
                        ┌────────▼────────┐
                        │   Data Layer    │
                        └─────────────────┘
```

## Data Model and System Design

### Core Entities

**Item**
```javascript
{
  itemId: string (UUID),
  sku: string,
  name: string,
  category: string,
  productionDate: timestamp,
  expirationDate: timestamp,
  currentLocation: string,
  status: enum ['produced', 'in_transit', 'in_store', 'sold', 'wasted'],
  qualityMetrics: {
    temperature: number[],
    humidity: number[]
  },
  blockchainTxHash: string
}
```

**Store Inventory**
```javascript
{
  storeId: string,
  itemCounts: Map<sku, quantity>,
  thresholds: Map<sku, {
    minimum: number,
    optimal: number,
    maximum: number,
    confidence: float
  }>,
  lastUpdated: timestamp,
  pendingOrders: Order[]
}
```

**ML Feature Store**
```javascript
{
  storeId: string,
  sku: string,
  features: {
    avgDailySales: number,
    seasonalityIndex: float,
    weatherImpact: float,
    eventProximity: float,
    dayOfWeekPattern: number[],
    shelfLifeRemaining: number
  },
  lastCalculated: timestamp
}
```

## Security and Compliance Requirements

### Security Standards
- **SOC 2 Type II Compliance:** Annual audit requirement
- **PCI DSS Level 1:** For payment data integration
- **Food Safety Compliance:** FDA Food Safety Modernization Act
- **Data Privacy:** CCPA, GDPR compliance for international operations

### Security Implementation
- **Encryption:** AES-256 at rest, TLS 1.3 in transit
- **Authentication:** Multi-factor authentication for all users
- **Authorization:** Role-based access control (RBAC)
- **Audit Logging:** Complete audit trail with blockchain integration
- **Vulnerability Management:** Monthly security scans, quarterly penetration testing

## AI/ML Capabilities

### Demand Forecasting Model
**Architecture:** LSTM with attention mechanisms
**Input Features:**
- Historical sales (2 years minimum)
- Weather data (temperature, precipitation, forecast)
- Local events calendar
- Store location demographics
- Day/time patterns
- Holiday calendar

**Output:** 7-day hourly demand forecast per SKU per store

### Dynamic Threshold Optimization
**Architecture:** Reinforcement Learning (PPO algorithm)
**Objective Function:** Minimize (stockout_cost + waste_cost + holding_cost)
**Action Space:** Threshold adjustments per SKU
**State Space:** Current inventory, forecasted demand, shelf life

### Waste Prediction Model
**Architecture:** XGBoost with custom loss function
**Features:**
- Current inventory levels
- Remaining shelf life
- Historical waste patterns
- Upcoming demand forecast
- Temperature excursions

**Output:** Probability of waste within 24/48 hours

### Route Optimization
**Algorithm:** Modified Vehicle Routing Problem with Time Windows
**Constraints:**
- Delivery time windows
- Vehicle capacity
- Driver hours regulations
- Traffic patterns

**Output:** Optimized delivery routes reducing time by 15%+

## Integration Requirements

### POS System Integration
- **Protocol:** REST API with webhook notifications
- **Data Format:** JSON with Avro schema registry
- **Latency:** <100ms for transaction updates
- **Backward Compatibility:** Support legacy XML format during transition

### Financial System Integration
- **System:** SAP integration via middleware
- **Sync Frequency:** Real-time for transactions, batch for reconciliation
- **Data Elements:** Cost centers, GL codes, inventory valuation

### External Integrations (Future Phase)
- Weather API (NOAA or Weather.com)
- Event APIs (Ticketmaster, local event systems)
- Traffic APIs (Google Maps, HERE)

## User Interface Design Principles

### Design System Requirements
- **Accessibility:** WCAG 2.1 AA compliance
- **Responsive Design:** Mobile-first approach
- **Brand Consistency:** Starbucks design language
- **Performance:** <3 second page load time

### Key UI Components
- Real-time data visualization (D3.js or Chart.js)
- Alert system with priority levels
- Drag-and-drop order management
- Interactive forecasting tools
- Mobile barcode scanning interface

## Hardware and Infrastructure

### Tracking Technology Choice
Based on cost-effectiveness analysis, **QR codes** are recommended over RFID:
- Cost: $0.01-0.05 per label vs $0.10-1.00 for RFID
- Implementation: Uses existing smartphone cameras
- Reliability: 99.9% scan success rate
- No special hardware required at stores

### Infrastructure Requirements
- **Data Centers:** AWS us-east-1 (primary), us-west-2 (DR)
- **CDN:** CloudFront for static assets
- **Monitoring:** Datadog or New Relic
- **Backup:** Daily snapshots, 30-day retention

## Development Phases and Milestones

### Phase 1: Foundation (Months 1-3)
- Core infrastructure setup
- Basic inventory tracking
- POS integration prototype
- Mock store testing
- **Deliverable:** Working prototype with 5 pilot stores

### Phase 2: AI/ML Integration (Months 4-6)
- Demand forecasting models
- Dynamic threshold system
- Historical data ingestion
- Model training pipeline
- **Deliverable:** AI-powered system in 50 stores

### Phase 3: Blockchain Implementation (Months 7-9)
- Hyperledger Fabric setup
- Smart contract development
- Supply chain partner onboarding
- Security audit
- **Deliverable:** Blockchain-enabled tracking in 200 stores

### Phase 4: Regional Rollout (Months 10-12)
- Scale to 1,000 stores
- Performance optimization
- User training programs
- Feedback incorporation
- **Deliverable:** Full regional deployment

### Phase 5: National Deployment (Months 13-18)
- Progressive rollout to all 17,000 stores
- 24/7 support establishment
- Continuous improvement cycle
- **Deliverable:** Complete system replacement

## Success Metrics and KPIs

### Technical KPIs
- System uptime: >99.95%
- Transaction latency: <100ms average
- Forecast accuracy: >85%
- API response time: <200ms p99

### Business KPIs
- Stockout reduction: 90%
- Food waste reduction: 15%
- Revenue increase: 8-12%
- ROI achievement: <18 months

### User Adoption Metrics
- Daily active users: >80% of store managers
- Mobile app usage: >60% of transactions
- Training completion: 100% before go-live
- User satisfaction: >4.5/5.0

## Risk Analysis and Mitigation

### Technical Risks
**Risk:** Integration complexity with legacy POS
- **Mitigation:** Adapter pattern, extensive testing, gradual rollout

**Risk:** ML model accuracy in new markets
- **Mitigation:** Transfer learning, continuous retraining, human oversight

**Risk:** Blockchain scalability
- **Mitigation:** Channel segregation, off-chain processing, performance testing

### Business Risks
**Risk:** User adoption resistance
- **Mitigation:** Comprehensive training, change management, incentive programs

**Risk:** Data quality issues during migration
- **Mitigation:** Data validation frameworks, reconciliation processes

## Cost Optimization Strategies

### Infrastructure Optimization
- Auto-scaling for 40% cost reduction during off-hours
- Reserved instances for predictable workloads
- Spot instances for batch processing
- Data lifecycle management with tiered storage

### Operational Optimization
- Automated testing reducing QA costs by 60%
- Self-service analytics reducing support tickets
- Predictive maintenance preventing downtime
- Open-source alternatives where appropriate

## Future Expansion Possibilities

### Additional Features (Post-Launch)
- Customer demand prediction based on app pre-orders
- Dynamic pricing integration
- Supplier quality scoring
- Carbon footprint tracking
- Automated reordering with suppliers
- Predictive equipment maintenance

### Platform Extensions
- Integration with customer mobile app
- Third-party marketplace for suppliers
- API platform for partner integrations
- International expansion capabilities
- Multi-tenant SaaS offering for other retailers

### Advanced Analytics
- Customer behavior analysis
- Store performance optimization
- Network effect analysis
- Competitive intelligence integration
- Economic indicator correlation

---

# 2. API Specifications

## Authentication Endpoints

### POST /auth/login
Authenticate user and receive access token

**Request Body:**
```json
{
  "email": "string",
  "password": "string",
  "storeId": "string (optional for store-specific login)"
}
```

**Response 200:**
```json
{
  "accessToken": "string",
  "refreshToken": "string",
  "expiresIn": 3600,
  "tokenType": "Bearer",
  "user": {
    "id": "string",
    "email": "string",
    "role": "string",
    "permissions": ["string"]
  }
}
```

### POST /auth/refresh
Refresh access token

**Request Body:**
```json
{
  "refreshToken": "string"
}
```

**Response 200:**
```json
{
  "accessToken": "string",
  "expiresIn": 3600
}
```

## Inventory Management Endpoints

### GET /inventory/stores/{storeId}
Get real-time inventory for a specific store

**Path Parameters:**
- `storeId` (string, required): Store identifier

**Query Parameters:**
- `category` (string, optional): Filter by product category
- `lowStock` (boolean, optional): Only return items below threshold
- `includeMetrics` (boolean, optional): Include AI predictions

**Response 200:**
```json
{
  "storeId": "string",
  "lastUpdated": "2025-05-26T10:30:00Z",
  "items": [
    {
      "sku": "string",
      "name": "string",
      "category": "string",
      "currentQuantity": 150,
      "threshold": {
        "minimum": 20,
        "optimal": 50,
        "maximum": 100,
        "confidence": 0.92
      },
      "predictedDemand": {
        "next24Hours": 45,
        "next7Days": 280,
        "accuracy": 0.87
      },
      "shelfLife": {
        "averageRemaining": 48,
        "expiringToday": 5,
        "expiringTomorrow": 12
      }
    }
  ],
  "alerts": [
    {
      "type": "LOW_STOCK",
      "sku": "string",
      "severity": "HIGH",
      "message": "Croissants below minimum threshold",
      "actionRequired": "REORDER"
    }
  ]
}
```

### POST /inventory/items/track
Track individual item (scan event)

**Request Body:**
```json
{
  "itemId": "string (UUID)",
  "action": "PRODUCED|SHIPPED|RECEIVED|SOLD|WASTED",
  "location": {
    "type": "STORE|DC|TRANSIT",
    "id": "string"
  },
  "timestamp": "2025-05-26T10:30:00Z",
  "metadata": {
    "temperature": 4.5,
    "scannedBy": "string (userId)",
    "posTransactionId": "string (optional)"
  }
}
```

**Response 201:**
```json
{
  "trackingId": "string",
  "itemId": "string",
  "blockchainTxHash": "string",
  "status": "CONFIRMED",
  "timestamp": "2025-05-26T10:30:00Z"
}
```

### PUT /inventory/thresholds
Update inventory thresholds (manual override)

**Request Body:**
```json
{
  "storeId": "string",
  "adjustments": [
    {
      "sku": "string",
      "threshold": {
        "minimum": 25,
        "optimal": 60,
        "maximum": 120
      },
      "reason": "SEASONAL_ADJUSTMENT|MANUAL_OVERRIDE|EVENT_BASED",
      "expiresAt": "2025-06-01T00:00:00Z (optional)"
    }
  ]
}
```

**Response 200:**
```json
{
  "updated": 3,
  "adjustments": [
    {
      "sku": "string",
      "previousThreshold": {...},
      "newThreshold": {...},
      "aiRecommendation": {...}
    }
  ]
}
```

## Supply Chain Endpoints

### GET /supply-chain/orders/{orderId}
Get order details and tracking

**Response 200:**
```json
{
  "orderId": "string",
  "status": "PENDING|CONFIRMED|IN_TRANSIT|DELIVERED",
  "createdAt": "2025-05-26T08:00:00Z",
  "estimatedDelivery": "2025-05-27T06:00:00Z",
  "items": [
    {
      "sku": "string",
      "quantity": 100,
      "unitCost": 2.50,
      "expirationDate": "2025-05-30T00:00:00Z"
    }
  ],
  "route": {
    "dcId": "string",
    "storeId": "string",
    "distance": 45.2,
    "estimatedTime": 90,
    "driver": "string"
  },
  "blockchainTracking": [
    {
      "event": "ORDER_CREATED",
      "timestamp": "2025-05-26T08:00:00Z",
      "txHash": "string"
    }
  ]
}
```

### POST /supply-chain/orders
Create new inventory order

**Request Body:**
```json
{
  "storeId": "string",
  "type": "AUTOMATIC|MANUAL|EMERGENCY",
  "items": [
    {
      "sku": "string",
      "quantity": 100,
      "urgency": "NORMAL|HIGH|CRITICAL"
    }
  ],
  "deliveryWindow": {
    "earliest": "2025-05-27T05:00:00Z",
    "latest": "2025-05-27T10:00:00Z"
  }
}
```

## Analytics Endpoints

### GET /analytics/predictions/{storeId}
Get AI predictions for store

**Query Parameters:**
- `timeframe` (string): "24h|7d|30d"
- `metrics` (array): ["demand","waste","stockout"]

**Response 200:**
```json
{
  "storeId": "string",
  "predictions": {
    "demand": {
      "timeframe": "7d",
      "items": [
        {
          "sku": "string",
          "predictedQuantity": 450,
          "confidence": 0.89,
          "factors": {
            "weather": 0.15,
            "seasonality": 0.30,
            "events": 0.05,
            "historical": 0.50
          }
        }
      ]
    },
    "waste": {
      "estimatedItems": 23,
      "estimatedValue": 145.67,
      "topRiskItems": ["sku1", "sku2"]
    }
  }
}
```

### GET /analytics/performance
Get system performance metrics

**Response 200:**
```json
{
  "metrics": {
    "inventoryAccuracy": 0.992,
    "stockoutReduction": 0.87,
    "wasteReduction": 0.15,
    "forecastAccuracy": 0.86
  },
  "systemHealth": {
    "uptime": 0.9995,
    "avgLatency": 87,
    "transactionsProcessed": 12450000
  }
}
```

## Webhook Events

### Inventory Alert Webhook
**Event:** `inventory.alert`
**Payload:**
```json
{
  "eventId": "string",
  "timestamp": "2025-05-26T10:30:00Z",
  "type": "inventory.alert",
  "data": {
    "storeId": "string",
    "alertType": "LOW_STOCK|EXPIRING|STOCKOUT",
    "items": [
      {
        "sku": "string",
        "currentQuantity": 5,
        "threshold": 20,
        "action": "REORDER_SUGGESTED"
      }
    ]
  }
}
```

### Transaction Completed Webhook
**Event:** `transaction.completed`
**Payload:**
```json
{
  "eventId": "string",
  "timestamp": "2025-05-26T10:30:00Z",
  "type": "transaction.completed",
  "data": {
    "transactionId": "string",
    "storeId": "string",
    "items": [
      {
        "itemId": "string",
        "sku": "string",
        "price": 4.95
      }
    ],
    "blockchainTxHash": "string"
  }
}
```

## Error Responses

All endpoints follow consistent error response format:

**Error Response:**
```json
{
  "error": {
    "code": "INVALID_REQUEST|UNAUTHORIZED|NOT_FOUND|CONFLICT|INTERNAL_ERROR",
    "message": "Human-readable error message",
    "details": {
      "field": "Additional context"
    },
    "requestId": "string",
    "timestamp": "2025-05-26T10:30:00Z"
  }
}
```

**HTTP Status Codes:**
- 200: Success
- 201: Created
- 400: Bad Request
- 401: Unauthorized
- 403: Forbidden
- 404: Not Found
- 409: Conflict
- 429: Rate Limited
- 500: Internal Server Error

---

# 3. Data Flow Diagrams

## Real-Time Sales Transaction Flow

```
┌─────────────┐     ┌──────────────┐     ┌─────────────┐     ┌──────────────┐
│   Customer  │     │  Store POS   │     │   RTIMS     │     │  Blockchain  │
└──────┬──────┘     └──────┬───────┘     └──────┬──────┘     └──────┬───────┘
       │                   │                     │                    │
       │  Purchase Item    │                     │                    │
       ├──────────────────>│                     │                    │
       │                   │                     │                    │
       │                   │  Scan QR Code       │                    │
       │                   ├────────────────────>│                    │
       │                   │                     │                    │
       │                   │                     │ Update Inventory   │
       │                   │                     ├───────────────────>│
       │                   │                     │                    │
       │                   │                     │ Record Transaction │
       │                   │                     ├──────────────────>│
       │                   │                     │                    │
       │                   │                     │<─────────────────┤
       │                   │                     │   Tx Hash         │
       │                   │                     │                    │
       │                   │ Transaction Success │                    │
       │                   │<────────────────────┤                    │
       │                   │                     │                    │
       │  Receipt          │                     │ Check Thresholds  │
       │<──────────────────┤                     ├──────────┐        │
       │                   │                     │          │        │
       │                   │                     │<─────────┘        │
       │                   │                     │                    │
       │                   │                     │ Alert if Low Stock │
       │                   │                     ├──────────┐        │
       │                   │                     │          │        │
       │                   │                     │          ▼        │
       │                   │                     │    Distribution    │
       │                   │                     │      Center        │
```

**Key Steps:**
1. Customer purchases item at POS
2. POS scans unique QR code on item
3. Transaction sent to RTIMS in real-time (<100ms)
4. Inventory updated immediately
5. Transaction recorded on blockchain
6. System checks if inventory below AI threshold
7. Automatic alert sent to distribution center if needed

## AI-Driven Restock Flow

```
┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│  Historical  │     │   Weather    │     │    Events    │     │   Current    │
│    Data      │     │     API      │     │     API      │     │  Inventory   │
└──────┬───────┘     └──────┬───────┘     └──────┬───────┘     └──────┬───────┘
       │                    │                    │                    │
       └────────────────────┴────────────────────┴────────────────────┘
                                        │
                                        ▼
                            ┌───────────────────────┐
                            │   Feature Pipeline    │
                            │  (Data Processing)    │
                            └───────────┬───────────┘
                                        │
                                        ▼
                            ┌───────────────────────┐
                            │    ML Models          │
                            │ - Demand Forecast     │
                            │ - Waste Prediction    │
                            │ - Threshold Optimizer │
                            └───────────┬───────────┘
                                        │
                                        ▼
                            ┌───────────────────────┐
                            │  Decision Engine      │
                            │  (Business Rules)     │
                            └───────────┬───────────┘
                                        │
                        ┌───────────────┴───────────────┐
                        ▼                               ▼
                ┌──────────────┐               ┌──────────────┐
                │ Auto-Reorder │               │    Alert     │
                │   Trigger    │               │   Manager    │
                └──────┬───────┘               └──────┬───────┘
                       │                              │
                       ▼                              ▼
                ┌──────────────┐               ┌──────────────┐
                │ Distribution │               │Store Manager │
                │   Center     │               │  Dashboard   │
                └──────────────┘               └──────────────┘
```

**ML Pipeline Details:**
- Runs every 15 minutes
- Processes last 2 years of historical data
- Incorporates real-time external factors
- Generates 7-day rolling forecasts
- Updates dynamic thresholds based on confidence levels

## Blockchain Transaction Flow

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   Event     │     │  RTIMS      │     │ Blockchain  │     │   Other     │
│  (Sale/     │     │  Core       │     │  Service    │     │   Nodes     │
│  Restock)   │     │             │     │             │     │             │
└──────┬──────┘     └──────┬──────┘     └──────┬──────┘     └──────┬──────┘
       │                   │                    │                   │
       │  Trigger Event    │                    │                   │
       ├──────────────────>│                    │                   │
       │                   │                    │                   │
       │                   │ Create Transaction │                   │
       │                   ├───────────────────>│                   │
       │                   │                    │                   │
       │                   │                    │ Validate Data     │
       │                   │                    ├─────────┐         │
       │                   │                    │         │         │
       │                   │                    │<────────┘         │
       │                   │                    │                   │
       │                   │                    │ Broadcast to Peers│
       │                   │                    ├──────────────────>│
       │                   │                    │                   │
       │                   │                    │ Consensus Protocol│
       │                   │                    │<─────────────────>│
       │                   │                    │                   │
       │                   │                    │ Add to Block      │
       │                   │                    ├─────────┐         │
       │                   │                    │         │         │
       │                   │                    │<────────┘         │
       │                   │                    │                   │
       │                   │  Transaction Hash  │                   │
       │                   │<───────────────────┤                   │
       │                   │                    │                   │
       │                   │ Update Local DB    │                   │
       │                   ├─────────┐          │                   │
       │                   │         │          │                   │
       │                   │<────────┘          │                   │
```

**Blockchain Details:**
- Hyperledger Fabric 2.5+
- 3-second block time
- Byzantine Fault Tolerant consensus
- Smart contracts for automated verification

---

# 4. Database Schema Documentation

## PostgreSQL Main Database Schema

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

## Time-Series Database (InfluxDB) Schema

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

## MongoDB Document Store Schema

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

## Redis Cache Schema

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

---

# 5. Integration Specifications

## POS System Integration

### Real-Time Transaction Interface

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

### Legacy POS Adapter

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

## SAP Financial System Integration

### Real-Time Interface

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

### Reconciliation Process

**Daily Reconciliation Job**
- Runs at 2 AM local time
- Compares RTIMS totals with SAP
- Generates discrepancy reports
- Auto-corrects minor differences (<$100)
- Flags major discrepancies for review

## External API Integrations

### Weather API Integration

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

### Events API Integration

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

## Blockchain Network Integration

### Hyperledger Fabric Configuration

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

### Integration Security

**Key Management:**
- Hardware Security Modules (HSM) for private keys
- Key rotation every 90 days
- Separate keys per organization

**Access Control:**
- Certificate-based authentication
- Role-based channel access
- Transaction endorsement policies

---

# 6. System Architecture Document

## High-Level Architecture Overview

### System Components

```
┌─────────────────────────────────────────────────────────────────────┐
│                          External Systems                             │
│  ┌─────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐            │
│  │Weather  │  │ Events   │  │   SAP    │  │   POS    │            │
│  │  APIs   │  │  APIs    │  │  System  │  │ Systems  │            │
│  └────┬────┘  └────┬─────┘  └────┬─────┘  └────┬─────┘            │
└───────┼────────────┼──────────────┼──────────────┼──────────────────┘
        │            │              │              │
┌───────▼────────────▼──────────────▼──────────────▼──────────────────┐
│                        Integration Layer                              │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐              │
│  │ API Gateway  │  │  Message     │  │  Adapter     │              │
│  │   (Kong)     │  │  Queue       │  │  Services    │              │
│  └──────┬───────┘  │  (Kafka)     │  └──────────────┘              │
│         │          └──────┬────────┘                                │
└─────────┼─────────────────┼──────────────────────────────────────────┘
          │                 │
┌─────────▼─────────────────▼──────────────────────────────────────────┐
│                     Application Services Layer                        │
│  ┌───────────┐  ┌───────────┐  ┌───────────┐  ┌───────────┐       │
│  │Inventory  │  │  ML/AI    │  │Blockchain │  │Analytics  │       │
│  │ Service   │  │ Service   │  │  Service  │  │ Service   │       │
│  └─────┬─────┘  └─────┬─────┘  └─────┬─────┘  └─────┬─────┘       │
│        │              │              │              │               │
│  ┌─────▼──────────────▼──────────────▼──────────────▼─────┐        │
│  │                  Service Mesh (Istio)                    │        │
│  └──────────────────────────────────────────────────────────┘        │
└──────────────────────────────────────────────────────────────────────┘
                                    │
┌───────────────────────────────────▼──────────────────────────────────┐
│                         Data Layer                                    │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐           │
│  │PostgreSQL│  │InfluxDB  │  │ MongoDB  │  │  Redis   │           │
│  │(Primary) │  │(Metrics) │  │(Features)│  │ (Cache)  │           │
│  └──────────┘  └──────────┘  └──────────┘  └──────────┘           │
└──────────────────────────────────────────────────────────────────────┘
```

### Deployment Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                     AWS Multi-Region Deployment                      │
│                                                                      │
│  ┌──────────────────────────┐    ┌──────────────────────────┐      │
│  │   US-East-1 (Primary)    │    │  US-West-2 (DR Site)     │      │
│  │                          │    │                          │      │
│  │  ┌────────────────┐      │    │  ┌────────────────┐      │      │
│  │  │  EKS Cluster   │      │    │  │  EKS Cluster   │      │      │
│  │  │  (Production)  │      │    │  │   (Standby)    │      │      │
│  │  └────────────────┘      │    │  └────────────────┘      │      │
│  │                          │    │                          │      │
│  │  ┌────────────────┐      │    │  ┌────────────────┐      │      │
│  │  │   RDS Multi-AZ │◄─────┼────┼──┤  RDS Read      │      │      │
│  │  │   PostgreSQL   │      │    │  │  Replica       │      │      │
│  │  └────────────────┘      │    │  └────────────────┘      │      │
│  │                          │    │                          │      │
│  └──────────────────────────┘    └──────────────────────────┘      │
│                                                                      │
│  ┌─────────────────────────────────────────────────────────┐       │
│  │                    CloudFront CDN                         │       │
│  │              (Global Content Delivery)                    │       │
│  └─────────────────────────────────────────────────────────┘       │
└─────────────────────────────────────────────────────────────────────┘
```

## Microservices Architecture

### Core Services

**Inventory Service**
- Language: Java 17 with Spring Boot 3.x
- Responsibilities:
  - Real-time inventory tracking
  - Threshold management
  - Stock level monitoring
  - Order generation
- Database: PostgreSQL (primary), Redis (cache)
- API: REST + GraphQL
- Scaling: Horizontal auto-scaling based on CPU/memory

**ML/AI Service**
- Language: Python 3.11 with FastAPI
- Responsibilities:
  - Demand forecasting
  - Waste prediction
  - Dynamic threshold optimization
  - Feature engineering
- ML Stack: TensorFlow, XGBoost, scikit-learn
- Database: MongoDB (features), InfluxDB (predictions)
- Scaling: GPU-enabled instances for training

**Blockchain Service**
- Language: Go 1.20
- Framework: Hyperledger Fabric SDK
- Responsibilities:
  - Transaction recording
  - Supply chain transparency
  - Smart contract execution
  - Consensus management
- Infrastructure: Dedicated nodes per organization
- Scaling: Vertical scaling for orderer nodes

**Analytics Service**
- Language: Python + Scala (for Spark jobs)
- Responsibilities:
  - Real-time dashboards
  - Historical reporting
  - Performance metrics
  - Business intelligence
- Stack: Apache Spark, Databricks
- Database: Data Lake (S3) + Athena

### Service Communication

```
┌─────────────┐     gRPC      ┌─────────────┐
│  Inventory  ├───────────────►│    ML/AI    │
│   Service   │                │   Service   │
└──────┬──────┘                └──────┬──────┘
       │                              │
       │         Event Bus            │
       └──────────┐    ┌──────────────┘
                  ▼    ▼
            ┌──────────────┐
            │    Kafka     │
            │   Topics:    │
            │ - inventory  │
            │ - predictions│
            │ - alerts     │
            └──────────────┘
```

## Security Architecture

### Security Layers

```
┌─────────────────────────────────────────────────────────────┐
│                    Security Perimeter                        │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐        │
│  │    WAF      │  │   DDoS      │  │   IDS/IPS   │        │
│  │(CloudFlare) │  │ Protection  │  │  (AWS Guard)│        │
│  └──────┬──────┘  └──────┬──────┘  └──────┬──────┘        │
│         │                 │                 │               │
│  ┌──────▼─────────────────▼─────────────────▼──────┐       │
│  │              API Gateway (Kong)                   │       │
│  │  - Rate Limiting                                 │       │
│  │  - OAuth 2.0 Authentication                      │       │
│  │  - Request Validation                            │       │
│  └───────────────────┬──────────────────────────────┘       │
│                      │                                       │
│  ┌───────────────────▼──────────────────────────────┐       │
│  │           Service Mesh (Istio)                    │       │
│  │  - mTLS between services                         │       │
│  │  - RBAC policies                                 │       │
│  │  - Traffic encryption                            │       │
│  └───────────────────────────────────────────────────┘       │
└─────────────────────────────────────────────────────────────┘
```

### Data Security

**Encryption Standards:**
- At Rest: AES-256-GCM
- In Transit: TLS 1.3
- Key Management: AWS KMS with HSM
- Database: Transparent Data Encryption (TDE)

**Access Control:**
- Identity Provider: Okta SSO
- MFA: Required for all admin access
- Service Accounts: Short-lived tokens (15 minutes)
- API Keys: Rotating every 30 days

## Performance Architecture

### Caching Strategy

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   Client    │     │   CDN       │     │   API       │
│  Request    ├────►│  (Static)   ├────►│  Gateway    │
└─────────────┘     └─────────────┘     └──────┬──────┘
                                               │
                                        ┌──────▼──────┐
                                        │Redis Cache  │
                                        │  L1 Cache   │
                                        └──────┬──────┘
                                               │ Miss
                                        ┌──────▼──────┐
                                        │Application  │
                                        │  Service    │
                                        └──────┬──────┘
                                               │
                                        ┌──────▼──────┐
                                        │  Database   │
                                        │  (L2 Cache) │
                                        └─────────────┘
```

**Cache Layers:**
- CDN: Static assets, 24-hour TTL
- Redis L1: Hot data, 5-minute TTL
- Database L2: Query results, 1-hour TTL

### Load Balancing

- Global: Route 53 with geolocation routing
- Regional: Application Load Balancer (ALB)
- Service: Istio with circuit breakers
- Database: PgBouncer connection pooling

## Monitoring and Observability

### Monitoring Stack

```
Application Metrics → Prometheus → Grafana
Application Logs → Fluentd → Elasticsearch → Kibana
Distributed Tracing → Jaeger
Business Metrics → Custom Dashboards → Datadog
```

### Key Metrics

**System Health:**
- API response time (p50, p95, p99)
- Error rate by service
- Database connection pool usage
- Message queue lag

**Business Metrics:**
- Inventory accuracy by store
- Stockout frequency
- Waste percentage
- Forecast accuracy

---

# 7. Deployment and CI/CD Guide

## CI/CD Pipeline Architecture

### Pipeline Overview

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

### Build Pipeline Configuration

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

## Kubernetes Deployment

### Deployment Configuration

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
              key: db-password
        resources:
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

### Service Configuration

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

## Deployment Strategies

### Progressive Rollout Strategy

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

### Blue-Green Deployment

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

## Rollback Procedures

### Automated Rollback

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

### Manual Rollback Process

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

## Monitoring and Alerts

### Deployment Monitoring

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

# 8. Developer Quick Reference

## Local Development Setup

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

## API Examples

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

## Common Development Tasks

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

## Code Standards

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

## Troubleshooting

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

## Useful Resources

- **Documentation:** https://wiki.starbucks.com/rtims
- **API Docs:** https://api-docs.rtims.starbucks.com
- **Monitoring:** https://grafana.rtims.starbucks.com
- **Support Slack:** #rtims-support

---

## Summary

This comprehensive technical documentation provides everything needed to build and deploy the Starbucks Real-Time Inventory Management System. The system will:

1. **Eliminate stockouts** through real-time tracking and AI-driven predictions
2. **Reduce waste** by 15% through better demand forecasting
3. **Increase revenue** by 8-12% through improved availability
4. **Provide transparency** via blockchain technology
5. **Scale efficiently** to 17,000 stores

The phased rollout approach ensures risk mitigation while the modular architecture allows for future expansion and enhancement.

**Next Steps:**
1. Review documentation with all stakeholders
2. Finalize technology choices with infrastructure team
3. Begin Phase 1 development
4. Establish success metrics monitoring
5. Plan change management program

For questions or clarifications, please contact the RTIMS project team.