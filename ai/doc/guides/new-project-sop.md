# New Project SOP

Use this SOP when starting a new project or when introducing structure into an existing project.

## First Use In A Copied Project

Use this as the copied-project quickstart:

1. keep the entrypoints split: root `README.md` for humans, `AGENTS.md` and adapters for AI tools, `ai/README.md` for the `ai/*` namespace
2. keep the minimal starter set from `README.md`
3. decide whether the first slice is a default `small task` or a `phase-aware` long task
4. clarify the first reviewable slice in the planning workflow you already use
5. write a durable plan only if the current phase or handoff structure is worth re-reading later
6. derive the first narrow task spec before implementation
7. validate explicitly and write back only stable reusable context

The starter should stay lightweight on day one.
Do not create every optional artifact up front.

## Entrypoints In Copied Projects

When this starter is copied into a real project, keep the entrypoints split:

- let the root `README.md` become the human-facing project entrypoint
- keep `AGENTS.md` and any tool adapters as AI-tool entrypoints
- keep `ai/README.md` as the namespace map for AI workflow assets
- keep project-facing docs outside `ai/`
- when human readers need a recovery-first current-state view, use a root-level `project/` control surface and start with `project/CURRENT.md`
  If you adopt that control surface, also keep `ai/doc/templates/current-template.md`, `ai/doc/templates/doc-map-template.md`, and `ai/skill/session-closeout.md` so it stays small and current.

## Default startup order

1. clarify the project at a plan level
2. derive one or more task specs from the plan
3. implement narrowly
4. validate explicitly
5. write back stable facts
6. promote repeatable workflows into skills when justified

The default path stays lightweight.
Only move into the phase-aware variant when the work is long-running enough to need explicit phase, plan, and task hierarchy.
If you want to see one complete long-task chain before copying the pattern, read `ai/doc/guides/phase-aware-canonical-example.md`.

## What To Keep On Day One

The smallest practical copied-project set is:

- `AGENTS.md`
- `ai/README.md`
- `.cursor/rules/*`
- `ai/doc/templates/*`
- `ai/doc/specs/README.md`
- `ai/doc/facts/facts-index.md`
- `ai/skill/plan-to-spec.md`
- `ai/skill/design-whitebox-tests.md`

Add more files only when they solve a real current need.

If you want the guided first-use path to remain available after copying, also keep:

- `ai/doc/guides/new-project-sop.md`
- `ai/doc/guides/testing-strategy.md`
- `ai/doc/guides/task-lifecycle-and-escalation.md`
- `ai/doc/templates/release-batch-template.md` when the project will prepare real product releases and wants a lightweight batch-level release check
- `ai/doc/specs/20260104-001-example-first-copied-project-quickstart.md`
- `ai/doc/guides/phase-aware-workflow.md` when long-task guidance is needed
- `ai/doc/guides/phase-aware-canonical-example.md`
- `ai/doc/guides/phase-aware-example-main-plan.md`
- `ai/doc/guides/phase-aware-example-sub-plan.md`
- `ai/doc/specs/20260103-001-example-adoption-entrypoint-slice.md`

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

Use a durable written plan when one or more of these are true:
- the current phase needs checkpoints, dependencies, or handoff context that should survive later re-reading
- multiple people or models need to align on the same phase slice
- the work is long-running enough that the next task is not obvious without the parent plan

Skip the durable plan when:
- the first slice is already clear enough to narrow directly into one reviewable spec
- writing the plan would only restate what the current task request already says

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
Use `ai/doc/guides/phase-aware-canonical-example.md` when you want a compact, copyable example of that chain.
If you keep the guided first-use files, that example also links to concrete `main_plan` and `sub_plan` artifacts you can copy directly.

### 3. Derive task specs
Use `ai/skill/plan-to-spec.md`, `ai/doc/specs/README.md`, and `ai/doc/templates/task-spec-template.md`.

A task spec should shrink the plan into a narrow implementation contract.
See `ai/doc/specs/README.md` for naming, splitting, and lifecycle conventions.
For longer-running work, also use `ai/doc/guides/task-lifecycle-and-escalation.md` so repair, rollback, replan, and escalation stay explicit.
When a returning human needs to recover the current state before entering the active spec, start with `project/CURRENT.md`.

For the first copied-project slice:
- start with one spec, not a batch of specs
- make the first spec small enough to review in one pass
- use the phase-aware fields only when they make the current slice easier to hand off or recover

If you want a copyable default-path example, see `ai/doc/specs/20260104-001-example-first-copied-project-quickstart.md`.
If you want a copyable example that includes the minimal control-surface closeout path, see `ai/doc/specs/20260328-003-example-project-control-closeout-loop.md`.

### 4. Decide starter/code skeleton work deliberately
Project starter work is a result of planning, not a global precondition.
Do not assume a fixed technology stack.
Only define code skeleton and starter structure after the plan has made the current needs clear.

### 5. Validate in layers
- use black-box validation by default
- add white-box validation when triggered by internal complexity or regression sensitivity

See `ai/doc/guides/testing-strategy.md`.

For the first copied-project slice, prefer validation that a reviewer can quickly inspect:
- what user-visible behavior changed
- what check proves the slice is done
- whether any internal regression path also needs protection

### 6. Write back stable facts
After implementation and validation, create or update:

- `ai/doc/facts/project-scope.md` when scope or boundaries became clearer
- `ai/doc/facts/golden-cases.md` when stable reusable validation references are worth preserving

Write back only stable, reusable context.
Do not turn every task discussion into permanent docs.

For the first copied-project slice, write back only when something became stable enough to help the next task.
If nothing stable emerged, skip write-back.

### 7. Prepare release batches only when needed
Do not create release-readiness records for every task.
When the project is preparing a real product release, aggregate the release-sensitive slices at the batch level instead.
Use `ai/doc/templates/release-batch-template.md` if you want a lightweight release record that can be reviewed by both humans and future automation.

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
