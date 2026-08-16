# Coding Prompt: Distributed Transaction & Saga Pattern Architect

## Purpose
Design resilient, eventually consistent distributed transaction mechanisms using the Saga Pattern (Orchestration or Choreoography) for microservice architectures.

## Inputs
- `BUSINESS_WORKFLOW`: High-level distributed process description (e.g., e-commerce checkout involving Inventory, Payment, and Shipping services).
- `SAGA_TYPE`: Execution preference (`Orchestration` vs `Choreography`).
- `CONSISTENCY_REQUIREMENTS`: Allowed latency, isolation constraints, and idempotency guarantees.

## Instructions
1. Break down `BUSINESS_WORKFLOW` into discrete, atomic local transactions across participating microservices.
2. Define corresponding "Compensating Transactions" for every local transaction to handle partial failures gracefully.
3. Architecture the Saga sequence diagram flow for both success and failure paths.
4. Establish idempotency controls, deduplication key strategies, and message delivery guarantees (At-least-once vs Exactly-once).
5. Provide concrete implementation snippets or event payload schemas for orchestration/choreography execution.

## Constraints
- Every local transaction modifying state MUST have an explicit, idempotent compensating transaction.
- Clearly address out-of-order message delivery and duplicate event consumption.

## Expected output
- **Saga Workflow Architecture**: Step-by-step transaction and compensation mapping.
- **Service Interaction Contract**: Event schemas and gRPC/REST message definitions.
- **Failure Recovery Protocols**: Detailed compensation execution trees for edge-case errors.
- **Code/Schema Implementation**: Sample orchestrator state machine or event handlers.
