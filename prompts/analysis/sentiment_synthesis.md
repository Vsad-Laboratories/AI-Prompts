# Analysis Prompt: Qualitative Sentiment Synthesis

## Purpose
Synthesize unstructured qualitative comments from surveys, app reviews, or feedback forums into clear, clustered emotional sentiments and behavioral trends.

## Inputs
- `FEEDBACK_REVIEWS`: The raw text of 10 to 100 customer reviews, support transcripts, or feedback responses.
- `TARGET_PRODUCT_ASPECT`: The specific area we want to analyze (e.g., onboarding flow, pricing structure, reliability).

## Instructions
1. Review the `FEEDBACK_REVIEWS` to tag emotional undertones (e.g., frustrated, satisfied, indifferent, confused).
2. Categorize feedback into 3-5 distinct **Sentiment Themes** specific to the `TARGET_PRODUCT_ASPECT`.
3. Select representative direct quotes that best capture each sentiment theme.
4. Create a **Priority Matrix**: Rank the themes based on user volume and emotional intensity (e.g., High Frustration / High Volume should be priority #1).
5. Recommend 3 concrete product improvements or feature adjustments to address the top sentiment themes.

## Constraints
- Do not filter out negative reviews or highlight only positive reviews; represent the feedback distribution honestly.
- Rely solely on explicit statements in the feedback, avoiding over-interpretation or projecting personal assumptions.

## Expected output
- **Sentiment Themes & Quotes**: Table detailing theme name, emotional tone, volume estimate, and representative quotes.
- **Priority Matrix**: Grid or ranked list indicating which problems require immediate attention.
- **Actionable Feedback Response**: Recommendations for product, engineering, or support updates.
