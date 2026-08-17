# Structured Output & Context-Free Grammar (CFG) Compiler

## Purpose
Compile natural language generation requirements and complex JSON/YAML output specifications into hyper-rigid system prompts, dynamic EBNF (Extended Backus-Naur Form) grammars, and schema enforcement instructions that guarantee 100% deterministic, parseable, and zero-preamble LLM output compliance.

## Inputs
- `TARGET_OUTPUT_SCHEMA`: TypeScript interface, JSON Schema definition, Pydantic model, or required structural layout.
- `GRAMMAR_ENGINE_TARGET`: Target decoding enforcement engine (e.g., Llama.cpp GBNF, Outlines CFG, Guidance, OpenAI Structured Outputs, Native System Prompt Wrapper).
- `CONVERSATIONAL_PREAMBLE_POLICY`: Policy on conversational preambles (Default: STRICT ZERO PREAMBLE / NO CONVERSATIONAL FILLER).

## Instructions
1. **Parse Target Schema**: Deconstruct `TARGET_OUTPUT_SCHEMA` into fundamental scalar types (strings, numbers, booleans, enums), arrays, nested objects, and required/optional properties.
2. **Formulate Rigid Structural Anchors**: Construct explicit prompt instructions forcing the model to emit structural prefix anchors (e.g., "The response MUST begin immediately with `{` and end strictly with `}`").
3. **Compile EBNF / GBNF Grammar (If Applicable)**: If `GRAMMAR_ENGINE_TARGET` includes GBNF/Outlines, compile the target schema into a formal Context-Free Grammar rule set:
   ```ebnf
   root ::= object
   object ::= "{" ws "\"status\":" ws string "," ws "\"data\":" ws array "}"
   ```
4. **Compile Negative Constraints Wrapper**: Append robust negative instructions forbidding conversational introductions ("Sure, here is your JSON..."), markdown code block ticks (unless explicitly required), trailing commas, or postscript commentary.
5. **Incorporate Few-Shot Structural Anchor Examples**: Provide minimal valid and invalid output pairs demonstrating exact formatting expectations.

## Constraints
- **Zero Conversational Preamble**: The prompt MUST guarantee that output generation starts on byte 0 with the opening structural delimiter.
- **Strict Valid Syntax**: Emitted schema definitions MUST pass standard JSON/YAML schema validator tools without parsing errors.
- **Escape Handling**: Explicitly instruct the model on escaping quotes and special characters in string fields to prevent JSON string parsing syntax errors.

## Expected Output Format
```markdown
### 1. Compiled System Prompt Enforcement Wrapper
```text
You are a deterministic JSON compilation engine. You MUST output raw, valid JSON adhering strictly to the schema specification below.

CRITICAL GENERATION CONSTRAINTS:
1. Do NOT include any conversational preamble, intro text, or concluding explanations (e.g., do NOT say "Sure, here is your JSON").
2. Your response MUST begin immediately with the character '{' and end strictly with the character '}'.
3. Do NOT wrap output in markdown ```json ... ``` code blocks. Output raw JSON bytes only.
4. All object keys must be double-quoted. Trailing commas are strictly prohibited.

TARGET JSON SCHEMA SPECIFICATION:
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "type": "object",
  "properties": {
    "execution_status": { "type": "string", "enum": ["SUCCESS", "FAILED"] },
    "result_data": { "type": "array", "items": { "type": "string" } }
  },
  "required": ["execution_status", "result_data"]
}
```

### 2. Compiled GBNF Grammar Definition (For Local Llama.cpp / Outlines Encoders)
```ebnf
root ::= object
object ::= "{" ws "\"execution_status\":" ws status-enum "," ws "\"result_data\":" ws array "}" ws
status-enum ::= "\"SUCCESS\"" | "\"FAILED\""
array ::= "[" ws (string ("," ws string)*)? ws "]"
string ::= "\"" [^"\\]* "\""
ws ::= [ \t\n\r]*
```

### 3. Few-Shot Structural Demonstration
**Valid Output Example**:
```json
{"execution_status":"SUCCESS","result_data":["item_1","item_2"]}
```
```

## Evaluation Criteria
- **Parseability**: 100% successful JSON/YAML parse rate across 100 test runs.
- **Preamble Elimination**: Zero occurrences of conversational prefix or postfix text.
- **CFG Validity**: Compiled EBNF/GBNF grammar rule sets validate cleanly in standard parser tools.

## Failure Considerations
- **Trailing Commas**: Model generating valid JSON structure but including invalid trailing commas in arrays/objects.
- **Markdown Code Block Wrapping**: Model adding ```json wrapping when raw JSON output was requested.
