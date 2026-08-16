# Agents Prompt: Tool Schema Generation & Validation Protocol

## Purpose
Guide an LLM agent through inspecting, validating, generating, and sanitizing rigid JSON tool call schemas and function signatures to ensure strict API compliance and zero runtime parsing errors.

## Inputs
- `API_SPECIFICATION`: Raw API documentation, function requirements, or target endpoint definition.
- `TARGET_FRAMEWORK`: Target function calling framework (e.g., OpenAI Function Calling, Anthropic Tool Use, LangChain, Autogen).

## Instructions
1. Analyze the provided `API_SPECIFICATION` to identify all functions, parameters, data types, nested objects, required fields, and enumerations.
2. Translate the specification into a strict JSON Schema adhering to OpenAPI / JSON Schema Draft 7 standards.
3. Validate parameter types, enforcing explicit constraints (e.g., `minimum`, `maximum`, `enum`, `pattern`, `minLength`, `additionalProperties: false`).
4. Generate comprehensive parameter descriptions to guide downstream LLM tool selection during runtime execution.
5. Provide a invalid/valid payload test suite illustrating common edge cases and validation rules.

## Constraints
- Always set `additionalProperties: false` on object parameters to prevent unexpected payload keys.
- Every parameter must include a clear, non-ambiguous `description` string explaining its exact format and purpose.
- Do not use non-standard JSON schema keywords unsupported by `TARGET_FRAMEWORK`.

## Expected output
- **JSON Tool Schema Definition**: Production-ready, validated JSON tool specification block.
- **Validation Rules & Constraint Summary**: Explanations of type bounds, mandatory fields, and default values.
- **Payload Test Cases**: Examples of valid tool invocation payloads and handled invalid payloads.
