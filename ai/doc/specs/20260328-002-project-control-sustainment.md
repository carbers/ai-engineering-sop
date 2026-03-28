# Project Control Sustainment

Keep this task narrow. The goal is to add the smallest sustaining assets needed to keep the project control surface usable over time.

## Metadata

### Source Plan / Request
Follow-up implementation request to complete the remaining phases of the minimal project control surface rollout.

### Parent Phase
Control surface sustainment

### Parent Plan
Minimal recovery control surface

### Status
done

### Related Specs
- `20260328-001-minimal-project-control-surface.md`

## Goal
Add the sustaining templates, closeout workflow guidance, and facts routing guardrails needed to keep the minimal control surface consistent.

## In Scope
- Add `current-template.md`, `doc-map-template.md`, `decision-template.md`, and `experiment-readme-template.md`
- Add a closeout skill for control-surface synchronization and routing
- Update the skill registry
- Refine facts guidance so dashboard and ledger content stays out of facts

## Out of Scope
- New report or archive directories
- A full documentation program
- Changes to the core plan/spec/validation workflow

## Affected Area
- `ai/doc/templates/*`
- `ai/skill/*`
- `ai/doc/facts/facts-index.md`

## Task Checklist
- [x] Add the four sustaining templates
- [x] Add the closeout skill and register it
- [x] Refine facts routing boundaries for the new control surface
- [x] Keep the additions lightweight and operational

## Done When
The repository includes lightweight templates and one reusable closeout workflow that keep `project/*` maintainable, and the facts guidance clearly prevents project dashboard content from drifting back into `ai/doc/facts/*`.

## Validation

### Black-box Checks
- The new templates are lightweight and clearly state that generated instances belong under `project/*`
- The new skill has clear purpose, inputs, outputs, workflow steps, and failure modes
- `ai/doc/facts/facts-index.md` explicitly excludes dashboard-style current state and project-level ledgers

### White-box Needed
No

### White-box Trigger
This is a documentation and workflow-asset task with direct artifact review.

### Internal Logic To Protect
None.

## Write-back Needed
No

## Risks / Notes
The main risk is adding sustaining assets that feel heavier than the minimal control surface they are meant to support.