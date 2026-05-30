# FAQ Template

## Purpose

Reusable FAQ structure for any service page. Can be embedded within location, subject, curriculum, and combination pages.

## FAQ Formats

### Short Answer (1-2 sentences)
Use for straightforward factual questions.

**Example:**
> **Q: Do you offer online tutoring?**
> A: Yes, we offer online tutoring via video call for all subjects and curricula.

### Medium Answer (1 paragraph, 50-100 words)
Use for questions that need a brief explanation.

**Example:**
> **Q: Which curricula do your tutors support?**
> A: Our tutors support IB, IGCSE, A Level, Cambridge, British, American, and Australian curricula. We match tutors based on your child's specific curriculum and subject needs.

### Long Answer (2-3 paragraphs, 100-200 words)
Use for complex questions that need context.

**Example:**
> **Q: How does tutor matching work?**
> A: When you contact us, we ask about your child's subjects, curriculum, level, and any specific needs or goals. We then match you with a tutor who has the right subject expertise, curriculum knowledge, and personality fit.
>
> We arrange a trial session so you can see if the tutor is right for your child. If the fit isn't perfect, we'll match you with another tutor. There's no pressure to commit after the first session.

## Schema Markup Ready Structure

Each FAQ section should be formatted so it can easily be converted to JSON-LD schema markup:

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "Question text here?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Answer text here."
      }
    }
  ]
}
```

## Standard FAQ Questions (Adapt for Each Page)

### For Location Pages
1. Do you offer online tutoring in [Location]?
2. Which curricula do your [Location] tutors support?
3. How quickly can you match a tutor in [Location]?
4. Do your tutors come to our home in [Location]?
5. What subjects are most in demand in [Location]?
6. How much does tutoring cost in [Location]?
7. Can you help with exam preparation in [Location]?

### For Subject Pages
1. What age should my child start [subject] tutoring?
2. Which curriculum does your [subject] tutoring follow?
3. Do you offer online [subject] tutoring?
4. How do I know if my child needs a [subject] tutor?
5. Can a tutor help with [subject] exam preparation?
6. How long are [subject] tutoring sessions?
7. What should my child bring to a [subject] tutoring session?

### For Curriculum Pages
1. What is [curriculum] and is it right for my child?
2. Which schools in Thailand offer [curriculum]?
3. Do your tutors understand [curriculum] exam structure?
4. Can tutoring help with [curriculum] transition?
5. Do you offer online [curriculum] tutoring?
6. How does [curriculum] compare to other curricula?
7. What age should my child start [curriculum] tutoring?

### For Combination Pages
1. Do you offer [subject] tutoring in [location]?
2. Which curricula do your [location] [subject] tutors support?
3. Can the tutor come to our home in [location]?
4. How quickly can you match a [subject] tutor in [location]?
5. Do you offer online [subject] tutoring for [location] families?

## FAQ Writing Rules

- **Answer the question directly** in the first sentence
- **Keep it concise** — most FAQs should be 50-100 words
- **Link to related pages** where relevant
- **Don't repeat** information from the main page verbatim
- **Be honest** — if something varies (e.g., pricing), say so
- **Use the parent's language** — not education jargon
