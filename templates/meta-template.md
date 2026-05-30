# Meta Template

## SEO Title Formula

### Formula
`{Primary Keyword} | {Brand Name}`

or

`{Primary Keyword} in {Location} | {Brand Name}`

or

`{Service} for {Curriculum} | {Brand Name}`

### Rules
- Maximum 60 characters (including spaces and brand)
- Primary keyword at the beginning
- Brand name at the end
- No fluff words (best, top, #1)
- Every page must have a unique title

### Examples
| Page Type | Title | Char Count |
|---|---|---|
| Home | Private Tutoring Thailand | 26 |
| Location | Private Tutoring in Bangkok | 28 |
| Subject | Math Tutoring in Thailand | 27 |
| Curriculum | IB Tutoring in Thailand | 24 |
| Location+Subject | Math Tutor in Bangkok | 24 |
| Blog | How to Find a Tutor in Phuket | 32 |

## Meta Description Formula

### Formula
`{What the page offers}. {Why it matters}. {Call to action}.`

### Rules
- Maximum 160 characters
- Include primary keyword naturally
- Include a call to action
- Make it compelling for clicks
- Every page must have a unique description

### Examples
| Page Type | Meta Description | Char Count |
|---|---|---|
| Home | Find qualified private tutors in Thailand. One-to-one tutoring for IB, IGCSE, A Level, and more. Message us on WhatsApp. | 115 |
| Location | Find private tutors in Bangkok. Qualified tutors for international school students. IB, IGCSE, A Level support. WhatsApp us. | 120 |
| Subject | One-to-one math tutoring in Thailand. Qualified tutors for IB, IGCSE, A Level. In-person or online. Message us on WhatsApp. | 121 |
| Curriculum | Expert IB tutoring in Thailand. One-to-one support for PYP, MYP, and DP. Qualified tutors. In-person or online. WhatsApp us. | 122 |
| Blog | Moving to Phuket with children? Learn about international schools, curricula, and tutoring options in this parent guide. | 116 |

## H1 Rules

- One H1 per page
- Include primary keyword
- Be descriptive and specific
- Match user intent
- Keep under 70 characters

### Examples
- "Private Tutoring in Bangkok" (not "Welcome" or "Bangkok")
- "Math Tutoring in Thailand" (not "Math" or "Our Math Services")
- "IB Tutoring in Thailand" (not "IB" or "International Baccalaureate")

## URL Slug Rules

### Formula
`/{page-type}/{descriptive-slug}/`

### Rules
- All lowercase
- Hyphens between words
- No underscores
- No special characters
- No unnecessary words (a, the, and, in)
- Keep under 60 characters total

### Examples
| Page | URL |
|---|---|
| Home | `/` |
| Bangkok | `/locations/bangkok/` |
| Math | `/subjects/math-tutoring/` |
| IB | `/curriculum/ib-tutoring/` |
| Math in Bangkok | `/thailand/bangkok/math-tutor/` |
| Blog | `/blog/find-tutor-phuket/` |

## Open Graph Rules

### og:title
- Same as SEO title or slightly more conversational
- Maximum 60 characters

### og:description
- Same as meta description
- Maximum 200 characters

### og:image
- 1200 x 630 pixels
- Include brand name
- Relevant to page topic
- Use consistently across page types

### og:type
- `website` for service pages
- `article` for blog posts

## Canonical URL Rules

- Every page must have a canonical URL
- Use absolute URLs
- If a page is accessible via multiple URLs, canonical points to the preferred version
- No trailing slash inconsistency

## Structured Data

### Service Pages
Use `LocalBusiness` or `ProfessionalService` schema with:
- Name
- Description
- URL
- Area served (for location pages)
- Service type

### FAQ Sections
Use `FAQPage` schema (see `faq-template.md`)

### Blog Articles
Use `Article` schema with:
- Headline
- Author
- Date published
- Date modified
- Image
