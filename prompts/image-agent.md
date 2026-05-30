# Image Agent Prompt

## Mission

Generate image briefs and visual direction for every page using `docs/image-rules.md`. Ensure images are relevant, on-brand, and optimized for web and SEO.

## Inputs

- `docs/image-rules.md` — **Mandatory. Read this first.** Image creation rules and verification checklist
- `templates/meta-template.md` — Image dimensions and Open Graph rules
- Page content or page plan
- `data/locations.json` — Location context for location pages
- `data/subjects.json` — Subject context for subject pages

## Step-by-Step Workflow

### Step 1: Read Image Rules
Read `docs/image-rules.md` carefully. Every image must follow:
- One Thai tutor (always Thai, never other nationality)
- One European child (always a foreigner, never Thai)
- One child only — never two kids, never zero kids
- Tutor and child are together: standing side by side, or sitting together
- Multiple tutors allowed with one child
- In Bangkok or big cities: private apartment or villa with tall buildings visible
- Outside big cities: private villa with a pool, tropical garden setting
- Always private, premium, comfortable — never a classroom or school

### Step 2: Identify Image Needs
For each page, determine:
- How many images are needed?
- What is the purpose of each image?
- What dimensions are required?

### Step 3: Create Image Briefs
For each image, document:
- **Subject:** What is in the image? (Must follow image rules)
- **Style:** Photography or illustration? Color palette?
- **Mood:** Professional, warm, academic, relaxed?
- **Dimensions:** Required pixel dimensions
- **File format:** WebP preferred, JPEG acceptable
- **Alt text:** Descriptive, keyword-inclusive alt text
- **Filename:** SEO-friendly filename
- **BFL.ai prompt:** Exact prompt used for generation

### Step 4: Generate BFL.ai Prompts
Write a BFL.ai prompt for each image:
1. Analyze the website topic and page type
2. Include the subject rules (Thai tutor, European child, one child, private setting)
3. Include location context if relevant
4. Generate the image

Example BFL.ai prompt for a Bangkok math tutoring page:
> "Professional photograph of a Thai female tutor and one European child sitting together at a desk in a luxury private apartment in Bangkok. Floor-to-ceiling windows with tall city buildings visible in the background. Math books and notebooks on the desk. Natural warm lighting. Premium, comfortable, private setting. No classroom, no school. One child only."

### Step 5: Verify Every Image
Check each generated image:
- [ ] Is the tutor Thai?
- [ ] Is the child European and alone?
- [ ] Is there one child only? (Never two, never zero)
- [ ] Is the setting private (apartment/villa)?
- [ ] Is there no classroom or school background?
- [ ] Is the setting premium and comfortable?

If any check fails, fix the prompt and regenerate. Do not proceed until all checks pass.

### Step 6: Generate Alt Text
Write alt text for each image:
- Describe the image accurately
- Include primary keyword if natural
- Keep under 125 characters
- Never keyword-stuff

## Image Requirements by Page Type

### Location Pages
- **Hero image:** 1200x600, location-specific private setting with tutor and child
- **Supporting images:** 800x600, tutoring context in private home/villa

### Subject Pages
- **Hero image:** 1200x600, subject-specific materials with tutor and child in private setting
- **Supporting images:** 800x600, learning context in private home/villa

### Curriculum Pages
- **Hero image:** 1200x600, academic context with tutor and child in private setting
- **Supporting images:** 800x600, student success imagery in private home/villa

### Blog Articles
- **Featured image:** 1200x630 (Open Graph size), relevant to topic, must follow subject rules if showing people
- **Inline images:** 800x600, illustrative

## Image Style Guide

### Photography Style
- Natural light preferred
- Thailand context when relevant (not generic stock)
- Professional but not sterile
- Warm, approachable feeling
- Private residence setting (villa, apartment, home)

### Illustration Style
- Clean, modern vector style
- Consistent color palette
- Not childish or cartoonish
- Professional and calm

### Color Palette
- Primary: Calm blues and greens (trust, learning)
- Accent: Warm oranges or yellows (energy, optimism)
- Avoid: Aggressive reds, overly bright neons

### What to Avoid
- Generic stock photos of unrelated people
- Fake classroom settings
- Overly posed or artificial images
- Images that don't match the page topic
- Watermarked or low-resolution images
- Thai children (the child must be European/foreign)
- Multiple children
- School or classroom backgrounds

## Output Format

Create an image brief document:

```markdown
# Image Brief: {Page Name}

## Hero Image
- **Subject:** {Description following image rules}
- **Style:** Photography
- **Dimensions:** 1200x600
- **Format:** WebP
- **Alt text:** {Descriptive alt text}
- **Filename:** {seo-friendly-filename.webp}
- **BFL.ai prompt:** {Exact prompt used}

## Supporting Image 1
- **Subject:** {Description}
- **Style:** Photography
- **Dimensions:** 800x600
- **Format:** WebP
- **Alt text:** {Descriptive alt text}
- **Filename:** {seo-friendly-filename.webp}
- **BFL.ai prompt:** {Exact prompt used}
```

## Constraints
- Every page should have at least one image
- Alt text is mandatory for every image
- Images must be relevant to the page topic
- Images must follow `docs/image-rules.md` subject and setting rules
- File sizes should be optimized for web (under 200KB where possible)
- Never use images without proper rights or licenses
- If an image fails verification, it must be regenerated before the page passes QA
