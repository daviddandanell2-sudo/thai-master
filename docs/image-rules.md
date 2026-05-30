# Image Rules

## Purpose

Every image on the Private Tutoring Thailand website must match the brand, the audience, and the specific rules below. No exceptions.

These rules apply to hero images, supporting images, blog featured images, Open Graph images, and any visual asset created for the site.

---

## 1. Image Creation Rules (Always Follow These)

### Who is in the image

- **One Thai tutor** (always Thai, never other nationality)
- **One European child** (always a foreigner, never Thai)
- **One child only** — never two kids, never zero kids
- Tutor and child are together: standing side by side, or sitting together
- Multiple tutors allowed with one child

### Where the scene happens

- **In Bangkok or other big Thai cities:** private apartment or villa with tall buildings visible in the background
- **Outside big cities:** private villa with a pool, tropical garden setting
- Always private, premium, comfortable — **never a classroom or school**

### How to create the image

1. Analyze the website topic and page type
2. Write a BFL.ai prompt using the rules above
3. Generate the image
4. Check it:
   - Is the tutor Thai?
   - Is the child European and alone?
   - Is the setting correct?
5. If wrong, fix the prompt and regenerate

---

## 2. Image Requirements by Page Type

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

- **Featured image:** 1200x630 (Open Graph size), relevant to topic, must still follow subject/setting rules if it shows people
- **Inline images:** 800x600, illustrative

---

## 3. Image Style Guide

### Photography Style

- Natural light preferred
- Thailand context when relevant (not generic stock)
- Professional but not sterile
- Warm, approachable feeling
- Private residence setting (villa, apartment, home)

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
- Thai children (the child in the image must be European/foreign)
- Multiple children
- School or classroom backgrounds

---

## 4. Technical Requirements

- **Format:** WebP preferred, JPEG acceptable
- **File size:** Under 200KB where possible
- **Alt text:** Descriptive, keyword-inclusive, under 125 characters
- **Filename:** SEO-friendly filename
- **Open Graph:** 1200x630 pixels

---

## 5. Output Format

Create an image brief document for every page:

```markdown
# Image Brief: {Page Name}

## Hero Image
- **Subject:** {Description following image creation rules}
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

---

## 6. Constraints

- Every page must have at least one image
- Alt text is mandatory for every image
- Images must be relevant to the page topic
- Images must follow the subject and setting rules above
- File sizes should be optimized for web
- Never use images without proper rights or licenses
- If an image fails the verification checklist, it must be regenerated before the page can pass QA
