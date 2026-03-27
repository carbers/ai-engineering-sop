# New Project SOP

Use this SOP when starting a new project or when introducing structure into an existing project.

## Entrypoints In Copied Projects

When this starter is copied into a real project, keep the entrypoints split:

- let the root `README.md` become the human-facing project entrypoint
- keep `AGENTS.md` and any tool adapters as AI-tool entrypoints
- keep `ai/README.md` as the namespace map for AI workflow assets
- keep project-facing docs outside `ai/`

## Default startup order

1. clarify the project at a plan level
2. derive one or more task specs from the plan
3. implement narrowly
4. validate explicitly
5. write back stable facts
6. promote repeatable workflows into skills when justified

The default path stays lightweight.
Only move into the phase-aware variant when the work is long-running enough to need explicit phase, plan, and task hierarchy.

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
Use `ai/doc/templates/plan-template.md` only when the plan should become a durable repo artifact worth re-reading, sharing, or handing off.
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

When the work spans multiple milestones, dependencies, or long-lived handoffs, use the phase-aware guidance in `ai/doc/guides/phase-aware-workflow.md`.
That guide explains how to keep `project_target`, `current_target`, `phase`, `main_plan`, `sub_plan`, and `task` aligned without replacing the default spec-first workflow.

### 3. Derive task specs
Use `ai/skill/plan-to-spec.md`, `ai/doc/specs/README.md`, and `ai/doc/templates/task-spec-template.md`.

A task spec should shrink the plan into a narrow implementation contract.
See `ai/doc/specs/README.md` for naming, splitting, and lifecycle conventions.
For longer-running work, also use `ai/doc/guides/task-lifecycle-and-escalation.md` so repair, rollback, replan, and escalation stay explicit.

### 4. Decide starter/code skeleton work deliberately
Project starter work is a result of planning, not a global precondition.
Do not assume a fixed technology stack.
Only define code skeleton and starter structure after the plan has made the current needs clear.

### 5. Validate in layers
- use black-box validation by default
- add white-box validation when triggered by internal complexity or regression sensitivity

See `ai/doc/guides/testing-strategy.md`.

### 6. Write back stable facts
After implementation and validation, create or update:

- `ai/doc/facts/project-scope.md` when scope or boundaries became clearer
- `ai/doc/facts/golden-cases.md` when stable reusable validation references are worth preserving

Write back only stable, reusable context.
Do not turn every task discussion into permanent docs.

## Practical note

This SOP is intended to remain lightweight.  
The goal is not to create many documents.  
The goal is to create enough structure that implementation stays controlled, reviewable, and reusable.  
The goal is one or more small specs, not one large spec.

## When To Use The Phase-Aware Variant

Use the phase-aware variant when one or more of these are true:

- the work spans multiple phases or checkpoints
- a `main_plan` and one or more `sub_plan` views are both useful
- task ordering, dependency handling, or failure handling must be made explicit
- multiple people or models will hand the work across boundaries
- repair, rollback, replan, or escalation paths need to be reviewable

Do not use the phase-aware variant for every small task.
If a narrow task request is already clear and reviewable, stay on the default lightweight path.

## Multi-Model Collaboration Variant

If design discussion, planning, spec derivation, and execution are split across different tools or different people, use `ai/doc/guides/design-to-spec-handoff.md`.

That guide is an extension of this SOP, not a replacement for it.
The same core rule still applies: implementation should run from a clear task spec, not directly from a broad design discussion or a broad plan.
