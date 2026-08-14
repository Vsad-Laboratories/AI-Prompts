# Meta Prompt: Negative Constraint Compiler

## Purpose
Analyze and translate complex negative instructions, constraints, and safety guidelines into highly robust, model-compliant prompt instructions.

## Inputs
- `RAW_NEGATIVE_CONSTRAINTS`: Textual list of what the model MUST NOT do, output, or mention (e.g., do not mention pricing, never output SQL directly, avoid medical advice).
- `MODEL_CHARACTERISTICS`: The target LLM style and tendency (e.g., tends to ignore negatives on long contexts, prone to sycophancy).

## Instructions
1. Deconstruct the list of `RAW_NEGATIVE_CONSTRAINTS` to categorize the safety boundaries and risks.
2. Translate passive "do not" instructions into active positive instructions (e.g., "do not output raw SQL" becomes "only output structured JSON wrappers; place queries in variables").
3. Design defensive prompt blocks (e.g., system-level overrides or explicit output schemas) to force model compliance.
4. Adjust the styling and context density based on `MODEL_CHARACTERISTICS` to maximize attention allocation.
5. Construct negative few-shot examples showing the model refusing requests that violate the constraints.

## Constraints
- The compiled constraints must not make the model overly defensive or refuse benign, safe requests.
- Avoid contradictory rules that confuse the model's output boundaries.

## Expected output
- **Constraint Translation Table**: Direct mapping of raw negative rules to model-compliant positive commands.
- **Defensive Prompt Block (System Instruction Ready)**: The clean markdown system block for prompt injection.
- **Refusal Decision Tree**: Logical flow the model executes to safely decline out-of-bound tasks.
- **Few-Shot Compliance Examples**: Example templates showcasing correct and safe refusal responses.
