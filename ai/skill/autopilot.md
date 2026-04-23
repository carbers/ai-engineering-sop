# Skill: autopilot

## Purpose
Run a bounded autonomous execution loop without bypassing the repository's spec-first workflow.

Autopilot is an execution discipline, not a separate planning system or runtime state machine.

## When to use
Use this skill when the user asks the agent to continue through a reviewable slice with minimal interruption and the active task has a clear spec or is trivially narrow.

Do not use autopilot to start broad work directly from a plan when a spec is required.

## Inputs
- active task spec, unless the task is trivially narrow
- repository rules
- directly relevant source files or docs named by the spec
- validation commands or review checks
- current repair budget and escalation conditions

## Outputs
- bounded implementation or documentation change
- explicit validation result
- repair, rollback, `replan_required`, or `needs_decision` outcome when needed
- closeout/write-back decision

## Phase Gates

### Phase 0: Entry gate
Confirm the task has an active spec or qualifies for the tiny-task exception.
If a plan or phase slice exists but no spec exists, use `ai/skill/plan-to-spec.md` first.

### Phase 1: Spec-binding gate
Use `ai/skill/execute-from-spec.md` to reread the active execution contract before editing.

### Phase 2: Context gate
Read only the files needed for the active spec.
Do not broaden context just because related files exist.

### Phase 3: Implementation gate
Make the smallest coherent in-scope change.
Do not change frozen bytes, generated outputs, or dual-track artifacts unless the spec explicitly allows it.

### Phase 4: Validation gate
Run or document the required checks.
Black-box validation is the default; white-box validation is conditional.

### Phase 5: Repair gate
Repair only inside the declared budget and allowed edit scope.
If repair would exceed the contract, use `ai/skill/replan-or-escalate.md`.

### Phase 6: Closeout gate
Use `ai/skill/session-closeout.md` when current state, memory, decisions, experiments, facts, or skills may need a durable update.

## Sub-Agent Constraint
Use sub-agents only when the environment and user request allow delegation.
Delegated work must have a narrow, disjoint responsibility and must not redefine the active spec boundary.
The main executor remains responsible for integrating results against the active spec.

## Context Compaction Constraint
After context compaction or session resume, recover from the active spec and current control surface before continuing.
Do not continue from memory of prior conversation alone.

## Source Reading Constraint
Do not edit source files or workflow assets that have not been read in the current execution context, unless the change is a purely mechanical update whose input is already explicit.

## Common failure modes
- using autopilot as permission to skip spec creation
- continuing after validation changes the task boundary
- repairing without checking the repair budget
- delegating work that changes the spec boundary
- resuming after compaction without rereading the active source of truth
