# Coding Prompt: Security and Vulnerability Audit

## Purpose
Examine production code or system configurations to detect common security vulnerabilities, architectural security flaws, or compliance risks.

## Inputs
- `SOURCE_CODE_OR_CONFIG`: Code snippet, dependency list, dockerfile, or deployment configurations.
- `SECURITY_STANDARDS`: Targets and standards to audit against (e.g., OWASP Top 10, CWE, HIPAA, SOC2).

## Instructions
1. Inspect the `SOURCE_CODE_OR_CONFIG` carefully line-by-line.
2. Cross-reference the code against the `SECURITY_STANDARDS` to identify potential exploits (e.g., SQL Injection, XSS, CSRF, insecure deserialization, hardcoded secrets, outdated packages).
3. For each vulnerability discovered, provide a detailed explanation of the exploit vector (how an attacker would utilize it).
4. Provide a rewritten, secure version of the code that resolves the vulnerability without breaking the business logic.
5. Suggest security-oriented unit tests or static analysis rules to prevent this class of vulnerability from returning.

## Constraints
- Never provide actual executable exploit scripts or malicious payloads; keep explanations focused on defense and conceptual mechanics.
- Do not make generic security statements; make specific, line-by-line code recommendations.

## Expected output
- **Vulnerability Findings Table**: List of exploits, severity, line numbers, and standard categories (e.g., OWASP-1).
- **Exploit Vector Explanation**: Analytical explanation of how the bug could be triggered.
- **Remediated Code Implementation**: Clean, secure, and ready-to-merge refactored code.
- **CI/CD Defensive Checklist**: Specific static analysis or linting rules to add.
