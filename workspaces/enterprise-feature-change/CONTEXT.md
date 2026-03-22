# Enterprise Feature Change — Workspace Context

Task routing and rules for implementing a Jira ticket or user story end-to-end.

## Task Routing

| Task Type | Go To Stage | Description |
|---|---|---|
| Parse ticket, extract ACs, identify affected files | `stages/01-discovery/` | Everything downstream depends on this |
| Read affected code, understand current patterns | `stages/02-architecture-impact/` | Required for M/L tickets; optional for XS/S |
| Write the code changes | `stages/03-design-spec/` | The main implementation stage |
| Write tests, verify acceptance criteria | `stages/04-implementation-plan/` | Required for M/L tickets; recommended for S |
| Draft PR description, run final checklist | `stages/05-review-and-pr/` | Always required |

## Reference Materials

| Resource | Location | Contains |
|---|---|---|
| Ticket details and ACs | `_config/ticket-context.md` | Single source of truth for what is being built |
| Branch naming conventions | `shared/branch-naming.md` | Consistent branch and commit naming |
| PR description template | `shared/pr-template.md` | Structure for the PR description |
| AC verification guide | `shared/acceptance-criteria-guide.md` | How to verify each AC systematically |
| Stage outputs | `stages/*/output/` | Artifacts produced at each stage |

## Rules

1. Fill `_config/ticket-context.md` fully during Stage 01 before reading any code.
2. Run stages in the order defined by the ticket size routing table in `CLAUDE.md`.
3. Read existing code before writing changes. Never write code based on assumed patterns.
4. Every changed file must be traceable to an acceptance criterion.
5. Use `feature-[slug]-*.md` naming for all stage output artifacts, where `slug` is the Jira ticket ID (e.g. `feature-COMET-42-discovery.md`).
6. For `l`-size tickets: present the Stage 02 architecture impact report to the human and wait for explicit approval before proceeding to Stage 03.
