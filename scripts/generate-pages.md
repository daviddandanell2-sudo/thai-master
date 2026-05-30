# Generate Pages Workflow

## Purpose

End-to-end workflow for generating new pages from data, templates, and prompts.

This workflow follows `docs/EXECUTION-LOOP.md`.

## Prerequisites

Before generating pages, ensure:
- `docs/EXECUTION-LOOP.md` has been read
- `docs/TRACKING.md` has been checked
- `docs/STRATEGY.md` has been reviewed
- `docs/` files are complete and up to date
- `data/` files are populated
- Templates are finalized
- Prompts are tested

## Workflow Steps

### Step 1: Plan the Batch
1. Determine which pages to create and why
2. Check `data/page-types.json` for the correct page type
3. Verify primary keywords are assigned in `data/keywords.json`
4. Confirm no keyword cannibalization
5. Document the batch plan

### Step 2: Read Source Files
For each page, read:
- The appropriate template from `/templates/`
- Relevant data from `/data/`
- Brand voice from `docs/brand-voice.md`
- Content rules from `docs/content-rules.md`

### Step 3: Generate Content
Follow the `prompts/content-agent.md` instructions:
1. Read the template
2. Gather data
3. Plan the content
4. Write section by section
5. Apply brand voice
6. Add conversion elements
7. Self-check

### Step 4: Add Images
Follow `prompts/image-agent.md` and `docs/image-rules.md`:
1. Identify image needs for the page
2. Write BFL.ai prompts using the image rules (Thai tutor, European child, one child, private setting)
3. Generate images
4. Verify every image:
   - [ ] Is the tutor Thai?
   - [ ] Is the child European and alone?
   - [ ] Is there one child only?
   - [ ] Is the setting private (apartment/villa)?
   - [ ] Is there no classroom or school background?
5. If any check fails, fix the prompt and regenerate
6. Create image brief document with alt text and filenames

### Step 5: Add Meta Data
Using `templates/meta-template.md`:
1. Generate SEO title (max 60 chars)
2. Generate meta description (120-160 chars)
3. Verify H1 rules
4. Confirm URL slug

### Step 6: Add Internal Links
Using `prompts/internal-linking-agent.md`:
1. Identify related pages
2. Insert contextual links
3. Validate anchor text

### Step 7: Run QA
Using `prompts/qa-agent.md`:
1. Run automated checks
2. Run manual checks
3. Verify images against `docs/image-rules.md`
4. Score the page
5. Fix issues or flag for revision

### Step 8: MCP Browser Review
Using `docs/quality-control.md`:
1. Open the page in a browser using MCP
2. Look at it — Does it look good? Are the images correct?
3. Test mobile — Does it work well on phone screens?
4. Write a browser review report
5. Fix any issues found
6. Run the browser check one more time

### Step 9: Stage for Review
1. Save the page to `/content/` in the correct subdirectory
2. Save image briefs to `/reports/` or page folder
3. Run `git status` to confirm changes
4. Document what was created

## Batch Size Limits

- Phase 1: Max 15 pages
- Phase 2: Max 50 pages
- Phase 3+: Max 50 pages per batch
- If QA failure rate exceeds 20%, stop and fix the system

## Directory Structure

Save pages to the correct folder:
- Home, about, contact → `/content/pages/`
- Location pages → `/content/locations/`
- Subject pages → `/content/subjects/`
- Curriculum pages → `/content/curriculum/`
- Blog articles → `/content/blog/`

## Quality Gate

No page is considered complete until:
- [ ] QA score is 7 or higher
- [ ] All automated checks pass
- [ ] No fake claims
- [ ] Word count met
- [ ] Internal links present
- [ ] CTA included
