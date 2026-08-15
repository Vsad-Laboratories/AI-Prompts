# Productivity Prompt: Time-Boxing and Task Batching Optimizer

## Purpose
Optimize chaotic task backlogs, calendar commitments, and fragmented schedules into focused, deep-work time blocks using time-boxing and task-batching methodologies.

## Inputs
- `TASK_LIST`: Pending personal or team tasks with estimated durations and urgency/importance flags.
- `AVAILABILITY_WINDOWS`: Daily working hours, recurring meetings, fixed commitments, and energy peak hours.
- `COGNITIVE_LOAD_LEVELS`: Categorization of tasks by required mental focus (e.g., High Focus Coding vs. Low Focus Email Triage).

## Instructions
1. Group individual tasks into logical context batches (e.g., Administrative Batch, Code Review Batch, Strategic Writing Block) to minimize context switching overhead.
2. Align High Cognitive Load task batches with the user's peak focus windows in `AVAILABILITY_WINDOWS`.
3. Construct a hourly **Time-Boxed Schedule Agenda** enforcing 60-90 minute deep work blocks separated by short buffer intervals.
4. Apply Parkinson's Law by setting strict time caps for routine, low-value administrative tasks.
5. Provide contingency buffer rules for handling unexpected urgent interruptions.

## Constraints
- Do not schedule back-to-back high-focus cognitive blocks without rest intervals.
- Protect at least one 2-3 hour uninterrupted deep-work block daily.

## Expected output
- **Task Context Batches**: Grouping of related tasks with total time estimates.
- **Hourly Time-Boxed Agenda**: Chronological calendar layout mapping task blocks to time slots.
- **Interruption Guardrails**: Tactical rules for handling schedule disruptions.
