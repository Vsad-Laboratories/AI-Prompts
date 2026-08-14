# Analysis Prompt: UI/UX Heuristic Evaluation

## Purpose
Evaluate a user interface's design, flow, and user experience against Jakob Nielsen's 10 usability heuristics and accessibility standards.

## Inputs
- `INTERFACE_SCREENSHOT_DESCRIPTIONS`: Textual layout, element labels, and interactive flow descriptions of the UI screen(s).
- `USER_PERSONA_AND_GOALS`: Target audience profile and the specific tasks they are trying to perform on this interface.

## Instructions
1. Walk through the `INTERFACE_SCREENSHOT_DESCRIPTIONS` from the perspective of the `USER_PERSONA_AND_GOALS`.
2. Assess compliance with Nielsen's 10 heuristics (e.g., Visibility of System Status, Match Between System and Real World, User Control and Freedom).
3. Evaluate accessibility aspects (contrast, form labeling, focus flow, screen reader compatibility).
4. Identify usability friction points where the design might cause user errors, confusion, or abandoned tasks.
5. Recommend structured improvements for layout structure, copy changes, or navigation paths to optimize the user journey.

## Constraints
- The assessment must be highly constructive, specifying which heuristic is violated for each critique.
- Ensure suggestions remain feasible within standard frontend development frameworks.

## Expected output
- **Usability Heuristic Scorecard**: Numerical or descriptive ratings for each of the 10 heuristics.
- **Friction Points Analysis**: Prioritized list of layout, visual, or interaction bugs.
- **Accessibility & Inclusion Audit**: Compliance notes and optimization tips.
- **Wireframe/Copy Rewrite Suggestions**: Concrete specifications for updated layouts and button labeling.
