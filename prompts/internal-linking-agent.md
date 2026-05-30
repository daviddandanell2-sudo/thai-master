# Internal Linking Agent Prompt

## Mission

Connect all pages in the content tree with contextual internal links. Ensure no orphaned pages, no dead ends, and descriptive anchor text.

## Inputs

- `data/internal-links.json` — Linking matrix and rules
- `data/locations.json` — Location pages to link
- `data/subjects.json` — Subject pages to link
- `data/curricula.json` — Curriculum pages to link
- `/content/` — All existing content pages

## Step-by-Step Workflow

### Step 1: Scan the Content Tree
Read all files in `/content/` and build a list of:
- Existing pages
- Their page types
- Their slugs
- Their primary keywords

### Step 2: Read the Linking Matrix
Read `data/internal-links.json` to understand:
- Which page types should link to which
- Minimum and maximum links per page type
- Anchor text patterns
- Forbidden anchor text

### Step 3: Identify Missing Links
For each page, check:
- Does it have at least the minimum required internal links?
- Are the links to the right page types?
- Is the anchor text descriptive?
- Are there any broken links?

### Step 4: Insert Contextual Links
Add links within the content (not just at the bottom):
- Links should flow naturally within paragraphs
- Anchor text should describe the destination
- Links should be relevant to the surrounding content

### Step 5: Validate Anchor Text
Check every link against the rules:
- Minimum 2 words, maximum 6 words
- Not in the forbidden list ("click here", "read more", etc.)
- Descriptive of the destination page

### Step 6: Check for Orphans and Dead Ends
- Every page should have at least one internal link pointing to it
- Every page should have at least 3 internal links going out
- Exception: Home page may have more outgoing links

## Output Format

### For Link Updates
Modify existing content files in `/content/` to add or update links.

### For Link Reports
Create a report showing:

```markdown
# Internal Link Report

## Pages Analyzed
{Number}

## Links Added
{Number}

## Links Removed
{Number}

## Orphaned Pages
- {Page} — no internal links pointing to it

## Dead-End Pages
- {Page} — no outgoing internal links

## Anchor Text Issues
- {Page} → "click here" (forbidden)
- {Page} → "this" (too short)
```

## Constraints
- Never use "click here" or "read more" as anchor text
- Never link to the same page twice with different anchor text
- Never force a link where it doesn't make sense contextually
- Always use descriptive anchor text
- Always respect the min/max links per page type
