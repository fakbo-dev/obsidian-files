# {{title}}

**Created**: {{date}}
**Scale**: <expected QPS/users>
**Tags**: #system-design #architecture

## Requirements

1. **Functional**:
   -
2. **Non-Functional**:
   -

## Capacity Estimation

- **Traffic**:
- **Storage**:
- **Bandwidth**:

## High-Level Design

```mermaid
graph LR
    Client --> LB[Load Balancer]
    LB --> Service1
    LB --> Service2
    Service1 --> DB[(Database)]
```

## Components Deep Dive

### 1. <Component Name>

- **Responsibility**:
- **Interface**:

```proto
service ComponentName {
    rpc Method(Request) returns (Response);
}
```

## Data Storage

```mermaid
erDiagram
    USER ||--o{ POST : creates
    USER {
        string userId PK
        string name
    }
```

## Tradeoffs

| Option | Pros | Cons |
| ------ | ---- | ---- |
|        |      |      |
