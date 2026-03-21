# AI Engineering SOP Starter

A lightweight, tool-neutral SOP starter for AI-assisted engineering.

Use this repository when you want a project to move from planning to narrow execution without losing control of scope, validation, facts, or reusable workflows. It is intentionally not tied to a specific stack, app type, or framework.

## What this repository is for

This starter is for teams that want a practical default workflow for:

1. framing work with a plan
2. deriving narrow task specs
3. implementing the smallest coherent change
4. validating explicitly, with black-box checks by default
5. writing back stable facts
6. promoting repeated workflows into reusable skills

It is suitable for new projects, existing projects, non-web projects, and mixed engineering environments.

## Core workflow

The intended workflow is:

1. write or refine a plan
2. derive one or more narrow task specs
3. implement narrowly
4. validate explicitly
5. write back stable facts when justified
6. promote repeated workflows into skills when they stabilize

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
  Reusable working artifacts such as plans, task specs, and change summaries.

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
4. keep `docs/facts/facts-index.md`
5. keep the two initial skills: `skills/plan-to-spec.md` and `skills/design-whitebox-tests.md`
6. write a first plan, then initialize `docs/facts/project-scope.md` when stable scope is clear

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
3. write a first plan from `docs/templates/plan-template.md`
4. initialize `docs/facts/project-scope.md` when stable scope is clear
