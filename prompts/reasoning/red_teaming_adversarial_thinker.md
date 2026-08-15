# Reasoning Prompt: Red Teaming Adversarial Simulation

## Purpose
Simulate adversarial "Red Team" attacks against system architectures, business plans, AI safety guardrails, or policy frameworks to expose latent vulnerabilities, bypass strategies, and blind spots.

## Inputs
- `TARGET_SYSTEM`: Architecture blueprint, operational plan, security policy, or prompt system to red team.
- `ADVERSARY_PROFILE`: Capabilities, resources, and motivations of simulated attackers (e.g., Sophisticated Nation-State, Malicious Insider, Prompt Injection Attacker, Opportunistic Fraudster).
- `PROTECTED_ASSETS`: High-value target data, system controls, or core constraints to defend.

## Instructions
1. Analyze `TARGET_SYSTEM` from an adversarial perspective, ignoring intended usage guidelines and looking explicitly for exploit vectors.
2. Formulate 3-5 distinct **Attack Vectors** tailored to `ADVERSARY_PROFILE`, specifying:
   - *Exploit Mechanism*: How the vulnerability is triggered.
   - *Prerequisites*: Access or context required by the attacker.
   - *Impact*: Extent of compromise to `PROTECTED_ASSETS`.
3. Simulate step-by-step attack execution, anticipating defensive reactions or logging detection mechanisms.
4. Rate overall system vulnerability risk based on Likelihood vs Impact.
5. Provide concrete defensive hardening blueprints ("Blue Team" counter-measures) for each identified attack vector.

## Constraints
- Do not provide actionable real-world exploit instructions against named living individuals or active third-party infrastructure.
- Ensure adversarial simulations focus on structural weaknesses and design flaws rather than surface-level generic warnings.

## Expected output
- **Attacker Threat Model**: Capability assessment and motivation mapping.
- **Red Team Attack Vector Inventory**: Detailed breakdown of exploit paths.
- **Simulated Attack Execution Log**: Step-by-step simulation narrative.
- **Blue Team Hardening Blueprint**: Counter-measures and defensive controls.
