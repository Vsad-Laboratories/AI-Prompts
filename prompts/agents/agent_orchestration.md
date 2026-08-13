# Agents Prompt: Multi-Agent Orchestration Protocol

## Purpose
Coordinate and orchestrate multiple specialized AI agents working together toward a complex goal, ensuring clear task handoff, conflict resolution, and information convergence.

## Inputs
- `GOAL`: The complex multi-step objective.
- `AGENTS_LIST`: Specialized agents (e.g., Researcher, Editor, Code Generator, Auditor).

## Instructions
1. Analyze the overall `GOAL` and identify the required sequential or parallel phases.
2. Assign specific, mutually exclusive subtasks to each agent in `AGENTS_LIST`.
3. Design a **Handoff Protocol**: Define exactly how information is packaged and transferred from one agent to the next (e.g., state variables, JSON payload, summary reports).
4. Create a **Conflict Resolution Protocol**: Establish what happens when Agent A rejects Agent B's output (e.g., feedback loops, criteria checks).
5. Specify an **Orchestrator Role**: Define a central routing prompt responsible for state-tracking, scheduling, and declaring task completion.

## Constraints
- Avoid circular handoffs where agents get stuck loop-criticizing each other indefinitely; specify a maximum loop depth.
- Standardize all inputs and outputs between agents to maintain reliable parsing.

## Expected output
- **Orchestration Workflow Map**: Sequential phase definition.
- **Agent Handoff Specifications**: Templates and schemas for data exchanges.
- **Feedback & Rejection Rules**: Structured process for revisions.
- **Orchestrator System Instructions**: Control logic to run the multi-agent system.
