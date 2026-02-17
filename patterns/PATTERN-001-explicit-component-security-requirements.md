# PATTERN-001 — Explicit Component Security Requirements

**Status:** Draft  
**Scope:** Sector-agnostic  
**Note:** This is **normative guidance in natural language**. It does **not** define any DSL schema, rule IDs, or report formats.

## Intent
Make security properties actionable by requiring **explicit, verifiable security requirements** for each system component and trust boundary.

## Problem
Architecture documents often describe components, roles, and data flows — but leave unclear **which concrete security properties each component must fulfil**.  
This blocks implementers, evaluators, and auditors from producing consistent evidence.

## Normative Statement
For each identified **component** (and each relevant **trust boundary**), the system documentation **MUST** define:
1) explicit security requirements (as clear statements),  
2) testable acceptance criteria, and  
3) at least one verification/evidence approach.

## Acceptance Criteria (Given/When/Then)
- **Given** a system decomposes into components, **when** a component is documented, **then** its required security properties are stated explicitly (not implied).
- **Given** a component has security requirements, **when** acceptance criteria are written, **then** they are testable and observable (e.g., Given/When/Then).
- **Given** a security requirement is stated, **when** the verification approach is defined, **then** at least one evidence source is listed (e.g., tests, attestation, audit logs, code review, pen-test report).
- **Given** a trust boundary exists between components, **when** the boundary is documented, **then** security requirements are defined for the boundary conditions (e.g., authentication, integrity, confidentiality, replay protection).

## Evidence / Verification Ideas (non-exhaustive)
- Automated tests (unit/integration/security tests) proving the acceptance criteria
- Attestation statements or integrity proofs (where applicable)
- Configuration evidence (secure defaults, hardening profiles)
- Audit logs and monitoring signals supporting operational security claims
- Independent assessment artifacts (review reports, pen-test summaries)

## Minimal Structure (recommended)
For each component, provide a short “Component Security Sheet”:
- Component name and role
- Security objectives (properties)
- Requirements (MUST/MUST NOT statements)
- Acceptance criteria (GWT)
- Evidence approach (how to validate)

## Notes
- Requirements should be **atomic** (one requirement → one observable outcome).
- Avoid ambiguous language (e.g., “should be secure”, “as appropriate”).
- Component-level requirements should align with system-level security objectives, but remain explicit at component level.

## References
- (Optional) Threat model assumptions relevant to the component/trust boundary
- (Optional) Links to applicable standards or guidance documents
