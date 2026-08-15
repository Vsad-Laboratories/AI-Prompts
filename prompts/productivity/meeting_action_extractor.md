# Productivity Prompt: Meeting Transcript Action Item Extractor

## Purpose
Synthesize messy, unstructured meeting transcripts or raw discussion notes into concise, structured meeting summaries, key decisions, and assigned action items.

## Inputs
- `MEETING_TRANSCRIPT`: Raw transcript, chat log, or speaker notes from a team meeting.
- `MEETING_CONTEXT`: Objective of the meeting and key project stakeholders present.
- `DEFAULT_ASSIGNEES`: Known team members and their primary functional roles.

## Instructions
1. Filter out tangential small talk, filler comments, and unresolved conversational side tracks.
2. Extract the core **Executive Summary**: 3-4 sentence overview of key discussion points and outcomes.
3. Catalog all explicit **Key Decisions Made**: List strategic or operational conclusions reached during the meeting.
4. Extract all **Action Items**, explicitly specifying:
   - *Task Description*: Clear, actionable verb-driven task statement.
   - *Owner*: Named assignee responsible for execution.
   - *Due Date / Timeline*: Target delivery window mentioned or inferred.
5. Highlight unresolved questions requiring follow-up discussions.

## Constraints
- Do not assign generic action items without a specific named owner; match unassigned tasks against functional roles or flag as "Needs Owner".
- Maintain strict fidelity to choices actually agreed upon in the transcript.

## Expected output
- **Executive Meeting Summary**: High-level overview.
- **Key Decisions Log**: Bulleted list of binding decisions.
- **Action Item Tracker Table**: Structured table detailing Task, Assignee, Deadline, and Dependencies.
- **Open Questions & Follow-ups**: Unresolved points requiring future alignment.
