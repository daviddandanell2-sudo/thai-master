# Quality Control

## Pre-Publish Gate

No page may be published until it passes all checks in this document.

## Quality Checklist

### 1. Is the page useful?
- [ ] It answers a specific parent question
- [ ] It provides information not available on other pages
- [ ] A parent could read it and make a better decision

**Fail if:** The page is generic, thin, or doesn't answer a clear question.

### 2. Is the keyword intent clear?
- [ ] The primary keyword is in the H1
- [ ] The meta description includes the keyword and a CTA
- [ ] The content matches the search intent (informational vs. transactional)
- [ ] The page doesn't target the same keyword as another page

**Fail if:** No clear keyword, or keyword conflicts with another page.

### 3. Is the city or subject specific enough?
- [ ] Location pages explain why that location matters
- [ ] Subject pages explain what the subject covers and why parents worry
- [ ] Curriculum pages explain the curriculum structure
- [ ] The page couldn't apply to any other city/subject/curriculum without changes

**Fail if:** The page is a template with only the name swapped.

### 4. Is the page different from similar pages?
- [ ] It has unique content not found on other pages
- [ ] It serves a distinct search intent
- [ ] It doesn't duplicate sections from other pages verbatim

**Fail if:** Large sections are copy-pasted from another page.

### 5. Does the page link to related pages?
- [ ] At least 3 internal links to relevant pages
- [ ] Anchor text is descriptive (not "click here")
- [ ] Links are contextually relevant
- [ ] No broken links

**Fail if:** Fewer than 3 internal links, or links are irrelevant.

### 6. Does the page have a call to action?
- [ ] At least one CTA on the page
- [ ] The CTA is specific to the page topic
- [ ] The CTA is low-pressure and clear
- [ ] Contact information or form is accessible

**Fail if:** No CTA, or generic "contact us" without context.

### 7. Does the page avoid fake claims?
- [ ] No fake testimonials
- [ ] No fake statistics ("95% success rate")
- [ ] No fake tutor credentials
- [ ] No fake school partnerships
- [ ] No unverifiable claims ("best tutors in Thailand")

**Fail if:** Any claim cannot be verified or is invented.

### 8. Does the page match the brand voice?
- [ ] Clear and professional
- [ ] Parent-friendly, not corporate
- [ ] Direct and calm
- [ ] No jargon or buzzwords
- [ ] No fear-based language
- [ ] No fake urgency

**Fail if:** The tone is pushy, vague, or doesn't sound like the brand.

### 9. Does the page help parents make a decision?
- [ ] The parent understands what the service is
- [ ] The parent understands if it's for them
- [ ] The parent knows what to do next
- [ ] The page reduces uncertainty, not adds to it

**Fail if:** The parent finishes reading and still doesn't know what to do.

## Scoring Rubric

Each check is worth 1 point. Total: 9 points.

| Score | Rating | Action |
|---|---|---|
| 9 | Excellent | Ready to publish |
| 8 | Good | Minor fixes, then publish |
| 7 | Acceptable | Fixes required before publish |
| 6 or below | Poor | Major revision or discard |

## Automated QA Checks

These can be checked automatically:
- Word count (must be 800+)
- H1 presence and length
- Meta description length (120-160 chars)
- Internal link count (3+)
- FAQ item count (5+)
- Keyword in H1
- No broken links

## Manual QA Checks

These require human judgment:
- Is the content useful?
- Is the tone right?
- Are claims verifiable?
- Is the page truly unique?
- Does it help parents decide?

## QA Process

1. **Self-Check** — Content agent runs checklist on own work
2. **Peer Review** — Another agent or human reviews
3. **Fix Cycle** — Issues are fixed and re-checked
4. **Final Approval** — Human approves for publish

## Visual Quality Check (MCP Browser Review)

Every site must pass a visual quality check before going live.

### Step 1: Open the Site
- Open the site in a browser using MCP
- Navigate through key pages: home, location pages, subject pages, curriculum pages, blog articles

### Step 2: Visual Inspection
- Does the site look good?
- Are the images correct? (Thai tutor, European child, one child only, private setting)
- Is the text readable?
- Are buttons visible and clickable?
- Is spacing consistent?

### Step 3: Mobile Test
- Test on phone screen dimensions
- Does the layout adapt correctly?
- Is text still readable?
- Are CTAs accessible?
- Does navigation work?

### Step 4: Write a Report
Create a browser review report:

```markdown
# Browser Review Report: {Page/Batch Name}

## Date
{YYYY-MM-DD}

## Pages Reviewed
- {Page 1}
- {Page 2}

## What Looks Good
- {Positive observation}

## What Is Wrong
- {Issue 1}
- {Issue 2}

## What Can Be Improved
- {Improvement 1}
- {Improvement 2}
```

## Fix and Finalize

1. Take improvement suggestions from the browser review report
2. Fix the issues (images, layout, text, spacing, CTAs)
3. Run the MCP browser check one more time
4. Write a comment explaining what was changed
5. Deploy the site only after all issues are resolved

## Escalation Rule

If a page fails QA 3 times after fixes:
1. Stop working on the page
2. Document all 3 failures
3. Update `docs/TRACKING.md` with the failure history
4. Update `docs/RISKS.md` with the issue
5. Escalate to the Human project lead via Boss AI
6. Do not proceed without Human decision

The Human may decide to:
- Discard the page and rethink the approach
- Change the template or prompt
- Approve with known issues
- Assign a different worker

## QA Worker Rules

- QA Worker is strict. No page passes without meeting all criteria.
- QA Worker does not approve their own work.
- QA Worker reports to Boss AI.
- QA Worker follows `prompts/worker-qa-agent.md`.

## Remediation Rules

### If a Page Fails QA
1. Identify all failing checks
2. Determine if fixes are minor or major
3. Minor fixes: edit and re-check
4. Major fixes: return to content agent with specific feedback
5. If a page fails twice, discard and rethink the approach

### If a Batch Has High Failure Rate
- If more than 20% of pages in a batch fail QA:
  1. Stop creating new pages
  2. Analyze common failures
  3. Fix the template, prompt, or data source
  4. Re-create the batch from scratch
  5. Do not proceed until pass rate is above 80%
