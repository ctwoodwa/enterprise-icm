# Enterprise ICM

An ICM (Interpreted Context Methodology) workspace for designing and scaffolding enterprise-grade
.NET solutions built on Aspire, Blazor, YARP, Data API Builder, Scalar, GraphQL, and OpenTelemetry.

## What This Is

This repo is a design factory, not a code repo. It uses the Model Workspace Protocol (MWP)
five-layer architecture to help a senior developer produce consistent architecture decisions,
coding standards, service specs, and project scaffolds across multiple projects.

You run this workspace with Claude Code (personal) or GitHub Copilot (work).
The outputs feed directly into your actual .NET solution repos.

## Quick Start

1. Clone this repo to D:\\Projects\\enterprise-icm
2. Open in Claude Code
3. Type: setup
4. Answer the questionnaire once to configure the workspace for your org and stack
5. For each new project, navigate to the workspace and walk stages 01 through 05

## Workspace Structure

| Folder | Purpose |
|---|---|
| _core/ | MWP conventions and templates (read-only reference) |
| workspaces/enterprise-software-dev/ | Main workspace for .NET enterprise projects |
| workspaces/enterprise-software-dev/_config/ | Your org and stack config, filled once at setup |
| workspaces/enterprise-software-dev/shared/ | Cross-cutting rules: observability, security, API visibility |
| workspaces/enterprise-software-dev/stages/ | Five pipeline stages, each producing output artifacts |
| workspaces/enterprise-software-dev/setup/ | Onboarding questionnaire |

## The Five Stages

| Stage | Name | Produces |
|---|---|---|
| 01 | Discovery and Context | Problem brief, context map, constraints |
| 02 | Architecture and Patterns | System architecture, ADRs, service boundary map |
| 03 | Standards and Practices | Coding standards, 12-factor mapping, KISS rules, testing strategy |
| 04 | Service and App Specs | Blazor, YARP, DAB, Scalar, GraphQL Playground, OTEL specs |
| 05 | Scaffolds and Checklists | Project scaffolds, config templates, checklists, copilot-instructions.md |

## Multi-Project Usage

Use named project slugs in output filenames (e.g. myproject-problem-brief.md).
This keeps all project runs in git history without clearing outputs between runs.

## AI Tool Support

- Personal (Claude Code): full pipeline design and scaffold generation
- Work (VS Code + GitHub Copilot): use the generated .github/copilot-instructions.md
- Work (JetBrains Rider + Copilot): same copilot-instructions.md, loaded automatically

See workspaces/enterprise-software-dev/shared/copilot-integration.md for setup details.