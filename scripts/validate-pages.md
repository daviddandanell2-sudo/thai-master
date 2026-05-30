# Validate Pages Workflow

## Purpose

Validation workflow for running SEO and quality checks on pages before publishing.

## When to Run

- Before publishing any new page
- Before publishing any batch of pages
- Weekly on existing pages
- Before any major site update

## Validation Steps

### Step 1: Technical Checks
For each page, verify:
- [ ] File exists and is readable
- [ ] Frontmatter is complete (title, meta_description, slug)
- [ ] URL slug follows conventions
- [ ] No broken internal links
- [ ] No broken external links
- [ ] Images have alt text
- [ ] File size is reasonable

### Step 2: Content Checks
For each page, verify:
- [ ] Word count meets minimum (800+ service, 1200+ blog)
- [ ] H1 is present and includes primary keyword
- [ ] Meta description is 120-160 characters
- [ ] 5-7 FAQ items
- [ ] At least 3 internal links
- [ ] CTA is present
- [ ] No placeholder text ("Lorem ipsum", "TODO", etc.)

### Step 3: SEO Checks
For each page, verify:
- [ ] Primary keyword is unique (no cannibalization)
- [ ] Title is under 60 characters
- [ ] Meta description includes keyword
- [ ] URL is SEO-friendly
- [ ] Internal links use descriptive anchor text
- [ ] No duplicate content with other pages

### Step 4: Brand Voice Checks
For each page, verify:
- [ ] Tone matches brand voice (clear, professional, parent-friendly)
- [ ] No jargon or buzzwords
- [ ] No fake superlatives
- [ ] Active voice used
- [ ] Sentences are concise

### Step 5: Conversion Checks
For each page, verify:
- [ ] CTA is above the fold
- [ ] CTA is mid-page
- [ ] CTA is at bottom
- [ ] WhatsApp or contact method is clear
- [ ] CTA is specific to page topic

### Step 6: Fact Checks
For each page, verify:
- [ ] No fake testimonials
- [ ] No fake statistics
- [ ] No fake credentials
- [ ] School names are real
- [ ] Location details are accurate

## Validation Output

Create a validation report:

```markdown
# Validation Report

## Pages Checked
{Number}

## Passed
{Number}

## Failed
{Number}

## Issues
| Page | Issue | Severity | Fix Required |
|---|---|---|---|
| {page} | {issue} | High/Medium/Low | {fix} |

## Action Required
- {Specific action}
```

## Severity Levels

- **High:** Page cannot publish (fake claims, missing CTA, under word count)
- **Medium:** Should fix before publish (weak title, thin FAQ, poor anchor text)
- **Low:** Nice to have (additional internal link, image optimization)

## Pass Criteria

A page passes validation when:
- All High severity issues are resolved
- 90% of Medium severity issues are resolved
- No more than 2 Low severity issues remain
