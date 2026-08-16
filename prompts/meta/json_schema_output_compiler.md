# Meta Prompt: Rigid JSON Schema & Output Contract Compiler

## Purpose
Compile unstructured LLM generation requests into hyper-rigid system prompts that force LLMs to output valid, deterministic JSON adhering strictly to a JSON Schema specification without conversational filler.

## Inputs
- `TARGET_JSON_SCHEMA`: The desired JSON Schema object definition.
- `TASK_DESCRIPTION`: High-level goal or task the LLM must perform.

## Instructions
1. Analyze `TARGET_JSON_SCHEMA` to identify all required fields, data types, arrays, nested objects, and regex format constraints.
2. Formulate negative prompt instructions explicitly banning markdown backticks (unless requested), preambles, postambles, and conversational acknowledgments.
3. Inject structural schema anchor tags forcing the model to begin output immediately with `{` and terminate with `}`.
4. Construct an edge-case escaping instruction block to handle quotes, newlines, and special characters safely within JSON strings.
5. Provide a complete compiled System Prompt ready for API deployment.

## Constraints
- The generated prompt must guarantee 100% JSON parseability across lightweight and open-weight models.
- Explicitly enforce `additionalProperties: false` enforcement in prompt wording.

## Expected output
- **Compiled Output-Contract System Prompt**: Production prompt template ready for injection.
- **Escape & Parsing Safety Instructions**: Operational rules for handling raw strings and JSON special characters.
- **Verification Few-Shot Pair**: Example input and exact expected deterministic JSON output.
