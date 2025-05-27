# Diagram Conversion Examples
## From ASCII to Mermaid

This document shows examples of how the diagrams were converted from ASCII art to clean Mermaid format.

---

## Example 1: System Architecture

### Before (ASCII Art):
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
```

### After (Mermaid):
```mermaid
graph TB
    subgraph "Frontend Layer"
        A[Store POS]
        B[Mobile Apps]
        C[Web Dashboard]
    end
    
    subgraph "API Gateway"
        D[Kong API Gateway]
    end
    
    subgraph "Application Services"
        E[Core Services<br/>Java/Spring Boot]
        F[ML/AI Services<br/>Python/FastAPI]
        G[Blockchain Node<br/>Hyperledger]
    end
    
    A & B & C --> D
    D --> E & F & G
    
    style D fill:#00704A,color:#fff
```

---

## Example 2: Transaction Flow

### Before (ASCII Art):
```
┌─────────────┐     ┌──────────────┐     ┌─────────────┐
│   Customer  │     │  Store POS   │     │   RTIMS     │
└──────┬──────┘     └──────┬───────┘     └──────┬──────┘
       │                   │                     │
       │  Purchase Item    │                     │
       ├──────────────────>│                     │
       │                   │                     │
       │                   │  Scan QR Code       │
       │                   ├────────────────────>│
```

### After (Mermaid):
```mermaid
sequenceDiagram
    participant Customer
    participant POS as Store POS
    participant RTIMS as RTIMS Core
    
    Customer->>POS: Purchase Item
    POS->>POS: Scan QR Code
    POS->>RTIMS: Send Transaction<br/>(< 100ms)
    RTIMS-->>POS: Success Response
    POS-->>Customer: Receipt
```

---

## Benefits of Mermaid Diagrams

### 1. **Readability**
- Clear, professional appearance
- Consistent styling
- Easy to understand flow

### 2. **Maintainability**
- Text-based format
- Version control friendly
- Easy to update

### 3. **Flexibility**
- Multiple diagram types
- Customizable styling
- Export to various formats

### 4. **Integration**
- Works with GitHub/GitLab
- VS Code preview support
- Documentation tool compatibility

---

## Mermaid Syntax Quick Reference

### Flowchart
```mermaid
graph TD
    A[Start] --> B{Decision}
    B -->|Yes| C[Process]
    B -->|No| D[End]
```

### Sequence Diagram
```mermaid
sequenceDiagram
    Alice->>Bob: Hello
    Bob-->>Alice: Hi
```

### State Diagram
```mermaid
stateDiagram-v2
    [*] --> Active
    Active --> Inactive
    Inactive --> [*]
```

### Gantt Chart
```mermaid
gantt
    title Project Timeline
    section Phase 1
    Task 1  :a1, 2025-01-01, 30d
    Task 2  :after a1, 20d
```

---

## Styling with Mermaid

### Brand Colors
```mermaid
graph TD
    A[Starbucks Green]
    B[Success]
    C[Warning]
    D[Error]
    
    style A fill:#00704A,color:#fff
    style B fill:#4caf50,color:#fff
    style C fill:#ff9800,color:#fff
    style D fill:#ff5252,color:#fff
```

### Custom Themes
Mermaid supports custom themes and styling to match brand guidelines:
- Starbucks Green: `#00704A`
- Light Green: `#e8f5e9`
- Warning Orange: `#ff9800`
- Error Red: `#ff5252`

---

*All diagrams in the RTIMS documentation have been converted to this clean, maintainable format.*