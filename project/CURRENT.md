# CURRENT

## Current phase
Operate with the minimal project control surface and its sustaining assets in place.

## Current target
Keep a recovery-first human control surface at the repository root while preserving the spec-first execution model.

## Active slice
Use the minimal control surface as the default recovery path and keep it small as later work lands.

## In scope now
- Keep `project/CURRENT.md` as the recovery-first human artifact
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
- `project/DOC_MAP.md`
- `AGENTS.md`
- `ai/doc/facts/project-scope.md` for stable scope and boundary context
- the current active task spec in `ai/doc/specs/*`, if implementation work is underway

## Frozen decisions
- `project/` is the default name for the root-level human-facing control surface.
- `project/CURRENT.md` is the recovery-first artifact.
- The control surface stays intentionally narrow and does not become a broad documentation hub.
- Supporting templates and closeout guidance exist to keep the control surface current without duplicating execution artifacts.

## Latest experiment
None yet.

## Next 3 actions
1. Keep `project/CURRENT.md` and `project/DOC_MAP.md` small as later changes land.
2. Use `session-closeout` when future slices may affect current state, decisions, experiments, facts, or skills.
3. Add new control-surface artifacts only when a repeated recovery problem appears.

## Risks to watch
- `project/DOC_MAP.md` could grow into a duplicate navigation layer.
- `project/CURRENT.md` could drift into a project board instead of staying recovery-focused.
- Entry wording could blur the boundary between project control and AI execution assets.
- `ai/doc/facts/project-scope.md` could be treated like a live status file instead of a slower-moving scope fact.
