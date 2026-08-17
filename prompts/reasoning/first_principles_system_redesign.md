# First-Principles System Redesign Engine

## Purpose
Deconstruct legacy, overly complex, or inefficient software systems, organizational workflows, or physical processes into their foundational physical, mathematical, and logical constraints, eliminating historical legacy assumptions to engineer clean-slate, first-principles solutions.

## Inputs
- `LEGACY_SYSTEM_DESCRIPTION`: Overview of current architecture, historical workflows, tech stack, and accumulated operational friction.
- `CORE_OBJECTIVE`: The fundamental functional outcome the system MUST accomplish.
- `FUNDAMENTAL_CONSTRAINTS`: Non-negotiable physical, laws-of-physics, mathematical, regulatory, or hardware limitations.

## Instructions
1. **Strip Away Historical Analogs & Legacy Assumptions**: Identify and discard "that's how we've always done it" assumptions, obsolete hardware constraints, legacy compatibility hacks, and organizational inertia.
2. **Deconstruct to Atomic Axioms**: Reduce `LEGACY_SYSTEM_DESCRIPTION` to its absolute foundational elements:
   - What are the elemental inputs?
   - What is the essential state transformation required?
   - What are the absolute theoretical minimum resources ($O(1)$ time, $O(1)$ memory, minimum network round-trips) needed to complete `CORE_OBJECTIVE`?
3. **Analyze Fundamental Bottlenecks**: Distinguish between *artificial constraints* (imposed by current tooling/design choices) and *fundamental constraints* (imposed by physics, math, or network speed of light).
4. **Engineer Clean-Slate System Architecture**: Build a theoretical optimal system strictly from the fundamental axioms up, disregarding legacy interfaces.
5. **Formulate Pragmatic Migration Bridge**: Map a progressive migration pathway from the current legacy state to the clean-slate architecture.

## Constraints
- **Zero Legacy Analogy Fallback**: The prompt MUST NOT justify any architectural component based on industry convention or historical precedent.
- **Strict Axiomatic Reasoning**: Every component in the clean-slate design MUST explicitly link back to a fundamental constraint or fundamental objective.
- **Quantify Theoretical Limits**: Contrast current system performance against fundamental physics/mathematical limits (e.g., actual speed vs. network latency floor).

## Expected Output Format
```markdown
### 1. Deconstruction & Legacy Assumption Audit
| Current System Feature | Historical Assumption | Fundamental Truth / Axiom | Status |
| :--- | :--- | :--- | :--- |
| Batch ETL processing at midnight | Storage/compute was expensive in 1995 | Streaming event evaluation takes <1ms on modern memory | ARTIFICIAL CONSTRAINT (REMOVE) |
| Relational table lock synchronization | Single-node relational database required | Memory updates are commutative under CRDT logic | ARTIFICIAL CONSTRAINT (REMOVE) |

### 2. Fundamental Axioms & Theoretical Limits
- **Essential Objective**: Compute global account balance given stream of debit/credit transactions.
- **Theoretical Latency Floor**: Network RTT between client and closest edge region ($\approx 12\text{ms}$).
- **Minimum Compute Complexity**: $O(1)$ state update per transaction using streaming state machines.

### 3. First-Principles Clean-Slate Architecture
```text
[Client Event] ---> [Edge State Machine (WASM / In-Memory CRDT)] ---> [Append-Only Distributed Log]
```
- **Key Design Shift**: Replaced multi-layer relational ORM database with localized, stateful edge execution nodes.

### 4. Migration Bridge Strategy
- **Phase 1**: Intercept legacy writes and mirror stream to Edge State Engine.
- **Phase 2**: Dual-read verification.
- **Phase 3**: Deprecate legacy batch database pipelines.
```

## Evaluation Criteria
- **Depth of Deconstruction**: Successfully strips away hidden historical assumptions.
- **Axiomatic Integrity**: Clean-slate design is built purely from foundational mathematical and logical principles.
- **Innovation Index**: Delivers orders-of-magnitude improvements in simplicity, cost, or performance.

## Failure Considerations
- **Incremental Refactoring**: Simply tweaking existing legacy code without questioning fundamental design choices.
- **Impractical Abstractions**: Designing theoretical solutions that violate hard physical limits or regulatory laws.
