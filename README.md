# Trust Union Patterns

A neutral, sector-agnostic library of **requirement** and **security-by-design patterns** for **regulated, publicly funded digital artifacts**.

This repository focuses on **what must be true** (properties) and **how to verify it** (acceptance criteria + evidence ideas) — per **component** and per **trust boundary**.

---

## Purpose

Modern digital infrastructures are built across complex ecosystems. Trust Union Patterns exists to provide a **reusable, evidence-based corpus** that helps teams express requirements in a way that is:

- **Explicit** (no implicit security assumptions)
- **Testable** (acceptance criteria are concrete)
- **Traceable** (clear scope, component mapping, rationale)
- **Reusable** (cross-domain patterns, not sector-specific specs)

---

## What this repo is (and is not)

### This repo is
- A curated set of **patterns** written for humans **and** structured for reuse:
  - requirement intent
  - acceptance criteria (Given/When/Then)
  - verification & evidence ideas
  - applicability notes (component / trust boundary)
- A **neutral zone**: no vendor-first, no national-first framing.

### This repo is not
- A product, validator, or report generator.
- A replacement for implementation-specific architecture or system specs.
- A place for commercial tooling or operational playbooks.

> Note: Machine-readable standards, parsers, schemas, and validation engines belong to the [**DSL-Core** ecosystem]([https://link-url-here.org](https://github.com/rock-the-prototype/dsl-core/)). This repo stays technology-agnostic and focuses on **reusable patterns**.

---

## How to use these patterns

You can use patterns in three common ways:

1. **As a checklist** during design and threat modeling  
2. **As requirement seeds** to write explicit requirements per component  
3. **As test guidance**: translate Given/When/Then into automated checks

Each pattern is designed to be copied into your project and adapted with context-specific parameters.

---

## Repository structure

```text
/patterns/ # The pattern library (canonical source)
/patterns/acceptance/ # Acceptance-criteria focused patterns 
/patterns/evidence/ # Evidence / verification idea patterns
/templates/ # Issue and PR templates (contribution workflow)
```


### Pattern file naming
We use stable IDs to enable referencing:

```text
- `PATTERN-001-...`
- `AC-001-...` (acceptance patterns)
- `EVID-001-...` (evidence patterns)
```
---

## Pattern format (human-readable)

Each pattern typically contains:

- **Goal** (what property is required)
- **Rationale** (why it matters)
- **Scope** (where it applies: component / boundary)
- **Acceptance Criteria** (Given/When/Then)
- **Verification & Evidence** (how to prove it)
- **Common pitfalls** (what to avoid)
- **References** (standards, public sources)

---

## Contributing

We welcome contributions from practitioners, auditors, researchers, and builders.

- Start with an **Issue** (problem statement, evidence, context)
- Use a **Pull Request** for changes (new patterns or improvements)
- Apply the **minimal validation principle**: contributions should be reviewed and merged by someone else

See: `CONTRIBUTING.md`

---

## Status

This repository is in early formation. 

If you want to help shape the first baseline patterns, open an Issue with a concrete pain point and an example context.

