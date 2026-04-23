# Init-Project-From-Brief Skill

## Metadata

### Source Plan / Request
Users commonly enter a freshly copied SOP starter with a project brief in hand and want the starter transformed into a project-specific initial state (identity, control surface, scope fact) before any plan or spec work. The current `ai/doc/guides/new-project-sop.md` is a human-reading guide; running its steps manually each time is inconvenient.

### Parent Phase
Minimal project control surface sustainment.

### Parent Plan
None. This narrows the "turn copied starter into real project" recurring need into one reviewable slice.

### Status
done

### Related Specs
- `ai/doc/specs/20260423-001-init-plastic-scm-bootstrap.md` (delegated to when the copied project is on Plastic SCM)
- `ai/doc/specs/20260422-001-sop-execution-link-hardening.md` (spec-first workflow the new skill hands off to)

### Release Sensitivity
normal

## Goal
Give copied SOP starters a single reusable bootstrap skill that takes a project brief and initializes project identity, the control surface, and the scope fact, while keeping free-form text under human control and composing cleanly with `init-plastic-scm`, `plan-to-spec`, and `execute-from-spec`.

## Inputs
- `ai/doc/guides/new-project-sop.md` (human-reading guide, to be shrunk)
- `ai/doc/templates/current-template.md`
- `ai/doc/templates/doc-map-template.md`
- `ai/doc/templates/project-scope-template.md`
- `ai/doc/templates/project-memory-readme-template.md`, `project-memory-page-template.md`
- `ai/skill/init-plastic-scm.md` (downstream delegate)
- `ai/skill/plan-to-spec.md` (downstream handoff)
- `AGENTS.md`, `README.md`, `ai/skill/skill-registry.md`

## Expected Outputs
- A new reusable skill `ai/skill/init-project-from-brief.md` that reads a brief, extracts structured fields, and produces project-specific identity, control surface, and scope artifacts.
- A shrunk `ai/doc/guides/new-project-sop.md` that points at the skill for the executable path while staying a short human-reading reference.
- Registry, README, and AGENTS.md pointers so the new skill is discoverable.

## In Scope
- Create `ai/skill/init-project-from-brief.md`.
- Shrink `ai/doc/guides/new-project-sop.md` to a concise reference + explicit pointer to the new skill.
- Register the skill in `ai/skill/skill-registry.md`.
- Add a short bootstrap pointer to `AGENTS.md` (adjacent to the `Version control` bootstrap pointer) so AI tools know to run the skill before plan work on a copied project.
- Update `README.md` adoption sections to list the new skill.

## Out of Scope
- Producing a plan, spec, or code from the brief.
- Deciding tech stack, architecture, or file layout.
- Auto-rewriting free-form paragraphs in README.md (only the project-identity header block is structurally replaced; long prose is flagged for human review).
- Auto-producing a `DEC-*` decision record.
- Handling non-text briefs (images, spreadsheets) or multi-language brief merging.
- Pruning unused starter files. The skill only emits a "consider pruning" list in its report.
- Running the skill inside this SOP starter repository itself.

## Allowed Edits
- `AGENTS.md`
- `README.md`
- `ai/doc/guides/new-project-sop.md`
- `ai/skill/skill-registry.md`
- `ai/skill/init-project-from-brief.md` (new)
- this spec (new)

## Disallowed Edits
- `ai/doc/facts/project-scope.md` (describes the SOP starter's own scope; the new skill describes how a copied project re-seeds it, not this file)
- `project/CURRENT.md`, `project/DOC_MAP.md`, `project/memory/*` (same reason)
- Existing templates, facts, examples, specs, or other skills not listed under Allowed Edits
- `.cursor/rules/*`, `CLAUDE.md`
- `ai/skill/init-plastic-scm.md` (stable, only referenced)

## Frozen / Dual-Track Constraints
- The SOP starter remains tool-neutral and generic. The new skill must be written as a procedure that a copied project will run; do not embed one project's brief content as an example hardcoded into the skill.
- The skill must not rewrite the copied project's free-form README paragraphs beyond a narrow, clearly delimited identity block.

## Affected Area
Adoption-path documentation (`AGENTS.md`, `README.md`, `ai/doc/guides/new-project-sop.md`), skill registry, and the `ai/skill/*` tree.

## Task Checklist
- [ ] Draft `init-project-from-brief` skill with explicit fields-to-extract, Q&A fallback, 8-step workflow, delegation to `init-plastic-scm`, handoff to `plan-to-spec`, and init-report shape.
- [ ] Shrink `new-project-sop.md` to a short reference that points at the new skill for the executable path and keeps a compact day-one checklist for manual readers.
- [ ] Register `init-project-from-brief` in `skill-registry.md`.
- [ ] Add a bootstrap pointer in `AGENTS.md` near the Version-control bootstrap pointer.
- [ ] Update `README.md` adoption sets and "Copy Into A Real Project" sections to name the new skill as the recommended first step.
- [ ] Validate link closure and diff scope.

## Done When
A copied SOP starter can run `init-project-from-brief` with a project brief and get:
- structured project-identity header replacing the SOP-starter identity in `README.md`
- structured project-purpose block replacing the SOP-starter `## Repository purpose` in `AGENTS.md`
- initialized `project/CURRENT.md` and `project/DOC_MAP.md` seeded from templates with project-specific content
- seeded `ai/doc/facts/project-scope.md` with structured scope from the brief
- delegation to `init-plastic-scm` when the workspace is Plastic
- an init report with change list, human-review flags, prune suggestions, and a single next-step pointer to `plan-to-spec`
- before running the skill, AI tools reading the starter's `AGENTS.md` know that running the skill is the expected first step on a copied project.

## Validation

### Black-box Checks
- `ai/skill/init-project-from-brief.md` exists with Purpose, When to use, Inputs, Outputs, Non-Goals, Workflow (8 steps), Stop conditions, Common failure modes.
- The skill explicitly references `ai/skill/init-plastic-scm.md` (delegation), `ai/doc/templates/current-template.md`, `ai/doc/templates/doc-map-template.md`, `ai/doc/templates/project-scope-template.md`, `ai/doc/templates/project-memory-readme-template.md`, and `ai/skill/plan-to-spec.md` (handoff).
- `skill-registry.md` contains an `init-project-from-brief` row with Purpose, Trigger, Inputs, Outputs, Status.
- `new-project-sop.md` is shorter than before, no longer duplicates the full checklist prose, and contains an explicit pointer to `ai/skill/init-project-from-brief.md`.
- `AGENTS.md` contains a bootstrap pointer sentence naming `ai/skill/init-project-from-brief.md`.
- `README.md` mentions `ai/skill/init-project-from-brief.md` at least once in an adoption section.
- Git diff review confirms only files under Allowed Edits changed.

### White-box Needed
No

### White-box Trigger
Documentation and workflow wiring; no executable internal logic introduced.

### Internal Logic To Protect
None.

## Repair / Rollback

### Repair Budget
One local repair pass for broken links, missing registry fields, or duplicated content between the shrunk guide and the new skill.

### Rollback Scope
Revert only files listed in Allowed Edits if the new skill creates ambiguity with existing workflow rules.

### Escalation Condition
Return `needs_decision` if the user wants the skill to also auto-prune starter files (delete unused guides/examples) or to auto-write long free-form prose in README.md. Those are explicitly out of scope for this slice.

## Write-back Needed
Yes

Write back: new reusable workflow into `ai/skill/*` + registry; shrunk guide into `ai/doc/guides/*`; adoption pointers into `README.md` and `AGENTS.md`. No facts, memory, decisions, or experiments are produced by this slice.

## Risks / Notes
- Avoid duplicating the skill's workflow prose inside the shrunk guide. The guide becomes a pointer, not a parallel manual.
- Avoid inflating the skill with brief-parsing rules that cannot be faithfully executed; describe the fields to extract and let the executing agent parse the concrete brief at runtime.
- Keep README and AGENTS.md replacement scopes narrow: only the clearly delimited identity blocks. Long prose must be flagged to humans in the init report.
