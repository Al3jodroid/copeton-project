---
title: "Feature Change Management Protocol"
type: "framework-guide"
---

# Feature Change Management Protocol

## Purpose
This document defines how new features, requirement updates, and architectural pivots are handled within this framework. It ensures that no code is ever written without a prior specification, regardless of whether the change is large or small.

**Core Rule:** The spec always comes first. No spec → No tests → No code.

---

## The Two Realities of Software Development

### Reality 1: The Initial Build
When development starts, `business_brief.md` does not need to be complete. It only needs to be clear enough to define what you are building **right now**. The AI uses it to generate architecture, specifications, and tests for the initial feature set only.

This produces a **narrow, verified core** — not the full product. That is intentional.

### Reality 2: Requirements Always Evolve
New features are discovered during development. User feedback surfaces gaps. Business priorities shift. The question is not *whether* requirements will change, but *how* to handle changes without breaking the existing verified foundation.

---

## Change Classification & Protocol

### Class A — Small Addition
**Definition:** A new field, a new export format, a minor UI state, or a configuration option that does not alter the existing data model or system architecture.

**Protocol:**
1. Update `business_brief.md` with the new requirement.
2. Write a new spec file `/docs/specs/<feature_name>.md` using `technical_specification.md`.
3. Follow the mini Agentic Work Cycle: **Explore → Plan → Approve → Execute → Verify**.
4. Commit with a scoped message, e.g. `feat(catalog): add genre filtering to book search`.

**Version Tag:** No new milestone tag required. Captured in the current stage commit history.

---

### Class B — Medium Addition
**Definition:** A new user role, a new module, a new integration point, or a new entity that extends the system without replacing its core.

**Protocol:**
1. Update `business_brief.md` — revise the affected Personas or Functional Requirements section.
2. Update `/docs/architecture.md` if the module alters the system structure.
3. Write an Architecture Decision Record (ADR) in `/docs/` documenting *why* the design is changing and what alternatives were considered.
4. Write a new spec file → write tests → obtain lead engineer approval → implement → verify.
5. Tag as a minor version: `v1.1-<feature-name>`.

**Version Tag:** `v1.x-<feature-scope>` (e.g. `v1.1-user-roles`).

---

### Class C — Major Pivot
**Definition:** A new platform target, a core entity redesign, a new primary user persona, or a change that invalidates existing architectural decisions.

**Protocol:**
1. Rewrite or substantially update `business_brief.md`.
2. Revisit `/docs/architecture.md` — a new ADR is mandatory.
3. Run the full **Stage 1: System Architecture & Spec-Driven Development** cycle again, scoped to the new domain.
4. Rewrite or extend affected spec files in `/docs/specs/`.
5. Write new tests before touching existing implementation code.
6. Tag as a major version: `v2.0-stage1`.

**Version Tag:** `v2.0-stage1` (increments major version, re-runs the stage gate).

---

## Decision Tree

Use this decision tree when a new requirement arrives:

```
New requirement arrives
        │
        ▼
Does it replace or invalidate the core architecture?
   YES → Class C (Major Pivot) — full Stage 1 cycle
   NO  ↓
        ▼
Does it add a new module, entity, or user role?
   YES → Class B (Medium Addition) — ADR + new spec
   NO  ↓
        ▼
Is it a new field, format, or configuration option?
   YES → Class A (Small Addition) — spec + commit
        │
        ▼
   (Always) Write spec → Write tests → Approve → Implement → Verify → Commit
```

---

## How `engineering_roadmap.md` Tracks Feature Iterations

When new features arrive mid-project, add a versioned sub-section under the active stage in `engineering_roadmap.md`:

```markdown
## Stage 1 — System Architecture & Spec-Driven Development

- [x] Core catalog entity implemented and tested
- [x] Stage closing commit: v1.0-stage1

### Feature Iteration: v1.1 — Search & Filtering
- [ ] business_brief.md updated with search requirements
- [ ] ADR written if architecture is affected
- [ ] Spec written in /docs/specs/search.md
- [ ] Tests written and passing
- [ ] Commit: feat(search): implement title/author filtering
- [ ] Tag: v1.1-search
```

---

## Rules the AI Must Follow on Every Change

1. **Never modify implementation code before a spec exists.** If asked to add a feature without a spec, the AI must stop and write the spec first.
2. **Never skip the Approval step.** The AI proposes; the lead engineer signs off. This applies to Class A changes too.
3. **Never silently alter existing tests.** If a new feature changes existing behavior, the AI must explicitly flag the test delta and obtain approval before modifying passing tests.
4. **Always commit atomically.** Each spec, test suite, and implementation must be in separate commits. Never bundle unrelated changes.
5. **Always update `engineering_roadmap.md`** to reflect the feature iteration, even for Class A changes.

---

## Commit Convention for Feature Iterations

All change management commits follow the **Scoped Conventional Commits** format:

```text
<type>(<scope>): <short description in imperative mood>
```

- **Class A examples:**
  - `feat(catalog): add status filter to book search results`
  - `fix(export): handle empty CSV rows in PDF generation`
- **Class B examples:**
  - `feat(auth): add librarian admin role with elevated permissions`
  - `docs(adr): document decision to adopt role-based access control`
- **Class C examples:**
  - `feat(platform): migrate core engine to web target`
  - `docs(architecture): revise system design for multi-tenant deployment`

---

## Git Pushing Strategy (Remote Delivery Levels)

All commits and tags must be pushed to the remote repository according to the 3 delivery levels:

1. **Level 1 — Daily Feature Commits:** Pushed regularly during development:
   `git push origin main` (or active feature branch)
2. **Level 2 — Stage Milestone Tags:** Pushed upon completing a stage instruction prompt:
   `git tag -a v1.0-stageX -m "Stage X complete" && git push origin v1.0-stageX`
3. **Level 3 — Production Release Tags:** Pushed upon production delivery (triggers Stage 9 CI/CD deployment):
   `git tag -a v1.0.0 -m "Release v1.0.0" && git push origin v1.0.0`

---

## Summary

| Class | Scope | ADR Required | Stage Re-run | Version Tag |
| --- | --- | --- | --- | --- |
| **Class A (Small Addition)** | Field, format, config | No | No | None |
| **Class B (Medium Addition)** | Module, role, entity | Yes | No | `v1.x-scope` |
| **Class C (Major Pivot)** | Core redesign, new platform | Yes | Yes (Stage 1) | `v2.0-stage1` |
