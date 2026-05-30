# Checklist

## Purpose

Execution checklist for internal systems or operational workflows.

This project is primarily a **Type A: SEO / Sales Website**, so this checklist is used for system-level tasks and operational work.

## System Checklist

### Before Adding New Features
- [ ] Feature is tracked in `docs/TRACKING.md`
- [ ] Feature aligns with `docs/STRATEGY.md`
- [ ] Risks assessed in `docs/RISKS.md`
- [ ] Decision recorded in `docs/DECISIONS.md` (if needed)

### Before Modifying Templates
- [ ] Change is tracked in `docs/TRACKING.md`
- [ ] All affected templates are identified
- [ ] All affected prompts are updated
- [ ] QA checklist is updated if needed
- [ ] Decision recorded in `docs/DECISIONS.md`

### Before Adding New Page Types
- [ ] Page type is tracked in `docs/TRACKING.md`
- [ ] `data/page-types.json` is updated
- [ ] Template is created in `templates/`
- [ ] Prompt is created or updated in `prompts/`
- [ ] Content rules are updated in `docs/content-rules.md`
- [ ] QA checklist is updated in `docs/QA.md`
- [ ] Decision recorded in `docs/DECISIONS.md`

### Before Adding New Locations
- [ ] Location is tracked in `docs/TRACKING.md`
- [ ] `data/locations.json` is updated
- [ ] `data/keywords.json` is updated
- [ ] `data/internal-links.json` is updated
- [ ] Location page is created in `content/locations/`
- [ ] Combination pages are planned

### Before Adding New Subjects
- [ ] Subject is tracked in `docs/TRACKING.md`
- [ ] `data/subjects.json` is updated
- [ ] `data/keywords.json` is updated
- [ ] `data/internal-links.json` is updated
- [ ] Subject page is created in `content/subjects/`
- [ ] Combination pages are planned

### Before Adding New Curricula
- [ ] Curriculum is tracked in `docs/TRACKING.md`
- [ ] `data/curricula.json` is updated
- [ ] `data/keywords.json` is updated
- [ ] `data/internal-links.json` is updated
- [ ] Curriculum page is created in `content/curriculum/`

### Before Modifying Data Files
- [ ] Change is tracked in `docs/TRACKING.md`
- [ ] JSON is valid
- [ ] Related data files are updated
- [ ] No breaking changes to existing content

### Before Publishing
- [ ] All pages pass QA (score 7+)
- [ ] All images follow `docs/image-rules.md`
- [ ] All pages pass browser review
- [ ] Sitemap is updated
- [ ] robots.txt is correct
- [ ] Tracking is verified
- [ ] Human approval obtained

---

## Pre-Publish Checklist (Per Page)

Use this checklist for EVERY page before it goes live. No exceptions.

Source: `archive/audit-raw/audit/08-GOOGLE-SEO-RULES.md` Section 9 (archived)

| # | Check | Rule | Pass Criteria | Fail Action |
|---|-------|------|---------------|-------------|
| 1 | Content uniqueness | >=60% unique content vs other combination pages | Copyscape or manual comparison shows 60%+ unique | Rewrite or noindex |
| 2 | Word count | Minimum 800 words for combination pages | 800+ words | Expand content |
| 3 | Local context | 3+ specific local references (schools, landmarks, curriculum) | Mentions 3+ local entities | Add local context |
| 4 | Title tag | Unique, descriptive, <60 characters | Title <60 chars, includes city+subject, unique | Rewrite title |
| 5 | Meta description | Unique, compelling, <160 characters | Description <160 chars, unique, includes CTA | Rewrite description |
| 6 | H1 tag | One per page, includes city + subject | Exactly 1 H1, descriptive, unique | Fix heading structure |
| 7 | Canonical URL | Self-referencing, absolute URL | Canonical matches page URL exactly | Fix canonical tag |
| 8 | Structured data | Valid JSON-LD, correct type for page, passes Rich Results Test | Passes Rich Results Test with 0 errors | Fix schema errors |
| 9 | Internal links | 3+ contextual internal links | 3+ relevant internal links in body content | Add links |
| 10 | Anchor text diversity | No exact-match keyword >30% of links | Anchor text varies naturally | Rewrite anchor text |
| 11 | Image alt text | Descriptive, includes subject/city where relevant | All images have descriptive alt text | Add alt text |
| 12 | Mobile rendering | Content identical to desktop, no blocked resources | Mobile version has all content | Fix mobile display |
| 13 | Page speed | LCP < 2.5s target | Lighthouse LCP < 3.0s (immediate target) | Optimize images/code |
| 14 | No fake claims | No fabricated credentials, testimonials, or statistics | All claims verifiable | Remove or verify claims |
| 15 | Schema matches visible content | All structured data describes visible page content | No hidden schema | Remove or make visible |
| 16 | robots.txt not blocking | Page not disallowed in robots.txt | robots.txt allows crawl | Fix robots.txt or remove block |
| 17 | URL in sitemap | Canonical URL included in sitemap.xml | URL present in sitemap | Add to sitemap |
| 18 | No broken links | All internal and external links resolve | 0 broken links | Fix or remove broken links |
| 19 | Contact info present | Clear contact method on page | Email or phone visible | Add contact info |
| 20 | Publish date visible | Shows content freshness | Date visible on page | Add publish date |

---

## Operational Checklist

### Weekly
- [ ] Review `docs/TRACKING.md`
- [ ] Update task statuses
- [ ] Check for blockers
- [ ] Review `docs/RISKS.md`

### Monthly
- [ ] Review `docs/STRATEGY.md`
- [ ] Review `docs/SEO-PLAN.md`
- [ ] Update `docs/6-MONTH-PLAN.md`
- [ ] Review `docs/BACKLOG.md`
- [ ] Update `docs/CHANGELOG.md`

### Quarterly
- [ ] Full strategy review
- [ ] Competitor analysis
- [ ] Plan adjustments
- [ ] Team review
- [ ] Risk review
