# Coding Prompt: CSS Grid and Flexbox Troubleshooter

## Purpose
Inspect, debug, and optimize complex frontend layout code using CSS Grid and Flexbox to resolve responsive design, alignment, overflow, and rendering issues across modern browsers.

## Inputs
- `HTML_AND_CSS_CODE`: The code snippet containing the problematic grid or flex container and its children.
- `EXPECTED_LAYOUT_BEHAVIOR`: A description of how the layout should adapt, align, or scale under different viewports and conditions.

## Instructions
1. Analyze `HTML_AND_CSS_CODE` to isolate layout structure, positioning rules, and sizing declarations (e.g., fractional units, flex properties, min/max bounds).
2. Trace rendering issues (e.g., unintended child wrapping, unexpected overflows, alignment shifts) back to conflicting property settings.
3. Formulate structural modifications utilizing CSS Grid template areas or precise Flexbox scaling parameters.
4. Refactor the code to achieve the goals in `EXPECTED_LAYOUT_BEHAVIOR`, verifying responsive breakpoints.
5. Provide a clear visual walkthrough of the new layout behavior under different container dimensions.

## Constraints
- Avoid proposing external utility framework overrides (e.g., Tailwind CSS, Bootstrap) unless specified in the context.
- Ensure the refactored CSS maintains clean separation of layout concerns and avoids excessive nested wrapper tags.

## Expected output
- **Layout Conflict Analysis**: Precise breakdown of why the current CSS layout is broken.
- **Refactored HTML & CSS Code**: Valid, clean, and responsive grid/flex styles.
- **Responsive Dimension Matrix**: Sizing guidelines for mobile, tablet, and desktop viewports.
- **Cross-Browser Verification Notes**: Notes highlighting potential rendering variations in Safari, Chrome, and Firefox.
