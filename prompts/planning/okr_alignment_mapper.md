# Planning Prompt: OKR Alignment Mapper

## Purpose
Formulate company-wide Objectives and Key Results (OKRs) and map them systematically down to team-level and individual contributor (IC) targets.

## Inputs
- `COMPANY_MISSION_AND_STRATEGY`: High-level strategic pillars, mission statement, and yearly financial or growth goals.
- `TEAM_CAPABILITIES_AND_RESOURCES`: List of engineering, product, or sales teams, their sizes, focus areas, and bandwidth capacity.

## Instructions
1. Analyze the core pillars of `COMPANY_MISSION_AND_STRATEGY` to draft 3-4 top-level Objectives that are qualitative, inspirational, and time-bound.
2. Define 3-5 quantitative, measurable Key Results for each company-level Objective.
3. Cascade the company-level KRs down to the business units or teams listed in `TEAM_CAPABILITIES_AND_RESOURCES`.
4. Ensure vertical alignment: check that satisfying team-level OKRs directly impacts and fulfills company-level Key Results.
5. Plan a feedback loop protocol for key result tracking, status reporting, and grading cycles (e.g., quarterly retrospective).

## Constraints
- Do not create more than 5 objectives or 5 key results per objective to avoid dilution of focus.
- Ensure all key results are objectively measurable; do not use subjective words like "improve" without defining metrics.

## Expected output
- **Company-Level OKR Blueprint**: Inspirational objectives with highly quantifiable key results.
- **Cascaded Team-Level Mapping**: Matrix showing how specific team OKRs roll up to the company goals.
- **Horizontal Alignment Analysis**: Interdependency map between teams (e.g., engineering supporting product releases).
- **Tracking & Retro Protocol**: Playbook for grading, monitoring progress, and revising off-track key results.
