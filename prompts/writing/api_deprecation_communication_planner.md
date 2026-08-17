# API Deprecation & Migration Communication Planner

## Purpose
Formulate a comprehensive API deprecation strategy, developer breaking-change communication plan, and step-by-step SDK migration guide for enterprise APIs, guaranteeing zero unannounced service disruptions, transparent sunset timelines, and smooth developer migration.

## Inputs
- `DEPRECATED_API_SPECS`: Deprecated endpoint paths, parameters, schemas, or authentication headers.
- `REPLACEMENT_API_SPECS`: Target replacement API endpoints, modified schemas, and new authentication models.
- `SUNSET_TIMELINE`: Deprecation announcement date, formal sunset date (sunset HTTP header), and hard turn-off date (e.g., 6-month deprecation window).

## Instructions
1. **Define API Deprecation Policy & SLA**: Establish a multi-phase deprecation lifecycle schedule adhering to standard RFC 8594 (`Sunset` HTTP header) standards:
   - **Phase 1: Announcement & Warning Logs**: Publish breaking change notice, add `Deprecation: @<timestamp>` and `Sunset: <date>` HTTP headers to responses.
   - **Phase 2: Active Brownout Drills**: Execute scheduled 15-minute mock outages (brownouts) on deprecated endpoints to alert un-migrated client teams.
   - **Phase 3: Hard Sunset / Decommissioning**: Permanently disable old endpoints and return `410 Gone`.
2. **Draft Developer Communication Matrix**: Create tailored notifications across communication channels:
   - Developer Portal Changelog Announcement
   - Email Communication for Account Owners & API Key Contacts
   - In-Console Warning Banners & SDK Terminal Warnings
3. **Construct Detailed API Diff & Mapping Matrix**:
   - Map deprecated parameters/endpoints directly to replacement parameters/endpoints.
   - Highlight structural schema shifts (e.g., string timestamp $\rightarrow$ epoch integer).
4. **Draft Step-by-Step SDK Code Migration Examples**:
   - Provide side-by-side "Before vs. After" code snippets across major client SDK languages (Python, TypeScript/JavaScript, Go, Java, cURL).

## Constraints
- **RFC 8594 Header Compliance**: Always include exact HTTP header syntax for `Deprecation` and `Sunset`.
- **Zero Silent Breakage**: Never turn off an API endpoint without a documented deprecation window.
- **Provide Fully Functional Code Diffs**: Code migration examples MUST be copy-paste ready and syntactically valid.

## Expected Output Format
```markdown
# API Deprecation & Migration Guide: v1 to v2 Customer API

## 1. Executive Summary & Sunset Timeline
- **Deprecation Announcement Date**: October 1, 2026
- **Scheduled Brownout Drills**: March 15, 2027 (15-min scheduled outages)
- **Hard Sunset (Decommissioning) Date**: April 1, 2027 (6 Months Window)
- **End State Response**: HTTP `410 Gone`

### HTTP Header Deprecation Injections (Active Immediately)
All requests to `GET /v1/customers/{id}` will return:
```http
HTTP/1.1 200 OK
Deprecation: @1790812800
Sunset: Thu, 01 Apr 2027 00:00:00 GMT
Link: <https://developer.api.com/docs/v2-migration>; rel="deprecation"
```

## 2. API Endpoint & Schema Mapping Matrix
| Deprecated Field / Endpoint (`v1`) | Replacement Field / Endpoint (`v2`) | Breaking Changes / Schema Shift |
| :--- | :--- | :--- |
| `GET /v1/customers/{id}` | `GET /v2/accounts/users/{id}` | Endpoint path changed |
| `customer.full_name` | `user.first_name`, `user.last_name` | String split into two fields |
| `customer.created_at` (ISO 8601) | `user.created_timestamp` (Epoch ms) | Datetime string converted to unix epoch int |

## 3. Side-by-Side SDK Code Migration Examples
### Python Client Migration
#### Deprecated Code (`v1`)
```python
# DEPRECATED - Will cease functioning on April 1, 2027
customer = client.v1.get_customer(customer_id="cust_123")
print(f"Name: {customer.full_name}, Created: {customer.created_at}")
```

#### Migrated Code (`v2`)
```python
# MIGRATED - Production Ready (v2 API)
user = client.v2.get_user(user_id="cust_123")
full_name = f"{user.first_name} {user.last_name}"
print(f"Name: {full_name}, Created: {user.created_timestamp}")
```

### cURL Request Migration
#### Deprecated Request
```bash
curl -X GET "https://api.enterprise.com/v1/customers/cust_123" \
  -H "Authorization: Bearer SECRET_KEY"
```

#### Migrated Request
```bash
curl -X GET "https://api.enterprise.com/v2/accounts/users/cust_123" \
  -H "Authorization: Bearer SECRET_KEY"
```

## 4. Developer Support & Brownout Schedule
- **Scheduled 15-Min Brownout 1**: March 15, 2027 @ 14:00 UTC
- **Scheduled 15-Min Brownout 2**: March 22, 2027 @ 18:00 UTC
- **Developer Support Channel**: `https://developer.enterprise.com/support`
```

## Evaluation Criteria
- **Standards Compliance**: Adheres strictly to RFC 8594 Sunset header specifications.
- **Migration Clarity**: Provides unambiguous endpoint mapping and side-by-side code diffs.
- **Operational Safety**: Incorporates scheduled brownout drills to detect un-migrated legacy clients safely.

## Failure Considerations
- **Abrupt Endpoint Shutdowns**: Recommending hard endpoint cutoffs without warning headers or brownout phases.
- **Incomplete Schema Diffing**: Omitting underlying data type changes in API payload fields.
