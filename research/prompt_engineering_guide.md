# Prompt Engineering & Standards Guide

This guide describes the methodology, evaluation criteria, and design standards used to construct the templates in this repository.

## The Standard Blueprint
Every production-ready prompt should follow this standard blueprint to guarantee readability and consistent LLM outputs:

1. **Purpose**: Defines the high-level goal, target model, and scope of work.
2. **Inputs**: A structured set of context parameters enclosed in backticks or tags (e.g., `` `USER_CONTEXT` ``).
3. **Instructions**: Ordered, actionable, logical instructions using active verbs.
4. **Constraints**: Defensive rules to prevent hallucination, leaking instructions, or falling back on poor analogies.
5. **Expected output**: A specific markdown blueprint of headings, tables, or JSON schemas that the LLM must generate.

## The 12 Evaluation Criteria
We assess prompt quality based on these 12 variables:
- **Clarity**: Avoidance of ambiguous or circular vocabulary.
- **Specificity**: Precision of commands and structural definitions.
- **Reliability**: Consistent task execution across model restarts.
- **Reusability**: Ability to run the prompt on different inputs.
- **Generalization**: Model-agnostic performance (works across open-weights and commercial models).
- **Output consistency**: Conformance to the expected output schema.
- **Robustness**: High failure resistance under adversarial or low-quality inputs.
- **Practical usefulness**: Solves a real-world, high-value problem.
- **Novelty**: Offers a unique approach to task completion (e.g., First-Principles, Dialectical Debate).
- **Failure resistance**: Explicit instructions for edge-case recovery or error signaling.
- **Context efficiency**: Avoidance of verbose, redundant filler words.
- **Adaptability**: Graceful handling of different input lengths and complexity tiers.
