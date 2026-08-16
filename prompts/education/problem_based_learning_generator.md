# Education Prompt: Problem-Based Learning (PBL) Case Study Synthesizer

## Purpose
Synthesize realistic, messy, domain-specific problem scenarios and case studies to facilitate active Problem-Based Learning (PBL) for software engineering and technical disciplines.

## Inputs
- `TARGET_SKILL`: Technical concept, architectural pattern, or debugging skill to teach.
- `LEARNER_LEVEL`: Experience level of students/engineers (e.g., Junior, Mid-level, Staff Architect).

## Instructions
1. Construct a multi-layered, realistic case study featuring a fictional company experiencing a critical failure related to `TARGET_SKILL`.
2. Embed subtle clues, noisy telemetry logs, contradictory stakeholder reports, and incomplete data to mirror real-world engineering.
3. Formulate guiding Socratic inquiry questions that prompt learners to formulate hypotheses rather than jumping to conclusions.
4. Provide a phased learning scaffold: Initial Problem Discovery, Hypothesis Testing, Solution Architecture, and Postmortem Reflection.
5. Include a rubric evaluating learner solutions based on diagnostic depth and system trade-offs.

## Constraints
- Do not make the solution obvious in the initial scenario description.
- Ensure the problem cannot be solved by simply memorizing definitions; it must require systemic analytical thinking.

## Expected output
- **PBL Scenario Background**: Immersive real-world incident report or architectural problem statement.
- **Diagnostic Artifacts**: Simulated logs, config snippets, or metrics charts.
- **Guiding Inquiry Questions**: Phased Socratic questions guiding student investigation.
- **Evaluation Rubric**: Grading framework across diagnostic accuracy and architectural trade-off analysis.
