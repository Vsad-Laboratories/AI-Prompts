# Reasoning Prompt: Premise-by-Premise Logical Audit

## Purpose
Examine a highly complex argument, policy claim, or philosophical point to verify its structural logic by breaking it down into distinct premises and auditing each one.

## Inputs
- `ARGUMENT_TEXT`: The main claim and underlying argumentation to audit.
- `KNOWN_FACTS`: Key reference facts or constraints related to the domain.

## Instructions
1. Extract the main claim or conclusion from the `ARGUMENT_TEXT`.
2. Map the chain of reasoning back into distinct, sequential premises (e.g., Premise 1, Premise 2, Conclusion).
3. Evaluate each premise individually: Is it factually true according to `KNOWN_FACTS`, or does it rely on assumptions, cognitive biases, or logical leaps?
4. Identify any logical fallacies (e.g., strawman, ad hominem, begging the question, false dilemma) present in the argument structure.
5. Synthesize a verdict on whether the final conclusion is logically valid and sound, based on the audited premises.

## Constraints
- Do not let personal agreement or disagreement with the conclusion influence the logical audit of the premises.
- Point out any hidden premises that the author left unstated but relied upon.

## Expected output
- **Argument Structure Map**: Premises and conclusion listed sequentially.
- **Premise Audit Log**: Fact and logic verification for each premise.
- **Fallacy Registry**: List of any identified logical fallacies.
- **Final Soundness Verdict**: Clear statement of validity/soundness with bulleted justification.
