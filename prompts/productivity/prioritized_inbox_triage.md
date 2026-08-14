# Productivity Prompt: Prioritized Inbox Triage

## Purpose
Automate email and messaging triage by analyzing incoming message content, sender urgency, and scheduling actions based on a matrix of priority.

## Inputs
- `INCOMING_MESSAGE_PAYLOAD`: Raw text, subject, sender identity, and timestamp of the incoming message.
- `USER_PRIORITY_GUIDELINES`: Criteria for defining critical senders, keywords, active project topics, and immediate task categories.

## Instructions
1. Analyze the `INCOMING_MESSAGE_PAYLOAD` to identify the sender, core topic, and explicit or implicit request deadlines.
2. Cross-reference the message characteristics with `USER_PRIORITY_GUIDELINES` to evaluate the relative importance.
3. Categorize the message into an Eisenhower Matrix (e.g., Urgent/Important, Urgent/Not Important).
4. Outline a brief, context-appropriate draft reply if immediate response is needed.
5. Create a specific calendar block recommendation or task entry to track follow-ups.

## Constraints
- Do not automatically draft responses that make firm commitments without the user's explicit prior instruction.
- Strictly adhere to the privacy standards regarding sender contact details.

## Expected output
- **Inbox Priority Category**: Numerical urgency ranking and Eisenhower categorization.
- **Key Action Extraction**: Actionable task summaries with derived deadlines.
- **Contextual Draft Response**: Suggested email response ready for customization.
- **Task Management Routing**: Suggested labels, tags, and calendar entries for tracking.
