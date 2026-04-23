# Skill: decision-recording

## Purpose
Create concise project decision records for durable project-level choices worth re-reading later.

This skill keeps frozen decisions out of `project/memory/*` and prevents ordinary task choices from becoming permanent records.

## When to use
Use this skill when a choice changes:
- project direction
- scope boundary
- phase boundary
- control model
- durable operating rule
- repeated decision pattern

Do not use it for ordinary implementation choices, temporary tradeoffs, or task-local reasoning.

## Inputs
- decision context
- options considered
- chosen option
- reasoning
- expected impact on current state, memory, facts, skills, or workflow rules
- revisit trigger, if known

## Outputs
- one concise record under `project/decisions/*`
- optional pointer from `project/CURRENT.md` when the decision is currently in force
- no duplicate rationale in `project/memory/*` or `ai/doc/facts/*`

## Workflow

### 1. Check whether it is really a project decision
Create a record only when the choice should remain recoverable after the current task is forgotten.
If the choice is task-local, leave it in the spec, handoff, or change summary.

### 2. Use the canonical location
Store decision records under `project/decisions/` using:

`DEC-YYYYMMDD-NNN-short-name.md`

Do not store frozen project decisions in `project/memory/*`, `ai/doc/facts/*`, or ad hoc reports.

### 3. Keep the record reviewable
Include:
- status
- context
- options considered
- chosen option
- reasoning
- consequences
- revisit trigger

Keep rationale concise and link to related specs or facts only when they help recovery.

### 4. Sync the control surface
If the decision is currently in force, update `project/CURRENT.md` with a short pointer.
Do not paste full rationale into `project/CURRENT.md`.

## Common failure modes
- creating decision records for routine implementation choices
- using `project/memory/*` as a decision ledger
- duplicating the same rationale across CURRENT, memory, facts, and the decision record
- omitting a revisit trigger for a decision that may expire
