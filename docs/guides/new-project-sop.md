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

### 2. Write the first plan
Use `docs/templates/plan-template.md`.

The plan should clarify:
- problem
- goal
- non-goals
- constraints
- risks
- phased direction
- first slice

### 3. Derive task specs
Use `skills/plan-to-spec.md`, `docs/specs/README.md`, and `docs/templates/task-spec-template.md`.

A task spec should shrink the plan into a narrow implementation contract.
If the plan contains multiple reviewable slices, derive multiple specs instead of one large spec.
During iteration, refine the current spec while the work is still the same slice.
Create a new dated spec when the primary outcome, boundary, or validation path changes.
Only tiny task requests that are already effectively spec-complete and trivially narrow may skip spec creation.

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
