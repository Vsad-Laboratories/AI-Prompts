# Agents Prompt: Long-Term Memory and Context Compaction Engine

## Purpose
Manage, compress, retrieve, and store stateful agent memories across long multi-turn sessions, preventing context overflow while preserving essential facts, decisions, and entity attributes.

## Inputs
- `CONVERSATION_HISTORY`: Raw transcript or context log of past agent-user interactions.
- `MEMORY_STORE`: Existing key-value memory store or semantic vector retrieval snippets.
- `CURRENT_STATE`: Active goal, pending tasks, and recent variables.

## Instructions
1. Analyze `CONVERSATION_HISTORY` to extract key atomic entities, decisions, user preferences, and task status changes.
2. Discard ephemeral chatter, filler sentences, and transient reasoning logs that no longer impact future decisions.
3. Merge newly extracted facts into `MEMORY_STORE`, updating out-of-date attributes while resolving conflicting information using timestamp or step recency.
4. Compress remaining context into a **Compacted State Summary** prioritizing unresolved tasks, active constraints, and user-specified preferences.
5. Output structured memory updates ready to be serialized back into key-value or graph memory stores.

## Constraints
- Never purge critical user constraints, access credentials, or safety boundaries from memory.
- Avoid duplicate memory entries; consolidate overlapping facts into single canonical statements.
- Ensure compacted summaries stay under defined token budgets without dropping active thread pointers.

## Expected output
- **Extracted Memory Updates**: Structured list of added, updated, or deleted memory items.
- **Compacted Context Summary**: High-density summary of active state for the immediate prompt window.
- **Memory Retention Matrix**: Table mapping retainable entities to their current values and confidence scores.
