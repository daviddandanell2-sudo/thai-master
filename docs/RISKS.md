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
| R003 | Duplicate thin content (city-swap pages) | High | Medium | **High** | Builder Worker | Monitoring | `docs/content-rules.md` thin content rules + uniqueness checks in QA | Combination pages must have 60%+ unique content per Google doorway-page policy |
| R004 | Keyword cannibalization between pages | Medium | Medium | **Medium** | SEO Worker | Monitoring | `data/keywords.json` as single source of truth + SEO agent audits | Review before every batch |
| R005 | Project state is lost if session crashes | Medium | Low | **Low** | Boss AI | Active | `docs/TRACKING.md` updated after every task + all docs in git | Git commits after every major step |
| R006 | AI workers work outside the system (skip tracking, skip QA) | Medium | Medium | **Medium** | Boss AI | Active | `AGENTS.md` / `CLAUDE.md` enforce execution loop | Boss AI reviews all work before handoff |
| R007 | Human is overloaded with escalations | Medium | Low | **Low** | Human | Monitoring | Clear escalation criteria (3 failures) + good worker prompts + decision log | Track escalation frequency in tracking |
| R008 | SEO strategy becomes outdated | Medium | Low | **Low** | Research Worker | Monitoring | `docs/SEO-PLAN.md` reviewed monthly + research agent market updates | 12-month plan with monthly review |
| R009 | Competitor copies content or strategy | Low | Medium | **Low** | Research Worker | Monitoring | Unique angles per page + local expertise + real school names | Cannot be fully prevented |
| R010 | BFL.ai image generation produces low-quality or incorrect images | Medium | Medium | **Medium** | Image Worker | Monitoring | Detailed prompts + verification + regeneration loop + WebP optimization | Budget for regeneration |
| R011 | No executable automation scripts — all 5 scripts are .md specs only | Critical | High | **Critical** | Dev Agent | Active | Convert .md specs to TypeScript immediately. Prioritise generate-pages.ts and generate-sitemap.ts. ~3-4 weeks dev work. | Swarm audit finding: this is the #1 execution blocker. Without scripts, 70+ pages must be created manually. |
| R012 | Domain not registered — privatetutoringthailand.com is unregistered | Critical | Medium | **Critical** | Herman | Active | Herman must register domain immediately. Contingency: David registers and bills Herman. | Swarm audit finding: P0 hard blocker. No website can go live. All SEO work invisible. |
| R013 | Zero combination pages exist — primary SEO value driver missing | High | High | **High** | Content Agent | Active | Build combination template + first 3 Bangkok combos before scaling. Must pass doorway-page checklist. | Swarm audit finding: 5-layer SEO architecture cannot capture long-tail traffic without combo pages. |
| R014 | Combination pages flagged as doorway content — Google's March 2024 update | High | Medium | **High** | SEO Agent | Monitoring | Enforce 60%+ unique content, 800+ words, 3+ local signals, 3+ internal links per page. Audit first 3 before scaling. | Google's doorway page policy explicitly targets location-swapped template pages. |
| R015 | Scaled content abuse from velocity — publishing 90 pages on new domain | High | Medium | **High** | SEO Agent | Monitoring | Max 8 pages Month 1. 4-6 pages/week in Months 1-3. 48-hour gap between combination pages. | Google's March 2024 spam policy targets "scaled content abuse" regardless of generation method. |
| R016 | Competitor TutorChase SEO dominance — ranks #1 for "best tutoring companies Thailand" | High | Low | **High** | SEO Agent | Monitoring | Differentiate on in-person presence (they're online-only). Counter every online claim with physical availability. | TutorChase has strong SEO and could retaliate with more Thailand content. |
| R017 | Competitor Tutopiya price undercutting — ~$9/hr vs premium positioning | Medium | Medium | **Medium** | Content Agent | Monitoring | Position on curriculum expertise and vetting, not price. Transparent pricing page showing value. | Tutopiya is online-only and Singapore-based. Differentiate on quality and in-person. |
| R018 | Missing SEN tutor pool — site claims SEN support but no trained tutors | Medium | Medium | **Medium** | Herman | Monitoring | Have 3-5 vetted tutors confirmed before Month 3. Partner with SEN specialists as overflow. | SEN is the blue ocean bet. Must have real tutor capacity to fulfill leads. |
| R019 | Peak relocation season missed — May-July is critical window before August school start | High | Low | **High** | Content Agent | Monitoring | Front-load Bangkok/Phuket/Chiang Mai combination pages in Month 2-3. Publish "moving to Thailand" guide by July 15. | Missing the relocation window means waiting a full year for the next surge. |
| R020 | Keyword volumes unverified — all 163 keyword volumes are estimates | Medium | High | **Medium** | SEO Agent | Monitoring | Verify top 50 keywords via GSC once live. Pivot content calendar to actual demand at Month 2. Label all as ESTIMATE. | Swarm audit finding: prioritisation may be wrong if volumes don't match reality. |
| R021 | Fake data or testimonials published | Critical | Low | **Critical** | QA Worker | Monitoring | Human review of ALL content before publish. `check-seo.ts` validates claims. No fake credentials, reviews, or statistics. | Hard stop rule #1 from `docs/technical-seo.md` §8.2. FTC violation + manual action. |
| R022 | Self-generated star ratings in schema | High | Low | **High** | SEO Agent | Monitoring | Never add `aggregateRating` without real verified reviews. Validate every page in Rich Results Test. | Hard stop rule #5 from `docs/technical-seo.md` §8.2. Rich results removal + manual action. |
| R023 | Schema for invisible content | High | Low | **High** | SEO Agent | Monitoring | All JSON-LD must describe visible page content. Never add hidden schema. | Hard stop rule #13 from `docs/technical-seo.md` §8.2. Manual action for misleading structured data. |
| R024 | robots.txt blocks CSS/JS | Medium | Low | **Medium** | Dev Agent | Monitoring | robots.txt must Allow all CSS, JS, images. Google needs these to render. See `docs/technical-seo.md` §5.6. | Blocks mobile-first indexing. Pages may not render correctly for Googlebot. |
| R025 | Missing structured data phases | Medium | Medium | **Medium** | SEO Agent | Monitoring | Follow Phase 1-5 implementation order in `docs/technical-seo.md` §4. Validate each with Rich Results Test. | Missing schema = missed rich results. Wrong schema = manual action risk. |
| R026 | INP (Interaction to Next Paint) fails | Medium | Medium | **Medium** | Dev Agent | Monitoring | INP <= 200ms target. Use React Server Components, lazy load below-fold, optimize bundles. See `docs/technical-seo.md` §5.1. | INP is 40% of Core Web Vitals weight. Poor INP = ranking disadvantage. |

## Technical Debt

| ID | Debt | Impact | Owner | Plan to Resolve |
|---|---|---|---|---|
| TD001 | No automated deployment pipeline | Medium | Deployer Worker | Build deployment script when website framework is chosen |
| TD002 | No automated sitemap generation | Low | SEO Worker | `scripts/generate-sitemap.md` exists but not automated |
| TD003 | Image generation is manual (BFL.ai) | Medium | Image Worker | Consider API integration if BFL.ai offers one |
| TD004 | No automated browser testing | Medium | QA Worker | MCP browser review is manual per page |
| TD005 | Scripts are .md specs, not executable TypeScript | Critical | Dev Agent | Convert all 5 .md script specs to TypeScript. Highest-priority engineering task. ~3-4 weeks. |

## Blockers

| ID | Blocker | Blocking What | Owner | Resolution Needed |
|---|---|---|---|---|
| B002 | No live domain or hosting | Publishing, SEO indexing | Herman | Register privatetutoringthailand.com and set up Vercel project |
| B003 | No executable automation scripts | Content generation at scale | Dev Agent | Convert all 5 .md script specs to executable TypeScript |

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
