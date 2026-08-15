# Coding Prompt: API Backwards Compatibility Auditor

## Purpose
Audit existing API endpoints, data models, or client SDK schemas against proposed breaking changes to guarantee backwards compatibility and prevent downstream integrations from breaking.

## Inputs
- `EXISTING_API_SCHEMA`: OpenAPI/Swagger, GraphQL, or Protobuf definition of current API version.
- `PROPOSED_CHANGES`: Proposed modifications, new fields, removed endpoints, or type updates.
- `CLIENT_USAGE_PATTERNS`: Known client payload expectations or mobile SDK version constraints.

## Instructions
1. Compare `PROPOSED_CHANGES` against `EXISTING_API_SCHEMA` field-by-field and endpoint-by-endpoint.
2. Flag all **Breaking Changes**, including:
   - Field removals or name changes.
   - Changing optional fields into required fields.
   - Modifying field data types or response enum definitions.
   - Modifying status code definitions or error payload schemas.
3. Identify **Non-Breaking Changes** (e.g., adding optional parameters, introducing deprecation headers).
4. Propose safe migration strategies for breaking changes (e.g., field deprecation lifecycle, header-based API versioning, transformation adapters).
5. Output code/schema refactoring examples showing backward-compatible implementations.

## Constraints
- Never approve direct field removals in active API versions without a documented deprecation cycle.
- Ensure strict compliance with Semantic Versioning (SemVer) conventions.

## Expected output
- **Breaking Change Audit Matrix**: Categorized list of safe vs breaking modifications.
- **Client Impact Risk Assessment**: Impact evaluation across SDKs and integrations.
- **Backward-Compatible Refactored Schema**: Corrected API schema preserving legacy compatibility.
- **Deprecation & Versioning Strategy**: Step-by-step deprecation timeline.
