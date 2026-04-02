<!-- Target: ~800 tokens. Trim if longer. -->
# [Workspace Name]

[One sentence: what this workspace does.]

## Folder Map

```
[workspace-name]/
├── CLAUDE.md          (you are here)
├── CONTEXT.md         (start here for task routing)
├── setup/             (onboarding questionnaire)
├── skills/            (bundled Claude skills for domain knowledge)
├── [context-folder]/  (shared context files)
├── stages/
│   ├── 01-[name]/     ([brief description])
│   ├── 02-[name]/     ([brief description])
│   └── 03-[name]/     ([brief description])
└── shared/            (cross-stage reference files)
```

## Triggers

| Keyword | Action |
|---------|--------|
| `setup` | Run onboarding questionnaire |
| `status` | Show pipeline completion for all stages |

## Routing

| Task | Go To |
|------|-------|
| [Task type 1] | `stages/01-[name]/CONTEXT.md` |
| [Task type 2] | `stages/02-[name]/CONTEXT.md` |
| [Task type 3] | `stages/03-[name]/CONTEXT.md` |
| Run onboarding / check tool prerequisites | `setup/questionnaire.md` |

<!-- Build note: before adding cross-references, verify no circular
     dependencies. Target files must not reference back. See Pattern 3. -->
<!-- Build note: creative/build stages need Checkpoints and Audit sections.
     Linear/extraction stages can omit them. See Patterns 11 and 12. -->

## What to Load

<!-- Map each task to its minimal file set. Loading more files dilutes quality.
     The context window is working memory, not storage. -->
<!-- Every "Do NOT Load" entry must explain WHY those files are excluded,
     not just list them. This prevents accidental loading. See Pattern 1. -->

| Task | Load These | Do NOT Load |
|------|-----------|-------------|
| [Task 1] | [minimal file list] | [what to skip and why] |
| [Task 2] | [minimal file list] | [what to skip and why] |
<!-- example: | Build stage | stages/03-build/CONTEXT.md, skills/[name]/SKILL.md | Stages 01-02, unrelated skills | -->

## Stage Handoffs

Each stage writes its output to its own `output/` folder. The next stage reads from there. If you edit an output file, the next stage picks up your edits.
