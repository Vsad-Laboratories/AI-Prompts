# Coding Prompt: Robust API Endpoint Design

## Purpose
Design a highly secure, performant, resilient, and well-documented REST or GraphQL API endpoint that handles error cases gracefully and handles load efficiently.

## Inputs
- `ENDPOINT_DESCRIPTION`: What the endpoint does, including method, path, and purpose.
- `DATA_SCHEMA`: Input/output structures or databases involved.

## Instructions
1. Analyze the `ENDPOINT_DESCRIPTION` and `DATA_SCHEMA`.
2. Design the request validation rules (headers, parameters, body validation).
3. Outline the internal logic flow, including authorization checks, database transactions, caching strategy, and logging points.
4. Define standard error responses (400, 401, 403, 404, 429, 500) with specific message structures.
5. Provide a clean code implementation with integrated error handling, rate limiting, and defensive validation.

## Constraints
- Never return raw database exceptions or internal stack traces to the client.
- Always include input sanitization and parameter constraints (e.g., length, type, regex pattern).

## Expected output
- **API Specification Summary**: Method, path, headers, request schema, response schema.
- **Error Matrix**: List of errors, their HTTP status codes, and JSON response bodies.
- **Robust Implementation**: Clean, self-documenting code with inline comments explaining design decisions.
