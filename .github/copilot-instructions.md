# Copilot Instructions

## Project Type

**SEO / Sales Website (Type A)**

This is an external-facing website built to generate traffic, leads, and bookings.

## Read First (In This Order)

1. `docs/STRATEGY.md` — What this project is and why it exists
2. `docs/TRACKING.md` — What is being worked on now
3. `docs/TEAM.md` — Who does what
4. `docs/RISKS.md` — Known blockers
5. `docs/EXECUTION-LOOP.md` — The formal execution loop
6. `README.md`

## Execution Loop

Every task must follow the execution loop in `docs/EXECUTION-LOOP.md`.

Summary:
1. Read the project README
2. Read the tracking list
3. Identify project type
4. Check strategy or checklist
5. Confirm owner and responsibility
6. Check blockers and dependencies
7. Plan the smallest safe action
8. Execute only the necessary change
9. Verify the result
10. Update tracking
11. Update documentation
12. Record decisions
13. Mark next action

## Project Rules

This repository is the control system for Private Tutoring Thailand.

Before creating or editing anything, read README.md first.

Do not create random files.

Do not create full website pages yet.

First create the foundation structure from README.md.

Keep all work inside this repository.

Follow the folder structure defined in README.md.

Use markdown for documentation and content files.

Use JSON only for structured data files inside /data.

Every generated page must have a clear SEO purpose, parent intent, internal links, conversion action, and images that follow `docs/image-rules.md`.

Do not invent fake statistics, fake testimonials, fake tutor credentials, fake school partnerships, or fake claims.

Do not duplicate pages by only changing the city name.

Do not create hundreds of pages before the system is ready.

Create the system first.

Then create the pages.

When unsure, ask before changing structure.

## Image and Visual Quality Rules

Every page must pass image and visual quality checks:

1. Read `docs/image-rules.md` before creating any images
2. Every image must show: one Thai tutor, one European child, one child only, private setting
3. Generate images using BFL.ai with the exact prompt workflow in `docs/image-rules.md`
4. Verify every image before publishing
5. Run MCP browser review on every page before publishing (see `docs/quality-control.md`)
6. Test mobile view on every page
7. Fix issues and re-check before deploying

## Tracking Rules

- Every task must be recorded in `docs/TRACKING.md`
- Update status when starting, changing, or finishing work
- A task is not finished until tracking is updated
- If you encounter a blocker, add it to `docs/TRACKING.md` and `docs/RISKS.md`

## Decision Rules

- Every important decision must be recorded in `docs/DECISIONS.md`
- Include date, context, decision, reason, and rejected alternatives

## Escalation Rule

- If you fail 3 times on the same issue, stop and escalate to the human project lead
- Document the failures in `docs/TRACKING.md`
- Do not silently retry more than 3 times

## Project Control Rule

- No hidden work
- No undocumented changes
- No unclear ownership
- No random SEO pages
- No untracked features
- No silent scope expansion
- No undocumented decisions
- No unfinished tasks marked as done
