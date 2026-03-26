# AI Engineering SOP Starter

A lightweight, tool-neutral SOP starter for AI-assisted engineering.

Use this repository when you want a project to move from planning to narrow execution without losing control of scope, validation, facts, or reusable workflows. It is intentionally not tied to a specific stack, app type, or framework.

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

## Entrypoints

This repository intentionally uses split entrypoints:

- `README.md`
  Human-facing and project-facing entrypoint.

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

## What this repository is not

This repository is not:

- a fixed web stack starter
- a product application
- a heavy process framework
- a documentation portal
- a requirement to write large documents before coding
- an archive for all historical discussion

## Where to look next

1. read `AGENTS.md`
2. if you are wiring AI workflow assets, read `ai/README.md`
3. read `ai/doc/guides/new-project-sop.md`
4. read `ai/doc/specs/README.md`
5. create or refine a first plan, using `ai/doc/templates/plan-template.md` only when you want a durable written plan
6. initialize `ai/doc/facts/project-scope.md` when stable scope is clear

When design, planning, and execution are split across different tools or roles, also see `ai/doc/guides/design-to-spec-handoff.md` and the prompt scaffolds in `ai/doc/templates/design-to-planner-prompt-template.md` and `ai/doc/templates/spec-to-executor-prompt-template.md`.

---

**SOP Starter Version**: 0.2.0 - 2026-03-22
