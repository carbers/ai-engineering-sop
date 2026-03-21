# New Project SOP

Use this SOP when starting a new project or when introducing structure into an existing project.

## Default startup order

1. clarify the project at a plan level
2. initialize project scope facts
3. derive task specs from the plan
4. implement narrowly
5. validate explicitly
6. write back stable facts
7. promote repeatable workflows into skills when justified

## Startup checklist

### 1. Establish the current phase
Before coding, clarify:

- what this phase must achieve
- what this phase explicitly will not do
- the main constraints
- the first reviewable slice

### 2. Initialize project facts
Create or update:

- `docs/facts/project-scope.md`
- `docs/facts/golden-cases.md` if stable reference cases are already known

### 3. Write the first plan
Use `docs/templates/plan-template.md`.

The plan should clarify:
- problem
- goal
- non-goals
- constraints
- risks
- phased direction
- first slice

### 4. Derive task specs
Use `skills/plan-to-spec.md` and `docs/templates/task-spec-template.md`.

A task spec should shrink the plan into a narrow implementation contract.

### 5. Decide starter/code skeleton work deliberately
Project starter work is a result of planning, not a global precondition.
Do not assume a fixed technology stack.
Only define code skeleton and starter structure after the plan has made the current needs clear.

### 6. Validate in layers
- use black-box validation by default
- add white-box validation when triggered by internal complexity or regression sensitivity

See `docs/guides/testing-strategy.md`.

### 7. Write back stable facts
Write back only stable, reusable context.
Do not turn every task discussion into permanent docs.

## Practical note

This SOP is intended to remain lightweight.  
The goal is not to create many documents.  
The goal is to create enough structure that implementation stays controlled, reviewable, and reusable.
