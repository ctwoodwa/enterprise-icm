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
    ├── enterprise-feature-change/     (brownfield feature change workflow)
    ├── enterprise-standards-upgrade/  (brownfield standards analysis and upgrade workspace)
    ├── enterprise-api-change/         (brownfield API/event change under governance)
    ├── enterprise-observability-enhancement/ (brownfield observability improvement)
    └── enterprise-test-coverage/      (brownfield test coverage improvement)
```

## Routing

| You want to...                              | Go to                                                        |
|---------------------------------------------|--------------------------------------------------------------|
| Design an enterprise software platform      | `workspaces/enterprise-software-dev/CLAUDE.md`               |
| Add a feature to an existing project        | `workspaces/enterprise-feature-change/CONTEXT.md`            |
| Upgrade an existing repo to enterprise standards | `workspaces/enterprise-standards-upgrade/CLAUDE.md`     |
| Change APIs or events under governance      | `workspaces/enterprise-api-change/CLAUDE.md`                 |
| Improve observability for a service         | `workspaces/enterprise-observability-enhancement/CLAUDE.md`  |
| Increase test coverage for a service        | `workspaces/enterprise-test-coverage/CLAUDE.md`              |
| Read the full MWP specification             | `_core/CONVENTIONS.md`                                       |
| Understand the placeholder system           | `_core/placeholder-syntax.md`                                |
| Use a template for a new workspace          | `_core/templates/`                                           |

## Triggers

| Keyword  | Action                                                  |
|----------|---------------------------------------------------------|
| `setup`  | Run onboarding in whatever workspace you are in         |
| `status` | Show pipeline completion for the current workspace      |

## How It Works

Each workspace is self-contained with its own CLAUDE.md. Navigate into a workspace
folder and that workspace's CLAUDE.md takes over. You do not need to read this root
file once you are inside a workspace.
