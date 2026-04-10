# Example: Project Control Closeout Loop

> **This is an example spec** showing how a narrow task can update the minimal project control surface without turning it into a project board.
> It is not a real task in this repository.

## Metadata

### Source Plan / Request
Copied-project example request: show one complete loop from current project state to a task spec to a stable control-surface update.

### Status
`done`

### Related Specs
- `20260328-001-minimal-project-control-surface.md`

## Goal
Show how a team can start from `project/CURRENT.md`, optionally use `project/memory/*` for repeated project context, execute one narrow spec, and then update only the durable project-level control artifacts that changed.

## In Scope
- read `project/CURRENT.md` first to recover the active slice
- read `project/memory/README.md` next when repeated agreements or recurring patterns affect the slice
- implement one narrow reviewable task from a dated spec
- update `project/CURRENT.md` when the active slice changes
- update `project/memory/*` only when stable repeated project memory became clear
- add a decision record only if the task froze a project-level choice

## Out of Scope
- writing a work log into `project/CURRENT.md`
- seeding `project/memory/*` with made-up project memory before it exists
- copying task-local reasoning into facts
- creating a decision record for every implementation choice
- adding reports or archives

## Affected Area
- `project/CURRENT.md`
- optional `project/memory/*`
- the active task spec in `ai/doc/specs/*`
- optional `project/decisions/*`

## Task Checklist
- [x] recover the current state from `project/CURRENT.md`
- [x] check `project/memory/*` only when repeated project context is needed
- [x] execute one narrow task from a dated spec
- [x] update `project/CURRENT.md` only for durable state changes
- [x] update `project/memory/*` only for stable repeated memory
- [x] create a decision record only when a project-level choice was frozen

## Done When
A returning reader can follow the path `project/CURRENT.md` -> optional `project/memory/*` -> active task spec -> targeted control-surface update and see how the minimal control surface stays current without becoming a second execution system.

## Validation

### Black-box Checks
- confirm the example starts from `project/CURRENT.md` rather than a chat transcript or raw task list
- confirm `project/memory/*` is consulted only for repeated project context and updated only when durable memory emerged
- confirm the example keeps execution details in the spec rather than moving them into `project/*`
- confirm the example updates only durable control-surface artifacts after the slice completes

### White-box Needed
No

### White-box Trigger
This is a usage example.

### Internal Logic To Protect
None.

## Write-back Needed
Yes

If yes, what stable information should be written back, where does it belong, and which type best fits?
- `project/CURRENT.md` for active-slice and next-step changes
- `project/memory/*` with `project_memory` only when a repeated agreement, pattern, or reminder became stable
- `project/decisions/*` with `decision_rationale` only if the task froze a durable project-level choice

## Risks / Notes
- The main risk is treating `project/CURRENT.md` like a task log instead of a recovery artifact.
- copied projects may keep empty starter pages under `project/memory/*`, but those pages should not accumulate real entries until repeated project memory exists.
- If the example needs reports, archives, or experiment ledgers to make sense, the slice is no longer minimal.
