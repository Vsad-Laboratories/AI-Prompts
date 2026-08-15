# Coding Prompt: GraphQL Schema Design & Security Auditor

## Purpose
Design scalable, idiomatic GraphQL schemas while auditing query complexity, authorization boundaries, and N+1 query vulnerability mitigations.

## Inputs
- `DOMAIN_ENTITIES`: Core domain models, relationships, and business operations.
- `SECURITY_REQUIREMENTS`: Field-level permissions, role-based access controls (RBAC), and query rate limits.
- `PERFORMANCE_TARGETS`: Maximum allowed query nesting depth and batching constraints.

## Instructions
1. Design an idiomatic GraphQL SDL (Schema Definition Language) with clear types, interfaces, inputs, enums, and unions.
2. Enforce strict mutation patterns adhering to the `payload` input pattern with explicit error payload types.
3. Implement **Query Complexity & Depth Safeguards**: Configure maximum depth limits and query cost calculation rules to prevent Denial of Service (DoS) attacks.
4. Design **N+1 Resolver Patterns**: Provide DataLoader batching and caching resolver templates for nested relationships.
5. Audit field-level authorization directive rules to ensure protected user fields are not leaked.

## Constraints
- Avoid deep circular queries without depth limit guards.
- Do not return generic error messages on mutations; use explicit typed user errors.

## Expected output
- **GraphQL SDL Schema**: Modular, readable Schema Definition Language document.
- **Resolver Implementation Patterns**: Code examples demonstrating DataLoader batching.
- **Security & Complexity Rules**: Hardening guidelines for complexity, rate limiting, and RBAC.
