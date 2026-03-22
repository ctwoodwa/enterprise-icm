# Stage 02 - Code Reading

Read every file in the affected scope identified in Stage 01. Understand the current
implementation patterns, data shapes, and conventions that the new code must follow.
For M/L tickets, also assess architecture impact: contracts, migrations, and rollout risk.

> **Skip this stage for XS tickets.** Proceed directly to Stage 03.

## Inputs

| Source | File/Location | Section/Scope | Why |
|---|---|---|---|
| Ticket context | `../../_config/ticket-context.md` | Affected files, ACs | Defines what to read |
| Discovery summary | `../01-discovery/output/feature-[slug]-discovery.md` | Scope section | Confirms which files to read |
| Affected source files | `{{AFFECTED_FILES}}` (all of them) | Full file content | Required reading before writing any code |

## Process

1. Read every file listed in `_config/ticket-context.md` under Affected Files. Do not skip any.
2. For each file, note:
   - Existing patterns: naming, DI registration style, error handling, return types
   - Data shapes: request/response DTOs, entity fields, existing validation
   - Test coverage: is this file covered by existing tests? Which test file?
3. Identify the exact insertion or modification points for each AC:
   - For new endpoints: where does routing live? What does a similar endpoint look like?
   - For new fields: what is the DTO → entity → DB column chain?
   - For behavior changes: which method and which line needs to change?
4. **For M/L tickets only:** assess cross-cutting concerns:
   - Does any change break an existing API contract? (requires versioning decision)
   - Does any change require a DB migration? (requires schema change and seeder update)
   - Does any change affect the Gateway routing or auth? (requires Gateway config update)
   - Does any change affect multiple services? (requires coordination plan)
5. Save outputs.

## Outputs

| Artifact | Location | Format |
|---|---|---|
| Code reading notes | `output/feature-[slug]-code-reading.md` | Per-file: patterns observed, modification points |
| Architecture impact report | `output/feature-[slug]-architecture-impact.md` | (M/L only) Breaking changes, migration needs, coordination plan |

## Checkpoints

| After Step | Agent Presents | Human Decides |
|---|---|---|
| 3 | Modification point map (file → method → AC) | Confirm scope is complete and correct before implementation |
| 4 | Architecture impact report (M/L only) | **Explicit approval required before Stage 03 begins for L tickets** |

## Audit

| Check | Pass Condition |
|---|---|
| All affected files read | Every path in `_config/ticket-context.md` Affected Files has a note in the code reading output |
| Modification points identified | Each AC has at least one specific file + method/location mapped |
| Patterns documented | At least one example of each relevant pattern (routing, DI, error handling) is recorded |
| Breaking changes flagged | Any change to a public API contract or event schema is explicitly flagged |
