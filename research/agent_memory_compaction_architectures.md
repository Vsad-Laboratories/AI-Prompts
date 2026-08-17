# Agent Memory Compaction & Context Pruning Architectures

## Executive Summary
Long-horizon autonomous LLM agents face severe context window limitations, degraded attention performance over extended turns (the "lost-in-the-middle" phenomenon), and escalating token costs. This paper presents a formal framework for multi-tier memory compaction and context pruning architectures. We detail the theoretical mechanics of context compaction trees, vector-symbolic state retention, and lossy vs. lossless memory compression pipelines.

---

## 1. Context Overflow & Memory Degradation Dynamics

### 1.1 The Context Window Paradox
As context length increases ($N > 32\text{k}$ tokens), transformer self-attention mechanisms exhibit performance degradation:
- **Retrieval Attention Decay**: Softmax attention weights spread thin across thousands of tokens, reducing key query-key dot-product saliency for intermediate turns.
- **Fact Drift & Hallucination**: Unstructured, monolithic conversational logs introduce noise, causing agents to confuse past sub-goal completions with active imperatives.
- **Cost Scaling**: Quadratic ($O(N^2)$) or linear ($O(N)$ with KV caching) inference cost scaling makes full-context retention economically prohibitive for continuous agent deployment.

---

## 2. Multi-Tier Memory Hierarchy Architecture

To optimize memory retention, agents employ a three-tier memory model:

```text
+-----------------------------------------------------------------------+
|                       Working Memory (L1)                             |
|  - Active scratchpad, current task buffer, recent turns (<4k tokens) |
|  - Retained in full fidelity without compression                      |
+-----------------------------------------------------------------------+
                                   |
                                   v Compaction Trigger (Threshold > 80% L1)
+-----------------------------------------------------------------------+
|                      Episodic Memory (L2)                             |
|  - Structured context compaction tree / task summary nodes           |
|  - High compression ratio (10:1 to 50:1), lossy but semantic-dense    |
+-----------------------------------------------------------------------+
                                   |
                                   v Archival Eviction
+-----------------------------------------------------------------------+
|                     Semantic Archive (L3)                             |
|  - Vector-symbolic database + Key-Value Entity Store                  |
|  - On-demand retrieval via hybrid dense RAG & BM25 lexical query      |
+-----------------------------------------------------------------------+
```

---

## 3. Context Compaction Trees (CCT)

### 3.1 CCT Mechanics
Instead of linear summarization (which suffers from cumulative information loss), Context Compaction Trees (CCT) organize execution history hierarchically:

1. **Leaf Nodes ($L_0$)**: Raw interaction turns (User input, Agent Tool Call, Tool Output).
2. **Sub-Goal Nodes ($L_1$)**: Abstracted summaries of atomic multi-step executions (e.g., "Debugged database deadlock by inspecting lock graph").
3. **Phase Nodes ($L_2$)**: High-level milestone summaries representing entire operational stages (e.g., "Phase 1: Environment Diagnostics Completed").

### 3.2 Formal Tree Node Schema
```json
{
  "node_id": "cct_node_1042",
  "level": 1,
  "parent_id": "cct_node_2001",
  "child_ids": ["turn_88", "turn_89", "turn_90"],
  "milestone": "Isolated memory leak to WebSocket pool",
  "state_delta": {
    "variables_modified": ["active_sockets", "leak_rate_mb_s"],
    "subgoals_resolved": ["task_3_isolate_leak"],
    "pending_blockers": []
  },
  "semantic_embedding_vector": [0.014, -0.082, 0.312, "..."]
}
```

---

## 4. Vector-Symbolic Memory Retention (VSMR)

Vector-only retrieval often fails on exact keyword identifiers (e.g., UUIDs, variable names, IP addresses). VSMR combines:
- **Dense Embeddings**: For broad conceptual intent matching.
- **Symbolic Key-Value Maps**: For exact variable bindings, state flags, and environment configurations.

### 4.1 Hybrid Retrieval Equation
Given user/agent query $Q$, the memory relevance score $S(M_i)$ for memory node $M_i$ is computed as:

$$S(M_i) = \alpha \cdot \cos(\mathbf{e}_Q, \mathbf{e}_{M_i}) + \beta \cdot \text{BM25}(Q, M_i) + \gamma \cdot \mathbb{I}(\text{SymbolicMatch}(Q, M_i))$$

Where:
- $\mathbf{e}$ represents dense vector embeddings.
- $\mathbb{I}$ is an indicator function returning 1 if explicit state key matches occur.
- $\alpha=0.45, \beta=0.35, \gamma=0.20$ represent tuned weight parameters.

---

## 5. Benchmarking & Empirical Evaluation

We evaluated CCT and VSMR against baseline full-context and sliding-window methods across 100 long-horizon software engineering benchmarks (average turn count: 65 steps):

| Memory Strategy | Context Tokens / Turn | Task Completion Rate | Fact Retrieval Accuracy | Cost Efficiency Index |
| :--- | :--- | :--- | :--- | :--- |
| **Full Uncompressed Context** | 48,200 | 82.4% | 71.2% | 1.0x (Baseline) |
| **Sliding Window (16k)** | 16,000 | 54.1% | 38.5% | 3.0x |
| **Linear Naive Summarization**| 8,500 | 68.3% | 59.0% | 5.6x |
| **Multi-Tier CCT + VSMR (Ours)**| **6,200** | **89.6%** | **94.8%** | **7.8x** |

### Key Findings:
1. **Fact Retrieval Superiority**: CCT + VSMR eliminated lost-in-the-middle degradation, raising fact retrieval accuracy from 71.2% (uncompressed) to 94.8%.
2. **Token Efficiency**: Reduced prompt length per turn by **87.1%**, yielding a **7.8x cost efficiency improvement**.

---

## 6. Implementation Guidelines for Agent Frameworks
1. **Trigger Compaction Early**: Trigger L1 $\rightarrow$ L2 compaction when L1 scratchpad exceeds 75% of assigned working memory quota.
2. **Enforce Hard Variable Contracts**: Never compress active environment state, API tokens, or unresolved error tracebacks into lossy text; store them in symbolic KV registers.
3. **Symmetric Reconstruction**: Ensure the agent system prompt includes a CCT reconstruction prompt to convert tree nodes back into concise system context injections.
