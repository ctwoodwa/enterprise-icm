# Stage 02 - Architecture and Patterns

Choose architecture patterns, service topology, and produce Architecture Decision Records (ADRs).

## Inputs

| Source | File/Location | Section/Scope | Why |
|---|---|---|---|
| Stage 01 output | ../01-discovery-and-context/output/problem-brief.md | Full file | Problem and constraints to shape arch |
| Stage 01 output | ../01-discovery-and-context/output/constraints.md | Full file | Hard constraints on patterns |
| Config | ../../_config/architecture-principles.md | Full file | Preferred patterns and rules |
| Shared | ../../shared/enterprise-patterns.md | Full file | Available patterns catalogue |

## Process

1. Review problem brief and constraints from Stage 01.
2. Define solution topology: Aspire AppHost, service projects, shared libs.
3. Select architecture style (layered, ports-and-adapters, CQRS) per service type.
4. Document each significant decision as an ADR (context, decision, consequences).
5. Produce a system architecture diagram in text showing service boundaries and data flows.
6. Verify no circular dependencies across service boundaries.
7. Save outputs.

## Outputs

| Artifact | Location | Format |
|---|---|---|
| System architecture | output/system-architecture.md | Markdown |
| ADRs (one per decision) | output/architecture-decision-records/ | Markdown |
| Service boundary map | output/service-boundary-map.md | Markdown |