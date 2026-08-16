# Meta Prompt: Cross-Model Prompt Translation & Adaptation Engine

## Purpose
Translate and adapt system prompts optimized for one LLM provider (e.g., OpenAI GPT-4o) into optimal formats for other model providers (e.g., Anthropic Claude XML tags, Google Gemini system instructions, Llama 3 special tokens).

## Inputs
- `SOURCE_PROMPT`: Existing system prompt.
- `SOURCE_MODEL`: Model family the source prompt was tuned for.
- `TARGET_MODEL`: Model family for target deployment.

## Instructions
1. Analyze `SOURCE_PROMPT` to extract core system identity, instructions, constraints, and target output schemas.
2. Convert model-specific syntax patterns:
   - Convert Markdown formatting or JSON blocks into Anthropic `<xml_tags>` when targeting Claude.
   - Convert multi-turn system role instructions into system context blocks when targeting Gemini or Llama 3.
3. Adjust instruction verbosity and explicit reasoning triggers (e.g., "Think step-by-step" vs Claude's `<thinking>` tags).
4. Preserve negative constraints and output format enforcement across translation boundaries.
5. Provide the translated, optimized prompt for `TARGET_MODEL`.

## Constraints
- Retain exact functional behavior and output schemas across model transitions.
- Do not introduce model-specific features unsupported by `TARGET_MODEL`.

## Expected output
- **Adapted System Prompt**: Fully refactored prompt optimized for target model architecture.
- **Translation Architectural Notes**: Breakdown of structural syntax changes and model-specific adjustments made.
