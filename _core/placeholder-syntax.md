# Placeholder Syntax

Placeholders mark values that get filled during workspace setup (`setup` trigger).

## Format

All placeholders use double curly braces and SCREAMING_SNAKE_CASE:

```
{{SOLUTION_NAME}}
{{ORG_NAME}}
{{PRIMARY_CLOUD}}
{{DOTNET_VERSION}}
{{DB_PROVIDER}}
{{IDENTITY_PROVIDER}}
{{OBSERVABILITY_BACKEND}}
```

## Rules

- Placeholders appear in CONTEXT.md files, reference docs, and scaffold templates.
- During `setup`, the agent replaces every placeholder across the workspace.
- After setup, no placeholder should remain. The agent verifies this.
- Do not use placeholders in CONVENTIONS.md or this file.
- Placeholder names describe the value they represent, not where they are used.

## Common Placeholders for This Workspace

| Placeholder             | Example Value             | Used In                        |
|-------------------------|---------------------------|--------------------------------|
| {{SOLUTION_NAME}}       | MyPlatform                | All scaffold templates         |
| {{ORG_NAME}}            | Acme Corp                 | Standards, README              |
| {{DOTNET_VERSION}}      | net9.0                    | Scaffold project files         |
| {{PRIMARY_CLOUD}}       | Azure                     | Observability, deploy stubs    |
| {{DB_PROVIDER}}         | SQL Server                | DAB config, connection stubs   |
| {{IDENTITY_PROVIDER}}   | Azure AD B2C              | Auth stubs, YARP config        |
| {{OBSERVABILITY_BACKEND}}| Grafana / Azure Monitor  | OTEL config stubs              |
| {{ENVIRONMENTS}}        | dev, test, prod           | appsettings templates          |
