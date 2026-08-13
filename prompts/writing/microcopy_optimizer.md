# Writing Prompt: Microcopy and UX Writing Optimizer

## Purpose
Optimize UI text, buttons, modals, error messages, and onboarding microcopy to improve user clarity, conversion, and task success rates.

## Inputs
- `CURRENT_MICROCOPY`: The current text block or UI copy under review.
- `USER_CONTEXT_AND_STATE`: The screen name, user state (e.g., frustrated after a form failure, excited during checkout), and goal.

## Instructions
1. Analyze the `CURRENT_MICROCOPY` and evaluate its clarity, brevity, and emotional alignment with the `USER_CONTEXT_AND_STATE`.
2. Apply standard UX writing guidelines:
   - Be extremely clear and jargon-free.
   - Be concise (eliminate unnecessary filler words).
   - Be helpful and action-oriented (show the user exactly what to do next).
3. Draft 3 distinct alternative variants of the microcopy:
   - **Variant 1 (Ultra-Concise)**: Focuses on absolute minimum character count.
   - **Variant 2 (Conversational/Friendly)**: Adds warmth and emotional reassurance.
   - **Variant 3 (Value-Driven)**: Highlights the benefit of completing the action.
4. Recommend the best variant based on the user's current psychological state.

## Constraints
- Never use dark patterns or deceptive language to trick the user.
- Keep strict character constraints typical of mobile or web buttons and modals.

## Expected output
- **Copy Evaluation Summary**: Analysis of current copy friction points.
- **Optimized Copy Board**: Table showing the 3 copy variants mapped against key UI elements.
- **Psychological Justification**: Logical reasoning explaining why the selected variant is the most effective.
