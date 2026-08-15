# Planning Prompt: Technical Debt Valuation and Prioritization Matrix

## Purpose
Quantify, evaluate, and prioritize accumulated technical debt items against business roadmap features, balancing operational risks against feature delivery speed.

## Inputs
- `TECH_DEBT_BACKLOG`: List of technical debt items, architectural flaws, legacy dependencies, or missing automated tests.
- `PRODUCT_ROADMAP`: Upcoming strategic features, customer commitments, and expansion goals.
- `ENGINEERING_METRICS`: Outage frequencies, bug velocity, deployment friction logs, or cycle time data.

## Instructions
1. Evaluate each debt item in `TECH_DEBT_BACKLOG` across four core metrics:
   - **Interest Rate (Contagion & Maintenance Drag)**: How much extra time does this debt add to ongoing feature development?
   - **Principal Cost**: Estimated engineering effort required to resolve the debt.
   - **Blast Radius & Outage Risk**: Probability and severity of production failure if left unaddressed.
   - **Roadmap Blockade Factor**: Does this debt block crucial features in `PRODUCT_ROADMAP`?
2. Construct a **Tech Debt Prioritization Matrix** grouping items into four actionable quadrants:
   - *High Drag / High Risk*: Immediate refactoring targets (Sprint Priority).
   - *High Drag / Low Risk*: Incremental refactoring alongside feature work.
   - *Low Drag / High Risk*: Risk mitigation / safety guardrails.
   - *Low Drag / Low Risk*: Monitored backlog.
3. Draft business justification proposals translating technical refactoring into ROI terms suitable for product executive stakeholders.

## Constraints
- Do not label all legacy code as "critical technical debt"; justify prioritization with concrete engineering velocity or reliability metrics.
- Ensure refactoring recommendations include clear completion boundaries to prevent scope creep.

## Expected output
- **Tech Debt Valuation Breakdown**: Scored audit of technical debt items.
- **Prioritization Quadrant Matrix**: Visual/tabular classification of debt priority.
- **Executive ROI Proposal**: Business justification framing technical cleanup in terms of risk reduction and speed.
