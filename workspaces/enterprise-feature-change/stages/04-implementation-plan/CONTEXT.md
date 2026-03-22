# Stage 04 - Tests and Verification

Write or update tests for the changed code. Verify each acceptance criterion is met.
Mark ACs as verified in `_config/ticket-context.md`.

> **Skip this stage for XS tickets** if the change has no testable logic (e.g., a config tweak or copy change).
> For all other tickets, this stage is required.

## Inputs

| Source | File/Location | Section/Scope | Why |
|---|---|---|---|
| Ticket context | `../../_config/ticket-context.md` | ACs and Verified column | Defines what to verify |
| Change summary | `../03-design-spec/output/feature-[slug]-changes.md` | All changed files | What needs test coverage |
| Existing test project | Project test files | Current test structure | Patterns to follow for new tests |
| Code reading notes | `../02-architecture-impact/output/feature-[slug]-code-reading.md` | Test coverage section | Which files already have tests |

## Process

1. For each changed file in the change summary, check if an existing test file covers it.
2. For changed files with existing tests: add test cases for the new behavior. Do not delete existing tests.
3. For new files with no test coverage:
   - If the file contains business logic, a solver call, or data validation: write a unit test.
   - If the file is a new API endpoint: write an integration test (or describe what the integration test should assert if the test infrastructure isn't available in this session).
   - If the file is a new Blazor component or page: write a bunit component test.
4. Verify each AC against the implementation:
   - State how you know the AC is met (which test, which code path, or which observable behavior).
   - Mark the AC as `☑` in `_config/ticket-context.md`.
5. List any ACs that cannot be fully verified in this session (e.g., require a running environment) and describe the manual verification steps.
6. Save outputs.

## Outputs

| Artifact | Location | Format |
|---|---|---|
| Test files | Target project test folder | C# NUnit / bunit test files |
| Verification report | `output/feature-[slug]-verification.md` | Per-AC: how it's verified, test name or manual steps |
| Updated ticket context | `../../_config/ticket-context.md` | Verified column updated |

## Checkpoints

| After Step | Agent Presents | Human Decides |
|---|---|---|
| 3 | New test files (first one) | Approve pattern before writing remaining tests |
| 5 | Verification report with any unverified ACs | Confirm manual verification steps are sufficient |

## Audit

| Check | Pass Condition |
|---|---|
| All ACs have a verification method | No AC row in the ticket context has an empty verification note |
| Business logic is unit-tested | Every changed method with conditional logic has at least one test |
| Existing tests not broken | No existing test was deleted or its assertion weakened |
| Unverifiable ACs documented | ACs requiring a live environment have explicit manual steps |
| Ticket context updated | All verified ACs show `☑` in `_config/ticket-context.md` |
