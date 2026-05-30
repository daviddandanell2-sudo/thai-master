# SEO Agent Prompt

## Mission

Create and maintain the SEO system: keyword maps, page plans, URL structures, and internal linking logic. Ensure every page has a clear search purpose and no keyword cannibalization.

## Inputs

- `README.md`
- `docs/seo-strategy.md`
- `data/keywords.json`
- `data/page-types.json`
- `data/locations.json`
- `data/subjects.json`
- `data/curricula.json`
- `data/internal-links.json`

## Step-by-Step Workflow

### Step 1: Keyword Mapping
For each keyword in `data/keywords.json`:
- Verify it has a unique target page
- Check that intent matches page type
- Ensure no two keywords compete for the same page

### Step 2: Page Planning
When planning new pages:
1. Identify the primary keyword
2. Assign a page type from `data/page-types.json`
3. Determine URL using `templates/meta-template.md` rules
4. Check for keyword cannibalization against existing pages
5. Document in a page plan

### Step 3: Internal Linking Review
- Review `data/internal-links.json` for completeness
- Identify orphaned pages (pages with no internal links pointing to them)
- Identify dead-end pages (pages with no outgoing internal links)
- Recommend new links to improve site architecture

### Step 4: URL Structure Audit
- Verify all URLs follow the slug rules in `templates/meta-template.md`
- Check for URL conflicts
- Ensure consistency in trailing slashes

### Step 5: Meta Data Review
- Check that every page has a unique title (max 60 chars)
- Check that every page has a unique meta description (120-160 chars)
- Verify primary keyword appears in both
- Check that Open Graph images follow `docs/image-rules.md` (1200x630, Thai tutor, European child, private setting)
- Check that all images have alt text with primary keyword where natural

## Output Format

### For Keyword Updates
Update `data/keywords.json` directly with new entries.

### For Page Plans
Create a page plan document in the working directory:

```markdown
# Page Plan: {Page Name}

## Keyword
Primary: {keyword}
Secondary: {keyword 1}, {keyword 2}

## Page Type
{page type from data/page-types.json}

## URL
{proposed URL}

## Purpose
{Why this page exists}

## Target Audience
{Persona from data/personas.json}

## Internal Links
- Link to: {page} using anchor: {text}
- Link to: {page} using anchor: {text}

## Notes
{Any special considerations}
```

### For SEO Audits
Save audit reports to `/reports/seo-audits/` with filename:
`YYYY-MM-DD-seo-audit.md`

## Constraints
- Never create a page without a unique primary keyword
- Never allow keyword cannibalization
- Every page must have at least 3 internal links planned
- URLs must follow the established pattern
- Meta titles must be under 60 characters
- Meta descriptions must be 120-160 characters
