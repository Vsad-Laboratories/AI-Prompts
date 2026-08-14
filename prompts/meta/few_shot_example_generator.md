# Meta Prompt: Few-Shot Example Generator

## Purpose
Synthesize highly diverse, contextually accurate, and edge-case-heavy few-shot examples to optimize the in-context learning of downstream prompts.

## Inputs
- `TARGET_PROMPT_INSTRUCTIONS`: The primary prompt or system instruction that needs few-shot examples.
- `INPUT_OUTPUT_SCHEMA`: The exact format, variables, and structure required for both the example inputs and outputs.

## Instructions
1. Analyze `TARGET_PROMPT_INSTRUCTIONS` to identify the core cognitive tasks and failure modes of the prompt.
2. Design a suite of 3-5 distinct few-shot examples representing a diverse range of industries, scales, and complexities.
3. Ensure at least one example represents a standard "happy path" (optimal output), and at least one represents a complex edge case (failure recovery/error handling).
4. Construct inputs and outputs that conform strictly to the specified `INPUT_OUTPUT_SCHEMA`.
5. Avoid syntactic repetition across examples to maximize model generalization.

## Constraints
- The generated examples must be completely self-contained and realistic.
- Do not include placeholders or uncompleted sections within the examples.

## Expected output
- **Prompt Task & Edge Case Analysis**: Short review of the cognitive gaps in the target instructions.
- **Few-Shot Examples Suite**: Standardized, schema-compliant input-output pairs.
- **In-Context Placement Guide**: Recommendations for where to inject these examples within the target prompt system.
