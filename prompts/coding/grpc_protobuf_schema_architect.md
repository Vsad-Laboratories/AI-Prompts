# gRPC & Protocol Buffers (Protobuf) Schema Architect

## Purpose
Design scalable, backwards-compatible, high-performance gRPC API interfaces and Protocol Buffers (proto3) schema definitions for microservices communication, enforcing strict field numbering rules, streaming semantics, error handling models, and linting guidelines.

## Inputs
- `SERVICE_REQUIREMENTS`: Functional specifications, domain entities, RPC methods required, streaming requirements (Unary, Server Streaming, Client Streaming, Bidirectional Streaming).
- `API_VERSIONING_POLICY`: Versioning strategy (e.g., `v1`, `v1alpha1`, `v2`), package naming guidelines.
- `PERFORMANCE_CONSTRAINTS`: Target message size limits, serialization latency budgets, field frequency assumptions.

## Instructions
1. **Design Proto3 Package & File Structure**: Establish directory structures, package declarations (`package enterprise.order.v1;`), and options for target language generation (`go_package`, `java_package`, `csharp_namespace`).
2. **Define Field ID Allocation Strategy**:
   - Assign field numbers `1` through `15` to frequently transmitted, high-throughput fields (encoded in 1 byte varint tag).
   - Assign field numbers `16` through `2047` for less frequent or secondary fields (encoded in 2 bytes).
3. **Architect Enums & Default Value Rules**:
   - Every enum MUST begin with a `0` value named `<ENUM_NAME>_UNSPECIFIED` to safely handle proto3 default value zeroing.
4. **Architect Service RPC Definitions**:
   - Structure unary and streaming RPC signatures using explicit request/response message types (e.g., `rpc CreateOrder(CreateOrderRequest) returns (CreateOrderResponse);`). Never use empty types directly in RPC declarations unless using `google.protobuf.Empty`.
5. **Enforce Backwards Compatibility Rules**:
   - Mark deprecated fields with `[deprecated = true];`.
   - Utilize `reserved` statements (`reserved 4, 8, 12 to 15;`, `reserved "legacy_field";`) to prevent future developers from reusing deleted field tags.
6. **Incorporate Standardized gRPC Error Handling**:
   - Utilize Google's `google.rpc.Status` rich error model (`code`, `message`, `details` containing `google.rpc.BadRequest` or `google.rpc.PreconditionFailure`) rather than string parsing error bodies.

## Constraints
- **Never Modify Field Tag Numbers**: Once published in a production package version, field numbers MUST NEVER be reassigned or altered.
- **Proto3 Syntax Strictness**: Use `syntax = "proto3";` exclusively.
- **Explicit Reserve Declarations**: Any deleted message field or enum value MUST be added to a `reserved` block immediately.

## Expected Output Format
```markdown
### 1. Protobuf Package Architecture
- **Proto Package**: `enterprise.[domain].[subdomain].v1`
- **Source File Path**: `proto/enterprise/[domain]/v1/[service].proto`

### 2. Complete Protobuf (proto3) Schema Definition
```protobuf
syntax = "proto3";

package enterprise.order.v1;

option go_package = "github.com/enterprise/gen/go/order/v1;orderv1";
option java_multiple_files = true;
option java_package = "com.enterprise.order.v1";

import "google/protobuf/timestamp.proto";
import "google/rpc/status.proto";

// Enum definition with mandatory UNSPECIFIED zero value
enum OrderStatus {
  ORDER_STATUS_UNSPECIFIED = 0;
  ORDER_STATUS_PENDING = 1;
  ORDER_STATUS_PROCESSING = 2;
  ORDER_STATUS_COMPLETED = 3;
  ORDER_STATUS_CANCELLED = 4;
}

// Main Order Service Interface
service OrderService {
  rpc CreateOrder(CreateOrderRequest) returns (CreateOrderResponse);
  rpc StreamOrderUpdates(StreamOrderUpdatesRequest) returns (stream StreamOrderUpdatesResponse);
}

message CreateOrderRequest {
  // Frequently accessed fields (1-15 byte tag optimization)
  string order_id = 1;
  string customer_id = 2;
  int64 total_amount_cents = 3;

  OrderStatus status = 4;
  google.protobuf.Timestamp created_at = 5;

  // Reserved tags from deleted fields
  reserved 6, 7;
  reserved "legacy_payment_token";
}

message CreateOrderResponse {
  string order_id = 1;
  OrderStatus status = 2;
}

message StreamOrderUpdatesRequest {
  string customer_id = 1;
}

message StreamOrderUpdatesResponse {
  string order_id = 1;
  OrderStatus new_status = 2;
  google.protobuf.Timestamp updated_at = 3;
}
```

### 3. Backwards Compatibility & Linting Verification
- **Buf Lint Compliance**: [Passed]
- **Field Tag Tagging Efficiency**: [Tags 1-5 allocated to high-frequency attributes]
- **Error Model Handling**: [Utilizes standard google.rpc.Status details payload]
```

## Evaluation Criteria
- **Schema Validation**: Proto file parses cleanly without syntax errors using standard `protoc` or `buf` linters.
- **Tag Number Optimization**: Critical attributes utilize tags 1-15 for low wire-format serialization overhead.
- **Compatibility Preservation**: Uses `reserved` blocks and strict field numbering rules to guarantee backwards binary compatibility.

## Failure Considerations
- **Non-Zero Default Enum**: Starting an enum with a non-zero or specific domain state value instead of `UNSPECIFIED`.
- **Reusing Deleted Field Tags**: Assigning a new attribute to a previously deleted field tag number without a `reserved` statement.
