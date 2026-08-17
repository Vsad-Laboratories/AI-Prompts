# Event Sourcing & CQRS Architectural Designer

## Purpose
Design a resilient, high-throughput Event Sourcing and Command Query Responsibility Segregation (CQRS) system architecture for complex domain bounded contexts, guaranteeing event append-only immutability, optimistic concurrency control, eventual consistency projections, and robust schema evolution.

## Inputs
- `DOMAIN_BOUNDED_CONTEXT`: Business requirements, aggregate boundaries, core entities, state transitions, and transactional volume expectations.
- `READ_WRITE_RATIO`: Target read/write load characteristics (e.g., 95:5 read-heavy vs 50:50 write-intensive).
- `INFRASTRUCTURE_TARGETS`: Target database and messaging technologies (e.g., EventStoreDB, PostgreSQL, Kafka, DynamoDB, Elasticsearch, Redis).

## Instructions
1. **Deconstruct Domain Aggregates**: Define aggregate root boundaries, consistency boundaries, state transitions, and business invariants within `DOMAIN_BOUNDED_CONTEXT`.
2. **Define Command & Event Contracts**:
   - **Commands**: Imperative requests representing intent (`CreateOrderCommand`, `CancelSubscriptionCommand`). Define validation rules, aggregate IDs, and payload schemas.
   - **Domain Events**: Immutable, past-tense facts (`OrderCreatedEvent`, `SubscriptionCanceledEvent`). Define event IDs, aggregate IDs, sequence versions, timestamps, payloads, and correlation/causation metadata.
3. **Architect Write-Side Event Store**:
   - Design an append-only event store schema supporting optimistic concurrency control (version checks on append).
   - Incorporate a Transactional Outbox pattern to guarantee at-least-once event delivery to message brokers without distributed two-phase commits.
4. **Architect Read-Side CQRS Projections**:
   - Design denormalized read-model schemas tailored to specific query patterns.
   - Define asynchronous projection processors that subscribe to the event stream and update read-side storage (e.g., PostgreSQL views, Elasticsearch documents).
5. **Architect Distributed Reliability Patterns**:
   - **Snapshotting Strategy**: Define snapshot triggers (e.g., every 100 events) to prevent infinite event replays during aggregate rehydration.
   - **Event Schema Evolution (Upcasting)**: Establish event versioning strategies (`OrderCreatedV1` $\rightarrow$ `OrderCreatedV2`) using event upcasters to transform historical events at deserialization time.
   - **Idempotency & Deduplication**: Guarantee projection idempotency when processing duplicate or out-of-order event streams.

## Constraints
- **Strict Event Immutability**: Events MUST NEVER be modified or deleted in place. Corrections require compensatory events (`OrderCancelledEvent`).
- **Optimistic Concurrency Control**: All write-side appends MUST validate `expected_aggregate_version`.
- **Absolute CQRS Separation**: Command handlers MUST NOT return read-model query projections. Query handlers MUST NOT mutate system state or append events.

## Expected Output Format
```markdown
### 1. Domain Aggregate & Command/Event Contracts
#### Commands
```json
{
  "command_name": "CreateOrderCommand",
  "aggregate_id": "UUID",
  "payload": { ... }
}
```

#### Domain Events
```json
{
  "event_id": "UUID",
  "event_type": "OrderCreatedEvent",
  "aggregate_id": "UUID",
  "aggregate_version": 1,
  "timestamp": "ISO-8601 UTC",
  "correlation_id": "UUID",
  "causation_id": "UUID",
  "payload": { ... }
}
```

### 2. Event Store Data Schema & Write Pipeline
```sql
-- Append-only Event Store Schema (PostgreSQL / SQL representation)
CREATE TABLE event_store (
    sequence_id BIGSERIAL PRIMARY KEY,
    aggregate_id UUID NOT NULL,
    aggregate_version INT NOT NULL,
    event_type VARCHAR(255) NOT NULL,
    payload JSONB NOT NULL,
    metadata JSONB NOT NULL,
    created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP,
    CONSTRAINT uq_aggregate_version UNIQUE (aggregate_id, aggregate_version)
);
```

### 3. Read-Side CQRS Projections & Pipeline Architecture
- **Target Projection Storage**: [Elasticsearch / PostgreSQL / Redis]
- **Event Consumer Protocol**: [Kafka Consumer Group / EventStoreDB Persistent Subscription]
- **Eventual Consistency SLA**: [Target latency, e.g., <50ms projection lag]

### 4. Schema Evolution & Snapshotting Strategy
- **Snapshot Frequency**: Every N events
- **Upcasting Pipeline**: [Deserialization transformer implementation logic]
```

## Evaluation Criteria
- **Architectural Separation**: Clean isolation between Command write models and Query read models.
- **Concurrency Robustness**: Prevents lost updates using optimistic concurrency version locks.
- **Scalability**: Projections scale horizontally independently of the event append pipeline.

## Failure Considerations
- **Event Store Mutation**: Attempting `UPDATE` operations on historical event rows.
- **Dual Write Anomaly**: Writing to the event store and publishing to Kafka outside a transactional outbox.
