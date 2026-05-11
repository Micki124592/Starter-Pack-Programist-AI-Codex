# AGENTS.md

Version: 1.0.0
Status: Stable
Updated: 2026-05-11

---

# Overview

This repository uses a standardized AI/Codex project structure.

The goal of this structure is to keep changes predictable, reduce architectural drift, preserve maintainability, improve repository discoverability, reduce unnecessary token usage, and allow safe collaboration between specialized AI agents.

---

# Source of truth

Agents live in `ai/agents`.

Skills live in `ai/skills`.

`.agents` contains compatibility symlinks only:

```text
.agents/agents -> ../ai/agents
.agents/skills -> ../ai/skills
```

Rules:
- Do not duplicate files between `ai` and `.agents`.
- Prefer symlinks over copies.
- If symlinks are unavailable, copying is allowed only as fallback behavior.

---

# Forbidden structure

Never create:
- `.claude`
- duplicated agent trees
- duplicated skill trees
- secondary conflicting AGENTS systems

---

# Stable file format

All agents and skills must use stable production format with YAML frontmatter, versioning, status, updated date, priority, explicit workflows, explicit rules, and explicit output format.

Skills are instruction-only, non-executable, reusable workflow definitions.

---

# Project structure

```text
ai/
  agents/
  skills/
  project-map/
    PROJECT_MAP.md
    FILE_INDEX.md
    ANCHORS.md
    MODULES.md
    WORKFLOWS.md
  validation/
    validate_ai_structure.py

.agents/
  agents -> ../ai/agents
  skills -> ../ai/skills

AGENTS.md
```

---

# Repository discovery workflow

Before making changes:

1. Read `AGENTS.md`.
2. Read `ai/project-map/PROJECT_MAP.md` if available.
3. Detect package manager.
4. Detect framework/runtime.
5. Detect monorepo tooling.
6. Detect ORM/database.
7. Detect test runner.
8. Detect lint/typecheck/build tooling.
9. Inspect related files.
10. Identify existing conventions.
11. Reuse existing patterns before creating new ones.

---

# Global engineering rules

Always:
- prefer edit over rewrite,
- prefer incremental improvements,
- prefer smallest safe change,
- reuse existing architecture,
- reuse existing UI patterns,
- reuse existing testing patterns,
- reuse existing DTO/schema patterns.

Never invent APIs, routes, DTOs, database fields, services, env vars, commands, or deployment flows.

---

# Build and verification rules

Always identify real repository commands.

Never invent commands.

When available, identify install, dev, lint, typecheck, test, build, start, and deployment commands.

If a command cannot be run, explain why.

---

# Definition of Done

A task is done only when relevant files were updated, related checks were run when possible, skipped checks were explained, risks were reported, no unrelated refactors were introduced, project map was updated if structure changed, AGENTS.md was updated if standards changed, and output follows concise reporting format.

---

# Standard reporting format

```md
## Result

Status: Done / Partial / Blocked

Changed:
- [path](path) - short reason

Verified:
- `command`

Skipped:
- `command` - reason

Risks:
- short risk or `None`

Next:
- short follow-up or `None`
```

---

# Agent routing

Priority order:

1. security-engineer
2. debugger
3. database-engineer
4. backend-engineer
5. frontend-engineer
6. testing-engineer
7. performance-engineer
8. devops-engineer
9. architect
10. reviewer
11. documentation-writer
12. product-engineer

---

# Standard skills

Review skills:
- api-review
- frontend-qa
- security-check
- code-review
- nextjs-review
- nestjs-review
- typescript-quality-check
- database-query-review
- prisma-migration-review
- dependency-audit
- env-config-review

Workflow skills:
- build-verification
- project-bootstrap
- repo-analysis
- debugging-workflow
- refactor-plan
- test-generation
- release-checklist
- documentation-update

---

# Bootstrap requirements

Bootstrap/update workflow must support creating missing structure, updating existing repositories, detecting missing agents, detecting missing skills, regenerating symlinks, auto-merging AGENTS.md, validating integrity, preserving non-empty custom files, and generating project map files.

Bootstrap behavior must be idempotent, merge-safe, and convention-preserving.

---

# Validation requirements

Validation must verify required directories, required agents, required skills, AGENTS.md consistency, broken symlinks, duplicated files, missing project map files, and invalid structure.

---

# Meta-rules

Always read existing code first, prefer edit over rewrite, avoid unnecessary abstractions, preserve existing conventions, keep changes reviewable, keep reports concise, prefer links over pasted content, and reduce unnecessary token usage.

Never hallucinate repository structure, commands, APIs, schemas, env vars, or deployment workflows.

---

# Final rule

The repository is the source of truth.

If repository reality conflicts with assumptions, inspect the code, follow the code, update documentation, and avoid speculation.
