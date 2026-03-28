# AI Engineering SOP Starter

A lightweight, tool-neutral SOP starter for AI-assisted engineering.

Use this repository when you want a project to move from planning to narrow execution without losing control of scope, validation, facts, or reusable workflows. It is intentionally not tied to a specific stack, app type, or framework.

## Choose Your Path

- `Small task / narrow change`
  Stay on the default lightweight path when the next slice is already clear and reviewable. Start with the [specs guide](ai/doc/specs/README.md) and the [task spec template](ai/doc/templates/task-spec-template.md).

- `Long task / multi-phase / multi-handoff`
  Use the phase-aware variant when the work needs explicit phase, plan, handoff, or failure-boundary structure. Start with the [phase-aware workflow guide](ai/doc/guides/phase-aware-workflow.md) and the [canonical example](ai/doc/guides/phase-aware-canonical-example.md).

Both paths still converge on one or more narrow task specs before implementation.

If you are returning to active work in a project that uses `project/*`, start with `project/CURRENT.md` before diving into specs or guides.

## What this repository is for

This starter is for teams that want a practical default workflow for:

1. framing work with a plan
2. deriving one or more narrow task specs
3. implementing the smallest coherent change
4. validating explicitly, with black-box checks by default
5. writing back stable facts
6. promoting repeated workflows into reusable skills

It is suitable for new projects, existing projects, non-web projects, and mixed engineering environments.

## Core workflow

The intended workflow is:

1. create or refine a plan
2. derive one or more narrow task specs in `ai/doc/specs/`
3. implement narrowly
4. validate explicitly
5. write back stable facts when justified
6. promote repeated workflows into skills when they stabilize

See `AGENTS.md` for the full working model, including when plans should be persisted, when specs may be skipped, and how validation layers work.

The repository's AI-managed SOP assets live under `ai/`.
This keeps workflow docs, templates, facts, specs, and skills separate from project-facing product documentation.
See `ai/README.md` for the AI workflow namespace map and boundary rules.

When a project uses `project/*`, its human-facing recovery layer lives there.
Start with `project/CURRENT.md` when you need to recover the current phase, active slice, next actions, or the current source of truth.

## Project Control Surface

When a project uses `project/*`, use it as the minimal control surface for human readers returning to the work.

- `project/CURRENT.md`
  Recovery-first current state for humans.

- `project/DOC_MAP.md`
  Short explanation of which document answers which question.

- `project/decisions/*`
  Frozen project-level decisions worth re-reading later.

- `project/experiments/*`
  Readable experiment summaries when experiments become part of the workflow.

Use `ai/*` for AI-managed execution assets.
Use `project/*` for human-facing recovery and control.

## Entrypoints

This repository intentionally uses split entrypoints:

- `README.md`
  Human-facing and project-facing entrypoint.

- `project/CURRENT.md`
  Recovery-first entry for the current human-facing project state when the project uses `project/*`.

- `AGENTS.md` and adapter files such as `CLAUDE.md`
  AI-tool entrypoints.

- `ai/README.md`
  Namespace map for AI workflow assets after entering through the AI-tool guidance.

## Repository roles

- `README.md`
  Human-facing entry point and adoption guide for this starter.

- `AGENTS.md`
  Canonical AI-tool operating rules for the repository.

- `CLAUDE.md`
  Lightweight AI-tool adapter that points back to `AGENTS.md`.

- `ai/README.md`
  Namespace map for AI-managed workflow assets, boundaries, and navigation.

- `.cursor/rules/*`
  Execution guardrails for Cursor.

- `ai/doc/guides/*`
  Practical workflow guidance for adopting and using the SOP.

- `ai/doc/templates/*`
  Reusable working artifacts such as plans, task specs, change summaries, and prompt scaffolds for multi-model handoff.

- `ai/doc/specs/*`
  Task specs used as the default execution artifact between plan and implementation.

- `ai/doc/facts/*`
  Stable reusable context, not an archive of task chatter.

- `ai/skill/*`
  Lightweight reusable workflow capabilities.

## Adopting this starter

Use this repository in one of two ways:

### Maintain the SOP starter itself
In this repository, `README.md` explains the SOP system.

### Copy it into a real project
Copy the relevant files into the project, initialize the facts and templates you actually need, and keep the operating rules in `AGENTS.md`, `.cursor/rules/*`, `ai/doc/*`, and `ai/skill/*`.

After copying, let `README.md` become the project's human-facing README.
Keep `AGENTS.md` plus any tool adapters as the AI-tool entrypoints.
Keep `ai/README.md` as the namespace map for AI workflow assets.
Keep project-facing docs outside `ai/` so the namespace remains reserved for AI workflow assets.
When the copied project uses a root-level `project/` control surface, use it as the human-facing recovery layer, with `project/CURRENT.md` as the first file to read when returning to the project.

## Minimal adoption path

The smallest practical starting point is:

1. keep `AGENTS.md`
2. keep `ai/README.md`
3. keep `.cursor/rules/*`
4. keep `ai/doc/templates/*`
5. keep `ai/doc/specs/README.md`
6. keep `ai/doc/facts/facts-index.md`
7. keep the two initial skills: `ai/skill/plan-to-spec.md` and `ai/skill/design-whitebox-tests.md`
8. create a first plan in your planning workflow, then initialize `ai/doc/facts/project-scope.md` when stable scope is clear

That list is the bare minimum.
If you also want the recommended recovery-first control surface for humans, keep:

- `project/*`
- `ai/doc/templates/current-template.md`
- `ai/doc/templates/doc-map-template.md`
- `ai/skill/session-closeout.md`

If you want the guided first-use path to remain available after copying, also keep:

- `ai/doc/guides/new-project-sop.md`
- `ai/doc/guides/testing-strategy.md`
- `ai/doc/guides/task-lifecycle-and-escalation.md`
- `ai/doc/templates/release-batch-template.md` when the project will prepare real product releases and wants a lightweight batch-level release check
- `ai/doc/specs/20260104-001-example-first-copied-project-quickstart.md` when you want the small-task example
- `ai/doc/guides/phase-aware-workflow.md` when long-task guidance is needed
- `ai/doc/guides/phase-aware-canonical-example.md`, `ai/doc/guides/phase-aware-example-main-plan.md`, `ai/doc/guides/phase-aware-example-sub-plan.md`, and `ai/doc/specs/20260103-001-example-adoption-entrypoint-slice.md` when you want the closed long-task example

## Copy Into A Real Project In 10 Minutes

1. Copy the minimal adoption set into the real project. If you want this guided walkthrough to remain available inside the copied project, also copy the guided first-use files listed above. Keep the split entrypoints: root `README.md` for humans, `AGENTS.md` for AI tools, and `ai/README.md` for the `ai/*` namespace.
  If you want a recovery-first control surface for humans, copy `project/*` together with `ai/doc/templates/current-template.md`, `ai/doc/templates/doc-map-template.md`, and `ai/skill/session-closeout.md`, then start with `project/CURRENT.md`.
2. Decide whether the first slice is a `small task / narrow change` or a `long task / multi-phase / multi-handoff`.
3. Clarify the first reviewable slice in your normal planning workflow.
4. Persist a written plan only if the phase, handoff, or checkpoint structure is worth re-reading later. Otherwise move directly to the first spec.
5. Derive the first task spec with the [specs guide](ai/doc/specs/README.md) and the [task spec template](ai/doc/templates/task-spec-template.md).
6. Implement from the spec, validate explicitly, and write back only stable reusable context.

If you want the copied-project walkthrough, read the [new-project SOP guide](ai/doc/guides/new-project-sop.md).
If you want a copyable example of the minimal control-surface loop, read [20260328-003-example-project-control-closeout-loop.md](ai/doc/specs/20260328-003-example-project-control-closeout-loop.md).

## What this repository is not

This repository is not:

- a fixed web stack starter
- a product application
- a heavy process framework
- a documentation portal
- a requirement to write large documents before coding
- an archive for all historical discussion

## Where to look next

1. if the project uses `project/*` and you need the current project state, read `project/CURRENT.md`
2. read `AGENTS.md`
3. if you are wiring AI workflow assets, read `ai/README.md`
4. for a first copied-project run, read `ai/doc/guides/new-project-sop.md`
5. for the default lightweight path, read `ai/doc/specs/README.md`
6. for the phase-aware long-task path, read `ai/doc/guides/phase-aware-workflow.md` and `ai/doc/guides/phase-aware-canonical-example.md`
7. create or refine a first plan, using `ai/doc/templates/plan-template.md` only when you want a durable written plan
8. initialize `ai/doc/facts/project-scope.md` when stable scope is clear

When design, planning, and execution are split across different tools or roles, also see `ai/doc/guides/design-to-spec-handoff.md` and the prompt scaffolds in `ai/doc/templates/design-to-planner-prompt-template.md` and `ai/doc/templates/spec-to-executor-prompt-template.md`.

## What's New In 0.3.0

- the homepage now splits the default `small task` path from the `long task` phase-aware path
- copied-project adoption now has a faster first-use route in `README.md` and `ai/doc/guides/new-project-sop.md`
- both paths now have copyable examples: a closed phase-aware chain and a first-use small-task spec
- task status and escalation wording are now aligned across the specs guide, lifecycle guide, and task spec template
- the repository now includes a minimal `project/*` control surface with closeout guidance to keep human recovery state separate from AI execution assets
- real product releases can use an optional lightweight batch-level release check instead of adding release paperwork to every spec

---

**SOP Starter Version**: 0.3.0 - 2026-03-27
