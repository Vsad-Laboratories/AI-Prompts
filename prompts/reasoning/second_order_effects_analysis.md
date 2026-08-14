# Reasoning Prompt: Second-Order Effects Analysis

## Purpose
Forecast and map the indirect, long-term, systemic, and unintended consequences of complex business or technical decisions.

## Inputs
- `PRIMARY_DECISION`: The immediate policy change, architectural shift, or business strategy being evaluated (e.g., migrating to remote-only work, deprecating a legacy API, or banning a material).
- `SYSTEM_ENVIRONMENT_DETAILS`: Description of the market, software system, or organizational culture where this decision will be implemented.

## Instructions
1. Define the immediate, direct (first-order) results of implementing `PRIMARY_DECISION`.
2. Trace the ripple effects of those first-order results: What do these changes trigger in related subsystems, competitor behavior, or customer sentiment? (Second-order effects).
3. Project further down the timeline to map third-order (long-term structural changes) and systemic feedback loops.
4. Identify counter-intuitive, self-defeating, or adversarial reactions to the decision (e.g., Cobra Effect or Jevons Paradox).
5. Propose diagnostic measures and guardrails to monitor and mitigate negative systemic feedback loops.

## Constraints
- Focus on logical, high-probability connections rather than far-fetched, speculative domino theories.
- All forecasted effects must be rooted in the specific dynamics described in `SYSTEM_ENVIRONMENT_DETAILS`.

## Expected output
- **First-to-Third-Order Cascade Map**: Structured visual or nested outline tracing the downstream progression of effects.
- **Systemic Feedback Loop Analysis**: Narrative of reinforcing (+) and balancing (-) feedback cycles.
- **High-Risk Unintended Consequences**: Warning guide detailing counter-intuitive or self-defeating risks.
- **Strategic Guardrails & KPIs**: Specific telemetry metrics and design patterns to stabilize the system.
