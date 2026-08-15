# Meta Prompt: Complex Prompt Task Decomposition Framework

## Purpose
Deconstruct monolithic, overly broad, or multi-faceted prompt requests into structured sequences of modular, specialized sub-prompts linked by explicit data contracts.

## Inputs
- `MONOLITHIC_PROMPT`: The original, complex prompt that attempts to solve multiple distinct subtasks simultaneously.
- `TARGET_PIPELINE_ARCHITECTURE`: Single-agent sequential, multi-agent parallel, or DAG execution model.
- `TOKEN_CONSTRAINTS`: Context window limits or latency budgets per pipeline execution stage.

## Instructions
1. Analyze `MONOLITHIC_PROMPT` to identify distinct cognitive subtasks (e.g., retrieval, filtering, reasoning, code generation, critique, formatting).
2. Map out a **Pipeline DAG (Directed Acyclic Graph)** defining the logical flow and dependency order of subtasks.
3. Formulate individual, single-purpose **Sub-Prompts** for each stage in the pipeline.
4. Establish explicit **Data Contracts (Schemas)** for inputs and outputs transferred between each sub-prompt stage.
5. Create an **Orchestrator Control Ruleset** to handle stage failures, invalid sub-outputs, and dynamic routing decisions.

## Constraints
- Ensure each decomposed sub-prompt adheres strictly to single-responsibility principles.
- Avoid loose string interfaces between steps; enforce structured JSON or key-value data passing schemas.

## Expected output
- **Task Decomposition DAG**: Visual or textual flow diagram of decomposed stages.
- **Sub-Prompt Specifications**: Complete modular prompts for each execution stage.
- **Inter-Stage Data Schemas**: JSON input/output schemas for data transfer between stages.
- **Pipeline Failure Recovery Rules**: Instructions for stage retries and fallback execution.
