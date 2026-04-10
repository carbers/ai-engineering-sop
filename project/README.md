# Project Control Surface

This directory is the minimal human-facing control surface for the repository.
This file is only a directory explainer, not a live source-of-truth document.

Use `project/*` to reduce context-recovery cost when returning to the project.
Use `ai/*` for AI-managed workflow assets such as specs, facts, templates, guides, and skills.

## Directory role

Start with `CURRENT.md` for live recovery context.
Use `memory/README.md` when you need the long-lived project memory that should keep shaping later work.
Use `DOC_MAP.md` when you need the reading order or document-role explanation.
Read the active task spec in `ai/doc/specs/*` for execution scope, validation, and allowed edits when implementation work is underway.
Use `decisions/` and `experiments/` only when the work produces a stable project-level decision or a reusable experiment record worth re-reading later.

## Boundary

This directory is not a project board, work log, or archive.
Keep it small.
If a detail is task-local, leave it in the active spec, an optional change summary if the project keeps one, or the normal handoff notes.
If a detail is stable project memory, route it to `memory/*`.
If a detail is stable and reusable across projects or future AI runs, route it to the appropriate fact or skill.

## Naming

- `CURRENT.md` is the recovery-first artifact.
- `memory/README.md` is the entry for project memory.
- `memory/working-agreements.md` is a recommended starter page for long-lived project-specific agreements and constraints.
- `memory/recurring-patterns.md` is a recommended starter page for recurring project patterns, repeated pitfalls, and stable local tactics.
- `DOC_MAP.md` explains document roles and reading order.
- `decisions/DEC-YYYYMMDD-NNN-short-name.md` holds frozen project-level decisions.
- `experiments/EXP-YYYYMMDD-NNN/README.md` holds readable experiment summaries when experiments become part of the workflow.
