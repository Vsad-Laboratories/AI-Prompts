# Asynchronous Decision Memo & RFC Writer

## Purpose
Synthesize complex technical trade-offs, architectural proposals, organizational choices, or product direction decisions into a structured, persuasive, and asynchronous Request for Comments (RFC) / Executive Decision Memo designed for cross-functional alignment.

## Inputs
- `PROPOSED_DECISION`: Core hypothesis or architectural choice requiring organizational approval.
- `TECHNICAL_CONTEXT`: Existing infrastructure, constraints, current pain points, and strategic goals.
- `ALTERNATIVES_CONSIDERED`: List of competing vendor, framework, or architectural options evaluated.
- `KEY_STAKEHOLDERS`: Primary decision makers (e.g., CTO, VP Engineering, Security Lead, Product Manager).

## Instructions
1. **Apply Minto Pyramid Principle**: State the executive summary, primary recommendation, and bottom-line impact immediately in the first section before detailing supporting evidence.
2. **Structure the Problem Statement**: Articulate the current state pain points, technical debt risks, and business costs of maintaining the status quo.
3. **Detail Proposed Architecture / Solution**: Explain the proposed direction with clear system diagrams, data flow descriptions, API contracts, and implementation timelines.
4. **Construct Multi-Dimensional Trade-Off Matrix**: Compare the proposed option against `ALTERNATIVES_CONSIDERED` across standardized evaluation axes:
   - Implementation Effort & Complexity
   - Financial Cost (OpEx/CapEx)
   - Operational Maintenance Burden
   - Scalability & Performance SLAs
   - Security & Compliance Impact
5. **Detail Anti-Goals & Explicit Out-of-Scope Items**: Define explicit boundaries to prevent scope creep during review loops.
6. **Address Frequently Asked Questions (FAQ) & Objections**: Proactively answer predictable stakeholder objections (e.g., migration downtime, team learning curves, vendor lock-in).

## Constraints
- **Self-Contained Readability**: The document MUST be fully understandable asynchronously without requiring a meeting.
- **Explicit Recommendation**: The memo MUST take a firm, defensible stance rather than presenting a neutral list without guidance.
- **Quantified Business Metrics**: Include specific ROI, latency, or cost figures wherever applicable.

## Expected Output Format
```markdown
# RFC-104: Migration to Event-Driven Microservice Architecture

## Executive Summary & Recommendation
- **Core Recommendation**: Adopt Apache Kafka as the central event bus to decouple monolithic synchronous REST dependencies.
- **Key Business Impact**: Reduces checkout service P99 latency from 850ms to 120ms and eliminates single-point-of-failure cascade outages.
- **Estimated Effort**: 3 Engineering Sprints (6 weeks).

## Problem Statement & Pain Points
- Current monolithic architecture suffers from cascading HTTP timeouts during peak flash sales.
- Database connection pool exhaustion causes 99.9% SLA breaches twice per quarter.

## Multi-Dimensional Alternatives Comparison
| Evaluation Axis | Proposed: Apache Kafka | Alternative A: RabbitMQ | Alternative B: AWS SQS/SNS |
| :--- | :--- | :--- | :--- |
| **Throughput (msg/sec)** | High (>100k) | Medium (~30k) | High (Serverless) |
| **Event Replayability** | Native (Log Retention) | Limited (DLQ only) | Limited |
| **Monthly Cost ($)** | $1,200/mo (MSK) | $800/mo | $450/mo |
| **Operational Overhead**| Low (Managed MSK) | Medium | Zero (Serverless) |

## Implementation Roadmap & Anti-Goals
### In Scope
- Transactional Outbox implementation for Order Service.
- Event Schema Registry setup using Protobuf.

### Anti-Goals (Out of Scope)
- Rewriting secondary back-office admin tools to event consumers during Phase 1.

## Stakeholder FAQ & Risk Mitigation
- **Q: How do we handle duplicate message processing?**
  - *A: All event consumers will implement Redis-based deduplication keys enforcing strict idempotency.*
```

## Evaluation Criteria
- **Argumentation Clarity**: Follows a top-down logical hierarchy state recommendation upfront.
- **Trade-Off Rigor**: Evaluates competing options objectively across cost, effort, and performance.
- **Asynchronous Completeness**: Proactively addresses stakeholder objections to drive consensus without meetings.

## Failure Considerations
- **Wishy-Washy Stance**: Presenting options without explicitly advocating for a primary recommendation.
- **Hidden Trade-offs**: Omitting operational downsides or migration risks of the proposed choice.
