# Init-Plastic-SCM Bootstrap

## Metadata

### Source Plan / Request
Project startup on Plastic SCM (Unity Version Control) workspaces repeatedly hits the same problems: AI tools default to Git commands, Cursor opens the Plastic GUI via `cm diff`, `.gitignore` / `.gitkeep` remnants conflict with `ignore.conf`, and the project's AGENTS.md never learns that the workspace is not Git.

### Parent Phase
Minimal project control surface sustainment.

### Parent Plan
None. This narrows the recurring bootstrap problem into one reviewable slice.

### Status
done

### Related Specs
- `ai/doc/specs/20260422-001-sop-execution-link-hardening.md` (spec-first execution wiring consumed by this skill)

### Release Sensitivity
normal

## Goal
Give copied projects on Plastic SCM a single reusable bootstrap procedure that produces correct ignore files, removes Git-only artifacts, and declares the VCS backend in the project's own entrypoints, plus a minimal SOP-wide safety rail that prevents Cursor's default `cm` behavior from opening the Plastic GUI before the init ran.

## Inputs
- `AGENTS.md` (current SOP repository entrypoint)
- `README.md`
- `ai/doc/guides/new-project-sop.md`
- `ai/skill/skill-registry.md`
- `ai/skill/plan-to-spec.md`, `ai/skill/execute-from-spec.md`, `ai/skill/decision-recording.md`, `ai/skill/session-closeout.md`
- `E:/DataStore/jx3-lore-injection-lab/AGENTS.md` and `ignore.conf` as reference patterns (read-only, not modified)

## Expected Outputs
- A new bootstrap skill that runs once per copied project using Plastic SCM.
- Two generation templates for `ignore.conf` and `.cursorignore`.
- One paste-in template for a project AGENTS.md `## Version control` section.
- A new `## Version control` section in the SOP repository's own `AGENTS.md` that is VCS-neutral for detection and gives concrete Plastic red-line rules.
- Registry, guide, and README updates so the new skill and templates are discoverable through the existing adoption path.

## In Scope
- Create `ai/skill/init-plastic-scm.md`.
- Create `ai/doc/templates/ignore-conf-template.md`.
- Create `ai/doc/templates/cursorignore-template.md`.
- Create `ai/doc/templates/agents-version-control-section.md`.
- Add `## Version control` to `AGENTS.md` (this repository's own), containing:
  - VCS detection rule and marker list
  - Plastic SCM subsection with non-interactive `cm diff` enforcement, `ignore.conf` over `.gitignore`, no `.gitkeep` rule
  - Pointer to `ai/skill/init-plastic-scm.md`
- Register `init-plastic-scm` in `ai/skill/skill-registry.md`.
- Add a Plastic bootstrap pointer under the guided first-use path in `ai/doc/guides/new-project-sop.md`.
- Extend the `README.md` optional adoption set with the new skill and templates.

## Out of Scope
- `init-git`, `init-perforce`, `init-hg`, or any other backend-specific bootstrap skill.
- Automatic rewriting of the project's README free text or project description.
- Automatic production of a `DEC-*` decision record from init.
- A full `cm` command cheatsheet beyond the red-line rules needed to avoid GUI interactions.
- Runtime automation, CLI wrappers, or shell scripts.
- Changes to `project/memory/*`, `ai/doc/facts/*`, or existing task examples.

## Allowed Edits
- `AGENTS.md`
- `README.md`
- `ai/doc/guides/new-project-sop.md`
- `ai/skill/skill-registry.md`
- `ai/skill/init-plastic-scm.md` (new)
- `ai/doc/templates/ignore-conf-template.md` (new)
- `ai/doc/templates/cursorignore-template.md` (new)
- `ai/doc/templates/agents-version-control-section.md` (new)
- this spec
- `project/CURRENT.md` only if the slice materially changes current source of truth or next actions

## Disallowed Edits
- `project/memory/*`
- `ai/doc/facts/*`
- `.cursor/rules/*` (the VCS rule belongs in AGENTS.md, not as a new cursor rule file)
- existing specs, skills, guides, or templates not listed under Allowed Edits
- `CLAUDE.md` (adapter, already defers to AGENTS.md)

## Frozen / Dual-Track Constraints
- The SOP repository stays Git. Do not introduce a `.plastic/` marker or `ignore.conf` at this repo's root. Plastic-specific artifacts (`ignore.conf`, `.cursorignore`, project-level `## Version control` section) are produced **by** this skill for **copied projects**, never committed back into this starter.
- Keep `AGENTS.md` changes narrow: one new section, no rewriting existing sections.

## Affected Area
Repository-level operating rules (`AGENTS.md`), adoption docs (`README.md`, `new-project-sop.md`), and the `ai/skill/*` + `ai/doc/templates/*` trees.

## Task Checklist
- [x] Draft `init-plastic-scm` skill with 7-step workflow and explicit non-actions.
- [x] Draft `ignore-conf-template.md` generic skeleton with project-specific slot.
- [x] Draft `cursorignore-template.md` Cursor-indexing-only skeleton with SCM-boundary note.
- [x] Draft `agents-version-control-section.md` paste-in snippet for target projects.
- [x] Add `## Version control` section to this repo's `AGENTS.md`.
- [x] Register `init-plastic-scm` in `skill-registry.md`.
- [x] Add Plastic bootstrap pointer to `new-project-sop.md` guided path.
- [x] Extend `README.md` optional set with the new skill and templates.
- [x] Validate link closure and red-line keyword presence.

## Done When
A project cloned from this starter can identify Plastic SCM, run one skill to produce correct `ignore.conf`, `.cursorignore`, a project-specific AGENTS.md `## Version control` section, an updated `project/CURRENT.md` VCS declaration, and a removal list for `.gitignore` and all `.gitkeep`, and even before running the skill Cursor is prevented by this repository's `AGENTS.md` from using GUI-opening `cm diff` forms.

## Validation

### Black-box Checks
- `AGENTS.md` search finds `## Version control`, `.plastic/plastic.selector`, `cm diff`, `--format`, `ignore.conf`, and a pointer to `ai/skill/init-plastic-scm.md`.
- `ai/skill/skill-registry.md` contains an `init-plastic-scm` row with Trigger, Inputs, Outputs.
- `ai/doc/guides/new-project-sop.md` contains a Plastic bootstrap pointer.
- `README.md` optional-set section lists `ai/skill/init-plastic-scm.md` and the two templates.
- `ai/skill/init-plastic-scm.md` references `ai/doc/templates/ignore-conf-template.md`, `ai/doc/templates/cursorignore-template.md`, and `ai/doc/templates/agents-version-control-section.md`.
- `ai/doc/templates/cursorignore-template.md` top comment explicitly says SCM ignores live elsewhere.
- `ai/doc/templates/ignore-conf-template.md` top comment explicitly says it is for Plastic and differs from `.gitignore`.
- Git diff review confirms only files listed under Allowed Edits changed.

### White-box Needed
No

### White-box Trigger
Documentation and skill wiring change. No executable internal logic is introduced.

### Internal Logic To Protect
None.

## Repair / Rollback

### Repair Budget
One local repair pass for broken links, missing registry fields, duplicated wording across `AGENTS.md` and templates, or ignore-pattern errors in the templates.

### Rollback Scope
Revert only the files listed in Allowed Edits if the new section in `AGENTS.md` or the skill creates ambiguity with existing workflow rules.

### Escalation Condition
Return `needs_decision` if the user wants the init skill to also handle non-Plastic backends (Perforce, hg, svn) or to auto-rewrite README/project description free text. Those are explicitly out of scope for this slice.

## Write-back Needed
Yes

Write back: new reusable workflow into `ai/skill/*` + registry; new templates into `ai/doc/templates/*`; adoption pointers into `README.md` and `ai/doc/guides/new-project-sop.md`; one new operating-rule section in `AGENTS.md`. No facts, memory, decisions, or experiments are produced by this slice.

## Risks / Notes
- Avoid bloating `AGENTS.md`: the new section must be short and must not duplicate rules that belong inside the skill or templates.
- Avoid turning the init skill into a general VCS framework. Keep it narrow to Plastic SCM; a future backend gets a sibling skill, not a hidden fork inside this one.
- The init skill deletes `.gitignore` and `.gitkeep`. That must be surfaced in the init report and only after the detection step confirms the workspace is Plastic (not a dual-track Git+Plastic layout).
