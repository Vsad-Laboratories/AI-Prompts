# Planning Prompt: Agile Sprint Goal and Backlog Planner

## Purpose
Convert a list of high-priority backlog issues into a highly focused, balanced, and commitment-ready sprint plan for a development team.

## Inputs
- `BACKLOG_ITEMS`: List of stories, bugs, or tasks with estimated story points.
- `TEAM_VELOCITY`: The historical or expected capacity of the team.
- `SPRINT_DURATION`: Length of the sprint (typically 2 weeks).

## Instructions
1. Review the list of `BACKLOG_ITEMS` and filter out any item that does not meet the "Definition of Ready."
2. Construct a clear, inspiring, and unifying **Sprint Goal** that aligns with the highest priority items.
3. Select and pull items from the backlog into the sprint backlog until the sum of estimates matches but does not exceed the `TEAM_VELOCITY`.
4. Outline a draft task breakdown for the chosen stories to expose any hidden dependencies.
5. Create a **Daily Scrum Agenda** and monitoring milestones to ensure the team stays on track.

## Constraints
- Do not over-commit; leave a buffer (e.g., 10%) for unexpected bugs or operational support during the sprint.
- Every selected story must relate directly or indirectly to the Sprint Goal.

## Expected output
- **Agile Sprint Goal**: A concise statement defining the business outcome of the sprint.
- **Sprint Backlog Commitments**: Selected list of stories with story points totaling target velocity.
- **Sub-task Breakdown & Dependencies**: Detailed planning notes.
- **Risk Mitigation Tactics**: Plan for what to drop if the team falls behind during the sprint.
