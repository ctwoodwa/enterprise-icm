# Stage 03 - Implementation

Write the code changes. This is the main implementation stage. Apply changes one file at a
time, following the patterns observed in Stage 02. Every change must map to an AC.

## Inputs

| Source | File/Location | Section/Scope | Why |
|---|---|---|---|
| Ticket context | `../../_config/ticket-context.md` | ACs, affected files, scope | What to build and where |
| Code reading notes | `../02-architecture-impact/output/feature-[slug]-code-reading.md` | Patterns, modification points | How to build it — skip to source files if Stage 02 was skipped |
| Affected source files | All files identified in Stage 01/02 | Full content | Read before editing |

## Process

1. Order the changes: dependencies first (e.g., DTOs before endpoints, entities before DbContext, DB layer before service layer before API layer).
2. For each change, in order:
   a. Re-read the file to confirm current content before editing.
   b. Write the change following the exact conventions observed in Stage 02.
   c. State which AC this change satisfies.
   d. If the change requires a new file (e.g., a new endpoint class, a new migration), create it matching the naming and structure of existing files.
3. After each file change, check:
   - Do method signatures match what callers expect?
   - Are new DI registrations added where needed?
   - Are nullable reference types handled?
4. For DB schema changes: produce the EF Core migration command to run and describe the expected migration content.
5. After all code changes are written, produce the complete change summary.
6. Save outputs.

## Outputs

| Artifact | Location | Format |
|---|---|---|
| Change summary | `output/feature-[slug]-changes.md` | Table: file, change type (new/modified/deleted), AC satisfied, notes |

> The actual code changes are written directly to the target project's source files.

## Checkpoints

| After Step | Agent Presents | Human Decides |
|---|---|---|
| 1 | Ordered change list | Confirm ordering before any edits are made |
| 2 (first change) | First changed or created file | Approve the pattern before applying remaining changes |
| 5 | Complete change summary | Confirm all ACs are addressed before moving to Stage 04 |

## Audit

| Check | Pass Condition |
|---|---|
| All ACs addressed | Every AC in `_config/ticket-context.md` maps to at least one change in the summary |
| Dependencies ordered | No change references a type or method that was added later in the same batch |
| Conventions followed | New code matches the naming, error handling, and DI patterns from Stage 02 notes |
| No scope creep | No changed file is outside the scope agreed in Stage 01 (or newly approved in Stage 02) |
| DI registrations updated | Any new service, repository, or handler is registered in the DI container |
| Nullable types handled | No new `null` dereference warnings introduced |
