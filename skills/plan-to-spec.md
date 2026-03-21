# Skill: plan-to-spec

## Purpose
Convert a plan into one or more narrow, reviewable task specs.

This skill exists to bridge planning and execution without forcing the implementer to work directly from a broad plan.

## When to use
Use this skill when:
- a plan is already available
- the next step is still too broad to implement directly
- task boundaries, validation, or write-back needs are still implicit

## Inputs
- current plan
- current phase context
- known constraints
- known risks
- known reusable facts or golden cases

## Outputs
- one or more task specs
- clear in-scope / out-of-scope boundaries
- affected area and reviewable done condition
- black-box validation guidance
- white-box trigger judgment
- write-back guidance

## Workflow

### 1. Choose the smallest reviewable slice
Turn broad plan statements into the smallest reviewable task that still moves the phase forward.

### 2. One task, one primary outcome
If a candidate task mixes design, implementation, migration, and cleanup, split it.

### 3. Make the execution contract explicit
Each task spec should say what is in scope, what is out of scope, what area is affected, and what must be true when the task is done.

### 4. Make validation explicit
Every task spec should define how completion is verified, with black-box checks as the default acceptance path.

### 5. Judge white-box need
Ask whether black-box checks are enough.
Trigger white-box guidance when internal logic is branch-heavy, stateful, regression-sensitive, contract-sensitive, or tied to a deterministic bugfix path.

### 6. Decide write-back deliberately
Only mark write-back as needed when the task is expected to clarify stable, reusable context.
If write-back is needed, name the destination.

## Common failure modes
- turning the plan directly into one giant task
- copying plan text into the task spec without narrowing it
- leaving validation vague
- omitting out-of-scope boundaries
- leaving the affected area or done condition implicit
- writing back too much task-local detail
