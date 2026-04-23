# Skill: init-project-from-brief

## Purpose
Turn a freshly copied SOP starter into a project-specific initial state using one or more project brief documents, so later work can enter `plan-to-spec` / `execute-from-spec` against the real project rather than the starter's default scaffolding.

This skill runs **once** per copied project.

## When to use
Use this skill when:
- the SOP starter has been copied into a new project directory
- the user arrives with one or more project brief documents (or is willing to answer structured questions interactively)
- no prior init has been performed (the copied `AGENTS.md` still contains the SOP starter's `## Repository purpose` wording and `project/CURRENT.md` still matches the starter example)

Do not use this skill:
- inside the SOP starter repository itself (the starter's own identity is not a project)
- after an earlier init already personalized `AGENTS.md` / `README.md` / `project/CURRENT.md`
- as a substitute for planning or spec derivation (this skill ends by handing off to `plan-to-spec`)

## Inputs
- one or more project brief documents (file paths, pasted text, or both)
- optional interactive Q&A answers when the brief is missing required fields
- the copied starter's current `AGENTS.md`, `README.md`, `project/CURRENT.md`, `project/DOC_MAP.md`, `ai/doc/facts/project-scope.md`
- `ai/doc/templates/current-template.md`
- `ai/doc/templates/doc-map-template.md`
- `ai/doc/templates/project-scope-template.md`
- `ai/doc/templates/project-memory-readme-template.md`
- `ai/skill/init-plastic-scm.md` (delegated to when Plastic is detected)
- `ai/skill/plan-to-spec.md` (handed off to at the end)

## Outputs
- personalized `AGENTS.md` `## Repository purpose` block (structured bullets)
- personalized `README.md` identity header (title + one-line description + structured bullets; long prose untouched)
- initialized `project/CURRENT.md` from template with project-specific scaffolding (not the starter's example state)
- initialized `project/DOC_MAP.md` from template
- seeded `ai/doc/facts/project-scope.md` from `project-scope-template.md` with scope bullets drawn from the brief
- `project/memory/*` left as empty scaffolding from `project-memory-readme-template.md` unless the brief contains stable repeated agreements
- cleaned `ai/doc/specs/` so only the specs guide `README.md` remains; starter development history and starter example specs are deleted, and README references to deleted example spec filenames are trimmed
- delegation to `init-plastic-scm` when `.plastic/plastic.selector` exists
- an init report with: changes made, human-review flags, prune suggestions, and a single next-step handoff to `plan-to-spec`

## Non-Goals
- producing a plan, a task spec, or any code
- deciding technology stack, architecture, directory layout, or test framework
- rewriting long free-form prose in `README.md` (only the identity header is structurally replaced)
- deleting or renaming starter files (the skill only suggests prune candidates in the report)
- producing a `DEC-*` decision record automatically
- translating briefs across languages
- parsing non-text briefs (images, spreadsheets, binary formats)

## Fields to extract from the brief
Treat these as the minimum structured fields. Missing ones trigger Q&A fallback.

- `project_name` (short, human-readable)
- `one_line_description`
- `primary_problem` (what is broken, missing, or hard without this project)
- `primary_outcome` (what success looks like; one sentence)
- `non_goals` (at least one; explicit exclusions)
- `key_constraints` (technical, organizational, or time-boxed)
- `in_scope_now` (bullets describing the current phase if known; otherwise `to be defined in the first plan`)
- `out_of_scope_now` (bullets)
- `open_risks` (optional but recommended)
- `known_modules_or_boundaries` (optional; named subsystems, data sources, external interfaces)
- `current_phase` (optional; `to be defined in the first plan` is acceptable)

## Workflow

### 1. Read the brief
Read each provided brief document. Extract the fields listed above.
Do not invent values. Mark unfilled fields as `missing` for step 3.

### 2. Detect the workspace VCS
Check for version control markers at the repo root:
- `.git/` for Git
- `.plastic/plastic.selector` for Plastic SCM

If `.plastic/plastic.selector` exists, call `ai/skill/init-plastic-scm.md` first and wait for its init report. Continue this skill only after Plastic bootstrap returns cleanly.
If both markers are present, stop and return `needs_decision`.

### 3. Fill missing fields
For every field still marked `missing` after brief extraction, ask the user one focused question at a time. Keep questions tight:
- `What is the primary outcome of this project in one sentence?`
- `List at least one non-goal.`
- `What is one key constraint that shapes the current phase?`

If the user declines to answer a required field (`project_name`, `one_line_description`, `primary_outcome`, at least one `non_goal`), stop and return `needs_decision`. Do not continue with placeholder identity.

### 4. Replace `## Repository purpose` in `AGENTS.md`
Locate the existing `## Repository purpose` section in the copied `AGENTS.md`.
Replace it with a structured block of this shape:

```
## Repository purpose

This repository is **<project_name>**.

<one_line_description>

### Primary outcome
- <primary_outcome>

### Non-goals
- <non_goal_1>
- <non_goal_2>
- ...

### Key constraints
- <key_constraint_1>
- ...

This project uses the AI Engineering SOP workflow model (plan -> task spec -> implement -> validate -> selective write-back). See the sections below for details.
```

Do not alter the rest of `AGENTS.md`.
If the section is already personalized (does not match the SOP starter wording), stop and return `needs_decision`.

### 5. Replace the identity header in `README.md`
Locate the top identity block in `README.md` (the H1 title plus the first two or three paragraphs describing the SOP starter).
Replace it with:

```
# <project_name>

<one_line_description>

## Current focus
- Primary outcome: <primary_outcome>
- Non-goals: <non_goal_1>, <non_goal_2>, ...
- Key constraints: <key_constraint_1>, ...

## How this project operates
This project uses the AI Engineering SOP workflow. Start here:

- `AGENTS.md` for AI tool operating rules
- `project/CURRENT.md` for current operating state
- `ai/skill/plan-to-spec.md` to derive the next task spec
- `ai/skill/execute-from-spec.md` to implement from a spec
```

Leave the remaining sections of `README.md` unchanged. Flag the starter-specific sections (`Adopting this starter`, `Minimal adoption path`, `Copy Into A Real Project In 10 Minutes`, `What's New`) in the init report as "consider pruning or rewriting for this project".

### 6. Initialize the control surface
Replace `project/CURRENT.md` content by instantiating `ai/doc/templates/current-template.md` with:
- `Current phase`: `current_phase` or `to be defined in first plan`
- `Current target`: narrower objective from the brief, or `to be defined in first plan`
- `Active slice`: `None yet. First action: run ai/skill/plan-to-spec.md on the first brief-derived plan.`
- `In scope now`: `in_scope_now`
- `Out of scope now`: `out_of_scope_now`
- `Current source of truth`: `AGENTS.md`, `ai/doc/facts/project-scope.md`, `project/memory/README.md` (if kept), and the placeholder note "no active spec yet"
- `Frozen decisions`: `None yet.`
- `Latest experiment`: `None yet.`
- `Next 3 actions`: `1. Run ai/skill/plan-to-spec.md with the brief-derived plan.` `2. Create the first task spec under ai/doc/specs/.` `3. Execute from that spec via ai/skill/execute-from-spec.md.`
- `Risks to watch`: `open_risks` plus `control surface may grow stale if closeout discipline is not maintained`

Replace `project/DOC_MAP.md` by instantiating `ai/doc/templates/doc-map-template.md` with the default reading order (`project/CURRENT.md` first, then `AGENTS.md`, then active spec or `ai/doc/specs/README.md`, then `ai/doc/facts/project-scope.md`).
Keep the DOC_MAP role-based; do not list every file in the repo.

If `project/memory/*` is kept in the copied project, initialize `project/memory/README.md` from `project-memory-readme-template.md` as an empty scaffold, with a one-line note that memory pages should be added only when stable repeated agreements emerge.

### 7. Seed `ai/doc/facts/project-scope.md`
Instantiate `ai/doc/templates/project-scope-template.md` with:
- `Project Target`: `primary_outcome`
- `Stable Current Target`: narrower current objective, or the same as `Project Target` when unclear
- `Stable Phase Goal`: from `current_phase` field when present, otherwise `to be defined in first plan`
- `In Scope`: `in_scope_now`
- `Out of Scope`: `non_goals` + `out_of_scope_now`
- `Key Constraints`: `key_constraints`
- `Current Assumptions`: record the assumptions that the brief implies; if none are stated, leave a single bullet `to be refined during the first plan`
- `Open Risks`: `open_risks`

Do not leave the SOP starter's own scope text in place. This file is seeded fresh per project.

### 8. Clean starter spec residue
In the copied project, `ai/doc/specs/` still contains the SOP starter's own task specs and example specs carried over from the starter repository. These are development history for the starter itself and are noise in a new project.

Delete every file under `ai/doc/specs/` whose filename matches the dated spec pattern `YYYYMMDD-NNN-*.md` (for example `20260104-001-example-first-copied-project-quickstart.md` or `20260422-001-sop-execution-link-hardening.md`). Keep `ai/doc/specs/README.md`; that is the specs guide and is not a spec instance.

After deletion, scan the copied `README.md` and the copied `ai/doc/guides/*` for citations that name any deleted spec filename. Remove those specific lines or bullet items; do not rewrite surrounding prose. Generic phrases like "see the example spec" that do not name a file may stay.

Do not delete files under `ai/doc/guides/*`, `ai/doc/templates/*`, or `ai/skill/*` in this step. Those are prune suggestions, not automatic removals, and belong in the init report's `Prune suggestions` section.

Record the deletion list and the edited README / guide lines in the init report.

Before this step runs, the starter-self guard in `Stop conditions` must already have cleared; if `ai/doc/facts/project-scope.md` still describes "reusable SOP starter", stop instead of deleting.

### 9. Emit the init report
Produce a short report with these sections:
- `Changed files`: list of files modified or created, with section names when helpful
- `Deleted`: list of deleted starter spec files and any README / guide lines pruned because they cited deleted specs
- `Delegated bootstraps`: init-plastic-scm result when applicable
- `Flagged for human review`: starter-specific README sections to prune or rewrite, any free-form paragraphs that were not auto-updated
- `Prune suggestions`: list of starter files that are unlikely to apply to this project (guides, examples, optional skills under `ai/doc/guides/*`, `ai/doc/templates/*`, `ai/skill/*`). Do not delete them; let the user decide.
- `Next step`: a single handoff line pointing to `ai/skill/plan-to-spec.md` with the brief as its plan-level input

## Stop conditions
Return `needs_decision` without editing files when:
- the copied `AGENTS.md` does not contain a recognizable `## Repository purpose` section (already personalized or structurally changed)
- the user declines to provide `project_name`, `one_line_description`, `primary_outcome`, or any `non_goal`
- both `.git/` and `.plastic/plastic.selector` exist and the user has not declared which backend is authoritative
- the repository appears to be the SOP starter itself (for example, `ai/doc/facts/project-scope.md` still describes "reusable SOP starter")

Return `replan_required` when:
- any referenced template (`current-template.md`, `doc-map-template.md`, `project-scope-template.md`, `project-memory-readme-template.md`) is missing
- `ai/skill/plan-to-spec.md` is missing (later stages would have nothing to hand off to)

## Common failure modes
- inventing project fields that the brief did not provide
- rewriting long README prose that belongs to humans
- leaving the SOP starter's `## Repository purpose` wording in place
- keeping the SOP starter's own scope text inside `ai/doc/facts/project-scope.md`
- seeding `project/memory/*` with invented agreements when none existed in the brief
- auto-deleting starter files the user might still want
- producing a decision record without being asked
- running twice and stacking identity blocks
- deleting `ai/doc/specs/README.md` during spec residue cleanup
- deleting files under `ai/doc/guides/*`, `ai/doc/templates/*`, or `ai/skill/*` during spec residue cleanup instead of listing them as prune suggestions
- rewriting long prose in `README.md` or guides when trimming citations of deleted example specs
