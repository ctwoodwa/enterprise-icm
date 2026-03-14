# MWP Conventions

The rules for building and maintaining MWP workspaces. This is the canonical source.
Every workspace follows these patterns.

This file is a pointer to the upstream spec. For the full specification see:
https://github.com/RinDig/Interpreted-Context-Methdology/blob/main/_core/CONVENTIONS.md

---

## Five-Layer Routing Architecture

Agents read down the layers. They stop as soon as they have what they need.

```
Layer 0: CLAUDE.md           -> "Where am I?"           (always loaded, ~800 tokens)
Layer 1: CONTEXT.md          -> "Where do I go?"        (read on entry, ~300 tokens)
Layer 2: Stage CONTEXT.md    -> "What do I do?"         (read per-task, ~200-500 tokens)
Layer 3: Reference material  -> "What rules apply?"     (loaded selectively, varies)
Layer 4: Working artifacts   -> "What am I working with?" (loaded selectively, varies)
```

---

## Pattern 1: Stage Contracts

Every stage CONTEXT.md follows this three-section shape:

```markdown
## Inputs

| Source | File/Location | Section/Scope | Why |
|--------|--------------|---------------|-----|
| ...    | ...          | ...           | ... |

## Process

1. Step one
2. Step two
3. Step three

## Outputs

| Artifact | Location | Format |
|----------|----------|--------|
| ...      | ...      | ...    |
```

---

## Naming Conventions

- Folders and files: `lowercase-with-hyphens`
- Stage folders: zero-padded numbers prefix: `01-`, `02-`, `03-`
- Placeholders: `{{SCREAMING_SNAKE_CASE}}`
- Output artifacts: `[topic-slug]-[artifact-type].md`
- No spaces in file or folder names

---

## Quality Guardrails

- CONTEXT.md files: under 80 lines
- Reference files: under 200 lines (if longer, split into multiple files)
- Use plain English. Avoid jargon where possible.
- No em dashes anywhere in the repo
- Every folder that should persist but starts empty gets a `.gitkeep` file
- Every markdown file should be readable by someone who understands markdown and git basics
