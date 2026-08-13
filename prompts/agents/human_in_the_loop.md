# Agents Prompt: Human-in-the-Loop Collaboration Protocol

## Purpose
Design a highly reliable collaboration protocol that lets an autonomous AI agent smoothly escalate complex, edge-case, or high-risk tasks to a human supervisor, and integrate human feedback back into its workflow.

## Inputs
- `AGENT_WORKFLOW`: Description of what the agent normally does autonomously.
- `ESCALATION_CRITERIA`: Trigger conditions for human intervention (e.g., confidence score below 0.7, payment amount above $1000, user frustration).

## Instructions
1. Analyze the `AGENT_WORKFLOW` and map the precise decision points where `ESCALATION_CRITERIA` must be evaluated.
2. Formulate an **Escalation Trigger**: Instructions explaining how the agent detects it needs help and how it packages the task context (e.g., historical transcripts, current state, specific reason for escalation).
3. Design a **Human-Review Interface Schema**: Describe what information must be displayed to the human reviewer to make the decision trivial (clear options, risk indicators).
4. Establish the **Feedback Integration Protocol**: Define exactly how the agent parses the human's input (e.g., direct approval, text revision, rejection with notes) and continues the workflow.
5. Create a fallback protocol in case the human supervisor does not respond within a specific timeout.

## Constraints
- Ensure the agent does not excessively escalate simple tasks; it must strive for maximum autonomy while respecting the strict risk boundaries.
- Keep the escalation context concise to avoid wasting human reviewer time.

## Expected output
- **Workflow Escalation Points Map**: Visual or structured list of check points.
- **Context Packaging Schema**: Template for the JSON payload passed to the human review system.
- **Agent Handoff Instructions**: Specific prompt templates the agent runs when a human responds.
- **Timeout Fallback Plan**: Fallback procedure if the supervisor is offline.
