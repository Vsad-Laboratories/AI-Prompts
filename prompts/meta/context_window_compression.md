# Meta Prompt: Context Window Compression and Summarization

## Purpose
Compress oversized document collections, codebase contexts, or prompt histories into dense, information-rich summaries while guaranteeing zero loss of key variables, structural facts, or constraints.

## Inputs
- `RAW_CONTEXT`: Large input text, source code snippets, or conversational transcripts to compress.
- `TARGET_COMPRESSION_RATIO`: Target token reduction percentage (e.g., 50%, 80%, 90%).
- `CRITICAL_INVARIANTS`: Specific variables, code signatures, dates, constraints, or decisions that MUST be preserved verbatim.

## Instructions
1. Perform an **Information Density Scan** on `RAW_CONTEXT` to classify text into High-Value Invariants, Medium-Value Narrative Context, and Low-Value Redundancy/Filler.
2. Strip all conversational pleasantries, repetitive preamble, passive voice constructs, and redundant examples.
3. Convert narrative paragraphs into high-density bulleted logic statements, relational tables, or concise structured key-value pairs.
4. Verify that all elements listed in `CRITICAL_INVARIANTS` remain present without modification or truncation.
5. Calculate and report the final compression token ratio alongside an integrity evaluation.

## Constraints
- Never truncate or alter code signatures, cryptographic keys, numeric thresholds, or business rules explicitly marked in `CRITICAL_INVARIANTS`.
- Avoid lossy summarization that substitutes specific facts with vague generalities (e.g., replacing exact timestamps with "recently").

## Expected output
- **Compacted Context Payload**: High-density compressed representation of original context.
- **Invariant Preservation Check**: Verification matrix confirming invariant integrity.
- **Compression Efficiency Metrics**: Token reduction percentage and estimated token savings.
