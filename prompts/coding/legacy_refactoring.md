# Coding Prompt: Legacy Code Refactoring and Modernization

## Purpose
Safely refactor, clean up, and modernize legacy code while preserving its exact functionality and performance characteristics.

## Inputs
- `LEGACY_CODE`: The code snippet or module to be modernised and cleaned up.
- `TARGET_STANDARDS`: The programming language version, style guidelines, or patterns to adopt (e.g., modern C++20, ES6 features, clean architecture).

## Instructions
1. Analyze the `LEGACY_CODE` to understand its core behavior, inputs, outputs, and side effects.
2. Identify specific "code smells" (e.g., long methods, global state, tight coupling, magic numbers, outdated libraries).
3. Draft a safe refactoring plan that preserves exact input-to-output mapping and runtime complexity.
4. Rewrite the code using the modern constructs and design patterns specified in `TARGET_STANDARDS`.
5. Provide a verification plan (such as unit tests or runtime checks) to prove functional equivalence.

## Constraints
- Never alter the public API, return types, or parameter contracts of the legacy module unless explicitly requested.
- Ensure that performance-critical hotpaths are not degraded by the modernization.

## Expected output
- **Code Smell Registry**: List of identified issues in the legacy block.
- **Refactoring Strategy**: Description of how to clean it up safely.
- **Modernized Implementation**: Clean, idiomatic, and documented code.
- **Equivalence Tests**: Unit test draft to verify functionality remains unchanged.
