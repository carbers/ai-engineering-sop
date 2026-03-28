# Minimal Project Control Surface

Keep this task narrow. The goal is to introduce a recovery-first control surface, not a broad project documentation system.

## Metadata

### Source Plan / Request
Product direction to define `project/` as a minimal control surface whose primary purpose is reducing context-recovery cost.

### Parent Phase
MVP of the project control surface

### Parent Plan
Minimal recovery control surface

### Status
done

### Related Specs
None.

## Goal
Introduce the smallest viable `project/` control surface and wire the repository entrypoints to it.

## Phase-Aware Contract

## Inputs
- Existing repository entrypoints and boundary docs in `README.md`, `AGENTS.md`, and `ai/README.md`
- Existing facts routing guidance in `ai/doc/facts/facts-index.md`
- Product decision to center the control surface on `project/CURRENT.md`

## Expected Outputs
- A new root-level `project/` directory with minimal control files
- Updated entrypoint and boundary docs that explain the `project/*` versus `ai/*` split

## In Scope
- Add `project/README.md`
- Add `project/CURRENT.md`
- Add `project/DOC_MAP.md`
- Add lightweight `project/decisions/README.md` and `project/experiments/README.md`
- Update root and AI entrypoint docs to point humans to `project/CURRENT.md`
- Add a narrow control-sync rule in `AGENTS.md`

## Out of Scope
- New templates under `ai/doc/templates/`
- New skills under `ai/skill/`
- `reports/` or `archive/`
- Broad reporting or ADR systems
- Changes to the core plan/spec/validation workflow

## Allowed Edits
- `README.md`
- `AGENTS.md`
- `ai/README.md`
- New files under `project/`

## Disallowed Edits
- `ai/skill/*`
- `ai/doc/templates/*`
- `ai/doc/facts/*`

## Affected Area
- Repository entrypoints
- AI namespace boundary docs
- New root-level human-facing control surface

## Task Checklist
- [x] Add the minimal `project/` control-surface files
- [x] Update root README to establish a recovery-first path
- [x] Update AGENTS and ai namespace docs to recognize the new layer
- [x] Keep the new surface intentionally narrow and non-duplicative

## Done When
The repository has a root-level `project/` control surface centered on `project/CURRENT.md`, and the entrypoint docs clearly direct human readers there without turning `project/` into a broad documentation hub.

## Validation

### Black-box Checks
- A human reader can start at `README.md` and find the recommended recovery path into `project/CURRENT.md`
- A reader of `AGENTS.md` and `ai/README.md` can distinguish the human control surface from the AI execution namespace
- The `project/` directory contains only the minimal recovery-oriented files declared in scope

### White-box Needed
No

### White-box Trigger
This slice is documentation and structure only; black-box review of wording and navigation is sufficient.

### Internal Logic To Protect
N/A

## Repair / Rollback

### Repair Budget
One focused revision pass if the wording creates ambiguity between `project/*` and `ai/*`.

### Rollback Scope
All new `project/` files and associated wording updates in the entrypoint docs.

### Escalation Condition
Stop if the minimal control surface starts to require templates, skills, or additional directories to make sense.

## Write-back Needed
No

## Risks / Notes
The main risk is creating a second navigation system that duplicates `README.md` and `ai/README.md` instead of shortening recovery time.