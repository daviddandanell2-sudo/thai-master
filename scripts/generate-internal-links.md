# Generate Internal Links Workflow

## Purpose

Workflow for updating internal links across the content tree.

## When to Run

- After creating new pages
- Before publishing a batch
- Monthly as maintenance
- When `data/internal-links.json` is updated

## Workflow Steps

### Step 1: Scan Content Tree
Read all files in `/content/` and identify:
- All existing pages
- Their page types
- Their current internal links
- Pages with no incoming links (orphans)
- Pages with no outgoing links (dead ends)

### Step 2: Read Linking Matrix
Read `data/internal-links.json` and verify:
- Rules are up to date
- Matrices cover all page types
- Min/max links are appropriate

### Step 3: Identify Missing Links
For each page, check against the matrix:
- Does it have the minimum required links?
- Are links to the correct page types?
- Is anchor text descriptive?

### Step 4: Plan Link Insertions
For each missing link, determine:
- Source page
- Target page
- Anchor text (following patterns in the matrix)
- Position in content (natural placement)

### Step 5: Insert Links
Add links to content:
- Within paragraph text where natural
- In "Related" sections at the bottom
- Ensure flow is not disrupted

### Step 6: Validate
Check all links:
- No broken links
- Anchor text is descriptive
- No forbidden anchor text ("click here", etc.)
- No more than maximum links per page

### Step 7: Report
Document changes:

```markdown
# Internal Link Update Report

## Date
{YYYY-MM-DD}

## Pages Updated
{Number}

## Links Added
{Number}

## Links Removed
{Number}

## Orphans Resolved
- {Page} — now linked from {source}

## Dead Ends Resolved
- {Page} — now links to {target}

## Anchor Text Issues Fixed
- {Page} — changed "click here" to "{descriptive text}"
```

## Maintenance Schedule

- **Weekly:** Check for orphans after new page creation
- **Monthly:** Full link audit
- **Quarterly:** Review and update linking matrix
