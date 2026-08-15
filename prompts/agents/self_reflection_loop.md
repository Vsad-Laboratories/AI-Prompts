# Agents Prompt: Agent Self-Reflection and Error Recovery Protocol

## Purpose
Enable an autonomous AI agent to evaluate its own intermediate reasoning, detect execution errors, diagnose root causes, and execute dynamic self-correction loops without human intervention.

## Inputs
- `TASK_GOAL`: The original objective assigned to the agent.
- `EXECUTION_LOG`: Step-by-step history of thoughts, tool outputs, and action attempts.
- `FAILED_STEP`: The specific action, code block, or response that produced an error or unexpected result.

## Instructions
1. Inspect `FAILED_STEP` alongside `EXECUTION_LOG` to identify the precise failure mode (e.g., syntax error, invalid assumptions, hallucinated parameters, unexpected tool output).
2. Execute a **Root Cause Diagnosis**: Explain *why* the previous reasoning or action failed rather than merely describing *what* failed.
3. Formulate a **Correction Hypothesis**: Propose a modified action sequence or strategy adjustment designed to bypass or resolve the error.
4. Evaluate the hypothesis against `TASK_GOAL` constraints to verify it does not introduce secondary regressions.
5. Re-execute the corrected task step with updated instructions and log the learning point for future steps.

## Constraints
- Limit self-correction loops to a maximum depth (e.g., 3 retries) to prevent infinite loops on unrecoverable external errors.
- Do not repeat the exact same failed action without modifying parameters or strategy.
- Maintain an explicit audit log of self-correction decisions.

## Expected output
- **Error Diagnosis**: Clear breakdown of failure cause.
- **Self-Critique Matrix**: Table listing flawed assumptions vs. corrected facts.
- **Revised Execution Plan**: Concrete next steps for retrying the failed operation.
