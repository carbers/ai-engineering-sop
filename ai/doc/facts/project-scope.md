# Project Scope

This fact holds relatively stable scope, boundary, and assumption context.
Do not update it for routine task progress or every active-slice change.
Use `project/CURRENT.md` for live operating state when the control surface is in use.

## Project Target
Maintain a practical, reusable, lightweight SOP starter for AI-assisted engineering work.

## Stable Current Target
Maintain a lightweight SOP starter that supports spec-first execution, phase-aware work when needed, a recovery-first human control surface, and optional batch-level release readiness without requiring runtime implementation in this repository.

## Stable Phase Goal
Keep the new `project/` control surface aligned with the existing spec-first workflow so humans can recover context quickly without turning the repository into a second execution system.

## In Scope
- repository-level guidance
- Cursor rules
- Claude adapter entry file
- practical templates and conventions for plan, task spec, spec artifact management, change summary, and project scope
- minimal human-facing project control surface under `project/*`
- lightweight optional support for batch-level release readiness in real product releases
- multi-model collaboration guidance and prompt handoff templates
- phase-aware workflow guidance and task lifecycle guidance
- initial facts structure
- initial reusable skills for plan-to-spec and white-box test design

## Out of Scope
- CLI tooling
- runtime orchestration or automation
- starter generators
- project-type-specific code templates
- large guide systems
- many example matrices
- advanced automation

## Key Constraints
- must remain technology-agnostic
- must stay lightweight enough to copy into real projects
- must separate rules, templates, facts, and skills clearly
- must keep AI-managed workflow assets separate from project-facing documentation
- must keep the human-facing control surface recovery-first and small
- must define only static protocol fields that a future runtime can consume

## Current Assumptions
- a plan-first workflow is central
- plans should narrow into one or more task specs before implementation
- phase-aware structure should extend, not replace, the default spec-first path
- task specs should stay small, track lightweight status, and show short execution checklists
- multi-model collaboration should still converge on spec-first execution
- a root-level `project/` control surface is the default recovery layer when humans need current-state navigation
- write-back must be selective
- skill promotion should happen only after patterns stabilize

## Open Risks
- docs may become too abstract if not exercised in real projects
- phase-aware fields may become too heavy if treated as mandatory for every task
- facts may grow too large if write-back rules are ignored
- task specs may become too heavy if plan content is duplicated or slices are not split soon enough
- `ai/doc/facts/project-scope.md` may be mistaken for a live status file instead of a slower-moving scope fact
- `project/CURRENT.md` may drift into a task log if closeout discipline is not maintained
- `project/DOC_MAP.md` may expand into a directory catalog instead of staying role-based
