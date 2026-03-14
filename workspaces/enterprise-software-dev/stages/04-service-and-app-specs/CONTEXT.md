# Stage 04 - Service and App Specs

Produce per-service specifications for Blazor, YARP, DAB, Scalar, GraphQL Playground, and OTEL.
Each spec defines the WHAT and the contracts. Stage 05 turns them into scaffolds.

## Inputs

| Source | File/Location | Section/Scope | Why |
|---|---|---|---|
| Stage 02 output | ../02-architecture-and-patterns/output/system-architecture.md | Full file | Service topology to spec against |
| Stage 02 output | ../02-architecture-and-patterns/output/service-boundary-map.md | Full file | Integration contracts |
| Stage 03 output | ../03-standards-and-practices/output/coding-standards.md | Full file | Standards every spec must follow |
| Stage 03 output | ../03-standards-and-practices/output/12-factor-mapping.md | Full file | 12-factor rules per service |
| Shared | ../../shared/api-visibility.md | Full file | Scalar and GraphQL Playground env rules |
| Shared | ../../shared/observability-guide.md | Full file | OTEL requirements per service |
| Shared | ../../shared/security-baseline.md | Full file | Auth and secrets rules |

## Process

1. Write Blazor UI spec: Telerik component patterns, routing, state management, theming defaults.
2. Write YARP gateway spec: routes per upstream, auth propagation, health probes, retry and circuit-breaker config.
3. Write DAB API spec: entities, REST and GraphQL shapes, permissions, dab-config.json conventions.
4. Write Scalar spec: OpenAPI endpoint, UI route, env-specific enable/disable flags, auth requirements.
5. Write GraphQL Playground spec: endpoint, introspection policy, env-specific exposure, CORS rules.
6. Write OTEL spec: resource attributes, sampling rates, exporter config per environment.
7. Verify all specs are consistent with Stage 03 standards. Flag any conflicts.
8. Save outputs.

## Outputs

| Artifact | Location | Format |
|---|---|---|
| Blazor UI spec | output/blazor-ui-spec.md | Markdown |
| YARP gateway spec | output/gateway-yarp-spec.md | Markdown |
| DAB API spec | output/dab-api-spec.md | Markdown |
| Scalar spec | output/scalar-spec.md | Markdown |
| GraphQL Playground spec | output/graphql-playground-spec.md | Markdown |
| OTEL spec | output/otel-spec.md | Markdown |