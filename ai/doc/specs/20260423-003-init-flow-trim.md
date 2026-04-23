# Init-Flow Trim

## Metadata

### Source Plan / Request
Two narrow observations on the just-completed init flow:

1. The SOP starter's own `AGENTS.md` hardcodes a `### Plastic SCM rules` subsection. That content is backend-specific and should only appear in a project's own `AGENTS.md` after `init-plastic-scm` injects it from `ai/doc/templates/agents-version-control-section.md`. Keeping it in the tool-neutral starter violates the "no backend-specific content in the starter" intent.
2. `init-project-from-brief` personalizes identity and the control surface but leaves the starter's 14 historical task specs under `ai/doc/specs/` in the copied project. These are development history for the starter itself and are pure noise in a new project.

### Parent Phase
Minimal project control surface sustainment.

### Parent Plan
None. Narrow refinement of the init flow introduced by `20260423-002`.

### Status
in_progress

### Related Specs
- `ai/doc/specs/20260423-002-init-project-from-brief-skill.md` (completed parent slice; this refines its skill by adding one workflow step)
- `ai/doc/specs/20260423-001-init-plastic-scm-bootstrap.md` (the skill receiving the new pre-execution guardrail block)

### Release Sensitivity
normal

## Goal
Make the SOP starter's `AGENTS.md` stay backend-neutral while preserving Plastic-GUI protection during the pre-init window, and make `init-project-from-brief` leave a clean `ai/doc/specs/` in the copied project.

## Inputs
- `AGENTS.md` (`## Version control` section)
- `ai/skill/init-plastic-scm.md`
- `ai/skill/init-project-from-brief.md`
- `ai/doc/templates/agents-version-control-section.md` (for reference only)
- `ai/skill/skill-registry.md`

## Expected Outputs
- Starter `AGENTS.md` `## Version control` keeps only generic `Detection` + `Bootstrap` guidance; the Plastic-specific subsection is removed.
- `init-plastic-scm` begins with an explicit `Pre-execution guardrails` block that holds the Plastic GUI and Git-on-Plastic red lines while this skill runs, covering the pre-init window.
- `init-project-from-brief` gains one workflow step that deletes the starter's dated spec residue in the copied project and adjusts any README citation of deleted example specs, with results recorded in the init report.
- `skill-registry.md` row for `init-project-from-brief` briefly reflects the residue-cleanup addition.

## In Scope
- Remove the `### Plastic SCM rules` subsection from starter `AGENTS.md`.
- Insert a short `## Pre-execution guardrails` section near the top of `ai/skill/init-plastic-scm.md` (after `Purpose`, before `When to use`).
- Add a new numbered step to `ai/skill/init-project-from-brief.md` that cleans starter spec residue in the copied project, and renumber the `Emit init report` step accordingly.
- Update the `init-project-from-brief` row in `ai/skill/skill-registry.md` so the Outputs column mentions spec residue cleanup.

## Out of Scope
- Deleting or renaming any example spec file inside this starter repository.
- Changing the skill's behavior on `ai/doc/guides/*`, `ai/doc/templates/*`, or `ai/skill/*` (still prune suggestions only).
- Rewriting the starter's README.md. The starter's README continues to reference its own example specs because those files still exist here.
- Adding Plastic detection or command logic to any file other than `ai/skill/init-plastic-scm.md`.
- Introducing a separate "clean-starter-residue" reusable skill; the behavior lives inside `init-project-from-brief` as one step.
- Producing a `DEC-*` record.

## Allowed Edits
- `AGENTS.md`
- `ai/skill/init-plastic-scm.md`
- `ai/skill/init-project-from-brief.md`
- `ai/skill/skill-registry.md`
- this spec (new)

## Disallowed Edits
- `README.md` (starter's own README, unaffected)
- `ai/doc/guides/*`, `ai/doc/templates/*`, `ai/doc/facts/*`, `ai/doc/specs/*` except this new spec
- `project/*`
- `.cursor/rules/*`, `CLAUDE.md`

## Frozen / Dual-Track Constraints
- The starter stays tool-neutral and backend-neutral.
- `init-project-from-brief` must refuse to run inside the SOP starter itself; the new cleanup step must not be able to delete starter specs from the starter repository. The existing starter-self guard (detect that `ai/doc/facts/project-scope.md` still describes "reusable SOP starter") continues to be the gatekeeper and must be crossed before step execution.

## Affected Area
Starter `AGENTS.md`, the two init skills, and the skill registry.

## Task Checklist
- [ ] Edit `AGENTS.md`: drop `### Plastic SCM rules`; keep `### Detection` and `### Bootstrap`; keep the top paragraph explaining the Git-vs-other-backend situation.
- [ ] Edit `ai/skill/init-plastic-scm.md`: add `## Pre-execution guardrails` with the `cm diff` GUI ban, no-Git-on-Plastic rule, no-`.gitkeep`/`.gitattributes`/`.gitignore` reintroduction rule; note that these apply when invoked directly or via `init-project-from-brief` before the project's own AGENTS.md is updated.
- [ ] Edit `ai/skill/init-project-from-brief.md`: insert a new numbered step `Clean starter spec residue` before `Emit the init report`; renumber accordingly; update `Outputs` and `Non-Goals` when needed; extend `Stop conditions` so the starter-self guard clearly blocks this step.
- [ ] Edit `ai/skill/skill-registry.md`: adjust the `init-project-from-brief` row so the Outputs column references spec residue cleanup.
- [ ] Validate link closure and diff scope.

## Done When
- Grep for `Plastic SCM rules` in starter `AGENTS.md` returns no hit.
- `ai/skill/init-plastic-scm.md` contains a `## Pre-execution guardrails` section that names the `cm diff` GUI ban.
- `ai/skill/init-project-from-brief.md` contains a workflow step titled `Clean starter spec residue` that specifies the deletion pattern `YYYYMMDD-NNN-*.md` under `ai/doc/specs/`, keeps `ai/doc/specs/README.md`, and records results in the init report.
- `ai/skill/skill-registry.md` Outputs column for `init-project-from-brief` mentions spec residue cleanup.
- Diff is limited to files in Allowed Edits.

## Validation

### Black-box Checks
- `rg "Plastic SCM rules" AGENTS.md` returns no matches.
- `rg "Pre-execution guardrails" ai/skill/init-plastic-scm.md` returns at least one match.
- `rg "Clean starter spec residue" ai/skill/init-project-from-brief.md` returns at least one match.
- The new step explicitly excludes `ai/doc/specs/README.md` from deletion.
- The `init-project-from-brief` registry row mentions `spec residue` or equivalent cleanup wording.
- `git status --short` lists only the files above.

### White-box Needed
No

### White-box Trigger
Documentation and workflow wiring; no executable internal logic.

### Internal Logic To Protect
None.

## Repair / Rollback

### Repair Budget
One local repair pass for section anchoring, link closure, or renumbering.

### Rollback Scope
Revert only files in Allowed Edits.

### Escalation Condition
Return `needs_decision` if the user wants cleanup to also delete example guides or templates in the copied project, or to rewrite README.md references to deleted specs in the copied project automatically. Both expand scope beyond this slice.

## Write-back Needed
Yes (skill + registry refinement; no facts, memory, decisions, or experiments produced).

## Risks / Notes
- The renumbering must keep cross-references inside `init-project-from-brief` consistent. No other file currently refers to the skill's internal step numbers, so external link breakage is unlikely.
- Pre-execution guardrails must stay short and not duplicate the `agents-version-control-section.md` template; they are runtime rules for the skill executor, not content injected into the project.
