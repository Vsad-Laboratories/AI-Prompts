# Planning Prompt: Strategic Product Roadmap

## Purpose
Formulate a long-term, high-impact product roadmap that balances technical debt, user demands, strategic business goals, and resource constraints.

## Inputs
- `BUSINESS_VISION`: The high-level direction of the company/product.
- `USER_FEEDBACK_AND_BACKLOG`: Top requested features and critical technical issues.
- `RESOURCES_AND_TIMELINE`: Team size, budget, and target release quarters (e.g., Q1-Q4).

## Instructions
1. Read the inputs to extract critical priorities and timelines.
2. Group roadmap elements into distinct thematic "pillars" (e.g., Security & Reliability, Core Experience, Growth & Monetization).
3. Evaluate and rank items in the `USER_FEEDBACK_AND_BACKLOG` using an **ICE (Impact, Confidence, Ease)** or **RICE (Reach, Impact, Confidence, Effort)** framework.
4. Distribute the prioritized items across the quarters (Q1-Q4), factoring in logical dependencies (e.g., do not plan feature X before platform migration Y is complete).
5. Identify potential risks, bottleneck resources, and critical path items.

## Constraints
- Do not plan more work than can be realistically completed given the `RESOURCES_AND_TIMELINE`.
- Every scheduled roadmap item must be directly connected to a pillar or business priority.

## Expected output
- **Product Vision Alignment**: Brief statement connecting the roadmap back to the core company goals.
- **ICE/RICE Prioritization Table**: Ranked list of features and tech-debt tasks.
- **Quarterly Roadmap (Q1-Q4)**: Clear, phased timeline of milestones and deliverables.
- **Risk and Dependencies Register**: Key blockers and mitigations.
