# Coding Prompt: System Design Architect

## Purpose
Design high-performance, fault-tolerant, scalable, and secure system architectures for web applications or distributed microservices based on specific scaling requirements.

## Inputs
- `SYSTEM_REQUIREMENTS`: Functional and non-functional requirements (e.g., target active users, throughput, latency targets, geographical distribution).
- `CONSTRAINTS`: Hardware limitations, budget caps, compliance rules, or tech stack requirements.

## Instructions
1. Deconstruct `SYSTEM_REQUIREMENTS` into core service domains, data storage requirements, and communication protocols.
2. Select appropriate architectural patterns (e.g., Microservices, Event-Driven Architecture, CQRS) that satisfy the scale requirements.
3. Plan the data storage strategy, outlining when to use relational databases, NoSQL, in-memory caches, or object stores.
4. Design the system's fault-tolerance mechanism, including load balancing, redundancy, failover scenarios, and circuit breakers.
5. Create a detailed API boundary specification between core services.

## Constraints
- Ensure the proposed architecture is realistically implementable and does not over-engineer simple requirements.
- Maintain strict compliance with the security constraints mentioned in `CONSTRAINTS`.

## Expected output
- **High-Level Architectural Blueprint**: Text-based overview of the services, data flow, and key components.
- **Data Lifecycle & Storage Strategy**: Specific database selections, schema structures, and caching layers.
- **Scalability & Resiliency Protocols**: Load balancing, partitioning, replication, and disaster recovery strategies.
- **Service API Specifications**: Key endpoints, request/response formats, and communication models.
