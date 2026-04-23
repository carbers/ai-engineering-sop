# CURRENT

## Current phase
Operate with the minimal project control surface and its sustaining assets in place.

## Current target
Keep a recovery-first human control surface at the repository root while preserving the spec-first execution model.

## Active slice
Use the minimal control surface as the default recovery path and keep it small as later work lands.

## In scope now
- Keep `project/CURRENT.md` as the recovery-first human artifact
- Keep `project/memory/*` as the long-lived project-memory layer for repeated agreements and patterns
- Keep `project/DOC_MAP.md` role-based and short
- Use `project/decisions/*` and `project/experiments/*` only for durable project-level outcomes
- Maintain the supporting templates, worked example, and `session-closeout` workflow as lightweight sustaining assets
- Support optional batch-level release readiness without turning it into the default task path

## Out of scope now
- `reports/` or `archive/`
- Broad reporting, dashboard, or ADR systems
- turning `project/*` into a project board or work log
- duplicating execution detail that already belongs in specs, facts, or skills

## Current source of truth
- `project/DOC_MAP.md` for reading order across the control surface
- `AGENTS.md` for repository-level operating rules
- `project/decisions/DEC-20260422-001-project-control-surface.md` for the active frozen control-surface decision
- The current active task spec under `ai/doc/specs/*`, when implementation is underway

## Frozen decisions
- `project/decisions/DEC-20260422-001-project-control-surface.md` — `project/` is the default root-level human-facing control surface, with `project/CURRENT.md` as the recovery-first artifact and `project/memory/*` as the long-lived project-memory layer. The control surface stays intentionally narrow and does not become a broad documentation hub.

## Latest experiment
None yet.

## Next 3 actions
1. Execute implementation from active specs through `ai/skill/execute-from-spec.md`.
2. Use `session-closeout` when future slices may affect current state, memory, decisions, experiments, facts, or skills.
3. Keep `project/CURRENT.md`, `project/memory/*`, and `project/DOC_MAP.md` small as later changes land.

## Risks to watch
- `project/CURRENT.md` or `project/DOC_MAP.md` drifting into a project board or duplicate navigation layer instead of staying recovery-focused.
- `project/memory/*` drifting into a running log or duplicate of `ai/doc/facts/*`.
- `ai/doc/facts/project-scope.md` treated like a live status file instead of a slower-moving scope fact.
