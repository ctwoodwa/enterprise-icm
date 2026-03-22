# Stage 05 - PR Preparation

Draft the pull request description, run the final pre-merge checklist, and produce everything
needed to get the change reviewed and merged.

## Inputs

| Source | File/Location | Section/Scope | Why |
|---|---|---|---|
| Ticket context | `../../_config/ticket-context.md` | All fields, verified ACs | PR title, Jira link, and AC verification status |
| Change summary | `../03-design-spec/output/feature-[slug]-changes.md` | All changed files | What changed section of the PR |
| Verification report | `../04-implementation-plan/output/feature-[slug]-verification.md` | All ACs | Test plan section of the PR |
| PR template | `../../shared/pr-template.md` | Full template | PR description structure |
| Discovery summary | `../01-discovery/output/feature-[slug]-discovery.md` | Notes and constraints | Context section of the PR |

## Process

1. Fill the PR template from `shared/pr-template.md` using the artifacts above.
2. Run the pre-merge checklist:
   - All ACs marked `☑` in `_config/ticket-context.md` — or unverified ones have documented manual steps.
   - No files changed outside the agreed scope (check the change summary).
   - No unresolved TODO comments added in this session.
   - DI registrations are complete.
   - No hardcoded secrets, connection strings, or environment-specific values.
   - If a DB migration was created: the migration command is documented.
   - If a new Jira ticket is needed for follow-up work: it is noted in the PR description.
3. List any follow-up tickets to create (out-of-scope items discovered during implementation).
4. Save outputs.

## Outputs

| Artifact | Location | Format |
|---|---|---|
| PR draft | `output/feature-[slug]-pr-draft.md` | Filled PR template — ready to paste into GitHub/ADO |
| Pre-merge checklist | `output/feature-[slug]-pre-merge-checklist.md` | Checklist with pass/fail per item |

## Checkpoints

| After Step | Agent Presents | Human Decides |
|---|---|---|
| 2 | Pre-merge checklist with any failing items | Resolve failures or accept risk before PR is finalized |

## Audit

| Check | Pass Condition |
|---|---|
| PR description is complete | All sections of `shared/pr-template.md` are filled — none left as placeholder |
| Jira ticket linked | PR description includes the ticket ID and URL |
| ACs referenced | Each AC is listed with its verification status |
| Pre-merge checklist passes | All items are ✅ or have an explicit risk-acceptance note |
| Follow-up tickets noted | Any out-of-scope work discovered is listed as a follow-up |
