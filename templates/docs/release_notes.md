---
version: "v1.0.0"
release_date: YYYY-MM-DD
author: "[Lead Engineer / Product Owner]"
status: "draft" # draft / published
git_tag: "v1.0.0"
---

# Release Notes — [Application Name] (v1.0.0)

## Executive Summary
[Provide a 2-3 sentence high-level overview of this release milestone, key highlights, and primary business or technical value delivered.]

---

## 1. New Features (`feat`)
- **[Feature Scope / Title]:** [Concise description of the user capability or feature added.]
- **[Feature Scope / Title]:** [Concise description of the user capability or feature added.]

## 2. Bug Fixes & Refactoring (`fix` / `refactor`)
- **[Module Scope]:** [Description of issue resolved or performance optimization.]
- **[Module Scope]:** [Description of issue resolved or performance optimization.]

## 3. Security & Compliance (`security`)
- **Vulnerability Remediation:** [Summary of security audits, dependency fixes, or prompt injection guardrails.]
- **Access Isolation:** [Tenant isolation or authorization boundary enhancements.]

## 4. Architectural & System Changes (`docs` / `chore`)
- **Architecture Decision Records:** [List ADR IDs incorporated in this release, e.g., ADR-001].
- **Dependency Updates:** [Major framework, database driver, or library version updates.]

## 5. Breaking Changes & Migration Steps
> [!WARNING]
> [Detail any breaking API changes, schema migrations, or manual environment variable updates required before upgrading.]

- **Schema Migration:** [Database migration steps or scripts to execute.]
- **Environment Variables:** [New required keys added to `.env`.]

## 6. Verification & Test Metrics
- **Automated Test Coverage:** [Target test coverage achieved, e.g. 85%]
- **Static Analysis & Security Audit:** [Status of linting, security blocker hooks, and vulnerability checks]
- **Verification Tag:** `git tag -a v1.0.0 -m "Release v1.0.0"`

## 7. Deployment Instructions
1. Pull the latest release tag: `git checkout v1.0.0`
2. Update environment configuration using `.env.example`.
3. Execute build/containerization commands: `docker build -t app:v1.0.0 .`
4. Run post-deployment health check endpoint: `/health`
