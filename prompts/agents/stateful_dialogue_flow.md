# Agents Prompt: Stateful Dialogue Flow

## Purpose
Design a state-aware agent dialogue manager that maintains conversational context, user intent history, and handles multi-turn state transitions reliably.

## Inputs
- `CONVERSATION_HISTORY`: The list of past user inputs and assistant responses representing the active session.
- `STATE_TRANSITION_RULES`: The finite state machine (FSM) or graph of allowed dialogue states (e.g., initial, identifying_account, payment_triage, confirm_resolution).

## Instructions
1. Analyze `CONVERSATION_HISTORY` to identify the user's current conversational intent and extract relevant variables.
2. Cross-reference the intent with `STATE_TRANSITION_RULES` to determine the current dialogue state.
3. Establish which state transitions are valid next steps based on the FSM layout.
4. Formulate the optimal agent response to guide the user to the next logical state while preserving session parameters.
5. Create dynamic rules to gracefully handle out-of-bounds user inputs (fallback state loops) without losing context.

## Constraints
- The dialog state machine must never enter an undefined or cyclic infinite-loop state.
- Do not make assumptions about user account data that has not been explicitly collected in the history.

## Expected output
- **Active State Diagnostics**: Identification of the current session state and variables.
- **Valid Transition Map**: Allowed next states based on the state machine rules.
- **Agent Dialogue Response**: The natural language output to the user, engineered to gather missing variables.
- **Out-of-Bounds Recovery Plan**: Fallback behavior instructions if the user shifts topics abruptly.
