# DEC-20260422-001 Project Control Surface

## Status
accepted

## Context
This repository needs a small human-facing recovery layer without turning the SOP starter into a broad reporting, dashboard, or archive system.

`project/CURRENT.md`, `project/memory/*`, and related control-surface assets were already listed as frozen decisions in `project/CURRENT.md`, but the rationale was not recoverable from a decision record.

## Options Considered
- Keep only `ai/*` workflow assets and omit a root-level project control surface.
- Use a broad `reports/` or `archive/` structure for current state and decisions.
- Use a narrow root-level `project/` control surface with explicit routing rules.

## Chosen Option
Use `project/` as the default root-level human-facing control surface.

Within that control surface:
- `project/CURRENT.md` is the recovery-first current-state artifact.
- `project/memory/*` holds long-lived project-specific memory, not task logs or decision ledgers.
- `project/decisions/*` holds frozen project-level decisions worth re-reading later.
- `project/experiments/*` holds readable experiment summaries only when real experiments occur.

## Reasoning
The narrow `project/` control surface gives returning humans a stable recovery path while preserving `ai/*` for AI-managed workflow assets.
It also prevents current state, long-lived memory, facts, decisions, and experiments from collapsing into one mixed archive.

## Consequences
- `project/CURRENT.md` should stay short and should point to active sources of truth.
- Frozen decisions currently in force should point to decision records instead of carrying full rationale in CURRENT.
- `project/memory/*` should remain empty or sparse until repeated project-specific memory exists.
- `reports/` and `archive/` are out of scope for the current control model.

## Revisit Trigger
Revisit this decision if copied projects repeatedly need a different human-facing control root, or if `project/*` begins to behave like a project board, archive, or duplicate facts directory.
