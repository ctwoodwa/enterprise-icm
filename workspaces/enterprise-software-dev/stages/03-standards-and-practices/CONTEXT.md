# Stage 03 - Standards and Practices

Generate coding standards, 12-factor mapping, KISS rules, testing strategy, and CI/CD expectations.
These outputs become canonical Layer 3 references consumed by all later stages.

## Inputs

| Source | File/Location | Section/Scope | Why |
|---|---|---|---|
| Stage 02 output | ../02-architecture-and-patterns/output/system-architecture.md | Full file | Architecture to align standards to |
| Config | ../../_config/architecture-principles.md | Full file | Org-level rules to encode |
| Config | ../../_config/quality-gates.md | Full file | Definition of done and SLAs |
| Shared | ../../shared/observability-guide.md | Full file | OTEL rules to bake into standards |
| Shared | ../../shared/security-baseline.md | Full file | Security rules to bake in |

## Process

1. Generate C# and .NET coding standards: naming, file layout, nullability, async patterns, error handling.
2. Generate Blazor-specific standards: component structure, state management, Telerik usage rules.
3. Map all 12 factors to this platform - one entry per factor explaining how Aspire/YARP/DAB implements it.
4. Define KISS rules: max abstraction layers, when NOT to use patterns, simplicity checkpoints.
5. Define testing strategy: unit, integration, contract, and smoke test expectations per service type.
6. Define CI/CD expectations: branch strategy, required pipeline gates, environment promotion rules.
7. Audit: every standard must be specific and testable, not aspirational. Revise any that are not.
8. Save outputs.

## Outputs

| Artifact | Location | Format |
|---|---|---|
| C# coding standards | output/coding-standards.md | Markdown |
| Blazor and Telerik standards | output/blazor-standards.md | Markdown |
| 12-factor mapping | output/12-factor-mapping.md | Markdown |
| KISS rules | output/kiss-rules.md | Markdown |
| Testing strategy | output/testing-strategy.md | Markdown |
| CI/CD expectations | output/cicd-expectations.md | Markdown |