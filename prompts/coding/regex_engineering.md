# Coding Prompt: Regex Engineering

## Purpose
Design, construct, and optimize highly precise, readable, and safe regular expressions to parse complex strings while mitigating Catastrophic Backtracking.

## Inputs
- `TARGET_PATTERN_DESCRIPTION`: Detailed description of the text pattern to match or capture (e.g., nested HTML tags, complex log structures, localized phone numbers).
- `SAMPLE_INPUT_MATCHES`: Examples of strings that should match successfully.
- `SAMPLE_INPUT_NON_MATCHES`: Examples of strings that must fail to match.
- `ENGINE_FLAVOR`: The regular expression parser flavor (e.g., PCRE, JavaScript, Python re, Rust regex).

## Instructions
1. Analyze the syntactic components of `TARGET_PATTERN_DESCRIPTION` to establish clear matching rules.
2. Draft a regular expression that cleanly separates capture groups and utilizes non-capturing groups when appropriate.
3. Validate the regex pattern against all provided `SAMPLE_INPUT_MATCHES` and `SAMPLE_INPUT_NON_MATCHES`.
4. Perform static analysis on the expression to identify nested quantifiers or overlapping match groups that could cause Catastrophic Backtracking under adversarial input.
5. Provide detailed, line-by-line annotation of the drafted regex pattern.

## Constraints
- Avoid lookbehind assertions if they are not supported by the selected `ENGINE_FLAVOR`.
- Ensure the regex does not cause catastrophic performance issues on very long, malformed input strings.

## Expected output
- **Engine-Optimized Regular Expression**: The exact compiled string pattern.
- **Detailed Token Breakdown**: Exhaustive explanations of every capture group, quantifier, and boundary assertion.
- **Security & Backtracking Analysis**: A security audit to guarantee safe computation time.
- **Test Matrix Validation**: Step-by-step trace of how the regex processes the sample inputs.
