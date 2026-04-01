# PATTERN-003 — Security Assessment Purpose, Scope & Accountability

**Status:** Draft  
**Scope:** Sector-agnostic  
**Type:** Governance / assessment pattern

## Intent

Ensure that every IT-Security assessment is understandable, accountable, decision-ready, and reusable.

This pattern defines the minimum meta-structure that a security assessment should provide before its technical findings are interpreted or acted upon.

## Why this pattern exists

IT Security assessments are often discussed as if their meaning were self-evident. In practice, their value depends on explicit clarity about:

- who created the assessment,
- who commissioned it,
- who is expected to use it,
- what exactly was assessed,
- for which decision or purpose it exists,
- which assumptions, limits, and criteria apply,
- and what consequences follow from its conclusions.

Without this clarity, a security assessment may exist as a document, but still fail as a trustworthy decision artifact.

## Pattern

Every security assessment should explicitly state the following:

1. **Author**
   - Who produced the assessment?
   - Was it created by an internal team, an external assessor, a manufacturer, an independent reviewer, or a laboratory?

2. **Commissioning party**
   - Who requested or commissioned the assessment?
   - Who is accountable for its initiation?

3. **Intended audience**
   - For whom is the assessment written?
   - Examples: operator, manufacturer, buyer, regulator, approval body, governance board, leadership, auditor.

4. **Decision purpose**
   - Which decision, process, or risk treatment does the assessment support?
   - Examples: go/no-go, release approval, procurement, onboarding, accreditation, exception handling, risk acceptance.

5. **Assessment object**
   - What exactly is being assessed?
   - Examples: system, subsystem, component, interface, service, release, operating model, deployment variant.

6. **Assessment scope**
   - What is in scope and what is outside the scope?
   - Which trust boundaries, dependencies, environments, and assumptions apply?

7. **Evaluation basis**
   - Against which criteria, requirements, standards, threat assumptions, or control objectives is the object assessed?

8. **Expected contribution**
   - What is the assessment expected to provide for its audience?
   - Examples: decision support, risk transparency, evidence, conditions for approval, prioritized remediation needs.

9. **Limits of statement**
   - Which assumptions, uncertainties, exclusions, and validity limits constrain the assessment?

10. **Consequences and follow-up**
    - Which actions may follow?
    - Examples: approval, approval with conditions, remediation, re-assessment, documented residual-risk acceptance, rejection.

11. **Validity and refresh triggers**
    - How long is the assessment valid?
    - Which events trigger review or require frequent renewal?
    - Examples: major it architecture change, new dependency, new release, incident, major threat change, regulatory change.

## Minimum output expectation

An IT Security assessment that follows this pattern should contain, at minimum:

- a clear title,
- version and date,
- assessment object,
- author and commissioning party,
- intended audience,
- decision purpose,
- scope and exclusions,
- evaluation basis,
- findings summary,
- assumptions and limitations,
- recommended actions,
- validity statement and refresh triggers.

## Acceptance criteria

### AC-1 — Accountability is explicit
**Given** a reader with no prior project context  
**When** they open the assessment  
**Then** they can identify the author, commissioning party, and intended audience without ambiguity.

### AC-2 — Purpose is explicit
**Given** the assessment document  
**When** the reader reviews its introduction  
**Then** the decision purpose and expected contribution of the assessment are clearly stated.

### AC-3 — Scope is explicit
**Given** the assessment document  
**When** a reviewer checks the object and boundaries  
**Then** they can distinguish what is in scope, what is out of scope, and which assumptions apply.

### AC-4 — Evaluation basis is explicit
**Given** the assessment document  
**When** a reviewer inspects the assessment method section  
**Then** the criteria, requirements, or standards used for evaluation are explicitly named.

### AC-5 — Limits are transparent
**Given** the findings of the assessment  
**When** the reader interprets the conclusions  
**Then** relevant limitations, exclusions, and uncertainty factors are documented.

### AC-6 — Follow-up is actionable
**Given** the conclusion of the assessment  
**When** the responsible stakeholders review it  
**Then** they can derive concrete next actions, decision options, or re-assessment triggers.

## Verification and evidence ideas

Evidence that this pattern is fulfilled may include:

- a completed assessment template,
- assessment terms of reference,
- documented scope statement,
- named decision owner,
- link to applicable requirements / standards / policies,
- review record confirming audience and purpose clarity,
- approval or follow-up record based on the assessment.

## Common pitfalls

- Treating the assessment as self-explanatory.
- Missing definitions or references
- Mixing technical findings with unclear decision intent.
- Omitting scope boundaries and exclusions.
- Using generic statements without naming the audience or decision context.
- Presenting conclusions without assumptions or validity limits.
- Treating one assessment as permanently valid regardless of system change.

## Reuse guidance

This pattern is intentionally generic.

It may be reused in:
- public-sector programs,
- regulated industries,
- any organisation or industry sector,
- procurement processes,
- it architecture governance,
- secure delivery workflows,
- audit and compliance preparation.

Projects may extend this pattern with domain-specific controls, but should preserve the accountability, scope, and purpose baseline.

## References

Add public standards, policy references, or project-specific criteria here where needed.
