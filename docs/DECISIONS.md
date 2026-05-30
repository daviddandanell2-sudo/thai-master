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

### 2026-05-30 — Swarm Audit & Strategy Update

**Context:** Comprehensive swarm audit completed across 6 research streams (system audit, SEO keyword plan, competitor intelligence, market research, 6-month takeover plan, Google SEO rules). The audit identified 16 issues (4 Critical, 5 High, 5 Medium, 2 Low) and revealed major gaps in the existing plan.

**Decision:**
1. Adopt the 3 strategic bets from the swarm audit: (a) In-person tutors in 13 Thai cities, (b) Curriculum specialists for IB/IGCSE/A-Level, (c) SEN & learning support as blue ocean.
2. Adopt the 163-keyword plan (24 seed + 139 expanded across 8 clusters A-J).
3. Adopt the 12-competitor intelligence database (expanded from 7).
4. Update the 6-month plan to reflect safe new-domain velocity (max 8 pages Month 1).
5. Update all project documentation to reflect audit findings.

**Reason:** The audit was evidence-based from 180+ sources across 25+ citations. The existing plan was generic and underestimated competitive pressure (TutorChase, Tutopiya) while overestimating safe content velocity for a new domain. The 3 strategic bets are validated by competitor gap analysis, keyword research, and market data.

**Rejected:**
- Keep original 12-page Month 1 target (risk of scaled content abuse penalty on new domain).
- Ignore SEN opportunity (competitors have zero SEN content; first-mover advantage is significant).
- Maintain 7-competitor list (misses regional players in Phuket, Chiang Mai, Pattaya).
- Continue with unverified keyword volumes (risk of wrong prioritisation).

**Files:**
- `docs/6-MONTH-PLAN.md` — major rewrite
- `docs/SEO-PLAN.md` — major rewrite
- `docs/STRATEGY.md` — updated with 3 bets and market sizing
- `docs/RISKS.md` — 10 new risks added
- `docs/TRACKING.md` — new tasks T007-T015 added
- `docs/DECISIONS.md` — this entry

---

### 2026-05-30 — Safe Velocity for New Domain

**Context:** Google's March 2024 spam policy update introduced "scaled content abuse" — targeting sites that generate many pages primarily to manipulate search rankings. The original 6-month plan called for 12 pages in Month 1, which exceeds safe velocity for a brand-new domain with zero authority. The swarm audit's Google SEO Rules document (08-GOOGLE-SEO-RULES.md) analysed this risk in detail.

**Decision:**
1. **Month 1 maximum:** 8 pages (not 12). Safe new-domain velocity.
2. **Weekly maximum:** 4-6 pages/week in Months 1-3; 8-10/week in Months 4-6.
3. **48-hour gap:** Minimum 48 hours between publishing programmatic combination pages.
4. **First 30 days:** Max 8 pages to establish crawl frequency trust with Google.
5. **Depth before breadth:** Reach 25-30 high-quality pages in primary topic area before expanding.

**Reason:**
- Danny Sullivan (Google Search Liaison): "we don't really care how you're doing this scaled content, whether it's AI, automation, or human beings. It's going to be an issue."
- New domains are under heightened scrutiny. A low, steady cadence establishes trust.
- Publishing 12 pages in Week 1 triggers scaled content abuse signals regardless of quality.
- The 8-page Month 1 target still covers: Home, About, Contact, Pricing, Bangkok, Phuket, Chiang Mai, Math Tutoring.

**Rejected:**
- Launch all 90 pages at once (highest-risk action; triggers immediate penalty).
- Original 12-page Month 1 target (too aggressive for new domain).
- Same-day bulk publishing of combination pages (clear spam signal).
- Ignore velocity rules and "hope Google doesn't notice" (reckless).

**Files:**
- `docs/6-MONTH-PLAN.md` — Month 1 updated to 8 pages
- `docs/SEO-PLAN.md` — content calendar reflects safe velocity
- `docs/RISKS.md` — R015 added (scaled content abuse)
- `archive/audit-raw/audit/08-GOOGLE-SEO-RULES.md (archived)` — source document

---

### 2026-05-30 — SEN as Blue Ocean

**Context:** The swarm audit's keyword research and competitor analysis revealed that SEN (Special Educational Needs) tutoring in Thailand is virtually uncontested. Competitors (TutorChase, Tutopiya, Krutoo, Superprof) have zero SEN-specific landing pages. Only No Limits Community Services competes for "ADHD tutor Thailand." Dyslexia tutor Bangkok has one OG-trained tutor listed on MyPrivateTutor. BKK Kids lists 12+ learning support centres but most are clinics, not tutors.

**Decision:**
1. Prioritise SEN pages in Month 3-4: ADHD tutor, dyslexia tutor, autism tutor, EAL support, general SEN support.
2. Publish 2 SEN parent guides in Month 4-5.
3. Add SEN-specialist structured data (Service schema with SEN specificity).
4. Target partnerships with 3 international school learning support departments by Month 6.
5. Position as "tutoring support for students with ADHD" — NOT "ADHD treatment" (medical liability).

**Reason:**
- First-mover advantage: no competitor has dedicated SEN tutoring landing pages in Thailand.
- High willingness to pay: SEN parents typically pay premium rates for specialist support.
- Low competition: keyword difficulty is "Low" for all SEN terms.
- Google rewards topical authority: owning the entire SEN cluster signals expertise.
- Ethical positioning: frame as educational support, not medical treatment.

**Rejected:**
- Treat SEN as a generic subject like math or English (misses the specialist positioning).
- Ignore SEN entirely (leaves significant revenue and SEO opportunity on the table).
- Frame as medical/treatment service (regulatory risk, outside scope).
- Wait until "later" to build SEN pages (competitors may move first).

**Files:**
- `docs/STRATEGY.md` — SEN added as Bet 3
- `docs/6-MONTH-PLAN.md` — SEN pages in Month 3-4
- `docs/SEO-PLAN.md` — SEN keywords in Clusters D, F, I
- `docs/RISKS.md` — R018 (missing SEN tutor pool) added

---

### 2026-05-30 — Duplicate github/ Removal

**Context:** The swarm system audit (01-SYSTEM-AUDIT.md) found two copies of `copilot-instructions.md` in the repository root:
- `.github/copilot-instructions.md` ← Correct GitHub location (GitHub Copilot reads from `.github/` only)
- `github/copilot-instructions.md` ← Incorrect duplicate (without leading dot, not a recognised GitHub path)

**Decision:** Delete `github/copilot-instructions.md`. Keep only `.github/copilot-instructions.md`.

**Reason:**
- Single source of truth. The `.github/` path is the standard recognised by GitHub Copilot.
- Having one copy eliminates the risk of divergence — if files diverge, the `github/` copy becomes a source of stale instructions.
- Potential confusion for AI agents: if any automation script walks the file tree looking for configuration, it may find both files and use the wrong one.
- The `github/` directory (without the dot) serves no purpose.

**Rejected:**
- Keep both files "just in case" (creates maintenance burden and divergence risk).
- Delete `.github/` and keep `github/` (wrong — GitHub Copilot won't read it).
- Merge the two into a new location (unnecessary — `.github/` is the correct convention).

**Files:**
- `github/copilot-instructions.md` — to be deleted
- `.github/copilot-instructions.md` — keep as single source of truth
- `docs/TRACKING.md` — T015 added for deletion task

---
