# Hierarchical Subagent Delegator Protocol

## Purpose
Design a production-grade, stateful hierarchical orchestration prompt that enables a primary orchestrator agent to decompose complex goals, dynamically spawn domain-specialized subagents with isolated context boundaries, monitor execution progress, handle subagent failures, and synthesize aggregated results into a coherent final deliverable.

## Inputs
- `PARENT_GOAL`: The overarching task or objective requiring multi-domain specialization.
- `AVAILABLE_SUBAGENTS`: Array or list of specialized subagent profiles, capabilities, tools, and constraints.
- `EXECUTION_CONTEXT`: Current system state, environmental variables, available resources, and budget constraints.
- `MAX_DELEGATION_DEPTH`: Maximum nested subagent call depth allowed (default: 2).

## Instructions
1. **Deconstruct Parent Goal**: Analyze `PARENT_GOAL` using first-principles task decomposition. Break down the goal into independent and dependent subtasks.
2. **Evaluate Subagent Capabilities**: Cross-reference subtasks against `AVAILABLE_SUBAGENTS`. Assign each subtask to the most suitable specialized subagent profile.
3. **Define Task Contracts & Context Isolation**: For each subagent assignment, construct a rigid operational contract specifying:
   - Target Subtask Objectives
   - Strict Input Parameters (pruned to avoid context bloat)
   - Mandatory Output Schema
   - Execution Time/Token Budget
4. **Execution Flow & Dependency Mapping**: Formulate an execution DAG (Directed Acyclic Graph) determining parallel execution tracks vs. sequential dependencies.
5. **Monitor & Evaluate Subagent Output**: Upon receiving subagent responses, evaluate them against task contract criteria. Detect incomplete execution, hallucination, or tool error state.
6. **Error Recovery & Re-delegation**: If a subagent fails or violates constraints, execute diagnostic self-reflection:
   - Retry with modified prompt parameters, OR
   - Re-delegate to an alternative subagent, OR
   - Fall back to orchestrator self-execution.
7. **Synthesis**: Aggregate verified outputs from all child subagents into a unified, coherent response adhering to the expected parent output format.

## Constraints
- **Strict Context Boundary**: Never pass the full parent execution transcript to child subagents. Pass only minimum required task context.
- **No Infinite Delegation Loops**: Enforce strict call depth tracking against `MAX_DELEGATION_DEPTH`.
- **Deterministic Handshake**: Subagent output MUST conform to the agreed JSON contract schema before being passed downstream.
- **Blameless Isolation**: Subagent crashes must be caught and handled gracefully without failing the entire parent orchestrator workflow.

## Expected Output Format
```markdown
### 1. Goal Decomposition & Delegation DAG
- **Task ID**: [Unique ID]
- **Specialized Subagent**: [Subagent Name]
- **Dependency**: [Dependencies or None]
- **Input Contract Summary**: [Key inputs provided]

### 2. Execution Log & Subagent Result Verification
- **Task ID**: [Unique ID]
- **Status**: [PASSED / FAILED / RETRIED]
- **Verification Score**: [0-100%]
- **Key Artifact Produced**: [Summary of verified output]

### 3. Final Synthesized Output
[Comprehensive, merged result addressing the PARENT_GOAL]
```

## Evaluation Criteria
- **Task Decomposition Quality**: Subtasks are modular, non-overlapping, and logically ordered.
- **Context Efficiency**: Context passed to subagents contains zero extraneous tokens.
- **Fault Resilience**: Subagent failure recovery mechanisms function deterministically.
- **Synthesis Integrity**: Final aggregate output completely resolves `PARENT_GOAL` without contradictions.

## Failure Considerations
- **Context Leakage**: Accidental inclusion of sensitive or oversized prompt context in subagent payloads.
- **Deadlocks in DAG**: Circular task dependencies preventing child subagents from starting.
- **Subagent Divergence**: Child subagent drifting from assigned sub-goal into unapproved operations.
