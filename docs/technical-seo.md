# Technical SEO Rules

**Source:** Swarm audit `08-GOOGLE-SEO-RULES.md` — all technical SEO non-negotiables, structured data, Core Web Vitals, robots.txt, sitemap, GBP, and penalty triggers.

---

## 1. Safe Content Velocity for a New Domain

### 1.1 The Core Risk

Google's March 2024 spam policy update introduced "scaled content abuse" — targeting sites that generate many pages primarily to manipulate search rankings. Danny Sullivan (Google Search Liaison): "we don't really care how you're doing this scaled content, whether it's AI, automation, or human beings. It's going to be an issue."

### 1.2 What Separates Natural Growth from Bulk Content Generation

| Natural Growth Signal | Bulk Generation Signal |
|---|---|
| 2-4 pages/week initially | 10+ pages in a single day |
| Content depth varies by page | Every page is exactly 800 words |
| Internal links grow organically | Identical internal link blocks on every page |
| Images unique per page | Same hero image with different alt text |
| Publish dates spread across weeks | All pages show same publish date |
| URLs submitted gradually | 90 URLs submitted to sitemap simultaneously |

### 1.3 Recommended Ramp Schedule (Months 1-6)

| Month | Safe Page Count | Max per Week | Notes |
|-------|-----------------|--------------|-------|
| 1 | 4-8 | 4 | Establish crawl frequency trust |
| 2 | 6-10 | 5 | Begin combination pages slowly |
| 3 | 8-14 | 5 | Accelerate if no GSC issues |
| 4 | 12-18 | 6 | Full combination page pipeline |
| 5 | 16-24 | 8 | Blog + guide expansion |
| 6 | 20-30 | 10 | Maintenance + optimization mode |

### 1.4 Critical Velocity Rules

1. **First 30 days: max 8 pages** — New domains are under heightened scrutiny
2. **48-hour minimum gap** between combination page publishes
3. **Depth before breadth** — Reach 25-30 high-quality pages in primary topic area before expanding
4. **Never batch-submit sitemaps** — Add URLs to sitemap as they go live, not all at once
5. **Stagger by page type** — Don't publish all location pages same week; mix subjects, curricula, blog

---

## 2. Combination Page Rules — Safe vs Penalised

### 2.1 The Doorway Page Risk

Google's doorway page policy explicitly targets pages created primarily to rank for specific search queries with little unique value. Combination pages (`/thailand/bangkok/math-tutor/`) are at high risk if done poorly.

### 2.2 Safe Combination Page Checklist

Every combination page MUST pass all 10 checks:

| # | Check | Rule | Pass Criteria |
|---|-------|------|---------------|
| 1 | Content uniqueness | >=60% unique vs other combination pages | Copyscape or manual comparison shows 60%+ unique |
| 2 | Word count | Minimum 800 words | 800+ words |
| 3 | Local context | 3+ specific local references | Mentions 3+ local entities (schools, landmarks, curriculum) |
| 4 | Title tag | Unique, descriptive, <60 characters | Title <60 chars, includes city+subject, unique |
| 5 | Meta description | Unique, compelling, <160 characters | Description <160 chars, unique, includes CTA |
| 6 | H1 tag | One per page, includes city + subject | Exactly 1 H1, descriptive, unique |
| 7 | Canonical URL | Self-referencing, absolute URL | Canonical matches page URL exactly |
| 8 | Structured data | Valid JSON-LD, correct type for page | Passes Rich Results Test with 0 errors |
| 9 | Internal links | 3+ contextual internal links | 3+ relevant internal links in body content |
| 10 | Anchor text diversity | No exact-match keyword >30% of links | Anchor text varies naturally |

### 2.3 Content Uniqueness Requirements Per Page

| Page Type | Minimum Unique Content | How to Achieve |
|-----------|----------------------|----------------|
| Location hub (`/locations/bangkok/`) | 100% | Unique local schools, neighborhoods, expat context |
| Subject page (`/subjects/math-tutoring/`) | 100% | Subject-specific methodology, curriculum alignment |
| Combination (`/thailand/bangkok/math-tutor/`) | 60%+ | City-specific tutoring approach + local school references + neighborhood context |
| Curriculum page (`/curriculum/ib-tutoring/`) | 100% | Curriculum-specific exam structure, subject coverage |
| Blog article | 100% | Original research, specific examples, unique angle |

### 2.4 What Makes a Combination Page "Helpful" vs "Doorway"

**Helpful (Safe):**
- Explains why THIS subject matters in THIS city specifically
- References actual schools in that city that teach the curriculum
- Mentions neighborhood-specific tutoring logistics
- Includes city-specific parent FAQs
- Links to relevant local resources

**Doorway (Penalty Risk):**
- Generic tutoring description with city name swapped
- Same FAQ on every combination page
- No local school references
- Identical structure, only city/subject changed
- Created primarily to capture search traffic with no user value

---

## 3. E-E-A-T for a New Tutoring Site

### 3.1 Understanding E-E-A-T for Education

Google evaluates: **Experience, Expertise, Authoritativeness, Trustworthiness**

For tutoring sites, E-E-A-T means:
- **Experience:** Tutors have real classroom or tutoring experience
- **Expertise:** Curriculum knowledge, subject mastery, SEN training
- **Authoritativeness:** References from schools, parent testimonials, curriculum alignment
- **Trustworthiness:** Transparent pricing, clear process, real contact info, privacy policy

### 3.2 What You CANNOT Fabricate (Hard Rules)

| Element | Why It Matters | Safe Alternative |
|---------|---------------|------------------|
| Tutor credentials | Fake credentials = fraud liability | List qualifications as "background-checked tutors with experience in [curriculum]" |
| Years in business | Cannot claim 10 years if new | Be honest: "Founded 2026, serving families across Thailand" |
| School partnerships | False claims = trademark infringement | "We tutor students attending [School Name]" (factual, not partnership) |
| Success rates / grade guarantees | Impossible to verify, FTC violation | "We match tutors carefully and adjust if the fit isn't right" |
| Testimonials | Fake reviews = manual action | Collect real testimonials from first 5 clients before adding Review schema |

### 3.3 What You CAN Do in Months 1-3 to Build E-E-A-T

| Month | Action | E-E-A-T Signal |
|-------|--------|----------------|
| 1 | Detailed About page with real team background | Trustworthiness |
| 1 | Curriculum-specific content depth | Expertise |
| 1 | Local school references (public information) | Authoritativeness |
| 2 | First real parent testimonials | Trustworthiness |
| 2 | SEN-specific content with qualified tutor credentials | Expertise |
| 2 | Blog articles answering real parent questions | Experience + Expertise |
| 3 | Google Business Profile with service areas | Local authority |
| 3 | Structured data on all pages | Technical trust signal |

### 3.4 About Page — Required Elements from Day One

The About page is the #1 E-E-A-T signal for a new site. It MUST include:

1. **Who runs the service** — Real names or real business entity
2. **Why tutoring in Thailand** — Personal or professional connection to the market
3. **Curriculum expertise** — Specific curricula supported, not generic "all subjects"
4. **Tutor vetting process** — How tutors are selected, checked, matched
5. **Physical presence** — Which cities are covered, how tutoring is delivered
6. **Contact information** — Real email, phone, WhatsApp (not just a form)
7. **Privacy policy** — How parent and student data is handled

### 3.5 Schema Types That Signal E-E-A-T

| Schema | E-E-A-T Signal | Priority |
|--------|---------------|----------|
| `Organization` | Brand identity, logo, URL | P0 |
| `LocalBusiness` (ProfessionalService) | Physical/service-area presence | P0 |
| `Service` | Specific offerings, area served | P1 |
| `Person` (tutors) | Real expertise credentials | P2 (when tutor profiles available) |
| `Review` | Social proof (only real reviews) | P2 |
| `FAQPage` | Transparent, helpful content | P1 |

---

## 4. Structured Data Implementation Order

### 4.1 Implementation Priority

Implement structured data in this exact order. Validate each type with Google's Rich Results Test before moving to the next.

#### Phase 1: Foundation (Week 1)

| Priority | Schema Type | Pages | Enables | Required Properties |
|----------|-------------|-------|---------|-------------------|
| 1 | `Organization` | Homepage | Knowledge Panel eligibility, brand identity | `name`, `url`, `logo` |
| 2 | `WebSite` + `SearchAction` | Homepage | Sitelinks search box | `url`, `potentialAction.query-input` |
| 3 | `LocalBusiness` (subtype: `ProfessionalService`) | Homepage | Local rich results, Knowledge Panel | `name`, `address` (as PostalAddress) |

#### Phase 2: Navigation (Week 1-2)

| Priority | Schema Type | Pages | Enables | Notes |
|----------|-------------|-------|---------|-------|
| 4 | `BreadcrumbList` | All non-homepage pages | Breadcrumb navigation in SERPs | Must match URL hierarchy |

#### Phase 3: Service Pages (Week 2-3)

| Priority | Schema Type | Pages | Enables | Required Properties |
|----------|-------------|-------|---------|-------------------|
| 5 | `Service` | All service/combination pages | Service understanding | `name`, `provider` (Organization), `areaServed` |
| 6 | `FAQPage` | Service pages with 3+ FAQs | FAQ rich results (if eligible) | Must have actual FAQ content visible on page |

#### Phase 4: Content (Week 3-4)

| Priority | Schema Type | Pages | Enables | Notes |
|----------|-------------|-------|---------|-------|
| 7 | `Article` or `BlogPosting` | All blog posts | Article rich results | Author, publish date required |
| 8 | `Person` | About page, blog author pages | Author entity | Credentials, photo, bio |

#### Phase 5: Future (When Tutor Profiles Launch)

| Priority | Schema Type | Pages | Enables | Notes |
|----------|-------------|-------|---------|-------|
| 9 | `Person` + `hasOccupation` | Individual tutor pages | Tutor entity in search | Only when real tutors available |

### 4.2 Critical Structured Data Rules

1. **Never add schema for content not visible on the page.** Hidden schema is a manual action risk.
2. **Always use JSON-LD format.** Google recommends JSON-LD where possible.
3. **Validate every page** with Google's Rich Results Test before publishing.
4. **Match schema to page type exactly.** Wrong schema type = misleading structured data.
5. **Only use `FAQPage` if FAQs are genuinely on the page.** Adding empty FAQ schema is spam.
6. **Keep `aggregateRating` honest.** Self-generated ratings trigger manual actions.
7. **Use most specific `LocalBusiness` subtype.** `ProfessionalService` > generic `LocalBusiness` for tutoring.
8. **Include `areaServed` on Service schema.** Critical for service-area business model.
9. **All URLs in schema must be canonical URLs.** No parameters, no tracking codes.
10. **Monitor Search Console Enhancement reports** weekly after implementation.

### 4.3 Mistakes That Trigger Removal or Manual Action

| Mistake | Consequence |
|---------|-------------|
| Fake reviews in `aggregateRating` | Manual action for misleading structured data |
| `FAQPage` schema without visible FAQ content | Removal from rich results |
| Wrong schema type for page | Ineligibility for rich results |
| Schema data contradicts page content | Misleading structured data penalty |
| Self-referential `aggregateRating` (rating your own business) | Manual action |
| Missing required properties | No rich result eligibility |
| Multiple conflicting schema blocks | Confused signals, no rich results |
| Schema on noindex pages | Wasted effort, potential confusion |

---

## 5. Technical Non-Negotiables for Next.js 15 + Vercel

### 5.1 Core Web Vitals Thresholds

Google measures Core Web Vitals at the 75th percentile of real user data. Failing pages receive a ranking disadvantage in the Page Experience signal.

| Metric | Good | Needs Improvement | Poor | Weight |
|--------|------|-------------------|------|--------|
| **LCP** (Largest Contentful Paint) | <= 2.5s | 2.5s - 4.0s | > 4.0s | 40% |
| **INP** (Interaction to Next Paint) | <= 200ms | 200ms - 500ms | > 500ms | 40% |
| **CLS** (Cumulative Layout Shift) | <= 0.1 | 0.1 - 0.25 | > 0.25 | 20% |

### 5.2 Next.js 15 App Router — What Delivers Out of the Box

| Feature | CWV Benefit | What You Must Configure |
|---------|-------------|------------------------|
| React Server Components | Reduces client JS (better INP) | Use Server Components by default; only add `'use client'` when interactivity required |
| `next/image` | Auto-optimizes images, prevents layout shift (LCP + CLS) | Add `priority` to above-fold images, specify `width` and `height` |
| `next/font` | Eliminates font layout shift (CLS) | Use with `display: 'swap'` |
| Static Generation (SSG) | Zero TTFB from CDN edge (LCP) | Use `generateStaticParams` for combination pages |
| Streaming SSR | Faster first paint (LCP) | Use `loading.js` for suspense boundaries |
| Code Splitting | Smaller bundles (INP) | Use dynamic imports for below-fold components |

### 5.3 Critical Next.js Config for This Site

```javascript
// next.config.js - essential configurations
const nextConfig = {
  images: {
    formats: ['image/webp', 'image/avif'],
    deviceSizes: [640, 750, 828, 1080, 1200],
    imageSizes: [16, 32, 48, 64, 96, 128, 256],
  },
  // Static generation for combination pages
  output: 'export', // or use ISR with generateStaticParams
};
```

```javascript
// For combination pages - use generateStaticParams
export async function generateStaticParams() {
  const cities = ['bangkok', 'phuket', 'chiang-mai', 'krabi'];
  const subjects = ['math', 'science', 'ib', 'a-level', 'igcse'];
  
  const params = [];
  for (const city of cities) {
    for (const subject of subjects) {
      params.push({ city, subject });
    }
  }
  return params;
}
```

### 5.4 Image Optimization Checklist

| Requirement | Implementation | Why |
|-------------|---------------|-----|
| Use `next/image` for all images | Replace all `<img>` tags | Auto WebP/AVIF, responsive sizing |
| Add `priority` to LCP images | Hero images, above-fold | Preloads critical images |
| Specify `width` and `height` | All images | Prevents layout shift (CLS) |
| Use `sizes` prop | Responsive images | Downloads correct image size |
| Lazy load below-fold images | `loading="lazy"` default | Reduces initial load |
| Do NOT lazy load LCP image | Use `priority` instead | LCP would be delayed |
| Set `fetchpriority="high"` | Hero image | Browser prioritizes loading |
| Use `placeholder="blur"` | Optional | Visual placeholder reduces perceived load |

### 5.5 Sitemap Strategy for 90+ Pages

For a 90-page site, use a **single sitemap file** (not a sitemap index). The limit is 50,000 URLs or 50MB — a 90-page sitemap is trivial.

| Decision | Recommendation |
|----------|---------------|
| Sitemap type | Single sitemap.xml |
| Dynamic or static | Dynamic (generated at build) |
| Location | `/sitemap.xml` at root |
| What to include | Only canonical, indexable pages |
| What to exclude | Drafts, utility pages, filtered variants |
| lastmod | Include accurate dates |
| priority | Optional (Google ignores it) |

**Next.js implementation:** Use `next-sitemap` package or generate in `app/sitemap.ts`.

```typescript
// app/sitemap.ts
import { MetadataRoute } from 'next';

export default function sitemap(): MetadataRoute.Sitemap {
  const cities = ['bangkok', 'phuket', 'chiang-mai', 'krabi', 'hua-hin'];
  const subjects = ['math', 'science', 'english', 'ib', 'a-level', 'igcse'];
  
  const combinationUrls = [];
  for (const city of cities) {
    for (const subject of subjects) {
      combinationUrls.push({
        url: `https://privatetutoringthailand.com/thailand/${city}/${subject}-tutor/`,
        lastModified: new Date(),
        changeFrequency: 'monthly' as const,
        priority: 0.7,
      });
    }
  }
  
  return [
    { url: 'https://privatetutoringthailand.com/', lastModified: new Date(), priority: 1.0 },
    { url: 'https://privatetutoringthailand.com/about/', lastModified: new Date(), priority: 0.8 },
    ...combinationUrls,
  ];
}
```

### 5.6 robots.txt Rules

```
# robots.txt for privatetutoringthailand.com
User-agent: *
Allow: /

# Disallow utility/admin paths
Disallow: /api/
Disallow: /_next/static/chunks/webpack-

# Prevent crawl of filtered/sorted variants
Disallow: /*?

# Sitemap reference
Sitemap: https://privatetutoringthailand.com/sitemap.xml
```

| Rule | Purpose |
|------|---------|
| `Disallow: /api/` | Internal API endpoints not for indexing |
| `Disallow: /*?` | URL parameters create duplicate content |
| `Disallow: /_next/` | Next.js build files (optional — Google usually ignores) |
| `Sitemap:` | Tells crawlers where to find sitemap |

**Critical rules:**
- Do NOT block CSS or JavaScript files — Google needs these to render pages
- Do NOT use robots.txt for canonicalization (use `rel=canonical` instead)
- Do NOT put `noindex` in robots.txt (unsupported since 2019)
- Keep robots.txt aligned with sitemap (don't sitemap pages that are disallowed)

### 5.7 Canonical URL Handling

Every combination page MUST have a self-referencing canonical tag. This is the #1 cause of programmatic SEO indexing failures.

| Page Type | Canonical Rule |
|-----------|---------------|
| `/thailand/bangkok/math-tutor/` | Self-referencing: `https://privatetutoringthailand.com/thailand/bangkok/math-tutor/` |
| Homepage | `https://privatetutoringthailand.com/` (trailing slash consistent) |
| With URL parameters | Canonical must point to parameterless version |
| With or without `www` | Choose one, redirect the other |
| HTTP vs HTTPS | Always canonical to HTTPS |

**Verification:** After publishing first 5 pages, use Google Search Console URL Inspection tool to check the "Google-selected canonical" field. It must match the page's URL exactly.

### 5.8 Mobile-First Indexing Checklist

Google switched to mobile-first indexing for all sites. Your mobile version IS what Google indexes.

| # | Check | Pass Criteria |
|---|-------|---------------|
| 1 | Responsive design | Same HTML/CSS adapts to screen size |
| 2 | Content parity | Mobile has ALL content from desktop (same text, images, structured data) |
| 3 | robots.txt doesn't block mobile resources | CSS, JS, images accessible to Googlebot |
| 4 | Structured data on mobile | Same schema on mobile and desktop |
| 5 | Image alt text matches | Same alt text on both versions |
| 6 | Internal links present | Mobile has same internal links as desktop |
| 7 | Meta robots match | No `noindex` on mobile that isn't on desktop |
| 8 | Touch targets adequate | Minimum 48x48px tap targets |
| 9 | Font readable | Minimum 16px base font on mobile |
| 10 | Viewport set | `<meta name="viewport" content="width=device-width, initial-scale=1">` |

---

## 6. Internal Linking Safety Limits

### 6.1 How Many Internal Links Per Page

| Page Type | Minimum | Maximum | Why |
|-----------|---------|---------|-----|
| Homepage | 10 | 50 | Hub page — links to all major sections |
| Location page | 5 | 15 | Links to subjects, curricula, related locations |
| Subject page | 5 | 15 | Links to locations, curricula, related subjects |
| Curriculum page | 5 | 15 | Links to locations, subjects, related curricula |
| Combination page | 3 | 10 | Links to related combos, parent location, parent subject |
| Blog article | 3 | 8 | Links to relevant service pages |

### 6.2 Anchor Text Patterns to Avoid

| Bad Pattern | Example | Risk |
|-------------|---------|------|
| Exact-match keyword >30% | Every link says "math tutor Bangkok" | Penguin-like suppression |
| Generic anchors | "click here", "read more", "learn more" | Wasted link equity |
| Keyword-stuffed anchors | "best private math tutor Bangkok Thailand IGCSE" | Over-optimization |
| Same anchor, different targets | Two links both say "tutoring" to different pages | Confused signals |

### 6.3 Internal Linking Structure for Combination Pages

Each combination page should link to:
- Parent location page
- Parent subject page
- 2-3 related combination pages (different subject, same city)
- 1-2 related combination pages (same subject, different city)
- 1 curriculum page (if applicable)

### 6.4 Crawl Budget on a 90-Page Site

With only 90 pages, crawl budget is NOT a concern. Focus on:
- Every page linked from at least one other page (no orphans)
- Homepage links to all major hubs
- XML sitemap submitted to GSC
- No redirect chains longer than 2 hops

---

## 7. Google Business Profile

### 7.1 Can a Service-Area Tutoring Business Register?

**Yes.** Google Business Profile explicitly supports service-area businesses with no physical storefront. Home tutoring is specifically listed as an example of businesses that don't need a physical address.

### 7.2 Step-by-Step Setup

| Step | Action | Details |
|------|--------|---------|
| 1 | Sign in to Google Business Profile | Use domain-level email (e.g., admin@privatetutoringthailand.com) |
| 2 | Enter business name | "Private Tutoring Thailand" — exact match to website |
| 3 | Choose business type | Select **"Service area business"** — "I visit customers at their location" |
| 4 | Select category | **"Tutoring service"** or **"Educational services"** |
| 5 | Define service area | Add up to 20 service areas (cities in Thailand) |
| 6 | Add contact info | Phone number + website URL |
| 7 | Enter mailing address | Required for verification but NOT shown publicly |
| 8 | Hide address | After verification, uncheck "Show business address to customers" |
| 9 | Add services | List all tutoring subjects offered |
| 10 | Verify | Phone, email, or video verification |

### 7.3 Service Area Configuration

| Rule | Recommendation |
|------|---------------|
| Maximum service areas | 20 (Google's limit) |
| Distance from mailing address | Within 2-hour drive time |
| For Thailand | Add Bangkok, Phuket, Chiang Mai, Krabi, Hua Hin, Pattaya |
| Home address | Can be used for verification but MUST be hidden |
| Virtual office | Can be used if you don't want to use home address |

### 7.4 Suspension Risks to Avoid

| Risk | Prevention |
|------|------------|
| Fake address | Use real mailing address (hidden); never use a fake address |
| Wrong business type | Choose "Service area" not "Storefront" if no walk-in location |
| Keyword stuffing in name | Use real business name, not "Best Math Tutor Bangkok Thailand" |
| Multiple listings for same business | Only ONE GBP per business |
| Virtual office misuse | Ensure you actually serve the claimed areas |
| Category mismatch | "Tutoring service" not "School" or "Consultant" |

### 7.5 Impact on Local Rankings

A Google Business Profile significantly improves local search visibility:
- Appears in Google Maps results for "tutor near me" searches
- Eligible for Local Pack (the map + 3 listings in search results)
- Service-area businesses CAN rank well — "hiding a physical location does not directly impact local rankings"
- Completeness and accuracy matter more than having a visible address

---

## 8. Hard Stop — Actions That Cause Penalties

### 8.1 Penalty Types and Triggers

| Penalty Type | What It Is | Trigger for This Site | Recovery Time |
|-------------|-----------|----------------------|---------------|
| **Manual Action** | Human reviewer applies penalty | Fake testimonials, doorway pages, link buying | 2-4 weeks after reconsideration request |
| **Scaled Content Abuse** (algorithmic) | SpamBrain detects bulk low-value content | Publishing all 90 pages at once, city-swap pages with no unique content | Months after fixing content |
| **Helpful Content System downgrade** | Site-wide algorithmic demotion | Content created for search engines not users, low E-E-A-T | Months after site-wide content improvement |
| **Core Update collapse** | Rankings drop during core update | Thin content, poor user experience, weak E-E-A-T | Recovery with next core update (months) |
| **Link-based manual action** | Unnatural links penalty | Buying backlinks, excessive link exchanges | 4-12 weeks after disavow/cleanup |

### 8.2 Hard Stop Checklist — Never Do These

| # | Action | Why | Consequence |
|---|--------|-----|-------------|
| 1 | **Launch all 90 pages at once** | Triggers scaled content abuse detection | Deindexing, months of recovery |
| 2 | **City-swap pages with only city name changed** | Classic doorway page pattern | Manual action for doorway pages |
| 3 | **Fake tutor profiles or credentials** | Deceptive content, trust violation | Manual action, legal liability |
| 4 | **Fabricated testimonials/reviews** | FTC violation + spam | Manual action, legal consequences |
| 5 | **Self-generated star ratings in schema** | Misleading structured data | Rich results removal + manual action |
| 6 | **Buying backlinks** | Link scheme violation | Manual action, link devaluation |
| 7 | **Exact-match anchor text >30% of links** | Over-optimization | Algorithmic suppression |
| 8 | **Hidden text or keyword stuffing** | SpamBrain detection | Automatic ranking suppression |
| 9 | **Cloaking (different content for Google vs users)** | Direct spam violation | Immediate deindexing |
| 10 | **Scraped or auto-generated content without human review** | Scaled content abuse | Site-wide penalty |
| 11 | **Multiple domains with same content** | Cross-domain duplicate | All sites penalized |
| 12 | **Noindex + sitemap inclusion** | Conflicting signals | Crawl budget waste, indexing confusion |
| 13 | **Schema for invisible content** | Misleading structured data | Manual action |
| 14 | **AI-generated content with no human oversight** | Scaled content abuse | Algorithmic suppression |
| 15 | **Clickbait titles not matching content** | Misleading content | High bounce rate + HCU demotion |

### 8.3 New Domain Specific Risks

| Risk Factor | Why New Domains Are Vulnerable | Mitigation |
|-------------|-------------------------------|------------|
| No established crawl frequency | Google doesn't trust the site yet | Start slow, build consistency |
| No backlink profile | Zero authority signals | Focus on content quality first |
| No historical user data | Can't demonstrate engagement | Every visitor counts — optimize UX |
| Google's "new site" scrutiny | Fresh domains watched more carefully | Perfect compliance with all guidelines |
| Quick wins temptation | Pressure to rank fast drives risky behavior | Accept 6-12 month timeline |

### 8.4 Recovery from Penalties

If penalized, the recovery process is:

1. **Identify the penalty type** — Check Search Console > Security & Manual Actions
2. **Fix ALL instances** — Site-wide fixes, not just examples Google provided
3. **Document the fixes** — Record what was changed and why
4. **Submit reconsideration request** (manual actions only) — Describe specific, irreversible fixes
5. **Wait** — Recovery takes 2-4 weeks for manual actions, 4-8 weeks for ranking restoration
6. **Monitor** — Watch Search Console for "All good" message
