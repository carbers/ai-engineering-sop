# Split Entrypoints For Adoption

Keep this spec narrow to the repository's human-vs-AI entrypoint model and how that model should survive after copying into a real project.

## Metadata

### Source Plan / Request
User clarification that `ai/*` is an AI workflow namespace and that human entrypoints and AI-tool entrypoints should remain distinct rather than unified.

### Status
`done`

### Related Specs
- `20260326-001-ai-doc-skill-restructure.md`
- `20260326-002-ai-namespace-boundary-hardening.md`

## Goal
Make the repository explicitly use split entrypoints and explain how to preserve that split when the starter is copied into a real project.

## In Scope
- clarify the role of `README.md` as the human/project-facing entrypoint
- clarify the role of `AGENTS.md` and `CLAUDE.md` as AI-tool entrypoints
- clarify the role of `ai/README.md` as the AI workflow namespace map, not the main project entrypoint
- update adoption guidance so the split survives after copying into a real project

## Out of Scope
- changing the SOP workflow itself
- introducing additional adapters for other tools
- adding automation for project bootstrap

## Affected Area
Top-level repository guidance, AI-tool adapters, namespace documentation, and new-project adoption guidance.

## Task Checklist
- [x] Add explicit split-entrypoint guidance to the top-level docs
- [x] Update AI-tool adapters to reference `ai/README.md` as namespace documentation rather than a shared main entrypoint
- [x] Add copied-project adoption guidance that preserves the split entrypoint model
- [x] Verify the resulting guidance is internally consistent

## Done When
The repository clearly distinguishes human/project entrypoints from AI-tool entrypoints, and copied-project guidance explains how to preserve that distinction.

## Validation

### Black-box Checks
Read `README.md`, `AGENTS.md`, `CLAUDE.md`, `ai/README.md`, and `ai/doc/guides/new-project-sop.md` and confirm they describe one consistent split-entrypoint model.

### White-box Needed
No

### White-box Trigger
This is a documentation-structure refinement task with direct artifact review rather than logic protection.

### Internal Logic To Protect
None.

## Write-back Needed
Yes

If yes, what stable information should be written back, and where does it belong?
Update the repository entry docs and adoption guide so the split-entrypoint model is part of the stable operating guidance.

## Risks / Notes
The main risk is reintroducing “one true entrypoint” language that blurs the intended distinction between human and AI-tool usage.
