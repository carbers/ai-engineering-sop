# Task SPEC Template

Keep this document narrow. Reference the plan when needed instead of restating it.
Store task specs in `ai/doc/specs/` and name them `YYYYMMDD-NNN-task-slug.md`.
For trivially narrow work, phase-aware fields may stay short or be omitted when the parent context is already obvious.

## Metadata

### Source Plan / Request
Which plan, phase slice, or directly scoped task request does this spec narrow?

### Parent Phase
Optional for phase-aware or long-running work.
Which current phase does this task belong to?

### Parent Plan
Optional for phase-aware or long-running work.
Which `main_plan` or `sub_plan` is this task executing?

### Status
Choose one steady-state status:
- `draft`: the spec exists, but it is not ready for implementation yet
- `todo`: the spec is ready to start, but implementation has not begun
- `in_progress`: implementation for this spec has started
- `validating`: implementation is complete enough for required validation to run
- `repairing`: validation exposed a fixable gap and the task is still inside its current repair budget
- `rolled_back`: the task's in-scope changes were reverted inside the declared rollback scope
- `blocked`: progress is waiting on a prerequisite, dependency, or decision
- `done`: `Done When` is satisfied and required validation has passed

Do not put `needs_decision` or `replan_required` in `Status`.
If the task stops for escalation, keep `Status` on the last accurate steady-state value and record the escalation outcome under `Risks / Notes` or in the handoff report.

### Related Specs
Optional. Link sibling, prerequisite, or follow-up specs when that helps navigation.

### Release Sensitivity
Optional. Use only when this task may need special attention in a real product release batch.
If omitted, treat it as `normal`.
Choose one:
- `normal`
- `release_sensitive`

If `release_sensitive`, briefly name why.
Typical reasons:
- data migration
- config or feature-flag dependency
- public API or compatibility impact
- auth, permissions, billing, or compliance impact
- rollback difficulty
- performance or reliability sensitivity

## Goal
What should this task accomplish?

## Phase-Aware Contract
Use the fields below when the task needs explicit parent mapping, handoff boundaries, or failure handling.
For small tasks, keep them terse or remove sections that add no clarity.

## Inputs
Optional for phase-aware, dependency-heavy, or multi-handoff work.
What existing artifacts, dependencies, assumptions, or repo context must already be available?

## Expected Outputs
Optional for phase-aware, dependency-heavy, or multi-handoff work.
What concrete deliverables should this task produce?

## In Scope
What is included in this task?

## Out of Scope
What is explicitly excluded from this task?

## Allowed Edits
Optional for phase-aware, dependency-heavy, or multi-handoff work.
Which files, modules, docs, or workflow assets may be edited in this task?

## Disallowed Edits
Optional for phase-aware, dependency-heavy, or multi-handoff work.
Which areas must remain untouched unless the task is explicitly replanned?

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

## Repair / Rollback
Use this section when the task needs explicit repair, rollback, or escalation boundaries.
For small low-risk tasks, keep it short or omit it.

### Repair Budget
How much repair is allowed after validation fails before the task must stop for rollback, replan, or escalation?

### Rollback Scope
Which in-scope changes may be reverted if repair is exhausted or the task must be abandoned?

### Escalation Condition
When should this task stop and return as `needs_decision` or `replan_required` instead of continuing?

## Write-back Needed
Yes / No

If yes, what stable information should be written back, where does it belong, and which type best fits?
After required validation and before reporting `done`, make an explicit closeout decision.
If the repository uses `project/*`, use `ai/skill/session-closeout.md` to decide whether `project/CURRENT.md`, `project/DOC_MAP.md`, `project/decisions/*`, `project/experiments/*`, facts, or skills need updates.
Suggested labels:
- `facts_update`
- `skill_promotion`
- `decision_rationale`
- `phase_lesson`
- `task_pattern`
- `anti_pattern`

## Risks / Notes
What should reviewers or implementers watch for?
If status is `blocked`, record the blocking reason here.
