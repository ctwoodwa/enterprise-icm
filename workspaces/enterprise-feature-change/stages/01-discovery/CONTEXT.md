# Stage 01 - Discovery and Context

Understand current behavior, constraints, and likely impact areas before designing changes.

## Inputs

| Source | File/Location | Section/Scope | Why |
|---|---|---|---|
| Feature request | Existing project ticket system | Ticket, acceptance criteria, linked docs | Establish problem and expected outcome |
| Canonical context | ../../../../docs/icm-defaults/010-context/context-and-principles.md | Full file | Align discovery with ICM foundations |
| Relevant architecture views | ../../../../docs/icm-defaults/030-architecture/*.md | Logical, data, integration, signal/reactive as needed | Scope impacted components |
| Existing project docs | Target project README, ADRs, and feature notes | Current behavior and constraints | Ground discovery in real implementation |

## Process

1. Read the feature ticket and summarize expected behavior.
2. List current behavior that will be affected.
3. Identify impacted domains, services, interfaces, events, and UI surfaces.
4. Flag assumptions, unknowns, and explicit constraints.
5. Save outputs.

## Outputs

| Artifact | Location | Format |
|---|---|---|
| Discovery summary | output/feature-[slug]-discovery.md | Markdown |
