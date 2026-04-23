# AI Engineering SOP Starter

A lightweight, tool-neutral SOP starter for AI-assisted engineering.

Use this repository when you want a project to move from planning to narrow execution without losing control of scope, validation, facts, or reusable workflows. It is intentionally not tied to a specific stack, app type, or framework.

## Choose Your Path

- `Small task / narrow change`
  Stay on the default lightweight path when the next slice is already clear and reviewable. Start with the [specs guide](ai/doc/specs/README.md) and the [task spec template](ai/doc/templates/task-spec-template.md).

- `Long task / multi-phase / multi-handoff`
  Use the phase-aware variant when the work needs explicit phase, plan, handoff, or failure-boundary structure. Start with the [phase-aware workflow guide](ai/doc/guides/phase-aware-workflow.md) and the [canonical example](ai/doc/guides/phase-aware-canonical-example.md).

Both paths still converge on one or more narrow task specs before implementation.

If you are returning to active work in a project that uses `project/*`, start with `project/CURRENT.md`, then `project/memory/README.md` when you need the longer-lived memory that shapes ongoing work.

## Minimal Default Context

For AI tools, the smallest useful default read set is:

1. `AGENTS.md`
2. `ai/README.md` only when you need `ai/*` namespace routing
3. `project/CURRENT.md` when the repository uses `project/*` and current state matters
4. `project/memory/README.md` only when `CURRENT.md` or the task shows that longer-lived project memory matters

Open guides, templates, facts, examples, and skills only when the current task needs them.

## What this repository is for

This starter is for teams that want a practical default workflow for:

1. framing work with a plan
2. deriving one or more narrow task specs
3. implementing the smallest coherent change
4. validating explicitly, with black-box checks by default
5. writing back stable reusable context selectively
6. promoting repeated workflows into reusable skills

It is suitable for new projects, existing projects, non-web projects, and mixed engineering environments.

## Core workflow

The intended workflow is:

1. create or refine a plan
2. derive one or more narrow task specs in `ai/doc/specs/`
3. implement narrowly
4. validate explicitly
5. write back stable reusable context when justified
6. promote repeated workflows into skills when they stabilize

See `AGENTS.md` for the full working model, including when plans should be persisted, when specs may be skipped, and how validation layers work.

## Navigation

Use the repository entrypoints and layers like this:

- `README.md`
  Human-facing entry and adoption guide.

- `AGENTS.md`
  Canonical AI-tool rules and default context discipline.

- `ai/README.md`
  Namespace map for `ai/*`.

- `project/CURRENT.md`
  Recovery-first current state when the repository uses `project/*`.

- `project/memory/README.md`
  Longer-lived project memory when repeated context should remain easy to recover.

The repository's AI-managed SOP assets live under `ai/`.
Project-facing recovery and control live under `project/*` when that control surface is in use.
Change summaries are optional task-local delivery notes and have no required repository directory by default.

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
Use `project/memory/*` as the next layer when the project needs durable memory that is broader than one task but narrower than reusable AI facts.

## Minimal adoption path

The smallest practical starting point is:

1. keep `AGENTS.md`
2. keep `ai/README.md`
3. keep `.cursor/rules/*`
4. keep `ai/doc/templates/*`
5. keep `ai/doc/specs/README.md`
6. keep `ai/doc/facts/facts-index.md`
7. keep the core initial skills: `ai/skill/init-project-from-brief.md`, `ai/skill/plan-to-spec.md`, `ai/skill/execute-from-spec.md`, and `ai/skill/design-whitebox-tests.md`
8. run `ai/skill/init-project-from-brief.md` with your project brief so `AGENTS.md`, `README.md`, `project/CURRENT.md`, and `ai/doc/facts/project-scope.md` reflect the real project before you start planning

That list is the bare minimum.
If you also want the recommended recovery-first control surface for humans, keep:

- `project/README.md`
- `project/decisions/`
- `project/experiments/`
- `project/memory/*`
- `ai/doc/templates/current-template.md`
- `ai/doc/templates/doc-map-template.md`
- `ai/doc/templates/project-memory-readme-template.md`
- `ai/doc/templates/project-memory-page-template.md`
- `ai/skill/session-closeout.md`

If the target project runs on Plastic SCM (Unity Version Control), also keep:

- `ai/skill/init-plastic-scm.md`
- `ai/doc/templates/ignore-conf-template.md`
- `ai/doc/templates/cursorignore-template.md`
- `ai/doc/templates/agents-version-control-section.md`

On first entry into such a project, running `ai/skill/init-project-from-brief.md` will delegate to `ai/skill/init-plastic-scm.md` automatically when `.plastic/plastic.selector` is detected. Run `ai/skill/init-plastic-scm.md` directly only when you want the VCS bootstrap in isolation. Projects on other backends do not need this bootstrap.

If you want the guided first-use path to remain available after copying, also keep:

- `ai/doc/guides/new-project-sop.md`
- `ai/doc/guides/testing-strategy.md`
- `ai/doc/guides/task-lifecycle-and-escalation.md`
- `ai/skill/replan-or-escalate.md`
- `ai/skill/decision-recording.md`
- `ai/doc/templates/release-batch-template.md` when the project will prepare real product releases and wants a lightweight batch-level release check
- `ai/doc/specs/20260104-001-example-first-copied-project-quickstart.md` when you want the small-task example
- `ai/doc/guides/phase-aware-workflow.md` when long-task guidance is needed
- `ai/doc/guides/phase-aware-canonical-example.md`, `ai/doc/guides/phase-aware-example-main-plan.md`, `ai/doc/guides/phase-aware-example-sub-plan.md`, and `ai/doc/specs/20260103-001-example-adoption-entrypoint-slice.md` when you want the closed long-task example

## Copy Into A Real Project In 10 Minutes

1. Copy the minimal adoption set into the real project. Keep the split entrypoints: root `README.md` for humans, `AGENTS.md` for AI tools, and `ai/README.md` for the `ai/*` namespace. If you want a recovery-first control surface for humans, also copy `project/README.md`, `project/decisions/`, `project/experiments/`, the starter memory pages under `project/memory/*`, the control-surface templates listed above, and `ai/skill/session-closeout.md`.
2. Run `ai/skill/init-project-from-brief.md` with your project brief. It personalizes `AGENTS.md` and `README.md` identity blocks, initializes `project/CURRENT.md` and `project/DOC_MAP.md`, seeds `ai/doc/facts/project-scope.md`, and delegates to `ai/skill/init-plastic-scm.md` when `.plastic/plastic.selector` is present. If you do not have a brief yet, it falls back to a structured Q&A for the required fields before editing anything.
3. Decide whether the first slice is a `small task / narrow change` or a `long task / multi-phase / multi-handoff`.
4. Persist a written plan only if the phase, handoff, or checkpoint structure is worth re-reading later. Otherwise move directly to the first spec.
5. Derive the first task spec with `ai/skill/plan-to-spec.md`, the [specs guide](ai/doc/specs/README.md), and the [task spec template](ai/doc/templates/task-spec-template.md).
6. Implement from the spec via `ai/skill/execute-from-spec.md`, validate explicitly, and write back only stable reusable context.

`ai/skill/autopilot.md` is an advanced, on-demand execution discipline for bounded autonomous work. Do not include it in the default copied-project set unless your team explicitly wants that mode.

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
2. if the project uses `project/*` and you need longer-lived agreements or recurring project memory, read `project/memory/README.md`
3. read `AGENTS.md`
4. if you are wiring AI workflow assets, read `ai/README.md`
5. for the default lightweight path, read `ai/doc/specs/README.md`
6. for the phase-aware long-task path, read `ai/doc/guides/phase-aware-workflow.md` and `ai/doc/guides/phase-aware-canonical-example.md`
7. for a copied-project first-use, run `ai/skill/init-project-from-brief.md`; the [new-project SOP guide](ai/doc/guides/new-project-sop.md) is the prose companion for readers who prefer to walk the flow manually
8. create or refine a first plan, using `ai/doc/templates/plan-template.md` only when you want a durable written plan

When design, planning, and execution are split across different tools or roles, also see `ai/doc/guides/design-to-spec-handoff.md` and the prompt scaffolds in `ai/doc/templates/design-to-planner-prompt-template.md` and `ai/doc/templates/spec-to-executor-prompt-template.md`.

## What's New In 0.3.0

- the homepage now splits the default `small task` path from the `long task` phase-aware path
- copied-project adoption now has a faster first-use route in `README.md` and `ai/doc/guides/new-project-sop.md`
- both paths now have copyable examples: a closed phase-aware chain and a first-use small-task spec
- task status and escalation wording are now aligned across the specs guide, lifecycle guide, and task spec template
- the repository now includes a minimal `project/*` control surface with project memory and closeout guidance to keep human recovery state separate from AI execution assets
- real product releases can use an optional lightweight batch-level release check instead of adding release paperwork to every spec

---

**SOP Starter Version**: 0.3.0 - 2026-03-27
