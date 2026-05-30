# Check SEO Workflow

## Purpose

Workflow for technical and on-page SEO checks.

## When to Run

- Before publishing any batch
- Weekly on the live site
- After any structural changes
- Before and after major content updates

## Technical SEO Checks

### Crawlability
- [ ] robots.txt allows search engines to crawl important pages
- [ ] No noindex tags on pages that should be indexed
- [ ] XML sitemap is submitted to Google Search Console
- [ ] No crawl errors in Search Console

### URL Structure
- [ ] All URLs are lowercase
- [ ] All URLs use hyphens, not underscores
- [ ] No URL parameters on important pages
- [ ] Canonical URLs are set correctly
- [ ] No duplicate URLs with and without trailing slashes

### Mobile
- [ ] Pages are mobile-friendly
- [ ] Text is readable without zooming
- [ ] Tap targets are appropriately sized
- [ ] No horizontal scrolling

### Speed
- [ ] Pages load in under 3 seconds
- [ ] Images are optimized
- [ ] No render-blocking resources
- [ ] Core Web Vitals are acceptable

### Security
- [ ] Site uses HTTPS
- [ ] No mixed content (HTTP resources on HTTPS pages)

## On-Page SEO Checks

### For Each Page
- [ ] Title tag is under 60 characters
- [ ] Meta description is 120-160 characters
- [ ] H1 is present and includes primary keyword
- [ ] Only one H1 per page
- [ ] H2 and H3 tags are used logically
- [ ] Primary keyword appears in first 100 words
- [ ] Images have alt text
- [ ] Images follow `docs/image-rules.md` (Thai tutor, European child, one child, private setting)
- [ ] Internal links use descriptive anchor text
- [ ] No broken links

### Structured Data
- [ ] FAQ schema is present on pages with FAQ sections
- [ ] LocalBusiness schema is on location pages
- [ ] Article schema is on blog posts
- [ ] Schema validates without errors

## Content SEO Checks

### Keyword Usage
- [ ] Primary keyword is in H1
- [ ] Primary keyword is in title
- [ ] Primary keyword is in meta description
- [ ] Primary keyword appears 2-3 times in body
- [ ] No keyword stuffing

### Uniqueness
- [ ] No duplicate content across pages
- [ ] No duplicate meta descriptions
- [ ] No duplicate titles

### Freshness
- [ ] Blog content is updated regularly
- [ ] Outdated content is updated or removed
- [ ] Last modified dates are accurate

## SEO Audit Output

Create an SEO audit report:

```markdown
# SEO Audit Report

## Date
{YYYY-MM-DD}

## Technical SEO
| Check | Status | Notes |
|---|---|---|
| robots.txt | Pass/Fail | {notes} |
| Sitemap | Pass/Fail | {notes} |
| Mobile-friendly | Pass/Fail | {notes} |
| HTTPS | Pass/Fail | {notes} |
| Page speed | Pass/Fail | {notes} |

## On-Page SEO
| Page | Title | Meta | H1 | Alt Text | Links |
|---|---|---|---|---|---|
| {page} | Pass/Fail | Pass/Fail | Pass/Fail | Pass/Fail | Pass/Fail |

## Issues Found
1. {Issue} — {Severity} — {Fix}

## Recommendations
1. {Recommendation}
```

## Severity Levels

- **Critical:** Page cannot be indexed or has major issues
- **High:** Significant impact on rankings or user experience
- **Medium:** Should be fixed for optimal performance
- **Low:** Minor improvements

## Tools

- Google Search Console
- Google PageSpeed Insights
- Mobile-Friendly Test
- Schema Validator
- Manual review
