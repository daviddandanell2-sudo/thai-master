# Execution Handoff

**Source:** Swarm audit `10-EXECUTION-HANDOFF.md` — guardrails, velocity tracker, definition of done, and quick reference for the execution swarm.

**Status:** Ready for execution. All streams mapped to `docs/6-MONTH-PLAN.md` and `docs/TRACKING.md`.

---

## 1. Guardrails (Non-Negotiable Rules)

These rules apply to every task. Violating any of them risks manual action, deindexing, or reputational damage.

| # | Rule | Violation Consequence | How to Enforce |
|---|------|----------------------|----------------|
| 1 | **No fake data** | Manual action for misleading content, permanent trust loss | Human review of all content before publish. `check-seo.ts` validates claims against source list |
| 2 | **No city-swap duplicates** | Doorway page penalty, deindexing | `check-seo.ts` enforces 60%+ unique content per combination page. Fail = noindex or rewrite |
| 3 | **Human approval before publish** | Scaled content abuse if auto-published | All pages pass `check-seo.ts` + human review before `git push` |
| 4 | **60%+ unique on combo pages** | Doorway page classification | `check-seo.ts` compares combination pages; flag if uniqueness < 60% |
| 5 | **Max 8 pages Month 1** | Scaled content abuse on new domain | Hard cap: 8 pages in first 30 days. Max 5-6/week in Months 1-3. Max 8-10/week in Months 4-6 |
| 6 | **48-hour gap between combination pages** | Bulk publishing spam signal | Publish combination pages Mon/Wed/Fri only. Never same-day batch |
| 7 | **No fabricated testimonials** | FTC violation, manual action | Only real testimonials from verified clients. No placeholder reviews |
| 8 | **No fake tutor profiles** | Trust signal collapse | Tutor profiles list real credentials, verifiable on request |
| 9 | **SEN content: not medical treatment** | Regulatory scrutiny, liability | Frame as "tutoring support." Include disclaimer. Require SEN training credentials |
| 10 | **School pages: no trademark claims** | Legal action from schools | Frame as "tutoring for families at [School]" not "official [School] tutor" |
| 11 | **Exact-match anchor text ≤ 30%** | Penguin-like algorithmic suppression | `check-seo.ts` audits anchor text diversity. Rotate 3-4 variations per target |
| 12 | **Indexing API ≤ 200 notifications/day** | Rate limiting, API revocation | Hermes daily counter, per-URL dedup (no resend within 24h) |
| 13 | **Schema must match visible content** | Manual action for misleading structured data | Validate every page in Rich Results Test before publish |
| 14 | **No hidden schema** | Rich results removal | Never add JSON-LD for content not rendered on page |

---

## 2. Content Velocity Tracker

| Month | Week | Pages to Publish | Cumulative | Max per Week | Cadence |
|-------|------|-----------------|------------|--------------|---------|
| 1 | 1 | 4 (Home, About, Contact, Bangkok) | 4 | 4 | 2 pages x 2 |
| 1 | 2 | 4 (Chiang Mai, Phuket, Math, English) | 8 | 4 | 2 pages x 2 |
| 1 | 3 | 0 | 8 | 0 | Infrastructure/testing |
| 1 | 4 | 0 | 8 | 0 | QA, GSC verification |
| 2 | 1 | 5 | 13 | 5 | 1 page/day |
| 2 | 2 | 5 | 18 | 5 | 1 page/day |
| 2 | 3 | 5 | 23 | 5 | 1 page/day |
| 2 | 4 | 4 | 27 | 5 | Combo pages start |
| 3 | 1 | 5 combo | 32 | 5 | Mon/Wed/Fri + 2 |
| 3 | 2 | 5 combo | 37 | 5 | Mon/Wed/Fri + 2 |
| 3 | 3 | 5 combo | 42 | 5 | Mon/Wed/Fri + 2 |
| 3 | 4 | 5 combo | 47 | 5 | Mon/Wed/Fri + 2 |
| 4+ | Varies | Per plan | 95+ by Month 6 | 8-10 | Flexible |

**Hard stops:** If GSC shows coverage issues, velocity drops to 2/week until resolved. If any combination page fails uniqueness check, no new combo pages until fix is verified.

**Velocity comparison:**

| Month | Safe Velocity (08-GOOGLE-SEO-RULES) | Planned (6-MONTH-PLAN) | Ratio | Status |
|-------|-------------------------------------|------------------------|-------|--------|
| 1 | 4-6 pages | 8 pages | 1.3-1.5x | PASS (within safe ramp) |
| 2 | 6-8 pages | 23 pages | 2.9-3.8x | WARNING |
| 3 | 8-12 pages | 20 pages | 1.7-2.5x | WARNING |
| 4 | 12-16 pages | 20 pages | 1.3-1.7x | WARNING |
| 5 | 16-20 pages | 15 pages | 0.8-0.9x | PASS |
| 6 | 20-30 pages | 10+ pages | 0.3-0.5x | PASS |

**Month 2-4 justification:** Higher velocity is safe because all pages are human-reviewed, 800+ words each, max 40% template sharing, staggered publishing with 48hr gaps. Monitor GSC weekly; drop to safe velocity if any issues.

---

## 3. Stream D: Hermes Automation

**Owner:** David | **Goal:** Build Hermes handlers, reports, dashboard, permission matrix

**Start condition:** Stream A delivers first deploy (site live).

| Task | Action | Blocked By | Effort | Acceptance Criteria |
|------|--------|-----------|--------|---------------------|
| **D1** | GSC handler — read-only analytics | Site live | 4h | `initialize()`, `querySearchAnalytics()`, `inspectUrl()`, `getTopKeywords()`. Hard-blocked: any write operation. |
| **D2** | GA4 handler — read-only session/event data | Site live | 4h | `initialize()`, `runReport()`, `getSessionsByPage()`, `getEventCounts()`, `getRealtimeUsers()`. Hard-blocked: property modification. |
| **D3** | Report generators (7 types) | D1 + D2 | 6h | Daily rank, weekly organic, weekly leads, post-deploy validation, content quality scan, SEO drift alert, index coverage alert. All write JSON to `exports/`. |
| **D4** | Permission broker + dashboard | D3 | 4h | 40-action permission matrix, 5 metric cards, alert feed, action queue, agent run log, one-click deploy. |
| **D5** | Remaining handlers | D4 | 12h | GitHub, Vercel, Claude, BFL, Indexing API handlers. All approval-gated where appropriate. |

**Source:** `docs/hermes-control.md`

---

## 4. Definition of Done

All streams complete when:

| Stream | Done When |
|--------|-----------|
| **A (Infrastructure)** | 8 pages live, domain resolves, CI/CD pipeline auto-deploys on push, all 5 scripts executable, templates render correctly |
| **B (Content)** | 27+ content files written (.md), all pass `check-seo.ts`, all combination pages pass 60% uniqueness, human review complete |
| **C (SEO)** | GSC + GA4 receiving data, all schema validates, sitemap submitted, GBP live, internal link graph defined |
| **D (Hermes)** | GSC + GA4 handlers running, daily rank + weekly organic/lead reports generating, dashboard accessible, permission matrix enforced |

**Project done (Month 1):** `privatetutoringthailand.com` loads, 8 pages live, GA4 receiving data, GSC verified, Hermes daily rank reports running.

---

## 5. Quick Reference

| Question | Answer |
|----------|--------|
| What goes live first? | Homepage + About + Contact + Bangkok location + Math/English subjects |
| What's the #1 SEO asset? | 40+ combination pages (`/thailand/{city}/{subject}-tutor/`) — highest intent, lowest competition |
| What's the biggest risk? | Doorway page penalty on combination pages → enforce 60% unique + 800+ words + 3+ local signals |
| What's the first-mover opportunity? | SEN/ADHD tutoring keywords — virtually uncontested in Thailand |
| Who registers the domain? | Herman (Day 1, P0 blocker) |
| Who builds the scripts? | Dev Agent (Week 1-2, P0 blocker) |
| Who writes content? | Content Agent (parallel to infrastructure, starts Day 1) |
| Who sets up GSC/GA4? | SEO Agent (Day 1-2, blocked by domain) |
| Who builds Hermes? | David (Week 3-4, blocked by first deploy) |
| Max pages Month 1? | 8 (hard cap for new domain) |
| Max combo pages per week? | 3 (Mon/Wed/Fri cadence, 48-hour gap) |
| How to check uniqueness? | Run `check-seo.ts` — fails if < 60% unique |
| How to validate schema? | Google Rich Results Test — zero errors required |
| What if GSC shows issues? | Drop velocity to 2 pages/week, fix issues before resuming |
