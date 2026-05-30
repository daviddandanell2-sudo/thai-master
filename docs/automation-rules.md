# Automation Rules

## What AI Agents Can Do Autonomously

AI agents may perform these tasks without human approval:

1. **Research** — Market research, keyword discovery, competitor analysis
2. **Data Updates** — Adding new entries to JSON data files (locations, subjects, keywords)
3. **Content Drafting** — Writing page drafts using templates and rules
4. **Internal Linking** — Inserting contextual links based on the linking matrix
5. **Meta Generation** — Creating SEO titles and descriptions using formulas
6. **FAQ Generation** — Writing FAQ sections based on common parent questions
7. **Image Briefs** — Generating image briefs for page visuals
8. **QA Checks** — Running quality control checklists on drafts
9. **Analytics Review** — Reviewing performance data and flagging issues
10. **Sitemap Updates** — Updating sitemap logic when new pages are added

## What Requires Human Approval

These tasks must be reviewed by a human before execution:

1. **Publishing Content** — No page goes live without human review
2. **Creating New Page Types** — Adding a new type of page requires approval
3. **Major Structural Changes** — Changing URL structure, folder organization, or data schemas
4. **Brand Voice Changes** — Modifying brand voice docs or tone guidelines
5. **Competitor Claims** — Any statement about a competitor must be fact-checked
6. **Pricing or Policy Changes** — Any content mentioning pricing or business policies
7. **Testimonials or Case Studies** — Real parent feedback only, never invented
8. **Tutor Profiles** — Only use verified tutor information
9. **Deleting Content** — Removing pages or data requires approval
10. **Scaling Beyond 50 Pages** — Creating large batches of pages requires review

## Scaling Guardrails

### Page Creation Limits
- **Phase 1:** Max 15 pages (foundation only)
- **Phase 2:** Max 50 pages (core pages + top combinations)
- **Phase 3:** Max 150 pages (expanded combinations)
- **Phase 4+:** Review required for batches over 50 pages

### Content Velocity (from `docs/execution-handoff.md`)
- **Month 1:** Max 8 pages (hard cap for new domain)
- **Months 1-3:** Max 5-6 pages/week
- **Months 4-6:** Max 8-10 pages/week
- **Combination pages:** Mon/Wed/Fri only, 48-hour gap minimum
- **Hard stop:** If GSC shows coverage issues, drop to 2/week until resolved

## Hermes Automation Rules (from `docs/hermes-control.md`)

### Automated Reports
The following reports run automatically once Hermes is built (Month 2):
- **Daily 06:00:** Rank snapshot (GSC top 30 keywords)
- **Weekly Mon 07:00:** Organic report + Lead report
- **Weekly Wed 08:00:** Content quality scan
- **Every 4 hours:** Index coverage check
- **Post-deploy:** Deploy validation

### Permission Levels
- **Auto-approved:** All read operations, local report generation, alert creation
- **Approval required:** Deploy triggers, workflow triggers, agent runs, image generation, indexing notifications
- **Blocked:** Direct file modification, commit pushing, branch creation, env var changes, non-PTB repo access

### Quality Gates
- Every batch of pages must pass QA before the next batch is created
- If a batch has more than 20% of pages failing QA, stop and fix the system
- No page under 800 words may be published
- No page without 5 FAQ items may be published
- No page without 3 internal links may be published
- No page without images following `docs/image-rules.md` may be published
- No page without passing MCP browser review may be published

### Duplication Prevention
- Before creating a new page, check if a similar page exists
- Location pages must have unique local content, not just city name swaps
- Subject pages must explain the subject, not just list it
- Combination pages must have a unique angle, not be a merge

### Keyword Cannibalization Prevention
- No two pages may target the same primary keyword
- If overlap is detected, merge pages or differentiate keywords
- Use `data/keywords.json` as the single source of truth for keyword assignments

## Agent Workflow Rules

### Before Starting Work
1. Read `README.md`
2. Read `AGENTS.md` or `CLAUDE.md`
3. Read relevant docs in `/docs/`
4. Read relevant data in `/data/`
5. Show the plan before executing

### During Work
1. Follow templates exactly
2. Follow brand voice rules
3. Follow content rules
4. Follow image rules (`docs/image-rules.md`)
5. Use data files as source of truth
6. Do not invent facts, numbers, or testimonials

### After Work
1. Show what changed
2. Run QA checklist on new content (including image verification)
3. Run MCP browser review on pages
4. Run `git status`
5. Stage changes for human review

## Error Handling

### If an Agent Is Unsure
- Stop and ask for clarification
- Do not guess
- Do not proceed with incomplete information

### If an Agent Detects a Problem
- Flag the issue
- Do not create broken or low-quality content to meet a quota
- Report the problem and suggest a fix

### If an Agent Finds Contradictions
- Flag the contradiction
- Do not proceed until resolved
- Example: If `data/locations.json` says Phuket is inactive but a prompt requests a Phuket page, flag it

## File Change Rules

### Allowed Changes
- Create new files in `/content/`, `/data/`, `/reports/`
- Modify existing files in `/content/`, `/data/`, `/reports/`
- Add new entries to JSON arrays
- Update markdown content

### Forbidden Changes
- Delete files in `/docs/`, `/templates/`, `/prompts/`, `/scripts/` without approval
- Modify `README.md`, `AGENTS.md`, or `CLAUDE.md` without approval
- Create files outside the repository
- Modify `.gitignore` or Git configuration

## Logging and Audit

- All changes should be committed with descriptive messages
- Batch changes should be committed together
- If a mistake is made, revert and explain
- Keep a log of major decisions in commit messages
