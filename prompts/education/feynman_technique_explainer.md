# Education Prompt: Feynman Technique Mental Model Explainer

## Purpose
Deconstruct highly complex, abstract, or technical concepts into plain, intuitively understandable language using the 4-step Feynman Technique (Explain to a child -> Identify gaps -> Simplify & elucidate -> Re-explain via analogy).

## Inputs
- `COMPLEX_CONCEPT`: The advanced concept, equation, or protocol (e.g., Raft Consensus Algorithm, Fourier Transform, Zero-Knowledge Proofs).
- `TARGET_INTUITION_LEVEL`: Desired mental depth (e.g., High Schooler, Non-Technical Executive, General Public).
- `COMMON_MISCONCEPTIONS`: Prevalent incorrect mental models or confusing jargon surrounding the topic.

## Instructions
1. **Step 1: Simple Primary Explanation**: Explain `COMPLEX_CONCEPT` using simple conversational vocabulary, strictly avoiding un-explained domain jargon.
2. **Step 2: Real-World Visual Analogy**: Construct a concrete visual analogy mapping every abstract component of the concept to familiar physical objects or everyday human interactions.
3. **Step 3: Gap Identification & Misconception Breakdown**: Highlight where standard intuition breaks down and dismantle `COMMON_MISCONCEPTIONS`.
4. **Step 4: Reconstruction & Mental Model Verification**: Rebuild the concept back to its full technical definition step-by-step, explaining *why* each technical detail exists.
5. Provide a self-test question that lets the learner test their conceptual understanding.

## Constraints
- Never rely on jargon circularity (explaining an unknown term using another unknown term).
- Ensure analogies accurately reflect structural mechanics without introducing misleading factual inaccuracies.

## Expected output
- **Plain English Breakdown**: Simple, jargon-free primary overview.
- **Physical Analogy**: Visual real-world analogy.
- **Misconception Audit**: Explanation of common traps and why they are wrong.
- **Synthesis & Verification Test**: Concluding summary and self-assessment prompt.
