# Tracking

## Purpose

This is the live task list. It is the source of truth for what is happening in the project.

When a task starts, changes, or finishes, update this file.

## Legend

| Status | Meaning |
|---|---|
| Not started | Planned but not begun |
| In progress | Being worked on right now |
| Waiting for input | Blocked, needs information or decision |
| Waiting for approval | Done, needs human sign-off |
| Blocked | Cannot proceed until something else is resolved |
| Testing | Under QA or review |
| Done | Complete and verified |
| Archived | Cancelled or no longer relevant |

| Priority | Meaning |
|---|---|
| P0 | Critical — blocks other work |
| P1 | High — important for current phase |
| P2 | Medium — planned for next phase |
| P3 | Low — nice to have |

---

## Active Tasks

| ID | Task | Area | Type | Owner | Status | Priority | Deadline | Blockers | Dependencies | Related Files | Last Updated | Notes |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| T001 | Integrate Image & Quality Rules | System | Internal | Boss AI | Done | P0 | 2024-01-15 | None | None | `docs/image-rules.md`, `prompts/image-agent.md`, `docs/quality-control.md` | 2024-01-15 | Complete. All pages now require images and browser review. |
| T002 | Implement Project Operating System | System | Internal | Boss AI | Done | P0 | 2024-01-15 | None | T001 | `docs/TRACKING.md`, `docs/STRATEGY.md`, `prompts/boss-agent.md`, `docs/EXECUTION-LOOP.md` | 2024-01-15 | Control layer, planning layer, agent layer, and integration complete. |
| T003 | Create Phase 1 Content Pages | Content | SEO | Builder Worker | Not started | P1 | 2026-06-30 | T002 | T001 | `content/pages/home.md`, `content/locations/bangkok.md`, `content/subjects/math-tutoring.md` | 2026-05-30 | Waiting for operating system to be in place. |
| T004 | Generate Phase 1 Images | Images | SEO | Image Worker | Not started | P1 | 2026-06-30 | T002, T003 | T003 | `docs/image-rules.md` | 2026-05-30 | Waiting for pages to be built. |
| T005 | Choose Website Framework | System | Internal | Boss AI | Done | P0 | 2026-05-30 | None | None | `.kimi/plans/banshee-nova-green-lantern.md` | 2026-05-30 | Decision: Next.js 15 + Vercel + single domain. See docs/DECISIONS.md. |
| T006 | Register Domain & Hosting | System | Internal | Herman | **Blocked** | P0 | 2026-06-06 | Herman not registered | T005 | — | 2026-05-30 | Framework decided. Herman to register privatetutoringthailand.com and create Vercel project. **BLOCKED — Herman still needs to act.** |
| T007 | Convert script specs to executable TypeScript | System | Dev | Dev Agent | Not started | P0 | 2026-06-13 | T006 | T005 | `scripts/*.md` | 2026-05-30 | Swarm audit found all 5 scripts are .md only, not executable. Critical blocker. |
| T008 | Build 46 missing files (P0 infrastructure) | System | Dev | Dev Agent | Not started | P0 | 2026-06-20 | T006 | T006 | `docs/6-MONTH-PLAN.md` §2 | 2026-05-30 | Missing files table from swarm audit. See 6-MONTH-PLAN.md for full list. |
| T009 | Write 10 new location hub pages | Content | SEO | Content Agent | Not started | P1 | 2026-07-15 | T006, T008 | T008 | `content/locations/*.md` | 2026-05-30 | Pattaya, Hua Hin, Koh Samui, Nonthaburi, Chonburi, Rayong, Udon Thani, Khon Kaen, Chiang Rai, Krabi. |
| T010 | Build 30+ combination pages (Bangkok/Phuket/Chiang Mai) | Content | SEO | Content Agent | Not started | P1 | 2026-08-15 | T006, T008 | T009 | `content/combinations/*.md` | 2026-05-30 | 21 Bangkok + 6 Phuket + 6 Chiang Mai combos. See SEO-PLAN.md matrix. |
| T011 | Build SEN-specific pages (ADHD, dyslexia, autism, EAL) | Content | SEO | Content Agent | Not started | P1 | 2026-08-15 | T006, T008 | T009 | `content/subjects/*-support.md` | 2026-05-30 | Blue ocean strategy — virtually no competition. |
| T012 | Verify keyword volumes via GSC/Keyword Planner | SEO | Research | SEO Agent | Not started | P0 | 2026-07-15 | T006 | T006 | `data/keywords.json` | 2026-05-30 | All 163 keyword volumes are estimates. Must verify top 50 once live. |
| T013 | Audit 12 competitors' backlink profiles | SEO | Research | SEO Agent | Not started | P1 | 2026-07-15 | None | None | `data/competitors.json` | 2026-05-30 | Swarm audit identified 12 competitors. Need backlink opportunity list. |
| T014 | Set up Google Business Profile (13 service areas) | SEO | Local | SEO Agent | Not started | P1 | 2026-07-15 | T006 | T006 | — | 2026-05-30 | Service-area business. No fake address. |
| T015 | Delete duplicate github/ folder | System | Dev | Dev Agent | Done | P2 | 2026-06-06 | None | None | `github/copilot-instructions.md` | 2026-05-30 | Deleted. Single source of truth: .github/copilot-instructions.md |
| T016 | Integrate archived audit info into live system | System | Dev | Boss AI | Done | P0 | 2026-05-30 | None | None | `docs/technical-seo.md`, `docs/hermes-control.md`, `docs/execution-handoff.md` | 2026-05-30 | All audit findings now distributed into operational docs. Archive contains only redundant raw material. |
| T017 | Build GSC handler (Hermes) | System | Dev | David | Not started | P1 | 2026-07-15 | T006 | T009 | `docs/hermes-control.md` §1.1, §3.2 | 2026-05-30 | Read-only GSC analytics. Blocked until site is live. |
| T018 | Build GA4 handler (Hermes) | System | Dev | David | Not started | P1 | 2026-07-15 | T006 | T009 | `docs/hermes-control.md` §1.2, §3.3 | 2026-05-30 | Read-only GA4 session/event data. Blocked until site is live. |
| T019 | Build report generators (7 types) | System | Dev | David | Not started | P1 | 2026-07-22 | T017, T018 | T017 | `docs/hermes-control.md` §2 | 2026-05-30 | Daily rank, weekly organic, weekly leads, post-deploy validation, content quality, SEO drift, index coverage. |
| T020 | Build permission broker + dashboard | System | Dev | David | Not started | P1 | 2026-07-29 | T019 | T019 | `docs/hermes-control.md` §4, §5, §6 | 2026-05-30 | 40-action permission matrix, metric cards, alert feed, action queue, one-click deploy. |

---

## Completed Tasks (Last 10)

| ID | Task | Area | Owner | Completed | Notes |
|---|---|---|---|---|---|
| T001 | Integrate Image & Quality Rules | System | Boss AI | 2024-01-15 | See `docs/CHANGELOG.md` for full details. |
| — | Swarm Audit: System Audit | Audit | Systems Analyst | 2026-05-30 | 16 issues identified: 4 Critical, 5 High, 5 Medium, 2 Low. See `archive/audit-raw/audit/01-SYSTEM-AUDIT.md` (archived). |
| — | Swarm Audit: SEO Keyword Plan | Audit | SEO Analyst | 2026-05-30 | 163 keywords identified, 10 quick wins, 8 clusters. See `archive/audit-raw/audit/02-SEO-KEYWORD-PLAN.md` (archived). |
| — | Swarm Audit: Competitor Intelligence | Audit | Research Analyst | 2026-05-30 | 12 competitors deep-profiled. See `archive/audit-raw/audit/03-COMPETITORS.md` (archived). |
| — | Swarm Audit: Market Research | Audit | Market Analyst | 2026-05-30 | 249 schools, 77,700+ students, 13 cities. See `archive/audit-raw/audit/04-MARKET.md` (archived). |
| — | Swarm Audit: 6-Month Takeover Plan | Audit | Strategy Analyst | 2026-05-30 | 3 strategic bets, 46 missing files, Day 1-7 task list. See `archive/audit-raw/audit/05-6MONTH-TAKEOVER.md` (archived). |
| — | Swarm Audit: Google SEO Rules | Audit | SEO Analyst | 2026-05-30 | Safe velocity rules, doorway page checklist, E-E-A-T guide. See `archive/audit-raw/audit/08-GOOGLE-SEO-RULES.md` (archived). |
| — | Update docs/6-MONTH-PLAN.md | Docs | Boss AI | 2026-05-30 | Major rewrite from swarm audit findings. Month 1: 8 pages max. 3 strategic bets included. |
| — | Update docs/SEO-PLAN.md | Docs | Boss AI | 2026-05-30 | Major rewrite. 163 keywords, 10 quick wins, SERP reality check, programmatic SEO matrix. |
| — | Update docs/TRACKING.md | Docs | Boss AI | 2026-05-30 | Added T007-T015. Marked T006 as Blocked. Added completed audit tasks. |

---

## Backlog

See `docs/BACKLOG.md` for the full idea backlog.

Top 10 ideas ready to schedule:

| ID | Idea | Area | Priority | Est. Effort | Target Month |
|---|---|---|---|---|---|
| B001 | Build home page | Content | P1 | Medium | Month 1 |
| B002 | Build Bangkok location page | Content | P1 | Medium | Month 1 |
| B003 | Build Phuket location page | Content | P1 | Medium | Month 1 |
| B004 | Build math tutoring subject page | Content | P1 | Medium | Month 1 |
| B005 | Build English tutoring subject page | Content | P1 | Medium | Month 1 |
| B006 | Build 5 SEN-specific pages (ADHD, dyslexia, autism, EAL, general SEN) | Content | P1 | Medium | Month 3 |
| B007 | Build school-specific pages (Bangkok Patana, NIST, ISB, Shrewsbury, BISP) | Content | P2 | Medium | Month 5 |
| B008 | Build parent guides (IB vs British, IGCSE guide, SEN support for expats) | Content | P2 | High | Month 5 |
| B009 | Build exam prep blog posts (IB, IGCSE, A-Level guides) | Content | P2 | High | Month 5 |
| B010 | Build combination pages for underserved cities (Hua Hin, Koh Samui, Pattaya, Krabi) | Content | P1 | Medium | Month 3-4 |

---

## Open Blockers

| ID | Blocker | Affects | Owner | Resolution Needed |
|---|---|---|---|---|
| B002 | No live domain or hosting | Publishing, SEO indexing, T006-T014 | Herman | Register privatetutoringthailand.com and set up Vercel project. **CRITICAL — this is the P0 hard blocker.** |
| B003 | No executable automation scripts | Content generation at scale, T007, T008 | Dev Agent | Convert all 5 .md script specs to TypeScript. ~3-4 weeks of dev work. |
| B004 | Zero combination pages exist | Long-tail SEO capture, T010 | Content Agent | Build combination template + first 3 Bangkok combos before scaling. |

---

## How to Update This File

When starting a task:
1. Add a new row with the next task ID
2. Set status to "In progress"
3. Update "Last Updated" with today's date

When a task changes:
1. Update the Status column
2. Add any new blockers or dependencies
3. Update "Last Updated"

When a task finishes:
1. Set status to "Done"
2. Move the row to "Completed Tasks"
3. Update "Last Updated"

When a new blocker appears:
1. Add it to "Open Blockers"
2. Link it to the affected tasks
3. Assign an owner

When a blocker is resolved:
1. Move it to "Resolved Blockers" at the bottom
2. Update affected tasks to remove the blocker

---

## Resolved Blockers

| ID | Blocker | Affected Tasks | Resolved | How |
|---|---|---|---|---|
| B001 | Website framework not chosen | T005, T006 | 2026-05-30 | Decision made: Next.js 15 (App Router) + Vercel + single domain. Recorded in docs/DECISIONS.md. |
