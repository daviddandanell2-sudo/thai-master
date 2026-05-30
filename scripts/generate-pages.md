# Generate Pages Workflow

## Purpose

End-to-end workflow for generating new pages from data, templates, and prompts.

## Prerequisites

Before generating pages, ensure:
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

### Step 4: Add Meta Data
Using `templates/meta-template.md`:
1. Generate SEO title (max 60 chars)
2. Generate meta description (120-160 chars)
3. Verify H1 rules
4. Confirm URL slug

### Step 5: Add Internal Links
Using `prompts/internal-linking-agent.md`:
1. Identify related pages
2. Insert contextual links
3. Validate anchor text

### Step 6: Run QA
Using `prompts/qa-agent.md`:
1. Run automated checks
2. Run manual checks
3. Score the page
4. Fix issues or flag for revision

### Step 7: Stage for Review
1. Save the page to `/content/` in the correct subdirectory
2. Run `git status` to confirm changes
3. Document what was created

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
