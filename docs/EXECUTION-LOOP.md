# Execution Loop

## Purpose

Every task in this project must follow this execution loop. No exceptions.

This loop ensures:
- No work happens outside the system
- Every task is tracked
- Every task is verified
- Every task is documented
- The project is always inspectable

## The Loop

### Step 1: Read the Project README
Read `README.md` to confirm project context, structure, and current state.

### Step 2: Read the Tracking List
Read `docs/TRACKING.md` to check:
- What is being worked on now
- What is blocked
- Who owns what
- What your current task is

If your task is not in tracking, add it before proceeding.

### Step 3: Identify Project Type
Classify the task:
- **Type A: SEO / Sales Website** — external-facing, traffic/leads/sales
- **Type B: Internal System** — admin, dashboard, CRM, workflow tool
- **Type C: Hybrid** — both public and internal elements

This project is **Type A**.

### Step 4: Check Strategy or Checklist
For Type A (SEO / Sales Website):
- Read `docs/STRATEGY.md`
- Read `docs/SEO-PLAN.md`
- Check `docs/6-MONTH-PLAN.md`
- Confirm the task aligns with the 12-month strategy

For Type B (Internal System):
- Read `docs/CHECKLIST.md` (if it exists)
- Check feature checklist
- Check workflow checklist

### Step 5: Confirm Owner and Responsibility
Check `docs/TEAM.md`:
- Who is responsible for this task?
- Who must be consulted?
- Who must approve?
- Who must be informed?

If responsibility is unclear:
- Mark it as unclear in `docs/TRACKING.md`
- Add it to open questions
- Request decision from the project lead

### Step 6: Check Blockers and Dependencies
Read `docs/RISKS.md` and `docs/TRACKING.md`:
- Are there blockers affecting this task?
- Are dependencies complete?
- If blocked, update tracking and stop. Do not proceed.

### Step 7: Plan the Smallest Safe Action
Create a small, focused plan:
- What is the minimum change needed?
- What files will be affected?
- What could go wrong?
- How will you verify the result?

Show the plan before executing (as required by `AGENTS.md`).

### Step 8: Execute Only the Necessary Change
Make the change:
- Keep changes focused
- Avoid unrelated edits
- Follow templates exactly
- Follow brand voice rules
- Follow content rules
- Follow image rules (`docs/image-rules.md`)
- Follow SEO rules

### Step 9: Verify the Result
Check your work:
- Does it match the plan?
- Does it follow all rules?
- Are there any errors?
- Run QA checklist if applicable
- Run browser review if applicable

### Step 10: Update Tracking
Update `docs/TRACKING.md`:
- Update the task status
- Add any new blockers or dependencies
- Update "Last Updated" with today's date

### Step 11: Update Documentation
Update relevant docs:
- `docs/CHANGELOG.md` — what changed and why
- `docs/RISKS.md` — any new risks identified
- `docs/DECISIONS.md` — any decisions made
- Other relevant docs

### Step 12: Record Decisions
If you made any important decisions:
- Add them to `docs/DECISIONS.md`
- Include date, context, decision, reason, rejected alternatives

### Step 13: Mark Next Action
In `docs/TRACKING.md`:
- Mark the task as Done, Testing, or Waiting for Approval
- If there is a next step, create a new task for it
- If the task is blocked, update the blocker and stop

## Important Rules

- **A task is not finished until tracking and documentation are updated.**
- **Never treat the work as finished before the project files are updated.**
- **Never work from isolated instructions if project documentation already exists.**
- **If you fail 3 times on the same issue, escalate to the human project lead.**
- **If you encounter a blocker, stop and update tracking. Do not proceed.**

## Recovery

If the session crashes or you need to resume:
1. Read `docs/TRACKING.md` — find the last active task
2. Read `docs/CHANGELOG.md` — understand what was last completed
3. Read `docs/RISKS.md` — check for active blockers
4. Resume from the last completed step in the execution loop
5. Update tracking to reflect the resume
