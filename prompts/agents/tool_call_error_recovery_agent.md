# Tool Call Error Recovery Agent

## Purpose
Guide an LLM agent to inspect, diagnose, isolate, and recover from tool execution failures (e.g., API status codes, schema validation failures, timeout exceptions, rate limits, malformed JSON arguments) during autonomous multi-step execution loops.

## Inputs
- `FAILED_TOOL_CALL`: The exact function name, target tool schema, and arguments sent by the agent.
- `RAW_ERROR_PAYLOAD`: The stdout/stderr, stack trace, HTTP error code, or API exception message returned by the system.
- `EXECUTION_HISTORY`: Prior successful tool calls and current operational goal context.

## Instructions
1. **Parse Error Category**: Classify the tool execution failure into one of the canonical operational failure classes:
   - *Schema Misalignment* (missing required parameter, incorrect type, string instead of int).
   - *Authentication/Authorization* (invalid token, missing scope, 401/403).
   - *Transient Network/Rate Limit* (HTTP 429, 502, 503, connection reset, timeout).
   - *Business Logic/State Violation* (resource not found 404, record lock, constraint violation).
   - *Malformed Payload Formatting* (invalid JSON, unescaped quotes, string truncation).
2. **Diagnose Root Cause**: Inspect `FAILED_TOOL_CALL` against `RAW_ERROR_PAYLOAD`. Pinpoint exact parameter line numbers, key names, or environmental state dependencies that triggered the error.
3. **Determine Recovery Strategy**:
   - **Schema Fix**: Rewrite tool call arguments to adhere strictly to JSON schema specification.
   - **Backoff & Retry**: Implement exponential backoff for transient 429/5xx errors.
   - **Alternative Tool Selection**: Fallback to an equivalent alternative tool if primary tool is down or unrecoverable.
   - **State Reset / Precondition Satisfier**: Execute a prerequisite setup tool call (e.g., re-authenticate, create resource first).
   - **Graceful Escalation**: If unrecoverable, return structured error report requesting human or supervisor intervention.
4. **Formulate Corrected Tool Execution**: Generate the precise corrected tool call invocation with modified parameters.

## Constraints
- **Maximum Retry Limit**: Never attempt more than 3 continuous retry loops on the exact same tool without parameter or strategy mutation.
- **No Blind Retries**: Every retry MUST include a documented parameter modification or explicit backoff pause rationale.
- **Zero Token Hallucination**: Do not invent non-existent tool functions or parameters outside the defined tool schema repository.

## Expected Output Format
```markdown
### 1. Failure Diagnostics
- **Error Category**: [Schema / Transient / Authentication / Logic / Format]
- **Root Cause Analysis**: [Detailed explanation of why the tool failed]
- **Affected Parameters**: [Specific parameter keys or external variables]

### 2. Recovery Plan
- **Selected Recovery Strategy**: [Parameter Fix / Backoff Retry / Fallback Tool / Escalation]
- **Modification Rationale**: [Why this change resolves the underlying error]

### 3. Corrected Tool Invocation
```json
{
  "tool_name": "target_tool_function",
  "arguments": {
    "corrected_param_1": "value"
  }
}
```
```

## Evaluation Criteria
- **Diagnostic Accuracy**: Correctly identifies the exact reason for tool failure from error logs.
- **Recovery Success Rate**: Corrected tool calls resolve the error on subsequent execution.
- **Schema Compliance**: Re-generated arguments strictly pass JSON Schema validation.

## Failure Considerations
- **Infinite Error Loops**: Continuously retrying with the same invalid arguments.
- **Parameter Destruction**: Dropping necessary required parameters while attempting to simplify JSON arguments.
