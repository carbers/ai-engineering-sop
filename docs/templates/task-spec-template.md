# Task SPEC Template

Keep this document narrow. Reference the plan when needed instead of restating it.
Store task specs in `docs/specs/` and name them `YYYYMMDD-NNN-task-slug.md`.

## Metadata

### Source Plan / Request
Which plan, phase slice, or directly scoped task request does this spec narrow?

### Status
Choose one:
- `draft`: the spec exists, but implementation should not start yet
- `in-progress`: implementation for this spec has started
- `blocked`: progress is waiting on a prerequisite, dependency, or decision
- `done`: `Done When` is satisfied and required validation has passed

### Related Specs
Optional. Link sibling, prerequisite, or follow-up specs when that helps navigation.

## Goal
What should this task accomplish?

## In Scope
What is included in this task?

## Out of Scope
What is explicitly excluded from this task?

## Affected Area
Which files, modules, or subsystems should be touched?

## Task Checklist
Use a short Markdown checkbox list. Keep it narrow, usually 3-7 items.
Checklist completion does not make the spec `done` by itself. Required validation must also pass.

- [ ] Example outcome-oriented task
- [ ] Example outcome-oriented task

## Done When
What reviewable outcome must be true when this task is complete?

## Validation

### Black-box Checks
How will externally visible behavior or acceptance be verified?

### White-box Needed
Yes / No

### White-box Trigger
Why is white-box validation needed or not needed?

### Internal Logic To Protect
If yes, which branch, state, contract, or regression path matters most?

## Write-back Needed
Yes / No

If yes, what stable information should be written back, and where does it belong?

## Risks / Notes
What should reviewers or implementers watch for?
If status is `blocked`, record the blocking reason here.
