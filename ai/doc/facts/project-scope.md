# Project Scope

## Project Target
Maintain a practical, reusable, lightweight SOP starter for AI-assisted engineering work.

## Current Target
Maintain a spec-first SOP that supports both narrow execution and longer phase-aware work without requiring runtime implementation in this repository.

## Current Phase Goal
Refine the SOP starter so its templates and guides expose the minimum static phase-aware contract that future runtime can consume.

## In Scope
- repository-level guidance
- Cursor rules
- Claude adapter entry file
- practical templates and conventions for plan, task spec, spec artifact management, change summary, and project scope
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
- must define only static protocol fields that a future runtime can consume

## Current Assumptions
- a plan-first workflow is central
- plans should narrow into one or more task specs before implementation
- phase-aware structure should extend, not replace, the default spec-first path
- task specs should stay small, track lightweight status, and show short execution checklists
- multi-model collaboration should still converge on spec-first execution
- write-back must be selective
- skill promotion should happen only after patterns stabilize

## Open Risks
- docs may become too abstract if not exercised in real projects
- phase-aware fields may become too heavy if treated as mandatory for every task
- facts may grow too large if write-back rules are ignored
- task specs may become too heavy if plan content is duplicated or slices are not split soon enough
