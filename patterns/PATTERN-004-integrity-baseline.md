# PATTERN-004 — Integrity Baseline

Status: Draft
Scope: Sector-agnostic
Type: Property baseline pattern
Note: This is normative guidance in natural language.

## Intent

Ensure that data, decisions, configuration, and system state cannot be changed without authorization and without detection.

## How to achieve

Systems SHOULD define integrity requirements explicitly per component and per trust boundary so that:
- implementers know which artifacts and states must remain correct and unaltered,
- reviewers can trace how integrity is protected,
- auditors can verify that tampering is prevented, detected, or contained.

## Normative Statement

For each identified component and each relevant trust boundary, the system documentation MUST define:

1. which integrity-relevant assets or states are protected,
2. which unauthorized modifications are in scope,
3. which controls preserve or verify integrity,
4. which failure handling applies if integrity cannot be established.

Integrity-relevant assets SHOULD (optional for NON-KRITIS artifacts) AND MUST (KRITIS artifacts) include:
- data in transit,
- data at rest,
- configuration,
- executable artifacts,
- messages,
- logs,
- security decisions,
- protocol state,
- business-critical records.

## Minimum Expectations

For each applicable component or boundary, document at least:
- protected asset or state,
- integrity risk or tampering scenario,
- integrity control(s),
- detection or verification mechanism,
- expected system behavior on integrity failure,
- evidence approach.

Typical controls include:
- cryptographic integrity protection,
- signatures,
- checksums for corruption detection,
- immutability controls,
- append-only logging,
- versioning,
- trusted comparisons,
- transactional consistency checks.

## Acceptance Criteria (Given/When/Then)

- Given a component processes integrity-relevant data, when its requirements are documented, then the protected assets and states are named explicitly.
- Given an integrity-relevant asset crosses a trust boundary, when the boundary is specified, then an integrity control is defined for that crossing.
- Given integrity verification fails, when the system detects tampering, corruption, or mismatch, then the failure is handled explicitly and the unsafe result is not silently accepted.
- Given a component depends on correct configuration or executable artifacts, when those artifacts are loaded or updated, then their integrity is verified before use.
- Given integrity is claimed, when reviewers inspect the documentation, then at least one verification or evidence source is defined.

## Evidence / Verification Ideas (non-exhaustive)

- Signature or MAC verification results
- Hash comparison records
- Build provenance or artifact verification records
- Configuration integrity checks
- Database consistency checks
- Audit logs showing detection of unexpected modification
- Test cases for tampered input, corrupted state, or altered artifacts

## Minimal Structure (recommended)

For each component, add a short “Integrity Sheet”:
- component name and role
- integrity-relevant assets/states
- tampering scenarios
- integrity controls
- failure behavior
- acceptance criteria
- evidence approach

## Notes

- Integrity is not limited to cryptography. Process integrity, configuration integrity, and state integrity matter as well.
- “Data is stored” does not imply integrity. The protection mechanism must be explicit.
- If integrity cannot be proven, the residual risk should be documented explicitly.

## References

- Links to applicable standards, public guidance, or project-specific criteria may be added here.
