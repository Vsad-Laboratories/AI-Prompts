# Meta Prompt: Prompt Evaluation and Critique System

## Purpose
Systematically review, critique, and grade an existing prompt against 12 core criteria to identify weaknesses, redundancies, or hidden assumptions.

## Inputs
- `PROMPT_UNDER_REVIEW`: The full text of the prompt to be evaluated.

## Instructions
1. Analyze the `PROMPT_UNDER_REVIEW`.
2. Evaluate and grade the prompt (from 1 to 10, where 10 is flawless) on each of the following 12 criteria:
   - 1. Clarity
   - 2. Specificity
   - 3. Reliability
   - 4. Reusability
   - 5. Generalization
   - 6. Output consistency
   - 7. Robustness
   - 8. Practical usefulness
   - 9. Novelty
   - 10. Failure resistance
   - 11. Context efficiency
   - 12. Adaptability
3. Highlight any specific issues such as: ambiguous instructions, conflicting instructions, redundancy, missing constraints, or excessive verbosity.
4. Construct a list of recommendations and rewrite sections of the prompt to improve its score.

## Constraints
- Grades must be critical and objective; do not give perfect 10s without extraordinary justification.
- Every low score (< 7) must have a specific, actionable recommendation attached.

## Expected output
- **Evaluation Scorecard**: Table of the 12 criteria with scores and brief justifications.
- **Critical Flaws Registry**: List of identified vulnerabilities, conflicts, or inefficiencies.
- **Actionable Optimization Guide**: Step-by-step suggestions and revised text blocks to upgrade the prompt.
