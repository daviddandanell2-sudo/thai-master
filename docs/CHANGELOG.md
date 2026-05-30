# Changelog

## Purpose

Every significant change to the project must be recorded here.

Format: `YYYY-MM-DD — [Area] — What changed — Why`

## Changelog

### 2024-01-15 — System — Image & Quality Rules Integration

**What:** Integrated the AI Website Builder Image & Quality Rules into the existing Private Tutoring Thailand system.

**Why:** Images and visual quality were not formally governed. Every page needs consistent, on-brand imagery and browser-based quality checks.

**Files created:**
- `docs/image-rules.md` — Image creation rules (Thai tutor, European child, private setting)

**Files modified:**
- `docs/quality-control.md` — Added MCP Browser Review and Fix/Finalize sections
- `prompts/image-agent.md` — Rewritten with BFL.ai workflow and verification checklist
- `prompts/qa-agent.md` — Added image verification and browser review steps
- `scripts/generate-pages.md` — Added image generation and browser review steps
- `scripts/validate-pages.md` — Added image verification and visual/browser checks
- `scripts/check-seo.md` — Added image rules check
- `templates/location-page-template.md` — Added Image Brief section
- `templates/subject-page-template.md` — Added Image Brief section
- `templates/curriculum-page-template.md` — Added Image Brief section
- `templates/location-subject-page-template.md` — Added Image Brief section
- `templates/blog-template.md` — Added Image Brief section
- `templates/meta-template.md` — Updated og:image rules
- `docs/content-rules.md` — Added images to mandatory structure and checklist
- `docs/automation-rules.md` — Added image/browser review to quality gates
- `data/page-types.json` — Added `"images"` to requiredSections for all page types
- `AGENTS.md` — Added Image & Visual Quality Rules section
- `CLAUDE.md` — Added Image & Visual Quality Rules section
- `.github/copilot-instructions.md` — Added Image & Visual Quality Rules section
- `prompts/content-agent.md` — Added image rules to inputs, planning, and self-check
- `prompts/seo-agent.md` — Added image rules to meta data review

---

### 2024-01-15 — System — Project Operating System + Boss AI Architecture

**What:** Implemented the full project operating system with Boss AI + Worker AI architecture.

**Why:** The project needs centralized control, tracking, strategy, and formal execution. No work should happen outside the system.

**Files created:**
- `docs/TRACKING.md` — Live task tracking
- `docs/STRATEGY.md` — Consolidated strategy
- `docs/DECISIONS.md` — Decision log
- `docs/RISKS.md` — Risk register
- `docs/TEAM.md` — Team roles and responsibilities
- `docs/CHANGELOG.md` — This file
- `docs/SEO-PLAN.md` — 12-month SEO roadmap
- `docs/6-MONTH-PLAN.md` — Month-by-month build plan
- `docs/BACKLOG.md` — Idea backlog
- `docs/EXECUTION-LOOP.md` — Formal execution loop
- `prompts/boss-agent.md` — Master orchestrator
- `prompts/worker-research-agent.md` — Research specialist
- `prompts/worker-builder-agent.md` — Page builder
- `prompts/worker-image-agent.md` — Image maker
- `prompts/worker-qa-agent.md` — Quality checker
- `prompts/worker-fixer-agent.md` — Issue fixer
- `prompts/worker-deployer-agent.md` — Deployer

**Files modified:**
- `README.md` — Rewritten as project control center
- `AGENTS.md` — Added execution loop and project type classification
- `CLAUDE.md` — Added execution loop and project type classification
- `.github/copilot-instructions.md` — Added execution loop and project type classification
- `docs/quality-control.md` — Added escalation rule (3 failures → human)
- `scripts/generate-pages.md` — Added execution loop reference
- `data/page-types.json` — Added `"images"` to requiredSections

---

### 2026-05-30 — System — Framework, Domain & Infrastructure Decision

**What:** Resolved blockers B001 (framework) and unblocked B002 (domain/hosting). Approved plan: Next.js 15 App Router + Vercel + single domain `privatetutoringthailand.com` + two-repo architecture.

**Why:** The project was stalled on infrastructure decisions. Without a framework and domain, no pages can be published and no SEO indexing can begin. Herman needs a clear brief to execute the technical setup.

**Files created:**
- `.kimi/plans/banshee-nova-green-lantern.md` — Full infrastructure plan with repo structure, Vercel config, implementation phases, and domain alternatives.

**Files modified:**
- `docs/DECISIONS.md` — Added framework/domain/infrastructure decision entry
- `docs/TRACKING.md` — T005 marked Done, T06 updated to Waiting for input (Herman), B001 moved to Resolved Blockers, B002 updated
- `docs/RISKS.md` — B001 resolved

**Decisions recorded in:** `docs/DECISIONS.md`

---

### [Template]

**Date:** YYYY-MM-DD

**Area:** System / Content / SEO / Images / QA / Deploy

**What:**

**Why:**

**Files created:**

**Files modified:**

**Decisions recorded in:** `docs/DECISIONS.md`
