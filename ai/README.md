# AI Namespace

This directory holds AI-managed SOP assets for the repository.

Use `ai/` to keep workflow assets separate from project-facing documentation and product artifacts.
This file is the namespace map for `ai/*`, not the main project entrypoint.
The human-facing project entrypoint remains the repository root `README.md`.
AI tools should enter through `AGENTS.md` or a tool adapter, then use this file to navigate `ai/*`.

## Namespace map

- `ai/doc/*`
  Durable SOP documents such as guides, templates, task specs, and stable facts.

- `ai/skill/*`
  Reusable workflow assets that reduce repeated reasoning work.

## Boundary rule

Put content in `ai/` when it primarily exists to guide AI-assisted planning, execution, validation, write-back, or reusable workflow behavior.

Do not put content in `ai/` when it is primarily project-facing documentation such as:
- product docs
- architecture docs for the shipped system
- ADRs
- runbooks
- user or operator documentation

Those project-facing materials should live outside `ai/` in the repository structure chosen by the project.
A recommended default is a root-level `project/` control surface, with `project/CURRENT.md` as the recovery-first file for humans returning to the work.

## Naming convention

The canonical namespace roots are singular by design:
- `ai/doc`
- `ai/skill`

Do not create parallel roots such as `ai/docs` or `ai/skills`.

## Minimal use after AI-tool entry

1. Enter through `../AGENTS.md` or a tool adapter such as `../CLAUDE.md`.
2. Use this file only to decide which `ai/*` area is relevant.
3. Open only the guide, template, spec, fact, or skill that the current task actually needs.
4. Do not treat the whole `ai/*` tree as default context.

## Maintenance rule

- When adding, removing, or renaming fact files under `ai/doc/facts/`, update `ai/doc/facts/facts-index.md`.
- When adding, removing, or renaming skills under `ai/skill/`, update `ai/skill/skill-registry.md`.
