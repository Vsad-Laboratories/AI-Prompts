# Reasoning Prompt: Premortem and Risk Mitigation Analysis

## Purpose
Prevent failures before they happen by imagining a scenario where a project or idea has completely failed, identifying all plausible causes of that failure, and constructing mitigation strategies.

## Inputs
- `PROJECT_PLAN`: The proposal, plan, or decision under consideration.
- `FAILURE_SCENARIO`: A hypothetical future description of complete project failure.

## Instructions
1. Read the `PROJECT_PLAN`.
2. Transport yourself to the hypothetical future specified in the `FAILURE_SCENARIO`. Assume the project failed catastrophically.
3. List 5 to 10 plausible, detailed reasons why the project failed. Be brutally honest and creative. Look for hidden assumptions, external dependencies, team dynamics, or operational issues.
4. For each failure point, assign a probability (Low/Medium/High) and impact (Low/Medium/High).
5. Develop specific, actionable mitigation strategies or plan modifications to address the high-risk failure points.

## Constraints
- Do not make excuses for the failure; assume the failure is 100% real and complete.
- Mitigation strategies must be concrete and integrated into the original plan, not just vague advice.

## Expected output
- **Catastrophic Failure Autopsy**: Detailed list of failure reasons with risk scoring.
- **Root-Cause Analysis**: Explanation of why these failure modes were overlooked initially.
- **Actionable Mitigations**: Step-by-step additions/revisions to make the original plan resilient.
