# AI Doc And Skill Restructure

Keep this spec narrow to the repository's SOP asset layout and path references.

## Metadata

### Source Plan / Request
User request to assess and, if appropriate, migrate repository SOP assets from the legacy top-level `docs` and `skills` folders into `ai/doc/` and `ai/skill/`.

### Status
`done`

### Related Specs
None.

## Goal
Move the repository's AI-authored SOP assets under a single `ai/` root while keeping the workflow, validation, and write-back guidance consistent and usable.

## In Scope
- move the legacy top-level `docs` folder to `ai/doc/`
- move the legacy top-level `skills` folder to `ai/skill/`
- update repository guidance, templates, and cross-references to the new canonical paths
- verify no stale path references remain in tracked files

## Out of Scope
- changing the actual SOP workflow semantics
- redesigning document contents beyond path and structure alignment
- adding new workflow layers unrelated to this migration

## Affected Area
Top-level repository guidance, Cursor rules, SOP guides/templates/spec docs, and skill documents.

## Task Checklist
- [x] Create the new `ai/` directory structure by moving existing SOP assets
- [x] Update all canonical path references from the legacy folders to `ai/doc/*` and `ai/skill/*`
- [x] Adjust repository guidance so the new structure is described consistently
- [x] Run a repo-wide verification pass for stale references

## Done When
The repository uses `ai/doc/*` and `ai/skill/*` as the documented canonical locations for SOP assets, and tracked files no longer point to the old paths.

## Validation

### Black-box Checks
Repo tree shows the new directories in place, and repo-wide search no longer finds stale canonical path references in tracked files.

### White-box Needed
No

### White-box Trigger
This is a structural documentation migration with direct path validation rather than fragile internal logic.

### Internal Logic To Protect
None.

## Write-back Needed
Yes

If yes, what stable information should be written back, and where does it belong?
Update `README.md`, `AGENTS.md`, `CLAUDE.md`, `.cursor/rules/*`, and affected SOP docs so the new canonical layout is the stable repository guidance.

## Risks / Notes
The main risk is leaving mixed old/new path references, which would make the starter internally inconsistent.
