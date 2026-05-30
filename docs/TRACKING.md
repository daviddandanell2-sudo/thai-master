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
| T002 | Implement Project Operating System | System | Internal | Boss AI | In progress | P0 | 2024-01-15 | None | T001 | `docs/TRACKING.md`, `docs/STRATEGY.md`, `prompts/boss-agent.md`, `docs/EXECUTION-LOOP.md` | 2024-01-15 | Creating control layer, planning layer, agent layer. |
| T003 | Create Phase 1 Content Pages | Content | SEO | Builder Worker | Not started | P1 | 2024-01-30 | T002 | T001 | `content/pages/home.md`, `content/locations/bangkok.md`, `content/subjects/math-tutoring.md` | 2024-01-15 | Waiting for operating system to be in place. |
| T004 | Generate Phase 1 Images | Images | SEO | Image Worker | Not started | P1 | 2024-01-30 | T002, T003 | T003 | `docs/image-rules.md` | 2024-01-15 | Waiting for pages to be built. |
| T005 | Choose Website Framework | System | Internal | Boss AI | Done | P0 | 2026-05-30 | None | None | `.kimi/plans/banshee-nova-green-lantern.md` | 2026-05-30 | Decision: Next.js 15 + Vercel + single domain. See docs/DECISIONS.md. |
| T006 | Register Domain & Hosting | System | Internal | Herman | Waiting for input | P0 | 2026-06-06 | None | T005 | — | 2026-05-30 | Framework decided. Herman to register privattutoringthailand.com and create Vercel project. |

---

## Completed Tasks (Last 10)

| ID | Task | Area | Owner | Completed | Notes |
|---|---|---|---|---|---|
| T001 | Integrate Image & Quality Rules | System | Boss AI | 2024-01-15 | See `docs/CHANGELOG.md` for full details. |

---

## Backlog

See `docs/BACKLOG.md` for the full idea backlog.

Top 5 ideas ready to schedule:

| ID | Idea | Area | Priority | Est. Effort | Target Month |
|---|---|---|---|---|---|
| B001 | Build home page | Content | P1 | Medium | Month 1 |
| B002 | Build Bangkok location page | Content | P1 | Medium | Month 1 |
| B003 | Build Phuket location page | Content | P1 | Medium | Month 1 |
| B004 | Build math tutoring subject page | Content | P1 | Medium | Month 1 |
| B005 | Build English tutoring subject page | Content | P1 | Medium | Month 1 |

---

## Open Blockers

| ID | Blocker | Affects | Owner | Resolution Needed |
|---|---|---|---|---|
| B001 | ~~Website framework not chosen~~ | T005, T006, deployment | Boss AI | **RESOLVED** — Next.js 15 chosen |
| B002 | No live domain or hosting | Publishing, SEO indexing | Herman | Register privattutoringthailand.com and set up Vercel project |

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
