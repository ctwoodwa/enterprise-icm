# Stage 05 - Scaffolds and Checklists

Generate reusable project scaffolds, config templates, and operational checklists from the specs.
Outputs are drop-in starting points for a real solution repo.

## Inputs

| Source | File/Location | Section/Scope | Why |
|---|---|---|---|
| Stage 04 output | ../04-service-and-app-specs/output/blazor-ui-spec.md | Full file | UI scaffold requirements |
| Stage 04 output | ../04-service-and-app-specs/output/gateway-yarp-spec.md | Full file | YARP config scaffold requirements |
| Stage 04 output | ../04-service-and-app-specs/output/dab-api-spec.md | Full file | DAB config scaffold requirements |
| Stage 04 output | ../04-service-and-app-specs/output/scalar-spec.md | Full file | Scalar registration requirements |
| Stage 04 output | ../04-service-and-app-specs/output/otel-spec.md | Full file | OTEL config scaffold requirements |
| Stage 03 output | ../03-standards-and-practices/output/coding-standards.md | Full file | Standards scaffolds must follow |

## Process

1. Generate Aspire solution structure as annotated text tree showing all projects and references.
2. Generate Aspire AppHost registration stub with service wiring comments.
3. Generate YARP appsettings.json route template with inline comments per route.
4. Generate dab-config.json template with entity placeholders and permission comments.
5. Generate appsettings.{Environment}.json templates for dev, test, and prod with OTEL and API UI toggles.
6. Generate Scalar and GraphQL Playground registration code stubs for Program.cs.
7. Generate new-service checklist, new-feature checklist, and production-readiness checklist.
8. Verify all scaffolds follow coding standards from Stage 03. Revise any that do not.
9. Save outputs.

## Outputs

| Artifact | Location | Format |
|---|---|---|
| Aspire solution structure | output/solution-structure.md | Markdown |
| AppHost stub | output/scaffold-templates/AppHost-stub.cs | C# |
| YARP config template | output/scaffold-templates/yarp-appsettings.json | JSON |
| DAB config template | output/scaffold-templates/dab-config.json | JSON |
| appsettings templates | output/scaffold-templates/ | JSON (one per env) |
| Program.cs stubs | output/scaffold-templates/Program-stubs.cs | C# |
| Checklists | output/checklists.md | Markdown |