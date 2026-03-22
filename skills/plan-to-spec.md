# Skill: plan-to-spec

## Purpose
Convert a plan or phase slice into one or more narrow, reviewable task specs.

This skill is the default bridge between planning and implementation.
It keeps implementers from working directly from a broad plan.

## When to use
Use this skill by default when:
- a plan or phase slice is already available
- work is about to move into implementation
- task boundaries, validation, or write-back needs are still implicit

See `AGENTS.md` § Working model for when spec creation may be skipped.

## Inputs
- current plan or phase slice
- current phase context
- known constraints
- known risks
- known reusable facts or golden cases

## Outputs
- one or more task specs in `docs/specs/`
- clear in-scope / out-of-scope boundaries
- affected area, status, short checklist, and reviewable done condition
- black-box validation guidance
- white-box trigger judgment
- write-back guidance

Name and store specs using the conventions in `docs/specs/README.md`.

## Workflow

### 1. Start from the current slice
Turn broad plan statements into the next smallest reviewable slice or slices that still move the phase forward.

### 2. One spec, one primary outcome
A spec should produce one primary reviewable outcome.
If a candidate spec mixes design, implementation, migration, cleanup, or unrelated follow-up work, split it.

### 3. Split before the spec becomes large
Split when the work would contain:
- multiple primary outcomes
- independently reviewable slices
- distinct validation paths
- a checklist that can no longer stay short

### 4. Make the execution contract explicit
Each task spec should say what is in scope, what is out of scope, what area is affected, and what must be true when the task is done.

### 5. Add lightweight execution state
Each task spec should have a status (`draft`, `in-progress`, `blocked`, `done`) and a short Markdown checklist.
Checklist completion alone does not make the spec `done`; required validation must also pass.

### 6. Make validation explicit
Every task spec should define how completion is verified, with black-box checks as the default acceptance path.

### 7. Judge white-box need
Ask whether black-box checks are enough.
Trigger white-box guidance when internal logic is branch-heavy, stateful, regression-sensitive, contract-sensitive, or tied to a deterministic bugfix path.

### 8. Decide write-back deliberately
Only mark write-back as needed when the task is expected to clarify stable, reusable context.
If write-back is needed, name the destination.

## Common failure modes
- turning the plan directly into one giant spec
- copying plan text into the task spec without narrowing it
- keeping multiple primary outcomes in the same spec
- leaving validation vague
- omitting out-of-scope boundaries
- leaving the affected area or done condition implicit
- leaving status implicit or never updating it
- using the checklist as a work log or full project board
- writing back too much task-local detail
