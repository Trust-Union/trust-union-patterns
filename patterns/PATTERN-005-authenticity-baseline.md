# PATTERN-005 — Authenticity Baseline

Status: Draft
Scope: Sector-agnostic
Type: Property baseline pattern
Note: This is normative guidance in natural language.

## Intent
This pattern supports Zero Trust by requiring explicit verification of claimed origins, issuers, signers, and security-relevant sources across components and trust boundaries.
That means: Ensure that identities, origins, claims, and security-relevant messages can be verified as genuine and attributable to the expected source.

Note: According to NIST, Zero Trust does not simply mean “verify the source,” but rather: no implicit trust, a focus on resources, authentication and authorization prior to access, continuous risk assessment, least privilege, monitoring, and policy enforcement. NIST explicitly describes Zero Trust as a paradigm without implicit trust, featuring continuous authentication and authorization of identity and security status for every access attempt.


## How to achieve

Systems MUST define authenticity requirements explicitly per component and per trust boundary so that:
- participants know which entities or artifacts must prove their origin,
- implementers can select appropriate authenticity mechanisms,
- reviewers and auditors can verify that false origin claims are prevented or exposed.

## Normative Statement

For each identified component and each relevant trust boundary, the system documentation MUST define:

1. which actors, components, artifacts, or messages require authenticity,
2. which source claims must be verifiable,
3. which authenticity mechanism is used,
4. which behavior applies when authenticity cannot be established.

Authenticity analysis MUST consider, where applicable, at least the following object classes. 
This results: The architecture documentation MUST state which of the following object classes are authenticity-relevant, not applicable, or intentionally out of scope:
- users,
- workloads,
- devices,
- services,
- APIs,
- tokens and assertions,
- credentials and key material,
- signed artifacts,
- commands,
- events,
- audit records.

Note: *Tokens* are typically transferable or presentable artifacts containing claims, such as access tokens, ID tokens, session tokens, JWTs, SAML assertions, or proof-of-possession tokens.
*Credentials* are a broader concept. They are proofs or means used to verify an identity or grant access. These include, for example, passwords, passkeys, client certificates, private keys, SSH keys, API keys, mTLS certificates, hardware-bound credentials, or bootstrap credentials.



## Minimum Expectations

For each applicable component or boundary, document at least:
- authenticity subject or object,
- expected source identity or issuer,
- mechanism used to establish authenticity,
- trust anchor or trust basis,
- failure behavior if authenticity checks fail,
- evidence approach.

Typical mechanisms MUST include:
- digital signatures,
- authenticated channels,
- certificate validation,
- issuer validation,
- attestation,
- proof-of-possession mechanisms,
- challenge-response protocols.

## Acceptance Criteria (Given/When/Then)

- Given a component receives a security-relevant message or artifact, when the source matters for trust, then the expected origin is defined explicitly.
- Given authenticity is required at a trust boundary, when a request, message, or artifact is accepted, then the authenticity mechanism is defined and verified.
- Given the claimed source cannot be authenticated, when verification fails or is missing, then the system does not silently treat the claim as trustworthy.
- Given a component relies on an issuer, signer, or attester, when the trust basis is documented, then the relevant trust anchor or validation basis is named explicitly.
- Given authenticity is claimed, when reviewers inspect the documentation, then at least one observable evidence source is listed.

## Evidence / Verification Ideas (non-exhaustive)

- Signature verification results
- Certificate/path validation records
- Authenticated session establishment logs
- Attestation results
- Token issuer and claim validation tests
- Negative tests with forged or substituted artifacts
- Review records for trust-anchor configuration

## Minimal Structure (recommended)

For each component or boundary, add a short “Authenticity Sheet”:
- component/boundary name
- authenticity subject/object
- claimed source / issuer / signer
- validation mechanism
- trust basis
- failure behavior
- acceptance criteria
- evidence approach

## Notes

- Authenticity answers “is this genuinely from the claimed source?” It does not automatically answer whether the source is authorized.
- Authenticity and integrity often work together, but they are not identical.
- Trust assumptions about issuers, signers, or attesters should remain explicit and reviewable.

## References

- Links to applicable standards, public guidance, or project-specific criteria may be added here.
