# Analysis Prompt: Cloud Migration & Application Modernization Gap Analysis

## Purpose
Analyze legacy application architecture, workload characteristics, and cloud target specifications to produce a detailed migration gap analysis and modernization strategy.

## Inputs
- `LEGACY_ARCHITECTURE`: Technical documentation, dependency trees, database schema, or infrastructure specs of legacy systems.
- `TARGET_CLOUD_ENV`: Preferred cloud provider, target services (e.g., AWS EKS, Serverless, GCP Cloud Run), and compliance requirements.

## Instructions
1. Evaluate `LEGACY_ARCHITECTURE` using Gartner's 6 Rs of Cloud Migration (Rehost, Replatform, Refactor, Repurchase, Retire, Retain).
2. Identify architectural gaps, including state management issues, tight database couplings, OS-level dependencies, and proprietary hardware drivers.
3. Map legacy application components to cloud-native target primitives in `TARGET_CLOUD_ENV`.
4. Assess security, compliance, data sovereignty, and networking compatibility.
5. Formulate a phased migration roadmap prioritizing low-risk workloads first.

## Constraints
- Explicitly identify stateful components and offer stateless refactoring strategies.
- Do not ignore database migration complexity or data transfer bandwidth bottlenecks.

## Expected output
- **Component Classification Matrix**: Workload-by-workload migration strategy classification (6 Rs).
- **Architectural & Compliance Gap Breakdown**: Detailed list of technical hurdles and security gaps.
- **Target Architecture Blueprints**: Cloud-native service mapping table.
- **Phased Migration Roadmap**: Execution phases with risk ratings and rollback gates.
