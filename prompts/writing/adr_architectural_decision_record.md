# Writing Prompt: Architecture Decision Record (ADR) Standardized Writer

## Purpose
Synthesize technical discussions, engineering trade-offs, and architectural choices into a standardized, clear Architecture Decision Record (ADR) following the Michael Nygard template.

## Inputs
- `DECISION_TITLE`: High-level architectural topic (e.g., Selecting Event Bus: Kafka vs RabbitMQ).
- `CONTEXT_AND_PROBLEM`: Problem statement, business drivers, constraints, and technical requirements.
- `OPTIONS_CONSIDERED`: List of architectural options evaluated during decision making.

## Instructions
1. Format document adhering strictly to standard ADR status headers (Title, Status, Context, Decision, Consequences).
2. Articulate the technical context, environmental constraints, and business drivers forcing a decision.
3. Detail every option considered, highlighting key architectural pros, cons, costs, and risks.
4. State the chosen decision clearly in active voice (e.g., "We will use Apache Kafka for...").
5. Outline positive and negative consequences resulting from the decision, including technical debt, operational overhead, and team training requirements.

## Constraints
- Frame decision rationale around objective engineering trade-offs rather than subjective preferences.
- Consequences section must contain both positive outcomes and negative trade-offs.

## Expected output
- **Standardized ADR Document**: Production-ready markdown ADR adhering to Nygard format.
- **Consequences & Trade-off Matrix**: Comprehensive evaluation of trade-offs and mitigation strategies.
