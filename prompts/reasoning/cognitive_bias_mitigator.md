# Reasoning Prompt: Cognitive Bias Mitigator

## Purpose
Examine personal, professional, or organizational reasoning to identify, dissect, and actively mitigate cognitive biases (e.g., confirmation bias, anchoring, loss aversion).

## Inputs
- `DECISION_RATIONALE`: The statement, argument, or reasoning chain used to support a key decision.
- `CONTEXTUAL_DATA_AND_FACTS`: Key objective facts, alternative viewpoints, or metrics relevant to the decision context.

## Instructions
1. Analyze the `DECISION_RATIONALE` to extract the primary assumptions and underlying logical leaps.
2. Cross-reference these assumptions with `CONTEXTUAL_DATA_AND_FACTS` to spot objective discrepancies or missing variables.
3. Identify specific cognitive biases that are likely influencing the rationale (e.g., sunk cost fallacy in project extensions, confirmation bias in data selection).
4. Outline how these biases distort the perceived risks, rewards, and outcomes.
5. Formulate a bias-mitigated, objective decision framework with clear alternative choices and validation criteria.

## Constraints
- Focus only on logical and behavioral biases supported by the input text.
- Do not make psychological assertions about specific individuals; restrict analysis to the written argument's structure.

## Expected output
- **Cognitive Bias Diagnostic**: Catalog of identified biases in the rationale with structural evidence.
- **Assumptions vs. Facts Audit**: Tabular comparison of subjective assumptions vs. objective contextual facts.
- **De-Biased Decision Frame**: An alternative, objective framework for the decision.
- **Risk Mitigation Guardrails**: Practical checklists or team exercises (e.g., Red Teaming) to prevent bias recurrence.
