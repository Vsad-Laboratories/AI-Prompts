# Coding Prompt: Secure Secrets Management

## Purpose
Design and implement programmatic patterns, environment controls, and pipeline architectures to securely manage application secrets, API keys, and certificates.

## Inputs
- `APPLICATION_TECH_STACK`: Languages, frameworks, and deployment environments (e.g., Node.js on Kubernetes, AWS Lambda, Python on bare metal).
- `SECRETS_MANAGEMENT_REQUIREMENTS`: Types of keys, rotation frequency, security standards, and audit logging needs.

## Instructions
1. Define a strict segregation policy for development, staging, and production secrets.
2. Outline programmatic retrieval patterns that avoid hardcoding or committing credentials into source code.
3. Design a secure integration setup with a secrets manager (e.g., HashiCorp Vault, AWS Secrets Manager, Doppler, or GitHub Secrets) for the given `APPLICATION_TECH_STACK`.
4. Specify a rotation protocol that details how credentials can be updated dynamically with minimal service interruption.
5. Outline pipeline validation steps to scan git repositories for accidental secrets leaks before commits are merged.

## Constraints
- Never suggest solutions that involve committing plaintext API keys to repository files.
- The workflow must prevent secrets from being printed in application execution logs or tracebacks.

## Expected output
- **Secrets Architecture Plan**: Strategy for secure injection, isolation, and logging.
- **Code Retrieval Templates**: Code snippets demonstrating secure retrieval in the target language.
- **Dynamic Rotation Policy**: Detailed steps for automated key rotation.
- **Git Leak Prevention Pipeline**: Configuration or hook setup to run local/CI pre-commit scans.
