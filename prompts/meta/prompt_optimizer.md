# Meta Prompt: Prompt Optimizer and Generator

## Purpose
Optimize a basic, unstructured, or weak user prompt into a high-quality, professional, and instruction-compliant prompt.

## Inputs
- `RAW_PROMPT`: The initial draft or idea of what the user wants to ask an AI.
- `TARGET_MODEL`: The class or style of the target model (e.g., reasoning-heavy model, fast API model).

## Instructions
1. Read the `RAW_PROMPT` to extract the underlying goal, constraints, and inputs.
2. Structure a new, optimized prompt containing all standard prompt elements:
   - Purpose
   - Inputs
   - Instructions
   - Constraints
   - Expected output
3. Enhance the instruction specificity: replace vague verbs (e.g., "help me write," "give some ideas") with active, analytical instructions.
4. Inject defensive prompt engineering: add explicit failure consideration rules and edge-case instructions.
5. Provide a clear example of how to supply inputs to the optimized prompt.

## Constraints
- Keep the optimized prompt clean and modular; avoid over-complicating if the task is simple.
- Do not lose the core intent or nuance of the user's original `RAW_PROMPT`.

## Expected output
- **Underlying Intent Analysis**: Short breakdown of what the raw prompt was actually trying to achieve.
- **Optimized Prompt Block**: Complete markdown block containing the newly structured prompt.
- **Why It's Better**: Explanations of specific changes made (e.g., "Added a constraints section to prevent hallucination").
