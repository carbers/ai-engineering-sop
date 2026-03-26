# AI Namespace Boundary Hardening

Keep this spec narrow to the `ai/` namespace's ownership boundary, entrypoint clarity, and maintenance rules.

## Metadata

### Source Plan / Request
User request to address the repository review findings around `ai/` discoverability, boundary clarity, and index maintenance.

### Status
`done`

### Related Specs
- `20260326-001-ai-doc-skill-restructure.md`

## Goal
Make the `ai/` namespace easier to discover and harder to misuse by clarifying what belongs there, what does not, and what indexes must stay in sync.

## In Scope
- add a local entry document for `ai/`
- clarify the ownership boundary between `ai/*` assets and project-facing documentation
- make the singular naming convention explicit for `ai/doc` and `ai/skill`
- add stable maintenance guidance for facts and skill indexes/registries
- fix the visible README encoding issue while touching repository entry guidance

## Out of Scope
- redesigning the SOP workflow
- adding new skills or new facts categories
- introducing automation or generators for index maintenance

## Affected Area
Repository entry guidance, boundary/write-back rules, facts/skill indexes, and `ai/` namespace navigation.

## Task Checklist
- [x] Add an `ai/` entrypoint document that explains the namespace and where to start
- [x] Update repository rules to define what belongs in `ai/*` versus project-facing docs
- [x] Add explicit maintenance guidance for `facts-index.md` and `skill-registry.md`
- [x] Verify the new guidance is consistent and the README display issue is resolved

## Done When
Readers can enter through `ai/`, understand the namespace boundary without inference, and see explicit guidance to keep facts and skill indexes in sync.

## Validation

### Black-box Checks
Open the top-level and `ai/` entry docs and verify they clearly explain the namespace, boundaries, and maintenance expectations. Confirm the visible README version line renders cleanly.

### White-box Needed
No

### White-box Trigger
This is a documentation/rules refinement task with direct artifact review rather than fragile internal logic.

### Internal Logic To Protect
None.

## Write-back Needed
Yes

If yes, what stable information should be written back, and where does it belong?
Update `README.md`, `AGENTS.md`, `.cursor/rules/*`, `ai/doc/facts/facts-index.md`, and `ai/skill/skill-registry.md` with the stable namespace and maintenance rules.

## Risks / Notes
The main risk is repeating the same boundary guidance in too many places instead of reinforcing one canonical explanation.
