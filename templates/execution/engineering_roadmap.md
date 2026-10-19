---
engineer: "[Lead Engineer / Developer]"
cli_assistant: "[AI Assistant / CLI Tool]"
stack: "[Language + Framework + Database]"
start_date: YYYY-MM-DD
---

# Engineering Execution Roadmap

## Project Stage Tailoring Matrix
**Stage Customization:** During Stage 0 bootstrap, review the stages below with the AI assistant. Mark each stage as `[Active]` or `[N/A]` (Skipped) based on your application scope. If a stage is marked `[N/A]`, the AI will execute the Stage Skip Protocol and advance.

| Stage | Status | Scope / Rationale |
| --- | --- | --- |
| **Stage 0: Repository Architecture & Engineering Baseline** | `[Active]` | Baseline Repo Architecture & Rules (Required) |
| **Stage 1: System Architecture & Spec-Driven Development** | `[Active]` | System Architecture & Core Specs (Required) |
| **Stage 2: Data Ingestion & Transformation Skill Infrastructure** | `[Active]` | Data Ingestion & Transformation Skill Infrastructure |
| **Stage 3: Subagent Automation & Deterministic Processing Engine** | `[Active]` | Subagent Automation & Rule Engine |
| **Stage 4: Multi-Agent Orchestration & Aggregation Pipelines** | `[Active]` | Multi-Agent Orchestration Pipelines |
| **Stage 5: Quality Assurance Baselines & Static Code Analysis** | `[Active]` | Quality Assurance Baselines & Static Analysis |
| **Stage 6: Autonomous Code Audit & Reporting Engine** | `[Active]` | Autonomous Code Audit & Reporting Engine |
| **Stage 7: Threat Modeling & Security Vulnerability Audit** | `[Active]` | Threat Modeling & Security Vulnerability Audit |
| **Stage 8: Security Guardrails & Multi-Tenant Data Isolation** | `[Active]` | Security Guardrails & Multi-Tenant Isolation |
| **Stage 9: Deployment, Containerization & Release Infrastructure** | `[Active]` | Deployment, Containerization & CI/CD Release |

---

## Stage 0 — Repository Architecture & Engineering Baseline

- [ ] Initialize git repository and create initial project folder structure
- [ ] Set up layout structure (`/src`, `/docs`, `.ai/agents/`, `.ai/skills/`, `.ai/templates/`)
- [ ] Copy standard templates from `/templates/` to `.ai/templates/`, `/docs/`, and project root
- [ ] Project README created with tech stack and directories explained
- [ ] Persistent AI memory file (`AGENTS.md` or `AI_RULES.md`) initialized
- [ ] Stage closing Conventional Commit made and tag `v1.0-stage0` pushed

**Notes:**

---

## Stage 1 — System Architecture & Spec-Driven Development

- [ ] Product requirements reviewed in `/docs/business_brief.md` before architectural design
- [ ] Technical architecture defined in `/docs/architecture.md`
- [ ] Technical spec for core logic written in `/docs/specs/core_logic.md` using the template
- [ ] Automated tests generated covering all acceptance criteria
- [ ] Core business logic module implemented in `/src/` and verified by tests
- [ ] Stage closing Conventional Commit made and tag `v1.0-stage1` pushed

**Notes:**

---

## Stage 2 — Data Ingestion & Transformation Skill Infrastructure

- [ ] Reusable data parser skill defined in `.ai/skills/data_parser.md` using the template
- [ ] Ingestion logic implemented in `/src/` supporting at least two raw formats (e.g. CSV, JSON)
- [ ] Integration and edge-case tests written verifying parser output
- [ ] Architecture Decision Record (ADR) documented in `/docs/`
- [ ] Stage closing Conventional Commit made and tag `v1.0-stage2` pushed

**Notes:**

---

## Stage 3 — Subagent Automation & Deterministic Processing Engine

- [ ] Development subagent contract defined in `.ai/agents/` using the template
- [ ] Deterministic rule-based processing module implemented in `/src/` (no LLMs at runtime)
- [ ] Subagent successfully invoked to perform a real task (e.g., test generation)
- [ ] Subagent transferability tested on other modules (e.g., the parser skill)
- [ ] Architecture Decision Record (ADR) documented in `/docs/`
- [ ] Stage closing Conventional Commit made and tag `v1.0-stage3` pushed

**Notes:**

---

## Stage 4 — Multi-Agent Orchestration & Aggregation Pipelines

- [ ] At least three specialized subagents defined in `.ai/agents/` (e.g., Schema Designer, Logic Implementer, Test Generator)
- [ ] Coordination pattern (e.g. Pipeline or Fan-out) documented in `/docs/` (ADR)
- [ ] Data aggregation and alerting module implemented in `/src/` using coordinated subagents
- [ ] Multi-agent workflow execution cost evaluated and documented in `/docs/coordination-metrics.md`
- [ ] Stage closing Conventional Commit made and tag `v1.0-stage4` pushed

**Notes:**

---

## Stage 5 — Quality Assurance Baselines & Static Code Analysis

- [ ] Baseline quality audit report generated in `/docs/audit/quality-base.md`
- [ ] Quality rules and code standards defined in `/docs/standards.md`
- [ ] Formatter and linter configured for the project stack
- [ ] Core modules refactored and test coverage gaps closed
- [ ] Local git hook or verification script (`ci.sh` / `pre-commit`) running formatter, linter, and tests
- [ ] Final quality audit report comparing metrics generated in `/docs/audit/quality-v2.md`
- [ ] Stage closing Conventional Commit made and tag `v1.0-stage5` pushed

**Notes:**

---

## Stage 6 — Autonomous Code Audit & Reporting Engine

- [ ] Quality reviewer subagent contract defined in `.ai/agents/quality_reviewer.md` with a comment cap
- [ ] Reviewer integrated into the local Git hooks or development workflow
- [ ] Analytics and export module (aggregations, CSV/JSON/PDF export) implemented under reviewer oversight
- [ ] Significant reviewer interactions logged in `/docs/reviewer-log.md`
- [ ] Quality reviewer agent refined based on log observations
- [ ] Stage closing Conventional Commit made and tag `v1.0-stage6` pushed

**Notes:**

---

## Stage 7 — Threat Modeling & Security Vulnerability Audit

- [ ] System threat model documented in `/docs/security/threat-model.md`
- [ ] Hardcoded secrets scanned and dependency vulnerabilities audited (npm audit / pip-audit)
- [ ] Boundary validation rules and logging data leakage checks implemented
- [ ] Custom skills and subagents tested against prompt injection payloads
- [ ] Security baseline audit report generated in `/docs/security/baseline.md`
- [ ] Stage closing Conventional Commit made and tag `v1.0-stage7` pushed

**Notes:**

---

## Stage 8 — Security Guardrails & Multi-Tenant Data Isolation

- [ ] Security reviewer subagent contract defined in `.ai/agents/security_reviewer.md` as a strict blocker
- [ ] Reviewer hook configured to automatically block commits containing blocking issues
- [ ] User authentication and secure session management implemented in `/src/`
- [ ] Multi-user isolation logic applied to data models and queries
- [ ] Negative test suite checking isolation boundaries written and passing
- [ ] Security reviewer interactions logged in `/docs/reviewer-log.md` and contract refined
- [ ] Stage closing Conventional Commit made and tag `v1.0-stage8` pushed

**Notes:**

---

## Stage 9 — Deployment, Containerization & Release Infrastructure

- [ ] Production environment template `.env.example` configured with zero checked-in secrets
- [ ] Dockerfile or stack-specific multi-stage build script authored and verified
- [ ] Automated CI/CD workflow configured executing linting, tests, build, and deployment gates
- [ ] Production health check endpoint (`/health`) implemented and verified
- [ ] Release notes and changelog generated in `/docs/release_notes.md` using the template
- [ ] Stage closing Conventional Commit made and release tag `v1.0.0` pushed

**Notes:**

---

