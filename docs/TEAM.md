# Team

## Project: Private Tutoring Thailand

## Human Roles

| Role | Name | Responsibility |
|---|---|---|
| **Project Lead / Admin** | Human | Final approval on all publishing decisions, brand voice changes, pricing, structural changes. Escalation target when AI fails 3 times. |

## AI Roles

| Role | Prompt File | Responsibility |
|---|---|---|
| **Boss AI** | `prompts/boss-agent.md` | Central orchestrator. Reads project state, assigns workers, tracks progress, triggers handoffs, escalates to human. |
| **Worker: Research** | `prompts/worker-research-agent.md` | Market research, competitor analysis, keyword discovery, parent insight gathering. |
| **Worker: Builder** | `prompts/worker-builder-agent.md` | Page construction from templates, data, and brand voice. Writes markdown content. |
| **Worker: Image** | `prompts/worker-image-agent.md` | Image generation via BFL.ai. Follows `docs/image-rules.md` strictly. |
| **Worker: QA** | `prompts/worker-qa-agent.md` | Quality checks, browser review, mobile testing, validation against all rules. |
| **Worker: Fixer** | `prompts/worker-fixer-agent.md` | Receives QA reports, fixes issues, re-submits for QA. |
| **Worker: Deployer** | `prompts/worker-deployer-agent.md` | Goes live after all gates pass. Handles deployment, sitemap updates, final checks. |

## Responsibility Matrix (RACI)

| Task | Boss AI | Research | Builder | Image | QA | Fixer | Deployer | Human |
|---|---|---|---|---|---|---|---|---|
| Read project files | R | I | I | I | I | I | I | I |
| Assign work | R | I | I | I | I | I | I | A |
| Market research | A | R | I | I | I | I | I | I |
| Write page drafts | A | I | R | I | I | I | I | I |
| Generate images | A | I | I | R | I | I | I | I |
| Run QA checks | A | I | I | I | R | I | I | I |
| Fix QA issues | A | I | I | I | I | R | I | I |
| Deploy pages | A | I | I | I | I | I | R | A |
| Update tracking | R | C | C | C | C | C | C | I |
| Approve publish | I | I | I | I | I | I | I | R/A |

**Legend:** R = Responsible (does the work), A = Accountable (owns the outcome), C = Consulted, I = Informed

## Escalation Path

1. Worker AI encounters issue → reports to Boss AI
2. Boss AI attempts resolution (re-assign, re-prompt, provide context)
3. Worker AI fails 3 times on same issue → Boss AI escalates to Human
4. Human decides: fix, discard, or change approach
5. Human updates `docs/DECISIONS.md` with the decision
6. Boss AI updates `docs/TRACKING.md` and resumes workflow

## Communication Rules

- Boss AI is the only AI that talks to the Human directly
- Workers only talk to the Boss AI
- All handoffs are documented in `docs/TRACKING.md`
- Every worker must read its prompt file before starting work
- Every worker must update tracking before finishing work
