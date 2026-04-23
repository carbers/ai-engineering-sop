# Skill: execute-from-spec

## Purpose
Execute implementation work from a task spec without drifting back to the parent plan or broad request.

This skill is the default bridge from an approved or ready task spec to implementation and validation.

## When to use
Use this skill when:
- a task spec exists and work is ready to move into implementation
- a prior plan or phase slice has already been narrowed into a spec
- a handoff requires the executor to preserve scope, validation, and write-back boundaries

Tiny tasks may still use the lightweight path only when `AGENTS.md` and `.cursor/rules/workflow.mdc` allow spec creation to be skipped.

## Inputs
- active task spec in `ai/doc/specs/*`
- repository rules and directly relevant context named by the spec
- required validation commands or review checks
- any current `project/CURRENT.md` context when the repository uses `project/*`

## Outputs
- the smallest coherent in-scope implementation
- updated spec status or checklist when the work materially moves
- explicit validation result
- bounded repair, rollback, `replan_required`, or `needs_decision` outcome when needed
- closeout/write-back decision after validation

## Workflow

### 1. Spec-binding gate
Before editing, reread the active spec sections that define the contract:
- `Goal`
- `In Scope`
- `Out of Scope`
- `Allowed Edits`
- `Disallowed Edits`
- `Affected Area`
- `Done When`
- `Validation`
- `Repair / Rollback`
- `Write-back Needed`

Use the spec as the execution source of truth.
Use the parent plan only to understand intent, not to expand the task.

### 2. Check for stop conditions
Stop before editing and return `needs_decision` or `replan_required` when:
- the required work no longer fits the spec boundary
- the allowed edit surface is too narrow or unclear for the required change
- the validation path is no longer meaningful
- the task would change project scope, phase scope, priority, policy, or dependency ordering
- the executor would need to invent a missing decision

Keep `needs_decision` and `replan_required` out of the spec `Status` field.
Record them as escalation outcomes in task-local notes or the handoff.

### 3. Implement narrowly
Make only the smallest coherent change that satisfies `Done When`.
Do not pull future-phase work, opportunistic cleanup, or unrelated refactors into the task.

When updating the spec checklist, keep items outcome-oriented.
Do not use the checklist as a running log, validation transcript, or project board.

### 4. Validate before done
Run or describe the required black-box checks.
Add white-box validation only when the spec's trigger says internal protection is needed.

Do not mark the task `done` until `Done When` is satisfied and required validation has passed.
If validation fails, repair only inside the declared repair budget and allowed edit scope.

### 5. Close out deliberately
After validation, use `ai/skill/session-closeout.md` when the repository uses `project/*` and the result may affect current state, memory, decisions, experiments, facts, or skills.
Prefer no write-back when nothing stable and reusable changed.

## Common failure modes
- implementing from the parent plan after a spec exists
- treating `Allowed Edits` as a suggestion instead of a boundary
- completing checklist items without validating `Done When`
- recording progress notes in the checklist
- repairing beyond the declared budget
- absorbing a needed replan into the current task
- updating multiple write-back layers with the same explanation
