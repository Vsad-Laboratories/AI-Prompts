# Reasoning Prompt: Abductive Reasoning & Best-Explanation Evaluation Protocol

## Purpose
Execute abductive reasoning to infer the most plausible explanation or root-cause hypothesis when presented with incomplete, contradictory, or ambiguous observational evidence.

## Inputs
- `OBSERVED_FACTS`: List of known symptoms, anomalies, log snippets, or physical evidence.
- `BACKGROUND_KNOWLEDGE`: Domain context, system topology, or baseline rules.

## Instructions
1. Enumerate all possible candidate hypotheses that could account for `OBSERVED_FACTS`.
2. Evaluate each hypothesis against the **Criteria of Best Explanation**:
   - Parsimony (Occam's Razor - minimal unnecessary assumptions).
   - Explanatory Scope (accounts for the largest number of observed facts).
   - Explanatory Depth (provides a coherent mechanistic cause).
   - Plausibility (aligns with baseline domain physics/engineering laws).
3. Identify anomalous facts that contradict or weaken each hypothesis.
4. Rank hypotheses in order of likelihood and formulate targeted empirical tests to falsify competing hypotheses.

## Constraints
- Do not dismiss facts that contradict a favored hypothesis; highlight them as critical discriminators.
- Recommend explicit, non-destructive test procedures to validate the top hypothesis.

## Expected output
- **Candidate Hypothesis Matrix**: Comparative table evaluating competing hypotheses against facts.
- **Explanatory Power Audit**: Evaluation across parsimony, scope, and depth metrics.
- **Ranked Diagnosis & Discriminatory Tests**: Prioritized hypotheses with specific falsification experiments.
