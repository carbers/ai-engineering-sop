# SOP Execution Link Hardening

## Metadata

### Source Plan / Request
User requested landing the structured SOP audit recommendations.

### Parent Phase
Minimal project control surface sustainment.

### Parent Plan
None. This narrows the audit findings into one reviewable documentation slice.

### Status
done

### Related Specs
None.

### Release Sensitivity
normal

## Goal
Close the main SOP workflow gaps found in the audit without redesigning the repository.

## Inputs
- `AGENTS.md`
- `.cursor/rules/*`
- `ai/doc/templates/task-spec-template.md`
- `ai/doc/templates/current-template.md`
- `ai/skill/*`
- `project/CURRENT.md`
- `project/decisions/README.md`

## Expected Outputs
- A reusable execution skill that starts from a task spec.
- Small reusable skills for replan/escalation and decision recording.
- A compact autopilot skill that does not bypass spec-first execution.
- Updated skill registry and core workflow references.
- A decision record backing the control-surface frozen decisions already listed in `project/CURRENT.md`.

## In Scope
- Add missing skills under `ai/skill/`.
- Update `ai/skill/skill-registry.md`.
- Refine workflow and spec template wording for spec-binding, validation, closeout, and routing labels.
- Add one decision record under `project/decisions/`.
- Update `project/CURRENT.md` only where the source of truth or frozen decision pointers changed.

## Out of Scope
- Creating a broad reporting system.
- Adding runtime automation or CLI behavior.
- Rewriting existing examples.
- Adding a dual-track workflow skill without concrete local dual-track evidence.

## Allowed Edits
- `AGENTS.md`
- `.cursor/rules/workflow.mdc`
- `README.md`
- `ai/doc/guides/new-project-sop.md`
- `ai/doc/guides/task-lifecycle-and-escalation.md`
- `ai/doc/templates/task-spec-template.md`
- `ai/doc/templates/current-template.md`
- `ai/skill/*`
- `project/CURRENT.md`
- `project/decisions/*`
- this spec

## Disallowed Edits
- Product-facing docs outside the listed files.
- Existing task examples unless validation exposes a broken reference.
- `project/memory/*` unless a stable repeated memory is created by this slice.

## Affected Area
SOP workflow documentation, reusable skills, and project control-surface decision backing.

## Task Checklist
- [x] Add spec-first execution, replan/escalation, decision-recording, and autopilot skills.
- [x] Register new skills and link the plan-to-spec handoff to execution.
- [x] Refine workflow rules and task spec template for spec-binding, validation, write-back labels, and optional freeze/dual-track constraints.
- [x] Back current control-surface frozen decisions with a decision record and update `project/CURRENT.md`.
- [x] Validate links, registry coverage, and key wording by search.

## Done When
The SOP has a readable path from plan to spec to spec-bound execution, escalation and decision routes are reusable, and current frozen control-surface decisions have a recoverable decision record.

## Validation

### Black-box Checks
- Search confirms new skills are registered.
- Search confirms `execute-from-spec` is referenced by workflow and plan-to-spec.
- Search confirms `spec-binding`, `replan_required`, `needs_decision`, and routing-label guidance are present in the appropriate workflow/template files.
- Git diff review shows only in-scope documentation files changed.

### White-box Needed
No

### White-box Trigger
This is a documentation workflow change with no executable internal logic.

### Internal Logic To Protect
None.

## Repair / Rollback

### Repair Budget
One local repair pass for broken links, missing registry entries, or unclear duplicated wording.

### Rollback Scope
Revert only files changed by this spec if the workflow becomes less coherent.

### Escalation Condition
Return `needs_decision` if the user wants a concrete dual-track or frozen-byte policy that is not inferable from current repository materials.

## Write-back Needed
Yes

Write back new reusable workflows to `ai/skill/*`, update `ai/skill/skill-registry.md`, and add a project decision record under `project/decisions/*`.
Use labels only as routing hints, not file categories.

## Risks / Notes
Avoid turning autopilot into a bypass around the spec-first workflow.
