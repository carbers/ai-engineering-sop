# Specs Directory

Task specs are the default execution artifact between planning and implementation.

## Purpose

Use `docs/specs/*` to hold narrow task specs that:
- bridge plans and implementation
- keep execution reviewable
- stay small enough to refine during iteration

This directory does not need a central index.
Use filenames plus optional `Related Specs` links for navigation.

## Naming

Store each spec as:

`docs/specs/YYYYMMDD-NNN-task-slug.md`

- `YYYYMMDD` is the spec creation date
- `NNN` is the same-day sequence, starting at `001`
- choose the next available same-day sequence by scanning existing spec filenames
- never renumber existing specs
- `task-slug` is lowercase kebab-case

Example:

`docs/specs/20260322-001-auth-session-hardening.md`

## Create Or Refine

- if a plan or phase slice exists, derive one or more specs before editing
- if iterating within the same reviewable slice, refine the existing spec
- if the primary outcome, boundary, or validation path changes, create a new dated spec first
- only tiny task requests that are already effectively spec-complete and trivially narrow may skip spec creation

## Keep Specs Small

One spec should produce one primary reviewable outcome.
One plan may produce multiple specs.

Split a spec when it would contain:
- multiple primary outcomes
- independently reviewable slices
- distinct validation paths
- a checklist that no longer stays short

## Status

Use one of these status values:

- `draft`: the spec exists, but implementation should not start yet
- `in-progress`: implementation for this spec has started
- `blocked`: progress is waiting on a prerequisite, dependency, or decision
- `done`: `Done When` is satisfied and required validation has passed

Checklist completion alone does not make a spec `done`.
Required validation must also pass.

## Checklist

Use a short Markdown checkbox list inside each spec.

- keep it narrow, usually 3-7 items
- make items concrete and outcome-oriented
- do not use the checklist as a work log
- do not use the checklist as a full project board
