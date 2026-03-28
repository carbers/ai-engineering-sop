# Specs Directory

Task specs are the default execution artifact between planning and implementation.
That remains true even when longer work is tracked with explicit phases, main plans, or sub-plans.

## Purpose

Use `ai/doc/specs/*` to hold narrow task specs that:
- bridge plans and implementation
- keep execution reviewable
- stay small enough to refine during iteration

This directory does not need a central index.
Use filenames plus optional `Related Specs` links for navigation.

## Example

See these examples:

- `20260101-001-example-api-rate-limiting.md` for a classic narrow implementation spec
- `20260102-001-example-phase-aware-guide-slice.md` for thin use of the phase-aware fields
- `20260103-001-example-adoption-entrypoint-slice.md` for one complete phase-aware task slice inside a longer chain
- `20260104-001-example-first-copied-project-quickstart.md` for a first-use small-task spec on the default lightweight path
- `20260328-003-example-project-control-closeout-loop.md` for a small-task example that also shows the minimal control-surface closeout path

See `ai/doc/guides/phase-aware-canonical-example.md` for a closed long-task example that links `project_target -> current_target -> phase -> main_plan -> sub_plan -> task -> validation -> write-back`.
If you want the matching small-task reference, start with `20260104-001-example-first-copied-project-quickstart.md`.

## Naming

Store each spec as:

`ai/doc/specs/YYYYMMDD-NNN-task-slug.md`

- `YYYYMMDD` is the spec creation date
- `NNN` is the same-day sequence, starting at `001`
- choose the next available same-day sequence by scanning existing spec filenames
- never renumber existing specs
- `task-slug` is lowercase kebab-case

Example:

`ai/doc/specs/20260322-001-auth-session-hardening.md`

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

Use only these steady-state values in the spec's `Status` field:

- `draft`: the spec exists, but implementation should not start yet
- `todo`: the spec is ready to start, but implementation has not begun
- `in_progress`: implementation for this spec has started
- `validating`: implementation is complete enough for required validation to run
- `repairing`: validation exposed a fixable gap and the task is still inside its current repair budget
- `rolled_back`: the task's in-scope changes were reverted inside the declared rollback scope
- `blocked`: progress is waiting on a prerequisite, dependency, or decision
- `done`: `Done When` is satisfied and required validation has passed

Checklist completion alone does not make a spec `done`.
Required validation must also pass.

Treat `replan_required` and `needs_decision` as escalation outcomes, not normal steady-state status values.
If a task stops for escalation, keep `Status` on the last accurate steady-state value and record the escalation outcome in `Risks / Notes` or the execution handoff.
If they occur, return to the planning or decision layer instead of stretching the current spec.

Older specs may still use `in-progress`.
They do not need to be rewritten retroactively; use the newer status set for new or materially revised specs.

## Phase-Aware Fields

For long-running, multi-phase, dependency-heavy, or repair-sensitive work, keep the parent mapping and execution contract explicit in the spec.
The main additions are:

- `Parent Phase`
- `Parent Plan`
- `Inputs`
- `Expected Outputs`
- `Allowed Edits`
- `Disallowed Edits`
- `Repair Budget`
- `Rollback Scope`
- `Escalation Condition`

Do not treat these fields as a reason to turn one spec into a project board.
If the spec grows large, split it instead.

## Release Sensitivity

Task specs are not release records.
Do not add release-readiness paperwork to every spec.

If a task may need special attention in a future real-product release batch, use the optional `Release Sensitivity` field:

- `normal`: no special batch-level release handling is expected
- `release_sensitive`: a future release batch should call out this slice because of deployment, migration, config, compatibility, auth/billing, performance/reliability, or rollback concerns

If the field is omitted, treat it as `normal`.
When a real release is being prepared, aggregate the few release-sensitive slices at the batch level instead of duplicating release review inside every spec.
Use `ai/doc/templates/release-batch-template.md` if the project wants a lightweight release record.

## Checklist

Use a short Markdown checkbox list inside each spec.

- keep it narrow, usually 3-7 items
- make items concrete and outcome-oriented
- do not use the checklist as a work log
- do not use the checklist as a full project board
