# Decisions

## Purpose

Every important decision must be recorded here. This is the project memory.

When a decision is made:
1. Add it to this file
2. Include the date
3. Include the context (why the decision was needed)
4. Include the decision (what was chosen)
5. Include the reason (why this choice)
6. Include any rejected alternatives

## Decision Log

### 2024-01-15 — Image Rules

**Context:** The website needs consistent, on-brand images that match the target audience (expat families in Thailand).

**Decision:** All images must show one Thai tutor, one European child, in a private apartment or villa setting. Never classrooms. Never Thai children. Never two children.

**Reason:** The target audience is expat parents. They need to see themselves and their children in the imagery. Thai tutors signal local expertise. Private settings signal premium, discreet service.

**Rejected:** Generic stock photos, classroom settings, group tutoring images.

**File:** `docs/image-rules.md`

---

### 2024-01-15 — Operating System Integration

**Context:** The project is growing. Multiple AI agents are working on pages, images, QA, and deployment. Work is becoming uncoordinated.

**Decision:** Implement a full project operating system with Boss AI + Worker AI architecture, tracking, strategy consolidation, and formal execution loop.

**Reason:** Prevents random work, ensures every task is tracked, provides recovery after crashes, enables human escalation, and makes the project inspectable at any time.

**Rejected:** Ad-hoc task management, minimal tracking layer.

**Files:** `docs/TRACKING.md`, `docs/STRATEGY.md`, `prompts/boss-agent.md`, `docs/EXECUTION-LOOP.md`

---

### 2026-05-30 — Framework, Domain & Infrastructure

**Context:** The project cannot proceed to deployment without choosing a website framework, domain strategy, and hosting setup. Blockers B001 (framework) and B002 (domain/hosting) have stalled T005 and T006. Herman controls the infrastructure layer.

**Decision:**
1. **Framework:** Next.js 15 (App Router) with TypeScript and Tailwind CSS.
2. **Hosting:** Vercel Pro (Herman owns the project).
3. **Domain strategy:** Single domain — `privatetutoringthailand.com`. No satellite domain.
4. **Repo architecture:** Two-repo separation:
   - This repo (`private-tutoring-thailand`) = content control center (brain). Private. AI team works here.
   - Website repo = Next.js app (body). Herman owns this. Content synced from control center.
5. **Content pipeline:** Markdown + JSON in control center → copied to website repo → Next.js `generateStaticParams()` builds static pages → Vercel deploys.

**Reason:**
- Next.js App Router provides `generateStaticParams()` for programmatic SEO page generation from JSON, ISR for updating pages without full rebuilds, built-in image optimization, and the Metadata API for dynamic SEO metadata. It is Vercel-native.
- A single domain consolidates all SEO authority. Thailand's tutoring market is mid-size; one domain can dominate. A satellite domain would split link equity and confuse users.
- Two-repo separation protects the codebase from accidental AI edits while keeping content workflows clean.

**Rejected:**
- Astro (no ISR, weaker dynamic routing for JSON-driven pages, smaller ecosystem).
- Satellite domain strategy (splits SEO authority, unnecessary complexity for this market size).
- Monorepo combining code + content (risk of AI agents modifying code when they should only edit content).
- WordPress (plugin bloat, poor version control for AI workflows).

**Files:**
- `docs/DECISIONS.md` — this entry
- `docs/TRACKING.md` — T005 marked Done, T006 unblocked
- `docs/CHANGELOG.md` — change logged
- `docs/RISKS.md` — B001 resolved
- Plan file: `/Users/openclaw/.kimi/plans/banshee-nova-green-lantern.md`

---

### [Template]

**Date:** YYYY-MM-DD

**Context:**

**Decision:**

**Reason:**

**Rejected:**

**Files:**
