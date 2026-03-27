# Example: Phase-Aware Lifecycle Guide Slice

> **This is an example spec** demonstrating thin use of the phase-aware task fields.
> It is not a real task in this repository.
> Use it when you want to see how the new fields can stay short while still giving future runtime stable structure.

## Metadata

### Source Plan / Request
`main_plan`: thin SOP upgrade so future runtime can consume phase-aware planning and task contracts.

### Parent Phase
Phase 1 - define the static phase-aware protocol surface without introducing runtime implementation.

### Parent Plan
`sub_plan`: document the task lifecycle and task-boundary contract for long-running work.

### Status
`todo`

### Related Specs
- `20260326-003-split-entrypoints-for-adoption.md` (repository guidance precedent)

## Goal
Add one narrow documentation slice that makes task lifecycle and escalation rules reusable without changing the repository's lightweight default workflow.

## Inputs
- the approved phase-aware hierarchy model
- the current task spec template
- the current write-back and validation rules

## Expected Outputs
- one lifecycle guide under `ai/doc/guides/`
- one task-spec-template update that points to repair, rollback, and escalation boundaries
- no new runtime directory, service, or automation layer

## In Scope
- define task lifecycle terms for phase-aware work
- define when `repair`, `rollback`, `replan_required`, and `needs_decision` should be used
- align the task spec template with those terms

## Out of Scope
- implementing a runtime state machine
- adding task orchestration tooling
- rewriting the default small-task workflow

## Allowed Edits
- `ai/doc/guides/task-lifecycle-and-escalation.md`
- `ai/doc/templates/task-spec-template.md`
- `ai/doc/specs/README.md`

## Disallowed Edits
- root entrypoint model in `README.md`
- canonical namespace roots under `ai/`
- speculative runtime or platform design files

## Affected Area
- `ai/doc/guides/task-lifecycle-and-escalation.md`
- `ai/doc/templates/task-spec-template.md`
- `ai/doc/specs/README.md`

## Task Checklist
- [ ] add a short lifecycle guide for phase-aware tasks
- [ ] add repair / rollback / escalation fields to the task spec template
- [ ] confirm the resulting guidance still preserves the default spec-first path

## Done When
Readers can tell when a task should keep repairing versus stop for rollback, replan, or escalation, and they can see the corresponding contract fields in the task spec template without reading a long planning document.

## Validation

### Black-box Checks
- read the lifecycle guide and confirm each term has a plain-language meaning
- read the task spec template and confirm the new fields map to the guide
- confirm the docs still describe the default path as `plan -> task spec -> implementation -> validation`

### White-box Needed
No

### White-box Trigger
This slice is a documentation and template alignment task with direct artifact review rather than fragile internal logic.

### Internal Logic To Protect
None.

## Repair / Rollback

### Repair Budget
One bounded repair pass for naming mismatches, missing links, or unclear lifecycle wording found during review.

### Rollback Scope
Revert the new lifecycle guide and the matching lifecycle-specific wording in the task spec template if the slice proves confusing or too heavy.

### Escalation Condition
Stop as `needs_decision` or `replan_required` if the slice would require changing repository entrypoints, redefining the default small-task workflow, or introducing runtime-specific implementation guidance.

## Write-back Needed
Yes

If yes, what stable information should be written back, where does it belong, and which type best fits?
If this slice establishes a reusable boundary rule for future phase-aware work, record it as a `phase_lesson` or `facts_update` in `ai/doc/facts/project-scope.md`. Otherwise keep delivery notes local.

## Risks / Notes
- The main risk is making the phase-aware example look mandatory for every small task.
- Keep each new field short and decision-oriented rather than turning the spec into a project tracker.
