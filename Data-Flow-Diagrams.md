# Data Flow Diagrams
## Starbucks Real-Time Inventory Management System (RTIMS)

---

## 1. Real-Time Sales Transaction Flow

```mermaid
sequenceDiagram
    participant Customer
    participant POS as Store POS
    participant RTIMS as RTIMS Core
    participant BC as Blockchain
    participant DC as Distribution Center
    participant Alert as Alert Manager
    
    Customer->>POS: Purchase Item
    activate POS
    POS->>POS: Scan QR Code
    POS->>RTIMS: Send Transaction<br/>(< 100ms)
    activate RTIMS
    
    par Inventory Update
        RTIMS->>RTIMS: Update Inventory
    and Blockchain Recording
        RTIMS->>BC: Record Transaction
        activate BC
        BC-->>RTIMS: Transaction Hash
        deactivate BC
    end
    
    RTIMS->>RTIMS: Check Thresholds
    
    alt Low Stock Detected
        RTIMS->>Alert: Generate Alert
        activate Alert
        Alert->>DC: Send Restock Request
        DC-->>Alert: Acknowledgment
        Alert-->>RTIMS: Alert Sent
        deactivate Alert
    end
    
    RTIMS-->>POS: Success Response
    deactivate RTIMS
    POS-->>Customer: Receipt
    deactivate POS
    
    Note over RTIMS,BC: Total processing time < 1 second
```

---

## 2. AI-Driven Restock Flow

```mermaid
flowchart TB
    subgraph "Data Sources"
        A[(Historical Data<br/>2+ Years)]
        B[Weather API]
        C[Events API]
        D[(Current Inventory)]
    end
    
    subgraph "Feature Pipeline"
        E[Data Ingestion<br/>Every 15 min]
        F[Feature Engineering]
        G[(Feature Store)]
    end
    
    subgraph "ML Models"
        H[Demand Forecast<br/>LSTM]
        I[Waste Prediction<br/>XGBoost]
        J[Threshold Optimizer<br/>PPO/RL]
    end
    
    subgraph "Decision Engine"
        K[Business Rules]
        L[Confidence Check]
        M[Human Override]
    end
    
    subgraph "Actions"
        N[Auto-Reorder]
        O[Store Alert]
        P[DC Notification]
    end
    
    A & B & C & D --> E
    E --> F
    F --> G
    G --> H & I & J
    H --> K
    I --> K
    J --> K
    K --> L
    L --> M
    M --> N & O & P
    
    style H fill:#e8f5e9
    style I fill:#e8f5e9
    style J fill:#e8f5e9
    style K fill:#00704A,color:#fff
    style N fill:#4caf50,color:#fff
    style O fill:#ff9800,color:#fff
```

---

## 3. Blockchain Transaction Flow

```mermaid
stateDiagram-v2
    [*] --> EventTriggered: Sale/Restock Event
    
    EventTriggered --> CreateTransaction: Generate Tx Data
    
    CreateTransaction --> ValidateData: Validate Format
    
    ValidateData --> BroadcastPeers: Valid
    ValidateData --> [*]: Invalid
    
    BroadcastPeers --> ConsensusProtocol: Send to Nodes
    
    ConsensusProtocol --> ValidateConsensus: Check Endorsements
    
    ValidateConsensus --> OrderTransaction: Consensus Reached
    ValidateConsensus --> BroadcastPeers: Retry
    
    OrderTransaction --> CreateBlock: Add to Block
    
    CreateBlock --> CommitLedger: Write to Ledger
    
    CommitLedger --> UpdateLocal: Update Local DB
    
    UpdateLocal --> [*]: Complete
    
    note right of ConsensusProtocol
        Byzantine Fault Tolerant
        Min 2/3 nodes agree
    end note
    
    note right of CreateBlock
        3-second block time
        Merkle tree structure
    end note
```

---

## 4. Supply Chain Integration Flow

```mermaid
graph TB
    subgraph "Store Operations"
        A[POS System]
        B[Store Manager App]
        C[Inventory Dashboard]
    end
    
    subgraph "RTIMS Core"
        D[API Gateway]
        E[Inventory Service]
        F[ML Service]
        G[Blockchain Service]
    end
    
    subgraph "Distribution Centers"
        H[DC System]
        I[Pick List Generator]
        J[Route Optimizer]
    end
    
    subgraph "External Systems"
        K[SAP Finance]
        L[Weather Service]
        M[Events Service]
    end
    
    A --> D
    B --> D
    C --> D
    
    D --> E
    D --> F
    D --> G
    
    E <--> H
    F --> I
    F --> J
    
    E <--> K
    F <--> L
    F <--> M
    
    style D fill:#00704A,color:#fff
    style E fill:#fff59d
    style F fill:#e8f5e9
    style G fill:#e3f2fd
```

---

## 5. ML Model Training Pipeline

```mermaid
flowchart LR
    subgraph "Data Collection"
        A[Sales Data]
        B[Inventory Data]
        C[External Data]
    end
    
    subgraph "Data Processing"
        D[Data Validation]
        E[Feature Engineering]
        F[Data Splitting]
    end
    
    subgraph "Model Training"
        G[Train Models]
        H[Hyperparameter Tuning]
        I[Cross Validation]
    end
    
    subgraph "Model Evaluation"
        J[Performance Metrics]
        K[A/B Testing]
        L[Business KPIs]
    end
    
    subgraph "Deployment"
        M[Model Registry]
        N[API Endpoint]
        O[Monitoring]
    end
    
    A & B & C --> D
    D --> E
    E --> F
    F --> G
    G --> H
    H --> I
    I --> J
    J --> K
    K --> L
    L -->|Approved| M
    L -->|Rejected| G
    M --> N
    N --> O
    O --> A
    
    style G fill:#4caf50,color:#fff
    style M fill:#00704A,color:#fff
```

---

## 6. Error Handling and Recovery Flow

```mermaid
flowchart TD
    A[Transaction Request] --> B{Validate Request}
    
    B -->|Valid| C[Process Transaction]
    B -->|Invalid| D[Return 400 Error]
    
    C --> E{Update Inventory}
    
    E -->|Success| F[Record to Blockchain]
    E -->|DB Error| G[Retry with Backoff]
    
    F --> H{Blockchain Commit}
    
    H -->|Success| I[Return Success]
    H -->|Timeout| J[Queue for Retry]
    
    G --> K{Retry Count}
    K -->|< 3| E
    K -->|>= 3| L[Dead Letter Queue]
    
    J --> M[Async Processor]
    M --> F
    
    L --> N[Manual Investigation]
    N --> O[Data Reconciliation]
    
    style D fill:#ff5252,color:#fff
    style G fill:#ff9800,color:#fff
    style I fill:#4caf50,color:#fff
    style L fill:#ff5252,color:#fff
```

---

## 7. Real-Time Dashboard Update Flow

```mermaid
sequenceDiagram
    participant UI as Dashboard UI
    participant WS as WebSocket Server
    participant Cache as Redis Cache
    participant DB as Database
    participant Event as Event Stream
    
    UI->>WS: Connect WebSocket
    WS->>UI: Connection Established
    
    loop Every Transaction
        Event->>WS: New Event
        WS->>Cache: Check Cache
        
        alt Cache Hit
            Cache-->>WS: Cached Data
        else Cache Miss
            WS->>DB: Query Data
            DB-->>WS: Fresh Data
            WS->>Cache: Update Cache
        end
        
        WS->>UI: Push Update
        UI->>UI: Update Display
    end
    
    Note over UI,WS: Updates within 100ms
```

---

## 8. Data Privacy and Compliance Flow

```mermaid
flowchart TB
    A[Raw Data] --> B{Contains PII?}
    
    B -->|Yes| C[Encryption Service]
    B -->|No| D[Standard Processing]
    
    C --> E[Tokenization]
    E --> F[Secure Storage]
    
    D --> G[Regular Storage]
    
    F --> H{Data Request}
    G --> H
    
    H --> I{Authorized?}
    
    I -->|Yes + PII| J[Decrypt Data]
    I -->|Yes + No PII| K[Return Data]
    I -->|No| L[Access Denied]
    
    J --> M[Audit Log]
    K --> M
    L --> M
    
    M --> N[Compliance Report]
    
    style C fill:#ff5252,color:#fff
    style F fill:#00704A,color:#fff
    style L fill:#ff5252,color:#fff
    style N fill:#4caf50,color:#fff
```

---

## 9. Store-to-DC Communication Flow

```mermaid
graph LR
    subgraph "Store Level"
        A[Inventory Level] --> B{Below Threshold?}
        B -->|Yes| C[Generate Order]
        B -->|No| D[Continue Monitoring]
    end
    
    subgraph "Order Processing"
        C --> E[Validate Order]
        E --> F[Check DC Stock]
        F --> G{Stock Available?}
    end
    
    subgraph "Distribution Center"
        G -->|Yes| H[Create Pick List]
        G -->|No| I[Backorder]
        H --> J[Schedule Delivery]
        I --> K[Notify Store]
    end
    
    subgraph "Delivery"
        J --> L[Load Truck]
        L --> M[In Transit]
        M --> N[Store Delivery]
        N --> O[Update Inventory]
    end
    
    O --> A
    K --> A
    
    style C fill:#ff9800,color:#fff
    style H fill:#4caf50,color:#fff
    style I fill:#ff5252,color:#fff
```

---

## 10. Performance Monitoring Flow

```mermaid
flowchart TD
    subgraph "Application Metrics"
        A[API Response Time]
        B[Database Query Time]
        C[Cache Hit Rate]
    end
    
    subgraph "Business Metrics"
        D[Inventory Accuracy]
        E[Stockout Rate]
        F[Waste Percentage]
    end
    
    subgraph "System Health"
        G[CPU Usage]
        H[Memory Usage]
        I[Network Latency]
    end
    
    A & B & C --> J[Prometheus]
    D & E & F --> J
    G & H & I --> J
    
    J --> K[Grafana Dashboards]
    J --> L[Alert Manager]
    
    L --> M{Threshold Breach?}
    
    M -->|Yes| N[PagerDuty]
    M -->|No| O[Log Event]
    
    N --> P[On-Call Engineer]
    P --> Q[Investigate Issue]
    Q --> R[Resolution]
    
    K --> S[Executive Dashboard]
    K --> T[Operations Dashboard]
    
    style J fill:#00704A,color:#fff
    style N fill:#ff5252,color:#fff
    style R fill:#4caf50,color:#fff
```

---

*End of Data Flow Diagrams*