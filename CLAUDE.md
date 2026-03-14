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
└── workspaces/
    └── enterprise-software-dev/       (enterprise .NET platform workspace)
```

## Routing

| You want to...                              | Go to                                                        |
|---------------------------------------------|--------------------------------------------------------------|
| Design an enterprise software platform      | `workspaces/enterprise-software-dev/CLAUDE.md`               |
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
