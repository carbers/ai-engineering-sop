# Phase-Aware Canonical Example

Use this guide when you want one compact, copyable example of the long-task path without turning the repository into a project board.

This example is intentionally small.
It shows the full chain:

`project_target -> current_target -> phase -> main_plan -> sub_plan -> task spec -> validation -> write-back`

The scenario is a productized adoption pass for a lightweight SOP starter.
The work is long enough to need explicit hierarchy and handoff boundaries, but still small enough to copy into a real project.

## Example Anchor

### Project Target
Make the SOP starter easy to adopt in real projects without changing its lightweight workflow model.

### Current Target
Improve first-use adoption so new users can tell where to start, when to stay on the default path, and when to use the phase-aware variant.

### Current Phase
Phase 1 - adoption clarity pass for copied-project use.

## Example Main Plan

Use a `main_plan` when you need the phase progression and checkpoints to stay visible:

For a copyable artifact, see `ai/doc/guides/phase-aware-example-main-plan.md`.
That example artifact shows:
- the stable `project_target`, `current_target`, and current `phase`
- the phase-level purpose, gates, and constraints
- the checkpoint-level breakdown for the current adoption phase
- the first slice that should narrow into a task spec

## Example Sub-Plan

Use a `sub_plan` only when the current phase needs explicit task ordering or failure handling:

For a copyable artifact, see `ai/doc/guides/phase-aware-example-sub-plan.md`.
That example artifact shows:
- how the current phase narrows into ordered task slices
- how the `sub_plan` stays attached to the parent `main_plan`
- how sequencing stays explicit without turning into a project board
- which slice should be executed first as a narrow task spec

## Example Task Spec

The task spec remains the default execution artifact.
For this example chain, see `ai/doc/specs/20260103-001-example-adoption-entrypoint-slice.md`.

That example spec shows:
- parent mapping back to the current phase and sub-plan
- explicit allowed and disallowed edits
- black-box validation
- optional repair, rollback, and escalation boundaries
- selective write-back instead of task-history sprawl

## Validation Closure

The long-task path still closes the same way as the default path:
- complete one narrow spec
- run the required validation named in the spec
- mark the task `done` only after validation passes

The extra hierarchy does not replace validation.
It only keeps the parent context and failure boundaries visible while the work is underway.

## Write-Back Closure

Write back only what became stable and reusable.
In this example, the stable reusable outcome is the long-task example pattern itself, so it is appropriate to update `ai/doc/facts/golden-cases.md`.

Do not write back:
- temporary execution chatter
- every checkpoint note
- task-local repair attempts with no reuse value

## How To Copy This Pattern

1. Keep your real `project_target`, `current_target`, and current `phase` visible.
2. Persist a `main_plan` only if the phase progression is worth re-reading or handing off.
3. Add a `sub_plan` only if task ordering, validation flow, or failure handling needs more structure.
4. Derive one narrow task spec at a time.
5. Validate explicitly and write back only stable reusable context.

If the next slice is already narrow and reviewable, skip the extra hierarchy and stay on the default lightweight path.
