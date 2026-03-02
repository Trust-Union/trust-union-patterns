# AC-001 — Testable Security Acceptance Criteria

**Status:** Draft  
**Type:** Acceptance Pattern  
**Scope:** Sector-agnostic  
**Normativity:** This pattern is normative guidance in natural language. It does not define DSL schemas, rule IDs, or report formats.

---

## Intent

Ensure that security requirements are validated through **clear, observable, and testable acceptance criteria**.

This pattern helps teams translate security intent into criteria that can be verified consistently by implementers, testers, evaluators, and auditors.

---

## Problem

Security requirements are often written as abstract goals (e.g., “must be secure”, “must prevent misuse”, “must ensure integrity”) without defining:

- what can be observed,
- under which conditions it is evaluated, and
- what outcome counts as success or failure.

As a result:

- implementation varies across teams,
- testing becomes inconsistent,
- evidence is weak or non-comparable,
- audits depend on interpretation instead of observable facts.

---

## Normative Statement

For each explicit security requirement, the system architecture **MUST** define acceptance criteria that are:

1. **Testable** (can be evaluated against observable behavior or artifacts),
2. **Unambiguous** (no vague qualifiers such as “secure enough”, “as appropriate”),
3. **Context-bound** (state conditions, trigger/action, and expected outcome),
4. **Traceable** (linked to the requirement, component, and/or trust boundary).

Where applicable, acceptance criteria **MUST** be written in a structured form such as **Given / When / Then (GWT)**.

If a requirement cannot yet be fully automated, the acceptance criteria **MUST** still define a repeatable verification condition (e.g., manual review with explicit checks, independent assessment criteria, documented inspection steps).

---

## What “Testable” Means

An acceptance criterion is considered testable when it defines:

- **Preconditions / context** (what state or setup exists),
- **Trigger / event** (what action occurs),
- **Expected observable outcome** (what must be true),
- **Evaluation basis** (how the outcome is detected or checked).

Testable does **not** necessarily mean “automated today”, but it must be **verifiable in a repeatable way**.

---

## Acceptance Pattern (Given / When / Then)

### Canonical Form

- **Given** a defined system/component/boundary context  
- **When** a relevant event, input, or interaction occurs  
- **Then** an observable and verifiable outcome must occur (or must not occur)

### Quality Rule for (Given / When / Then)

A GWT acceptance criterion is strong when the **Then** clause is:

- observable (log, response, state change, test result, alert, artifact),
- specific (not generic intent language),
- pass/fail evaluable.

---

## Acceptance Criteria (for this pattern)

### AC-001.1 — Security criteria are explicit and observable
**Given** a security requirement is documented for a component or trust boundary,  
**when** acceptance criteria are defined,  
**then** each criterion states an observable outcome (behavior, state, event, or artifact), not only a security intention.

### AC-001.2 — Security criteria are unambiguous
**Given** acceptance criteria are defined for a security requirement,  
**when** the criteria are reviewed,  
**then** they avoid vague language (e.g., “secure”, “sufficient”, “as needed”, “as appropriate”) unless concretized by measurable or reviewable conditions.

### AC-001.3 — Security criteria are context-bound
**Given** a security requirement is applicable only under certain conditions,  
**when** acceptance criteria are defined,  
**then** the relevant preconditions and triggering event are explicitly stated.

### AC-001.4 — Security criteria are traceable
**Given** acceptance criteria exist for a security requirement,  
**when** they are documented,  
**then** each criterion can be traced to the originating requirement and its component and/or trust boundary.

### AC-001.5 — Non-automated verification remains testable
**Given** an acceptance criterion cannot be fully automated,  
**when** it is documented,  
**then** it defines a repeatable manual or independent verification method with explicit pass/fail checks.

---

## Applicability Notes

This acceptance pattern is applicable to:

- **Component-level security requirements** (e.g., verifier service, wallet adapter, API gateway, key management service)
- **Trust-boundary requirements** (e.g., authentication, integrity, confidentiality, replay protection, protocol state handling)
- **Operational security claims** when they are part of requirements (e.g., logging, alerting, reviewability)

This pattern is especially useful in:

- regulated environments,
- multi-party ecosystems,
- public-sector digital infrastructure,
- systems requiring audit evidence.

---

## Good vs Weak Acceptance Criteria (Examples)

### Weak (not testable enough)
- “The component must be secure.”
- “Unauthorized access should be prevented.”
- “Replay attacks should be handled.”
- “Logs should be available where appropriate.”

### Stronger (testable / observable)
- **Given** a request contains an expired authentication token, **when** the component validates the token, **then** access is denied and the request is not processed further.
- **Given** the same nonce is reused within the defined validity window, **when** the verifier receives the second request, **then** the request is rejected and a replay-detection event is recorded.
- **Given** signature validation fails for an incoming message, **when** the message is processed, **then** no state-changing action is executed and the failure reason is recorded in the verification result.

---

## Verification & Evidence Guidance (for the acceptance criteria)

To validate that acceptance criteria are themselves testable and useful, reviewers may check for:

- Presence of **Given/When/Then** (or equivalent structured form)
- Explicit observable outcomes in the **Then** clause
- No vague language without concretization
- Link/reference to source requirement
- Link/reference to component and/or trust boundary
- Defined verification mode (automated / manual / independent assessment)
- Identified evidence source(s) where relevant

Possible evidence artifacts include:

- requirement review checklists,
- architecture/security review records,
- test case definitions,
- test reports,
- traceability matrices,
- audit-ready requirement catalogs.

---

## Common Pitfalls

- **Intent-only wording** (“must be secure”) without observable outcomes
- **Hidden assumptions** (criteria depend on context not written down)
- **Mixed concerns** (one criterion validates multiple unrelated properties)
- **Implementation coupling too early** (criterion names a tool/vendor instead of property/outcome)
- **No traceability** to requirement/component/boundary
- **Non-repeatable manual checks** (“review by expert”) without explicit review conditions

---

## Authoring Guidance (Recommended)

### 1) Keep criteria atomic
Prefer one criterion per observable outcome.

- Better: one criterion for rejection behavior, one for logging behavior
- Worse: one criterion that bundles validation, rejection, logging, alerting, and reporting

### 2) Prefer outcome language over solution language
Describe what must be observable, not how exactly it must be implemented.

- Prefer: “request is rejected and no state change occurs”
- Avoid (unless required): “service uses vendor X rule Y configuration”

### 3) Separate requirement vs acceptance criterion
- **Requirement** = what must be true (property)
- **Acceptance criterion** = how to check if it is true in a defined context

### 4) Make manual checks explicit
If human review is needed, define:
- review scope,
- check conditions,
- expected findings,
- pass/fail decision rule.

---

## Minimal Template (Reusable)

Use this as a lightweight template for writing acceptance criteria for a security requirement:

### Acceptance Criterion ID
`AC-<local-id>`

### Related Requirement
`REQ-...` (or reference/title)

### Applies To
- Component: `<name>`
- Trust Boundary (if applicable): `<boundary name>`

### Criterion (GWT)
- **Given** ...
- **When** ...
- **Then** ...

### Verification Mode
- Automated test / Manual review / Independent assessment / Other

### Observable Outcome
- `<state change / response / log event / artifact / report output>`

### Evidence Source(s) (optional but recommended)
- `<test report / log extract / attestation / review record / audit log>`

---

## Relationship to Other Patterns

This acceptance pattern complements:

- **component security requirement patterns** (what must be required)
- **evidence patterns** (how claims are substantiated)
- **trust-boundary patterns** (where controls and properties apply)

In particular, this pattern strengthens the bridge between:
- normative requirement statements, and
- verifiable evidence production.

---

## References

- (Optional) Threat model assumptions for the component / trust boundary
- (Optional) Public standards or guidance documents relevant to the requirement context
- (Optional) Project-specific glossary for control types (preventive / detective / corrective / compensating)
