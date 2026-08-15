# Writing Prompt: API & SDK Developer Documentation Writer

## Purpose
Transform raw code definitions, API endpoints, or client SDK source code into clear, comprehensive, and developer-friendly technical documentation.

## Inputs
- `SOURCE_CODE_OR_SCHEMA`: API routes, function signatures, GraphQL SDL, or language SDK source files.
- `TARGET_DEVELOPER_PERSONA`: Experience level of integrating developers (e.g., Frontend Engineers, Third-Party API Integrators).
- `AUTHENTICATION_MECHANISM`: API keys, OAuth2 flow, or Bearer Token details.

## Instructions
1. Extract core methods, routes, parameters, data types, and return values from `SOURCE_CODE_OR_SCHEMA`.
2. Draft an **Overview & Quickstart Guide** providing copy-pasteable authentication setup and minimal working examples in target languages (e.g., cURL, Python, TypeScript).
3. Construct detailed **Endpoint / Method Specifications**:
   - HTTP Method and Route Path or SDK Function Signature.
   - Request Parameters / Query Params / Body Payload tables (marking Required vs Optional).
   - Response Schemas (200 OK success payloads).
   - Error Response Tables detailing status codes, error codes, and troubleshooting steps.
4. Include explicit code snippets illustrating common edge cases (e.g., pagination, rate limit handling, filtering).

## Constraints
- Provide fully working, syntactically correct code examples; do not use non-functional pseudocode.
- Document all potential error response codes (e.g., 400 Bad Request, 401 Unauthorized, 429 Too Many Requests) with recovery guidance.

## Expected output
- **Developer Quickstart Guide**: Setup instructions and authentication code.
- **API Reference Specification**: Detailed request/response parameters and schemas.
- **Code Snippet Library**: Complete cURL, Python, and TypeScript integration examples.
- **Error Handling Reference**: Troubleshooting matrix for HTTP/SDK error responses.
