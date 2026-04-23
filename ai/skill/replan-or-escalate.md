# Skill: replan-or-escalate

## Purpose
Decide whether a task can continue, should repair, should roll back, needs a replan, or needs an owner decision.

This skill keeps scope expansion and missing policy choices out of task execution.

## When to use
Use this skill when:
- validation fails and the fix may exceed the current task contract
- the implementation path no longer matches the active spec
- scope, phase, priority, dependency, or policy boundaries become unclear
- a task may need to stop as `replan_required` or `needs_decision`

## Inputs
- active task spec
- current failure, ambiguity, or changed assumption
- declared `In Scope`, `Out of Scope`, `Allowed Edits`, `Disallowed Edits`
- declared `Repair Budget`, `Rollback Scope`, and `Escalation Condition`
- relevant parent phase or plan only when it clarifies the boundary

## Outputs
- one of: continue, repair, rollback, `replan_required`, or `needs_decision`
- short reason tied to the spec boundary
- handoff note or decision request when execution must stop

## Workflow

### 1. Classify the issue
Use `repair` when the fix stays inside the current task contract and repair budget.
Use `rollback` when the attempted in-scope changes are unsafe to leave in place and can be cleanly reverted.
Use `replan_required` when the task boundary, sequencing, assumptions, or validation path no longer fits.
Use `needs_decision` when a scope, priority, dependency, or policy choice belongs above the executor role.

### 2. Preserve status semantics
Do not put `replan_required` or `needs_decision` in the spec `Status`.
Keep `Status` on the last accurate steady-state value and record the escalation outcome in task-local notes or the handoff.

### 3. Avoid silent scope expansion
Do not solve a replan or decision problem by widening `In Scope`, `Allowed Edits`, or `Done When` during execution.
If those boundaries need to change, return to the planning or decision layer first.

### 4. Keep the handoff short
A useful stop note names:
- what changed or failed
- which spec boundary is affected
- why repair is insufficient
- what decision or replan is needed next

## Common failure modes
- calling a decision boundary a blocker without naming the needed decision
- continuing repair after the repair budget is exhausted
- changing the spec boundary to fit the attempted implementation
- treating `replan_required` as a normal progress status
- escalating without citing the violated or unclear contract section
