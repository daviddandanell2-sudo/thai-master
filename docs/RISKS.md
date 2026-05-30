# Risks

## Purpose

Every known risk, blocker, issue, and technical debt must be recorded here.

When a risk is identified:
1. Add it to this file
2. Rate it: Low / Medium / High / Critical
3. Assign an owner
4. Define the mitigation plan
5. Update status as it changes

## Risk Register

| ID | Risk | Impact | Likelihood | Rating | Owner | Status | Mitigation | Notes |
|---|---|---|---|---|---|---|---|---|
| R001 | AI generates images with wrong subjects (wrong nationality, wrong setting) | High | Medium | **High** | Image Worker | Monitoring | Strict `docs/image-rules.md` + verification checklist + regenerate on fail | All image prompts must include verification step |
| R002 | Pages are published with fake claims or fake credentials | Critical | Low | **Critical** | QA Worker | Monitoring | `docs/quality-control.md` fake claim checks + human approval for publish | No page goes live without human review |
| R003 | Duplicate thin content (city-swap pages) | High | Medium | **High** | Builder Worker | Monitoring | `docs/content-rules.md` thin content rules + uniqueness checks in QA | Combination pages must have 50%+ unique content |
| R004 | Keyword cannibalization between pages | Medium | Medium | **Medium** | SEO Worker | Monitoring | `data/keywords.json` as single source of truth + SEO agent audits | Review before every batch |
| R005 | Project state is lost if session crashes | Medium | Low | **Low** | Boss AI | Active | `docs/TRACKING.md` updated after every task + all docs in git | Git commits after every major step |
| R006 | AI workers work outside the system (skip tracking, skip QA) | Medium | Medium | **Medium** | Boss AI | Active | `AGENTS.md` / `CLAUDE.md` enforce execution loop | Boss AI reviews all work before handoff |
| R007 | Human is overloaded with escalations | Medium | Low | **Low** | Human | Monitoring | Clear escalation criteria (3 failures) + good worker prompts + decision log | Track escalation frequency in tracking |
| R008 | SEO strategy becomes outdated | Medium | Low | **Low** | Research Worker | Monitoring | `docs/SEO-PLAN.md` reviewed monthly + research agent market updates | 12-month plan with monthly review |
| R009 | Competitor copies content or strategy | Low | Medium | **Low** | Research Worker | Monitoring | Unique angles per page + local expertise + real school names | Cannot be fully prevented |
| R010 | BFL.ai image generation produces low-quality or incorrect images | Medium | Medium | **Medium** | Image Worker | Monitoring | Detailed prompts + verification + regeneration loop + WebP optimization | Budget for regeneration |

## Technical Debt

| ID | Debt | Impact | Owner | Plan to Resolve |
|---|---|---|---|---|
| TD001 | No automated deployment pipeline | Medium | Deployer Worker | Build deployment script when website framework is chosen |
| TD002 | No automated sitemap generation | Low | SEO Worker | `scripts/generate-sitemap.md` exists but not automated |
| TD003 | Image generation is manual (BFL.ai) | Medium | Image Worker | Consider API integration if BFL.ai offers one |
| TD004 | No automated browser testing | Medium | QA Worker | MCP browser review is manual per page |

## Blockers

| ID | Blocker | Blocking What | Owner | Resolution Needed |
|---|---|---|---|---|
| B002 | No live domain or hosting | Publishing, SEO indexing | Herman | Register privattutoringthailand.com and set up Vercel project |

## How to Update This File

When a risk changes:
1. Update the Status column
2. Add a note with the date
3. If resolved, move to the bottom under "Resolved Risks"

## Resolved Blockers

| ID | Blocker | Blocking What | Owner | Resolved | How |
|---|---|---|---|---|---|
| B001 | Website framework not chosen | Deployment, hosting, automated builds | Boss AI | 2026-05-30 | Decision made: Next.js 15 (App Router) + Vercel + single domain. See docs/DECISIONS.md for full rationale. |

---

## Resolved Risks

| ID | Risk | Resolved | How |
|---|---|---|---|
| — | — | — | — |

---

When a new risk is found:
1. Add a new row with the next ID
2. Rate it immediately
3. Assign an owner
4. Define mitigation
