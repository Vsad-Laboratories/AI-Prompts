# Productivity Prompt: Asynchronous Communication & Daily Digest Synthesizer

## Purpose
Synthesize fragmented, multi-channel team communications (Slack/Discord threads, PR comments, email chains) into structured, action-oriented asynchronous daily digests.

## Inputs
- `RAW_COMMUNICATION_FEEDS`: Unstructured chat logs, comment threads, or email message dumps.
- `PROJECT_CONTEXT`: Active project goals, current sprint milestones, or key stakeholders.

## Instructions
1. Parse `RAW_COMMUNICATION_FEEDS` to extract major project updates, technical decisions, blockers, and assigned tasks.
2. Filter out conversational noise, casual chatter, and redundant status updates.
3. Categorize information into clear headings: Key Decisions Made, Critical Blockers, Active PR/Code Reviews, and Direct Action Items.
4. Extract explicit ownership and deadlines for every identified action item.
5. Generate an executive daily digest formatted for quick 2-minute scanning.

## Constraints
- Do not fabricate task assignments or decisions not explicitly stated in source logs.
- Keep output concise, utilizing bullet points and bold highlights for maximum legibility.

## Expected output
- **Executive Summary**: 2-3 sentence overview of major daily progress.
- **Key Decisions Log**: Bulleted record of architectural and product decisions.
- **Action Item Tracker**: Structured table containing Task, Owner, Deadline, and Status.
