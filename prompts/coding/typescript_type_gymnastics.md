# Coding Prompt: TypeScript Type Gymnastics

## Purpose
Design, implement, and audit complex, compile-time safe, and highly optimized TypeScript utility types for type-driven APIs and library architectures.

## Inputs
- `TARGET_TYPE_SPECIFICATION`: Detailed requirements for the custom type behavior (e.g., deeply flattening nested objects, transforming keys, validating parameter schemas).
- `TS_CONFIG_SETTINGS`: Key TypeScript configuration options (e.g., strict null checks, compiler target, strict templates).

## Instructions
1. Analyze the functional logic requested in `TARGET_TYPE_SPECIFICATION` to map out conditional, recursive, or mapping type structures.
2. Draft the TypeScript utility using advanced techniques (e.g., type inference using `infer`, template literal types, mapped types with key remapping, and recursive utilities).
3. Verify type-level correctness under edge cases, such as handling `any`, `never`, optional properties, or readonly arrays.
4. Perform structural analysis to ensure the compilation complexity does not trigger TS2589 "Type instantiation is excessively deep and possibly infinite".
5. Provide interactive, step-by-step type-evaluation examples.

## Constraints
- Avoid runtime overhead or injecting actual JS logic; focus purely on compile-time type-checking constraints.
- Make sure to explicitly document any TypeScript version dependencies (e.g., 4.x, 5.x) required for the code.

## Expected output
- **Advanced TypeScript Utility Code**: Ready-to-use generic type declarations.
- **Type Evaluation Walkthrough**: Explanations of how the type compiler resolves different nested states.
- **Compilation Complexity Assessment**: Measures to prevent compiler performance degradation.
- **Type Unit Tests**: Assertion examples using `Expect` and `Equal` helpers.
