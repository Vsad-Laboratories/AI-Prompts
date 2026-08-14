# Agents Prompt: Multi-Agent Blackboard Orchestrator

## Purpose
Coordinate and orchestrate multiple specialized AI agents using a shared Blackboard pattern to solve complex, multi-step workflows cooperatively.

## Inputs
- `WORKFLOW_TASK_GOAL`: The complex multi-step task to solve (e.g., parsing, evaluating, refactoring, and documenting a massive code repository).
- `AGENT_REGISTRY_AND_CAPABILITIES`: Names, roles, inputs, and outputs of the available specialized agents.

## Instructions
1. Analyze `WORKFLOW_TASK_GOAL` to decompose the task into a logical graph of dependent subtasks.
2. Formulate a centralized Blackboard state structure where agents can read tasks, write intermediate results, and register updates.
3. Design the orchestrator logic that dynamically assigns subtasks to matching agents from the `AGENT_REGISTRY_AND_CAPABILITIES`.
4. Outline communication and conflict resolution protocols when agents write conflicting data to the Blackboard.
5. Establish a failure recovery loop to re-route subtasks if an agent times out, returns malformed data, or fails its execution limits.

## Constraints
- Ensure the blackboard system avoids infinite loops where agents repeatedly edit the same state without advancing the workflow.
- Maintain strict modularity; agents should communicate only through the blackboard and never directly with each other.

## Expected output
- **Blackboard State Schema**: Structural representation (e.g., JSON schema) of the shared state blackboard.
- **Orchestration Workflow Graph**: Step-by-step logic detailing how tasks are created and assigned.
- **Agent Coordination Protocols**: Failsafes and rules for conflict resolution and state progression.
- **Trace Scenario Execution**: Example showing how agents cooperatively solve a complex subtask sequence.
