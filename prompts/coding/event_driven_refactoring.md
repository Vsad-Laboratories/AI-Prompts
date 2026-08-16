# Coding Prompt: Monolith to Event-Driven Architecture Refactoring Guide

## Purpose
Guide engineers through refactoring tightly coupled, synchronous monolithic application code into an asynchronous, event-driven architecture.

## Inputs
- `MONOLITH_CODE`: Monolithic application source code or module specifications.
- `EVENT_BUS_TECH`: Target messaging broker (e.g., Apache Kafka, RabbitMQ, AWS EventBridge).

## Instructions
1. Identify synchronous function calls and tight coupling points within `MONOLITH_CODE`.
2. Deconstruct blocking function chains into Domain Events, Event Producers, and Event Consumers.
3. Design event schemas including event types, metadata headers, idempotency IDs, and payload bodies.
4. Apply the Transactional Outbox Pattern to guarantee atomic database updates and event publishing.
5. Provide refactored code demonstrating asynchronous event publishing and resilient consumer handling.

## Constraints
- Ensure transactional integrity using Outbox/CDC patterns rather than dual-writes.
- Include dead-letter queue (DLQ) retry strategies for consumer handling failures.

## Expected output
- **Domain Event Identification Matrix**: Catalog of extracted events and trigger conditions.
- **Event Schema Specifications**: Standardized JSON/Avro event format schemas.
- **Refactored Code Implementation**: Transactional outbox writer and consumer logic snippets.
