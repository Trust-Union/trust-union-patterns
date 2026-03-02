# PATTERN-002 — Threat Model Assumptions & Attack Surface as Inputs
**Status:** Draft  
**Scope:** Sector-agnostic  
**Note:** This is **normative guidance in natural language**.

## Intent
Ensure that component security requirements are **derived from explicit threat assumptions and attack surface analysis**.

## How to achieve
Security requirements MUST include a clear rationale including an explicit threat model, assumptions and an attack surface view, so that:
- reviewers can validate *why* requirements guarantee safe guards for digital services and data in transit and at rest,
- implementers can prioritize protections,
- auditors can assess completeness and consistency,
- different teams produce compatible and interoperable software based on well defined standards.

## Normative Statement
For each identified **component** and each relevant **trust boundary** it **MUST** be defined:
1) **Threat model assumptions** (attacker capabilities, constraints, trust assumptions), and  
2) **Attack surface** (entry points, exposed interfaces, data flows, privileged operations),  
as explicit inputs to the component’s security requirements and acceptance criteria.

## Threat Model Assumptions (minimum set)
For each component/trust boundary, document at least:
- **Attacker profile(s):** external attacker, insider, compromised client, supply-chain adversary, etc.
- **Capabilities:** network attacker, malware on device, physical access, privileged access, etc.
- **Constraints:** rate limits, required proximity, time window, detectable actions, etc.
- **Trust assumptions:** trusted execution environment, trusted build pipeline, trusted platform attestation, trusted key store, etc.
- **Assets at risk:** keys, credentials, tokens, personal data, integrity of decisions, availability, etc.
- **Security objectives:** integrity, authenticity, confidentiality, non-repudiation (if applicable), availability, isolation, update assurance.

## Attack Surface (minimum set)
For each component/trust boundary, document at least:
- **Entry points:** APIs, UI actions, network endpoints, IPC, file imports, admin interfaces.
- **Interfaces & protocols:** HTTP, message bus, local OS calls, crypto APIs, device sensors, etc.
- **Data flows:** inbound/outbound data types, trust boundary crossings, persistence points.
- **Privileges:** required permissions, elevated operations, key access, policy decisions.
- **Failure modes:** what happens on error, fallback logic, degraded operation, retry logic.

## Acceptance Criteria (Given/When/Then)
- **Given** a component is documented, **when** its security requirements are specified, **then** the applicable threat model assumptions are explicitly stated and referenced.
- **Given** threat assumptions are defined, **when** the attack surface is described, **then** all relevant entry points and boundary crossings are listed (not implied).
- **Given** an entry point exists, **when** security requirements are written, **then** at least one requirement addresses the top risks introduced by that entry point (e.g., authN/authZ, integrity, replay, injection, abuse).
- **Given** a trust assumption is used (e.g., “hardware-backed keystore”), **when** a requirement depends on it, **then** the assumption is testable or auditable (e.g., attestation evidence, configuration evidence).
- **Given** assumptions or attack surface change, **when** documentation is updated, **then** impacted security requirements and acceptance criteria are reviewed and updated accordingly.

## Evidence / Verification Ideas (non-exhaustive)
- Threat model artifact (lightweight): assets, actors, assumptions, top threats, mitigations
- Attack surface inventory: interface list, endpoint list, boundary crossing list
- Traceability note: “Threat/Entry Point → Requirement → Acceptance Criteria → Evidence”
- Tests and checks validating assumptions (e.g., attestation verified, TLS settings enforced)
- Security review record showing coverage of highest-risk entry points
- Pen-test / assessment scope aligned to declared attack surface

## Minimal Structure (recommended)
For each component, add a short “Threat & Surface Sheet”:
- Component name and role
- Assets
- Threat assumptions (attacker + capabilities + trust assumptions)
- Attack surface (entry points + boundary crossings)
- Derived security requirements (MUST/MUST NOT)
- Acceptance criteria (GWT)
- Evidence approach (how to validate)

## Notes
- Keep assumptions **explicit**: “We assume X” is valid only if it is reviewable and does not hide risk.
- Avoid false certainty: if an assumption is uncertain, document it as a risk and define compensating controls.
- Prefer minimal, actionable threat modeling over heavyweight frameworks — but do not skip the inputs.

## References
- (Optional) Links to threat modeling methods (STRIDE, LINDDUN, etc.)
- (Optional) Relevant standards/guidance used as supporting references
