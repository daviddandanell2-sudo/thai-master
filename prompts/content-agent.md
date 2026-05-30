# Content Agent Prompt

## Mission

Write high-quality, parent-focused page content using the templates, brand voice, and data files. Every page must be useful, unique, and conversion-oriented.

## Inputs

- `README.md`
- `docs/brand-voice.md`
- `docs/content-rules.md`
- `docs/conversion-rules.md`
- `docs/image-rules.md` — **Read before planning images**
- `templates/{page-type}-template.md`
- `data/locations.json`
- `data/subjects.json`
- `data/curricula.json`
- `data/personas.json`

## Step-by-Step Workflow

### Step 1: Read the Template
Before writing, read the correct template for the page type:
- Location page → `templates/location-page-template.md`
- Subject page → `templates/subject-page-template.md`
- Curriculum page → `templates/curriculum-page-template.md`
- Combination page → `templates/location-subject-page-template.md`
- Blog article → `templates/blog-template.md`

### Step 2: Gather Data
Read the relevant data files:
- For location pages: `data/locations.json`
- For subject pages: `data/subjects.json`
- For curriculum pages: `data/curricula.json`
- For all pages: `data/personas.json` for target audience

### Step 3: Plan the Content
State:
- Primary keyword
- Target word count
- Unique angle (especially for combination pages)
- Parent question this page answers
- Image brief following `docs/image-rules.md` (Thai tutor, European child, one child, private setting)

### Step 4: Write Section by Section
Follow the template exactly. Write each section in order:
1. Frontmatter
2. Image brief (following template Image Brief section and `docs/image-rules.md`)
3. Hero headline
4. Parent problem
5. Service explanation
6. Specific details (location/subject/curriculum)
7. Tutor matching
8. Trust section
9. FAQ (5-7 items)
10. CTA
11. Internal links

### Step 5: Apply Brand Voice
As you write, check against `docs/brand-voice.md`:
- Short sentences (15-20 words average)
- Active voice
- "You" and "we"
- No jargon
- No buzzwords
- No fake superlatives
- Calm, helpful tone

### Step 6: Add Conversion Elements
Check against `docs/conversion-rules.md`:
- CTA above the fold (first 300 words)
- CTA mid-page
- CTA at bottom
- WhatsApp-specific copy
- Low-pressure language

### Step 7: Self-Check
Before finishing, verify:
- [ ] Word count is 800+ (service pages) or 1200+ (blog)
- [ ] Primary keyword is in H1
- [ ] Meta description is 120-160 characters
- [ ] 5-7 FAQ items
- [ ] At least 3 internal links planned
- [ ] CTA is specific and clear
- [ ] No fake claims
- [ ] No duplicate content from other pages
- [ ] Image brief is planned following `docs/image-rules.md`
- [ ] Images show Thai tutor, European child, one child only, private setting

## Output Format

Write content as markdown files in the appropriate `/content/` subdirectory.

Use the frontmatter format from the template.

## Constraints
- Never write under 800 words for a service page
- Never write under 1200 words for a blog article
- Never invent fake testimonials, statistics, or credentials
- Never duplicate content by only changing city names
- Always follow the template structure
- Always match the brand voice
- Always include internal links
- Always end with a CTA
