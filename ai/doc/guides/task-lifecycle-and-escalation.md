# Task Lifecycle And Escalation

Use this guide when a task needs explicit lifecycle, repair, rollback, or escalation rules.

This guide keeps failure handling readable in SOP form.
It does not define an automated runtime state machine.

## Steady-State Status Values

Use only these values in a task spec's `Status` field for new or materially revised specs:

- `draft`: the task is defined, but implementation should not start yet
- `todo`: the task is defined and ready to start
- `in_progress`: implementation is underway
- `validating`: implementation is ready for required validation
- `repairing`: validation failed in a way that is still fixable inside the current task contract
- `rolled_back`: the task's in-scope changes were reverted inside the declared rollback scope
- `blocked`: progress is waiting on a prerequisite, dependency, or decision
- `done`: the task satisfies `Done When` and required validation has passed

These values describe the task's current state.
They do not replace planning or decision-making outside the task boundary.

## Escalation Outcomes

Use these as explicit outcomes when the task should stop instead of stretching itself:

- `replan_required`: the current spec or parent plan no longer provides a safe shape for the remaining work
- `needs_decision`: a scope, priority, dependency, or policy choice must be made above the executor level

These are escalation results, not steady-state progress values.
If a task stops for one of these reasons, keep `Status` on the last accurate steady-state value and record the escalation outcome in task-local notes or the handoff report.

## Repair vs Rollback vs Replan vs Escalate

- `repair`: stay inside the current task contract and fix a validation failure without broadening scope
- `rollback`: revert the task's in-scope changes inside the declared rollback scope so the repo returns to a known safe state
- `replan`: return to the planning layer because the current slice, ordering, or validation path is no longer the right one
- `escalate`: return to a planner, owner, or decision-maker because the task has crossed a decision boundary it should not resolve alone

## Default Transition Rules

Use these default interpretations:

- `draft -> todo` when the task is sufficiently clarified and ready to start
- `in_progress -> validating` when implementation is complete enough for required checks
- `validating -> done` when required checks pass
- `validating -> repairing` when checks fail but the fix is still inside the current task contract
- `repairing -> validating` after a bounded repair pass
- `repairing -> rolled_back` when the repair budget is exhausted and reverting is the safest move
- `blocked -> needs_decision` when the block is really a decision boundary rather than a missing input
- any active state -> `replan_required` when the spec boundary, sequencing, or assumptions are no longer valid

These transitions are guidance for human and AI operators.
They describe movement between steady-state status values and explicit stop outcomes; they are not pseudocode for a workflow engine.

## Common Triggers

Choose `repair` when:

- the failure is local to the current task
- the required fix stays inside allowed edits
- the task's goal, scope, and validation path still make sense

Choose `rollback` when:

- the attempted changes are unsafe to leave in place
- the task can be cleanly reverted inside its declared rollback scope
- continuing would create unclear or unreviewable state

Choose `replan_required` when:

- the task now spans multiple primary outcomes
- dependency ordering changed enough that the current slice is wrong
- assumptions encoded in the spec are no longer true
- the task needs a different validation or split strategy

Choose `needs_decision` when:

- an unresolved tradeoff changes scope or priority
- a dependency or external input must be chosen by someone above the executor role
- the work would otherwise force the executor to invent missing policy

## Practical Reminder

Keep lifecycle handling proportional.
Small tasks do not need elaborate failure notes.
Long-running, dependency-heavy, or multi-handoff tasks should make repair, rollback, replan, and escalation conditions explicit before execution starts.
