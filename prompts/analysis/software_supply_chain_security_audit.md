# Software Supply Chain Security Audit

## Purpose
Examine application bill of materials (SBOM), open-source dependency manifests, package lockfiles, container base images, and third-party CI/CD pipeline actions to detect, analyze, and mitigate software supply chain vulnerabilities, malicious typosquatting, dependency confusion, and license compliance risks.

## Inputs
- `DEPENDENCY_MANIFEST`: `package.json`, `package-lock.json`, `pom.xml`, `requirements.txt`, `Cargo.lock`, `go.mod`, or Dockerfile definitions.
- `SECURITY_TELEMETRY`: Vulnerability scanning outputs (CVE reports, Dependabot logs, Trivy scans, Snyk outputs).
- `COMPLIANCE_POLICIES`: Approved license list (MIT, Apache 2.0, BSD vs. restrictive GPL/AGPL), target severity thresholds.

## Instructions
1. **Analyze Dependency Tree**: Parse `DEPENDENCY_MANIFEST` to construct the full dependency graph, differentiating between direct and transitive dependencies.
2. **Detect Supply Chain Attack Vectors**:
   - *Typosquatting & Malicious Packages*: Identify suspicious package name variations (e.g., `reqeusts` vs `requests`).
   - *Dependency Confusion / Namespace Hijacking*: Scan for internal enterprise package names exposed to public package registries (NPM, PyPI, Maven).
   - *Unpinned / Floating Version Risks*: Identify loose version specifiers (`^`, `~`, `*`, `latest`) allowing unvetted upstream code execution.
   - *Abandoned / Unmaintained Libraries*: Highlight packages with zero commits in >24 months or archived repositories.
3. **Audit CVE & Known Vulnerabilities**: Map identified CVEs to application code usage. Evaluate whether the vulnerable function path is actually reachably invoked by the application.
4. **Evaluate Open-Source License Compliance**: Audit direct and transitive licenses against `COMPLIANCE_POLICIES`. Flag copyleft licenses (GPLv3, AGPL) that pose viral IP exposure risks to proprietary codebases.
5. **Formulate Mitigation & Remediation Roadmap**: Generate lockfile pinning updates, version bump commands, alternative library replacements, or vendor patch strategies.

## Constraints
- **Differentiate Direct vs. Transitive**: Explicitly state whether a vulnerability originates in a top-level dependency or deep transitive library.
- **Reachability Analysis**: Do not flag theoretical CVEs as high severity if the affected module/function is entirely unimported or unreachable.
- **Actionable Remediation Commands**: Provide exact terminal update commands (e.g., `npm audit fix --force`, `cargo update -p <pkg>`).

## Expected Output Format
```markdown
### 1. Supply Chain Risk Overview
- **Total Dependencies Scanned**: [Count] (Direct: [N], Transitive: [N])
- **Critical/High Vulnerabilities**: [Count]
- **License Compliance Breaches**: [Count]
- **Supply Chain Threat Index**: [LOW / MEDIUM / HIGH / CRITICAL]

### 2. Critical & High Vulnerability Analysis
| Package Name | Installed Version | CVE ID | Severity | Reachability | Remediation Version |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `lodash` | `4.17.15` | CVE-2021-23337 | HIGH | Reachable via template compiler | `>=4.17.21` |

### 3. Supply Chain Vector & License Audit
- **Dependency Confusion Vulnerabilities**: [Findings or None]
- **Floating Version Specifiers**: [Findings or None]
- **License Violations (GPL/AGPL in Proprietary Code)**: [Findings or None]

### 4. Remediation Steps & Lockfile Updates
```bash
# Terminal update command
npm install lodash@4.17.21 --save-exact
```
```

## Evaluation Criteria
- **Threat Detection Completeness**: Catches indirect transitive vulnerabilities and subtle typosquatting attempts.
- **Reachability Realism**: Reduces alarm fatigue by evaluating functional execution paths.
- **Remediation Precision**: Delivers exact dependency pinning instructions without breaking builds.

## Failure Considerations
- **False Alarm Overload**: Marking unreferenced devDependencies as critical production runtime risks.
- **Ignoring Transitive Chains**: Failing to trace which top-level package introduced a vulnerable transitive dependency.
