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
2. derive one or more narrow task specs in `docs/specs/`
3. implement narrowly
4. validate explicitly
5. write back stable facts when justified
6. promote repeated workflows into skills when they stabilize

When a plan or phase slice exists, the default path is `plan -> one or more task specs -> implementation -> validation`.
A plan may come from an interactive planning session or a written plan document.
Use `docs/templates/plan-template.md` only when the plan should become a durable repo artifact worth re-reading, sharing, or handing off.
Plans may remain temporary. The task spec is the default durable execution artifact.
During iteration, refine the same spec while the work is still the same reviewable slice and create a new dated spec when the outcome, boundary, or validation path changes.
Only tiny task requests that are already effectively spec-complete and trivially narrow may skip spec creation.

Black-box validation is the default acceptance path. White-box validation is added when internal logic is regression-sensitive, stateful, branch-heavy, or otherwise needs direct protection.

## Repository roles

- `README.md`
  Entry point and adoption guide for this starter.

- `AGENTS.md`
  Canonical operating rules for the repository.

- `CLAUDE.md`
  Lightweight adapter that points back to `AGENTS.md`.

- `.cursor/rules/*`
  Execution guardrails for Cursor.

- `docs/guides/*`
  Practical workflow guidance for adopting and using the SOP.

- `docs/templates/*`
  Reusable working artifacts such as plans, task specs, prompt scaffolds, and change summaries.

- `docs/specs/*`
  Task specs used as the default execution artifact between plan and implementation.

- `docs/facts/*`
  Stable reusable context, not an archive of task chatter.

- `skills/*`
  Lightweight reusable workflow capabilities.

## Adopting this starter

Use this repository in one of two ways:

### Maintain the SOP starter itself
In this repository, `README.md` explains the SOP system.

### Copy it into a real project
Copy the relevant files into the project, initialize the facts and templates you actually need, and keep the operating rules in `AGENTS.md`, `.cursor/rules/*`, `docs/*`, and `skills/*`.

After copying, `README.md` can gradually become the project's normal README while the rest of the repository continues to carry the SOP mechanics.

## Minimal adoption path

The smallest practical starting point is:

1. keep `AGENTS.md`
2. keep `.cursor/rules/*`
3. keep `docs/templates/*`
4. keep `docs/specs/README.md`
5. keep `docs/facts/facts-index.md`
6. keep the two initial skills: `skills/plan-to-spec.md` and `skills/design-whitebox-tests.md`
7. create a first plan in your planning workflow, then initialize `docs/facts/project-scope.md` when stable scope is clear

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
2. read `docs/guides/new-project-sop.md`
3. read `docs/specs/README.md`
4. create or refine a first plan, using `docs/templates/plan-template.md` only when you want a durable written plan
5. initialize `docs/facts/project-scope.md` when stable scope is clear

When design, planning, and execution are split across different tools or roles, also see `docs/guides/design-to-spec-handoff.md`.
