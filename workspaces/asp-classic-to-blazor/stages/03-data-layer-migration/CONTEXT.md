# Data Layer Migration

Replace ADO/ADODB and COM data access with EF Core, Dapper, or a hybrid approach behind a clean service layer.

## Inputs

| Source | File/Location | Section/Scope | Why |
|--------|--------------|---------------|-----|
| Previous stage | `../02-architecture-design/output/{{PROJECT_SLUG}}-architecture.md` | "Pattern Map" and "Project Structure" sections | Know the target data patterns and project layout |
| Inventory | `../01-inventory-assessment/output/{{PROJECT_SLUG}}-page-inventory.md` | Full file | Find all pages with database access |
| Pattern reference | `../../shared/asp-to-blazor-patterns.md` | ADO/ADODB rows | Map ADO patterns to EF Core/Dapper equivalents |

## Process

1. Read the architecture decisions and inventory from previous stages.
2. Extract every inline SQL statement and ADO connection string from the inventory.
3. Group SQL statements by table: identify all tables, their columns, and relationships.
4. Design entity models (C# classes) for each table, using {{DATABASE_TYPE}} conventions.
5. For {{DATA_ACCESS_APPROACH}}:
   - **EF Core**: Design DbContext with DbSet properties, configure relationships, plan migrations.
   - **Dapper**: Design repository interfaces with parameterized query methods.
   - **Hybrid**: EF Core for CRUD entities, Dapper repositories for complex queries and reports.
6. Design the service layer: one service per domain area, injected via DI.
7. Map each COM object (`Server.CreateObject`) to its .NET replacement service.
8. For each `On Error Resume Next` block around data access, design explicit error handling.
9. Produce the data migration plan.

## Audit

| Check | Pass Condition |
|-------|---------------|
| No inline SQL | Every SQL statement maps to a parameterized query or EF Core operation |
| All tables modeled | Every table referenced in the ASP source has a C# entity |
| COM objects replaced | Every `Server.CreateObject` has a named .NET service replacement |
| Connection strings secure | No hardcoded credentials; all connections use configuration or secrets |

## Outputs

| Artifact | Location | Format |
|----------|----------|--------|
| Data migration plan | `output/{{PROJECT_SLUG}}-data-plan.md` | Sections: Entity Models, DbContext/Repositories, Service Layer, COM Replacements, Error Handling |

<!-- Target: keep this file under 80 lines. -->
