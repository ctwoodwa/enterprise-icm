# Enterprise ICM

ICM workspace for designing and scaffolding enterprise-grade software, services, and utilities.
Built on the Model Workspace Protocol (MWP) five-layer architecture.

## Folder Map

```
enterprise-icm/
├── CLAUDE.md                          (you are here)
├── README.md                          (project overview)
├── LICENSE
├── _core/                             (shared conventions and templates)
│   ├── CONVENTIONS.md                 (source of truth for all patterns)
│   ├── placeholder-syntax.md          (how {{VARIABLES}} work)
│   └── templates/                     (blank starting points for new workspaces)
├── docs/
│   └── icm-defaults/                 (canonical Layer-3 enterprise standards library)
└── workspaces/
    ├── enterprise-software-dev/       (greenfield enterprise .NET platform workspace)
    ├── enterprise-standards-upgrade/  (brownfield standards analysis and upgrade workspace)
    ├── docs-generator/                (generate and update docs for any existing project)
    ├── data-layer-migration/          (replace in-memory store with SQL Server + DAB + EF Core)
    ├── ci-cd-pipeline/                (design and scaffold CI/CD pipelines for .NET solutions)
    ├── test-coverage-expansion/       (audit, strategy, and scaffolds for test coverage)
    └── enterprise-feature-change/     (implement a Jira ticket or user story end-to-end)
    ├── enterprise-feature-change/     (brownfield feature change workflow)
    ├── enterprise-standards-upgrade/  (brownfield standards analysis and upgrade workspace)
    ├── enterprise-api-change/         (brownfield API/event change under governance)
    ├── enterprise-observability-enhancement/ (brownfield observability improvement)
    ├── enterprise-test-coverage/      (brownfield test coverage improvement)
    └── enterprise-quality-control/    (quality gates, checklists, and test coverage toolkit)
```

## Routing

| You want to...                                   | Go to                                                       |
| ------------------------------------------------ | ----------------------------------------------------------- |
| Design an enterprise software platform           | `workspaces/enterprise-software-dev/CLAUDE.md`              |
| Add a feature to an existing project             | `workspaces/enterprise-feature-change/CONTEXT.md`           |
| Upgrade an existing repo to enterprise standards | `workspaces/enterprise-standards-upgrade/CLAUDE.md`         |
| Change APIs or events under governance           | `workspaces/enterprise-api-change/CLAUDE.md`                |
| Improve observability for a service              | `workspaces/enterprise-observability-enhancement/CLAUDE.md` |
| Increase test coverage for a service             | `workspaces/enterprise-test-coverage/CLAUDE.md`             |
| Use quality gates, checklists, and TDD guides    | `workspaces/enterprise-quality-control/CLAUDE.md`           |
| Generate or update docs for an existing project  | `workspaces/docs-generator/CLAUDE.md`                       |
| Migrate from in-memory to SQL Server + DAB       | `workspaces/data-layer-migration/CLAUDE.md`                 |
| Design and scaffold a CI/CD pipeline             | `workspaces/ci-cd-pipeline/CLAUDE.md`                       |
| Expand test coverage for an existing project     | `workspaces/test-coverage-expansion/CLAUDE.md`              |
| Implement a Jira ticket or user story            | `workspaces/enterprise-feature-change/CLAUDE.md`            |
| Read the full MWP specification                  | `_core/CONVENTIONS.md`                                      |
| Understand the placeholder system                | `_core/placeholder-syntax.md`                               |
| Use a template for a new workspace               | `_core/templates/`                                          |

## Triggers

| Keyword  | Action                                             |
| -------- | -------------------------------------------------- |
| `setup`  | Run onboarding in whatever workspace you are in    |
| `status` | Show pipeline completion for the current workspace |

## How It Works

Each workspace is self-contained with its own CLAUDE.md. Navigate into a workspace
folder and that workspace's CLAUDE.md takes over. You do not need to read this root
file once you are inside a workspace.
