# Agents Prompt: Dynamic Multi-Agent Handoff & State Transfer Protocol

## Purpose
Coordinate stateful task transfers, context serialization, and operational control handoffs between specialized autonomous agents in a multi-agent system.

## Inputs
- `SOURCE_AGENT`: Role, context, and current state of the transferring agent.
- `TARGET_AGENT`: Role, capabilities, and required input interface of the receiving agent.
- `TASK_CONTEXT`: Current task progress, completed milestones, intermediate artifacts, and remaining goals.

## Instructions
1. Inspect `TASK_CONTEXT` and extract key variables, facts, decisions, and intermediate outputs.
2. Structure a serialized "Handoff Packet" containing explicit task status, target goals, and operational constraints.
3. Define the precise triggering condition that necessitates the handoff.
4. Formulate the explicit confirmation acknowledgment schema required from `TARGET_AGENT` before control transfer completes.
5. Provide a complete multi-agent handoff simulation demonstrating seamless context preservation.

## Constraints
- Never lose historical facts or decisions during state serialization.
- Set strict boundaries on target agent responsibilities to avoid duplicated work.
- Handle state transfer failure gracefully with a rollback or escalation protocol.

## Expected output
- **Handoff Trigger Definition**: Explicit logic determining when handoff occurs.
- **Serialized Context Packet**: Structured state payload transferred between agents.
- **Target Agent Activation Instructions**: System instructions injected into the receiving agent.
- **State Transfer Walkthrough**: Concrete multi-agent handoff example.
