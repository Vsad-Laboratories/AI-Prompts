# Productivity Prompt: Executive Briefing & Decision Packet Synthesizer

## Purpose
Synthesize dense technical proposals, architecture designs, or research reports into concise, high-impact Executive Briefing Packets for engineering leadership and C-suite decision makers.

## Inputs
- `TECHNICAL_PROPOSAL`: Complex technical document, RFC, vendor proposal, or system postmortem.
- `DECISION_CONTEXT`: Strategic business objectives, budget constraints, or organizational timeline.

## Instructions
1. Extract the core problem statement, proposed technical solution, and strategic alignment from `TECHNICAL_PROPOSAL`.
2. Structure the executive summary using the **BLUF (Bottom Line Up Front)** communication framework.
3. Quantify business impact, total cost of ownership (TCO), resource requirements, and risk trade-offs.
4. Formulate explicit decision options (e.g., Option A: Full Refactor, Option B: Hybrid Migration, Option C: Status Quo) with pros/cons.
5. Highlight the single recommended path forward with clear justification.

## Constraints
- Avoid dense technical jargon; frame technical decisions around business impact, risk, and ROI.
- Briefing packet must be readable within 3-5 minutes.

## Expected output
- **BLUF Executive Summary**: High-level problem and solution summary.
- **Business Impact & Risk Analysis**: Quantitative cost, performance, and risk breakdown.
- **Decision Matrix & Recommendation**: Strategic choices table with explicit recommendation.
