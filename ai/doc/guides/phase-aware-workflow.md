# Phase-Aware Workflow

Use this guide when the default lightweight workflow needs a little more structure to support long-running or multi-handoff work.

This is an extension of the repository's existing SOP, not a replacement for it.
The core path remains `plan -> one or more narrow task specs -> implementation -> validation`.

## When To Use It

Use the phase-aware variant when one or more of these are true:

- the work spans multiple phases, milestones, or checkpoints
- a stable `project_target` and `current_target` must stay visible across handoffs
- the work benefits from separating `main_plan` and `sub_plan`
- task ordering, dependencies, or failure handling must be explicit
- multiple people or models will hand work across boundaries

Do not use this guide to force heavyweight planning onto every small task.
If the next slice is already narrow and reviewable, stay on the default workflow.

## Hierarchy Model

Use these terms consistently:

- `project_target`: the stable top-level objective the repository or initiative is serving
- `current_target`: the narrower objective being actively advanced now
- `phase`: the current stage of work with a clear purpose and gates
- `main_plan`: the plan for phase progression, milestones, dependencies, or checkpoints
- `sub_plan`: the plan for task decomposition, ordering, validation flow, or failure handling inside the current phase
- `task`: the smallest reviewable execution slice, usually carried by a task spec

Future runtime can consume this hierarchy as a static anchor for long-running work.
It does not tell runtime how to schedule or automate tasks; it only makes the parent-child relationships explicit.

## Phase Model

When a phase needs to be durable, define it with these fields:

- `purpose`
- `entry_criteria`
- `exit_criteria`
- `deliverables`
- `allowed_actions`
- `forbidden_actions`
- `gate_checks`

These fields help a future runtime understand what the phase is for, when it may start, and what should stop the work from drifting.
They do not require a separate phase file in every project.
Use the current plan to carry them when a durable phase artifact is needed.

## Main Plan vs Sub-Plan

Use `main_plan` when the plan primarily answers:

- what phase are we in
- what milestone or checkpoint comes next
- what dependencies shape progression
- what should happen before the next phase opens

Use `sub_plan` when the plan primarily answers:

- how this phase breaks into narrow tasks
- what order those tasks should run in
- how validation should sequence
- what failure handling or fallback path matters

One durable plan document may serve as either type.
Do not create both unless the distinction adds real clarity.

## Task Mapping

Task specs remain the default execution artifact.
For phase-aware work, each task should still stay narrow, but it should also map back to:

- `Parent Phase`
- `Parent Plan`

When failure handling or handoff risk is high, also make these explicit in the task spec:

- `Inputs`
- `Expected Outputs`
- `Allowed Edits`
- `Disallowed Edits`
- `Repair Budget`
- `Rollback Scope`
- `Escalation Condition`

Future runtime can use these fields to recover task context, boundaries, and safe fallback surfaces without needing the whole planning conversation.

## What Stays The Same

- plans may still remain temporary
- task specs remain the default durable execution artifact
- one spec should still produce one primary reviewable outcome
- black-box validation remains the default acceptance path
- facts remain selective write-back, not a task archive

The goal of this guide is to make longer work more legible, not to turn the repository into a project management system.
