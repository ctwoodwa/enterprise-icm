# Gap Resolution Context

Single source of truth for this resolution run. Populated during Stage 01. Every downstream stage reads from here.

## Target Project

| Field | Value |
|-------|-------|
| Project name | {{PROJECT_NAME}} |
| Project path | {{PROJECT_PATH}} |
| Technology stack | {{TECH_STACK}} |
| Repository URL | {{REPO_URL}} |

## Gap Analysis Source

| Field | Value |
|-------|-------|
| Entry path | {{ENTRY_PATH}} (existing / fresh) |
| Source files | {{GAP_SOURCE_FILES}} |
| Index file | {{GAP_INDEX_FILE}} (if applicable) |
| Analysis date | {{ANALYSIS_DATE}} |
| Scope | {{GAP_SCOPE}} (single / batch / systematic) |

## Target State

{{TARGET_STATE_DESCRIPTION}}

## Resolution Scope

| Field | Value |
|-------|-------|
| Area/module | {{RESOLUTION_AREA}} |
| Total gaps identified | {{TOTAL_GAPS}} |
| Critical | {{CRITICAL_COUNT}} |
| Important | {{IMPORTANT_COUNT}} |
| Nice-to-have | {{NICE_COUNT}} |
| Stage routing | {{STAGE_ROUTING}} |

## Resolution Tracking

| Stage | Status | Output |
|-------|--------|--------|
| 01-intake | pending | |
| 02-prioritize | pending | |
| 03-resolution-design | pending | |
| 04-remediation-plan | pending | |
| 05-implement | pending | |
| 06-validate | pending | |

## Constraints and Notes

{{CONSTRAINTS_AND_NOTES}}
