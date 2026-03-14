# Stage 01 - Discovery and Context

Capture the problem domain, constraints, stakeholders, and environment landscape.

## Inputs

| Source           | File/Location                        | Section/Scope | Why                              |
|------------------|--------------------------------------|---------------|----------------------------------|
| Setup answers    | `../../_config/org-context.md`       | Full file     | Org, cloud, compliance baseline  |
| Setup answers    | `../../_config/tech-stack-defaults.md` | Full file   | Tech constraints and preferences |

## Process

1. Ask conversationally: solution name, business domain, key stakeholders, SLAs.
2. Identify existing systems this solution integrates with or replaces.
3. List environments (dev, test, prod) and any cloud/hosting constraints.
4. Identify compliance or security requirements (GDPR, SOC2, HIPAA, etc.).
5. Produce a concise problem brief and a context map of systems and teams.
6. Save outputs.

## Outputs

| Artifact         | Location                        | Format   |
|------------------|---------------------------------|----------|
| Problem brief    | `output/problem-brief.md`       | Markdown |
| Context map      | `output/context-map.md`         | Markdown |
| Constraint list  | `output/constraints.md`         | Markdown |
