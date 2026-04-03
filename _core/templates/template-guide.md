<!-- Reference guide for workspace builders. Templates link here to stay terse. -->
# Template Guide

Quick reference for building and maintaining MWP workspaces.

---

## 1. Size Guardrails

| Template | Target | Hard Limit |
| -------- | ------ | ---------- |
| `workspace-claude-template.md` (CLAUDE.md) | ~800 tokens | 1 000 tokens |
| `workspace-context-template.md` (CONTEXT.md) | < 80 lines | 100 lines |
| `stage-context-template.md` (stage CONTEXT.md) | 25–80 lines | 100 lines |
| `questionnaire-template.md` | no guardrail | keep flat |

If guidance would push a template past its limit, put it here and add a one-line reference.

---

## 2. Do NOT Load Discipline

**Rule:** an agent loads only the files it is actively executing against.

**Why it matters:** the context window is working memory, not storage. Every extra file displaces reasoning capacity.

Common violations:

- Loading an upstream stage CONTEXT.md "for background" -- the stage's Inputs table already defines what it needs.
- Loading all shared/ reference files at workspace start -- load only what the current task requires.
- Loading a skill file that the current stage does not invoke.

**How to enforce it:**

- Every "Do NOT Load" cell in a What-to-Load table must state *why*, not just list files.
- Stage CONTEXT.md Inputs tables are the single source of truth for that stage's file set.
- If a builder is tempted to add a file to Inputs "just in case", remove it.

---

## 3. Custom Triggers

Root triggers (`setup`, `status`) are global. Add workspace-specific triggers only when they provide a meaningful shortcut -- skipping intake, activating a mode, or jumping mid-pipeline.

**Declaration location:** CLAUDE.md Triggers table (commented rows until confirmed) and CONTEXT.md Trigger Keywords table.

**Real patterns from mature workspaces:**

| Trigger | Pattern | When to use |
| ------- | ------- | ----------- |
| `ingest` | Accept a source artifact and run Stage 01 immediately | Input is already known; skip manual intake |
| `resolve` | Open Stage 03 with a named gap item pre-loaded | User wants to act on a specific gap without re-running earlier stages |
| `convert` | Jump to Stage 04 with a specific file as input | File conversion path where earlier analysis stages are irrelevant |
| `inventory` | Run Stage 01 in read-only / list mode, no output written | Exploration without committing to a full pipeline run |

**Declare in CLAUDE.md as a commented row first.** Uncomment once the trigger is wired to a stage CONTEXT.md step.

---

## 4. Content Boundaries

| Content type | Belongs in |
| ------------ | ---------- |
| Workspace routing table, trigger map | CLAUDE.md |
| Task-to-stage routing, shared resource map, workspace triggers | CONTEXT.md |
| Stage inputs, process steps, checkpoints, audit, outputs | Stage CONTEXT.md |
| Domain rules, quality standards, canonical defaults | `shared/` or `references/` (Layer 3) |
| Reusable procedural knowledge | `skills/[name]/SKILL.md` |
| Per-run project details (name, audience, scope) | Collected conversationally by entry stage |
| System-level config (tool paths, workspace options) | `setup/questionnaire.md` |

**Never put definitions, rules, or domain content in CLAUDE.md or CONTEXT.md.** Those files route; they do not teach.

---

## 5. Checkpoints vs Audits

| Mechanism | Purpose | When to include |
| --------- | ------- | --------------- |
| **Checkpoint** | Pause mid-process for human direction | Creative stages, branching decisions, content approval |
| **Audit** | Quality gate run by agent before saving output | Build stages, writing stages, any stage with correctness criteria |
| Neither | Stage runs straight through | Linear extraction, file conversion, deterministic rendering |

A stage can have both, one, or neither. See stage-context-template.md for the table shapes.

---

## 6. Skills Referencing

Skills are bundled domain-knowledge files stored in `skills/[name]/SKILL.md`. They are *loaded as inputs*, not executed as commands. To use a skill in a stage:

1. Add a row to the stage's Inputs table: `| Skill | skills/[name]/SKILL.md | Full file | [What domain knowledge it provides] |`
2. Reference it in the relevant Process step: "Apply the constraints from skills/[name]/SKILL.md §[Section]."
3. Only load a skill in stages that actually invoke its knowledge. Do not load skills workspace-wide.

Skills do not replace reference files. Use skills for procedural / voice / constraint knowledge; use `references/` for canonical standards and Layer-3 defaults.
