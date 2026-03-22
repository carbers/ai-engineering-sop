# New Project SOP

Use this SOP when starting a new project or when introducing structure into an existing project.

## Default startup order

1. clarify the project at a plan level
2. derive one or more task specs from the plan
3. implement narrowly
4. validate explicitly
5. write back stable facts
6. promote repeatable workflows into skills when justified

## Startup checklist

### 1. Establish the current phase
Before coding, clarify:

- what this phase must achieve
- what this phase explicitly will not do
- the main constraints
- the first reviewable slice

### 2. Establish the first plan
First establish the plan in the planning workflow you actually use.
A written plan document is optional.
Use `docs/templates/plan-template.md` only when the plan should become a durable repo artifact worth re-reading, sharing, or handing off.
By default, persist the task spec rather than the plan.

The plan should clarify:
- problem
- goal
- non-goals
- constraints
- risks
- phased direction
- first slice

If the plan is already clear from an interactive planning session, move directly to spec derivation.
Do not force a second written plan unless it adds durable value.

### 3. Derive task specs
Use `skills/plan-to-spec.md`, `docs/specs/README.md`, and `docs/templates/task-spec-template.md`.

A task spec should shrink the plan into a narrow implementation contract.
See `docs/specs/README.md` for naming, splitting, and lifecycle conventions.

### 4. Decide starter/code skeleton work deliberately
Project starter work is a result of planning, not a global precondition.
Do not assume a fixed technology stack.
Only define code skeleton and starter structure after the plan has made the current needs clear.

### 5. Validate in layers
- use black-box validation by default
- add white-box validation when triggered by internal complexity or regression sensitivity

See `docs/guides/testing-strategy.md`.

### 6. Write back stable facts
After implementation and validation, create or update:

- `docs/facts/project-scope.md` when scope or boundaries became clearer
- `docs/facts/golden-cases.md` when stable reusable validation references are worth preserving

Write back only stable, reusable context.
Do not turn every task discussion into permanent docs.

## Practical note

This SOP is intended to remain lightweight.  
The goal is not to create many documents.  
The goal is to create enough structure that implementation stays controlled, reviewable, and reusable.  
The goal is one or more small specs, not one large spec.

## Multi-Model Collaboration Variant

If design discussion, planning, spec derivation, and execution are split across different tools or different people, use `docs/guides/design-to-spec-handoff.md`.

That guide is an extension of this SOP, not a replacement for it.
The same core rule still applies: implementation should run from a clear task spec, not directly from a broad design discussion or a broad plan.
