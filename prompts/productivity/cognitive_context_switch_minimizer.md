# Productivity Prompt: Workday Task Batching & Cognitive Context Switching Minimizer

## Purpose
Optimize chaotic work backlogs, calendar schedules, and incoming commitments into focused deep-work blocks while minimizing cognitive context switching overhead.

## Inputs
- `TASK_BACKLOG`: List of pending engineering tasks, admin duties, meetings, and code review requests.
- `CALENDAR_CONSTRAINTS`: Fixed meetings, working hours, and energy/focus preference windows.

## Instructions
1. Group `TASK_BACKLOG` items into complementary cognitive categories (e.g., Deep Coding, Code Review/Triage, Strategic Planning, Admin/Email).
2. Calculate estimated cognitive load and context switching costs for switching between different task types.
3. Schedule tasks into time-boxed blocks aligned with peak cognitive focus hours (e.g., morning deep work).
4. Batch shallow administrative tasks and message reviews into dedicated low-energy buffer windows.
5. Formulate an optimized daily time-blocking schedule with explicit transition buffers.

## Constraints
- Prevent scheduling deep coding tasks in fragmented 30-minute gaps between meetings.
- Protect at least one unbroken 3-hour deep work block per workday.

## Expected output
- **Cognitive Load & Batch Classification**: Grouped task categories and energy ratings.
- **Optimized Time-Boxed Daily Schedule**: Hourly calendar breakdown with deep work buffers.
- **Context Switching Reduction Guidelines**: Actionable rules for batching incoming distractions.
