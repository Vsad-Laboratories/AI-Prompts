# Cloud-Native Zero Trust Security Architect

## Purpose
Design a comprehensive Cloud-Native Zero Trust Security Architecture for enterprise microservices, Kubernetes clusters, and multi-cloud environments, enforcing explicit identity verification, least privilege access, micro-segmentation, continuous posture monitoring, and end-to-end encryption.

## Inputs
- `CLOUD_INFRASTRUCTURE_TARGET`: Target deployment environment (EKS/GKE/AKS, AWS/GCP/Azure, Hybrid Cloud).
- `IDENTITY_PROVIDERS`: Enterprise IAM systems (Okta, Azure AD/Entra ID, OIDC, SPIFFE/SPIRE).
- `DATA_CLASSIFICATION`: Data sensitivity levels (Public, Internal, Confidential, Restricted PII/PCI).

## Instructions
1. **Apply the Core Axioms of Zero Trust**:
   - **Never Trust, Always Verify**: Explicitly authenticate and authorize every request based on all available data points (identity, device, context, location).
   - **Enforce Least Privilege Access**: Restrict user and service permissions using Just-In-Time (JIT) and Just-Enough-Access (JEA) models.
   - **Assume Breach**: Minimize blast radius by segmenting networks, encrypting all data in transit and at rest, and enforcing real-time threat detection.
2. **Architect Workload Identity (SPIFFE/SPIRE & Kubernetes mTLS)**:
   - Eliminate static API keys and long-lived AWS IAM user credentials.
   - Deploy SPIFFE/SPIRE or Service Mesh (Istio / Linkerd) to issue short-lived cryptographic X.509 SVID certificates to workloads dynamically.
3. **Architect Network Micro-Segmentation**:
   - Define Kubernetes `NetworkPolicies` or Cilium eBPF network policies enforcing default-deny egress and ingress across all pod namespaces.
   - Restrict east-west pod-to-pod communication strictly to explicitly approved service dependency graphs.
4. **Architect Data Protection & Encryption Matrix**:
   - **Data in Transit**: Enforce mandatory mTLS (TLS 1.3) with strict cipher suites across all internal microservice calls.
   - **Data at Rest**: Enforce envelope encryption using Cloud KMS / HashiCorp Vault with customer-managed keys (CMAK) rotated automatically.
5. **Architect Just-In-Time (JIT) Admin Privileged Access**:
   - Eliminate permanent SSH keys and administrative IAM roles.
   - Configure Teleport / AWS Systems Manager Session Manager with short-lived session certificates tied to multi-factor authentication (MFA) and ticket approvals.

## Constraints
- **Default Deny Rule**: All network policies, IAM policies, and ingress rules MUST default to deny-all.
- **No Static Long-Lived Credentials**: Zero plain-text passwords, static IAM keys, or persistent API tokens stored in code or environment variables.
- **Traceable Identity**: Every request context MUST carry verifiable caller identity (OIDC JWT / mTLS X.509 certificate).

## Expected Output Format
```markdown
### 1. Zero Trust Architectural Blueprint
- **Workload Identity Standard**: SPIFFE/SPIRE + Istio Mutual TLS (mTLS)
- **Primary Auth Boundary**: OIDC + OAuth 2.0 (mTLS bound access tokens)
- **Network Enforcement Engine**: Cilium eBPF Network Policies (Default Deny)

### 2. Kubernetes Micro-Segmentation Policy (Cilium / NetworkPolicy)
```yaml
apiVersion: cilium.io/v2
kind: CiliumNetworkPolicy
metadata:
  name: restrict-order-service-ingress
  namespace: production
spec:
  endpointSelector:
    matchLabels:
      app: order-service
  ingress:
    # Allow ingress ONLY from api-gateway on port 8080 via mTLS
    - fromEndpoints:
        - matchLabels:
            app: api-gateway
      toPorts:
        - ports:
            - port: "8080"
              protocol: TCP
  egress:
    # Allow egress ONLY to postgres database namespace
    - toEndpoints:
        - matchLabels:
            app: postgres-db
      toPorts:
        - ports:
            - port: "5432"
              protocol: TCP
```

### 3. Workload Identity & KMS Envelope Encryption Pipeline
- **Workload Cert Lifetime**: 1 hour (Auto-rotated via SPIRE agent)
- **Key Rotation Schedule**: 90-day automatic KMS key rotation
- **JIT Access Protocol**: Teleport Bastion Session with 15-minute approval window

### 4. Zero Trust Posture Audit Checklist
- [ ] Default-deny NetworkPolicies applied to all namespaces
- [ ] Mutual TLS (mTLS) enforced with strict TLS 1.3 ciphers
- [ ] Zero static IAM keys or hardcoded API secrets in repositories
- [ ] Teleport / SSM JIT access replacing persistent SSH keys
```

## Evaluation Criteria
- **Zero Trust Alignment**: Strictly enforces "Never Trust, Always Verify" across identity, network, and data layers.
- **Policy Completeness**: Provides functional default-deny NetworkPolicy YAMLs and work-identity architecture.
- **Operational Realism**: Balance security controls against developer velocity using automated short-lived credentials.

## Failure Considerations
- **Perimeter-Only Thinking**: Relying on VPNs or ingress firewalls while leaving east-west cluster traffic unencrypted and unauthenticated.
- **Overly Permissive Fallbacks**: Adding `0.0.0.0/0` ingress rules to troubleshoot network connections.
