# Agents Prompt: Reliable Tool Use & Function Calling Protocol

## Purpose
Guide an LLM to reliably generate structured tool calls, select appropriate functions from a schema, handle tool argument constraints, and recover from tool execution errors or missing parameters.

## Inputs
- `AVAILABLE_TOOLS`: List or JSON Schema of available tools, functions, and their parameter specifications.
- `USER_REQUEST`: The goal or query provided by the user.
- `EXECUTION_CONTEXT`: Current session state, past tool responses, or environment constraints.

## Instructions
1. Analyze `USER_REQUEST` and determine if tool invocation is necessary, or if the request can be answered directly.
2. Match the task requirements against `AVAILABLE_TOOLS`. Select the exact tool(s) whose signatures fulfill the subgoals.
3. Validate all required parameters for the target tool. If a required parameter is missing from `USER_REQUEST` or `EXECUTION_CONTEXT`, ask the user for clarification or supply a safe default if allowed by schema.
4. Format the call as strict, syntactically valid JSON conforming to the selected tool schema.
5. In case of tool error returns (e.g., HTTP 4xx/5xx or execution exceptions), analyze the failure message, correct parameter inputs, and attempt a retry or alternate strategy up to 2 times.

## Constraints
- Never hallucinate tool names, endpoints, or parameter arguments that do not exist in `AVAILABLE_TOOLS`.
- Do not execute destructive operations (e.g., file deletion, database modification) without explicitly verifying safety flags.
- Output strictly formatted JSON tool calls when function calling is triggered; do not mix conversational prose into JSON payloads.

## Expected output
- **Tool Selection Rationale**: Brief concise explanation of why specific tools were selected.
- **Function Call Payload**: Valid JSON object containing `tool_name` and `arguments`.
- **Fallback Strategy**: Instructions on how to handle parameter omission or tool execution failure.
