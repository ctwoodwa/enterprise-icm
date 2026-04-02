<!-- Target: under 80 lines. -->
# [Workspace Name]

[One sentence: what this workspace covers.]
<!-- No content here. Routing only. Rules and definitions belong in
     reference files. See Pattern 6. -->

## Task Routing

| Task Type | Go To | Description |
| --------- | ----- | ----------- |
| [Task 1] | `stages/01-[name]/CONTEXT.md` | [What this stage does] |
| [Task 2] | `stages/02-[name]/CONTEXT.md` | [What this stage does] |
| [Task 3] | `stages/03-[name]/CONTEXT.md` | [What this stage does] |

## Shared Resources

<!-- Pattern 4 (Selective Section Routing): "Section to Load" matches the
     Inputs table shape. Specify exactly which section Claude should read. -->

| Resource | Location | Section to Load | Why |
| -------- | -------- | --------------- | --- |
| [Context folder] | `[folder]/CONTEXT.md` | Full file | [What it routes to] |
| [Shared files] | `shared/` | Full file | [What cross-stage files live here] |
| [Skill name] | `skills/[name]/SKILL.md` | Full file | [What domain knowledge this skill provides] |

## Trigger Keywords

<!-- Optional. Add workspace-specific triggers here. Root triggers (setup, status)
     are inherited from the root CLAUDE.md. Only add triggers unique to this workspace. -->

| Keyword | Action |
| ------- | ------ |
| `{{TRIGGER_KEYWORD}}` | [What it does] |
