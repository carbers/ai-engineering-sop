# DOC MAP

This file explains which document answers which question.
It is intentionally short.

## Start order

1. `project/CURRENT.md` for current status, active slice, next actions, and recovery context.
2. `project/memory/README.md` for longer-lived project memory such as agreements and recurring patterns.
3. `README.md` for the repository purpose, adoption model, and top-level navigation.
4. `AGENTS.md` for repository-level AI operating rules.
5. `ai/README.md` for the AI workflow namespace map.

## Document roles

- `project/CURRENT.md`
  Current human-facing operating state.

- `project/memory/*`
  Longer-lived project memory that should stay easy to recover without becoming a task log.

- `project/decisions/*`
  Frozen project-level decisions worth re-reading later.

- `project/experiments/*`
  Readable summaries of experiments when experiments are part of the workflow.

- `ai/doc/specs/*`
  Narrow execution contracts between planning and implementation.

- `ai/doc/facts/*`
  Stable reusable context, not a current-status dashboard.

- `ai/skill/*`
  Repeatable workflows that reduce repeated reasoning.

## Priority rule

When documents appear to overlap, choose the layer that matches the question:

1. For current project state, recovery context, and next durable actions, prefer `project/CURRENT.md`.
2. For longer-lived project agreements, recurring patterns, and repeated reminders, prefer `project/memory/*`.
3. For task execution scope, validation, allowed edits, and done conditions, prefer the active task spec in `ai/doc/specs/*`.
4. For repository-wide operating rules and routing boundaries, prefer `README.md`, `AGENTS.md`, and `ai/README.md`.
5. For stable reusable AI-oriented context, prefer `ai/doc/facts/*`.
6. For task-local delivery detail, prefer an optional change summary if the project keeps one; otherwise prefer handoff notes.
