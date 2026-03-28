# Light Release Batch Readiness

Keep this task narrow. The goal is to support lightweight batch-level release checks without turning every task spec into a release document.

## Metadata

### Source Plan / Request
User request to add the lightest useful support for release-batch readiness and future automated pre-release checks.

### Parent Phase
Sustain the SOP as a lightweight but production-usable workflow

### Parent Plan
Minimal recovery control surface

### Status
done

### Related Specs
- `20260328-002-project-control-sustainment.md`

## Goal
Add the smallest set of artifacts and conventions needed to support batch-level pre-release checks for real product releases.

## In Scope
- add one optional release-batch template
- add one lightweight spec-level release-sensitivity marker
- document that release readiness is batch-level rather than per-spec
- document which existing fields are suitable for future release-check aggregation

## Out of Scope
- a required release process for every task
- a new runtime or automation layer
- a mandatory `project/releases/` directory
- per-spec release paperwork
- a heavyweight QA or release management framework

## Affected Area
- `ai/doc/templates/*`
- `ai/doc/specs/README.md`
- `ai/doc/guides/*`
- current repository control/state docs

## Task Checklist
- [x] add a lightweight release-batch template
- [x] add a minimal spec-level release sensitivity signal
- [x] update guidance so release readiness stays batch-level
- [x] keep the changes optional and lightweight

## Done When
The repository can support a lightweight pre-release batch review using existing spec and validation artifacts, without adding routine release overhead to every task.

## Validation

### Black-box Checks
- a reader can tell that release readiness is optional and batch-level, not required for every spec
- a reader can find one template for aggregating release-sensitive specs before a real product release
- a spec author can mark a task as release-sensitive without adding a large new section

### White-box Needed
No

### White-box Trigger
This is a documentation and workflow-asset refinement with direct artifact review.

### Internal Logic To Protect
None.

## Repair / Rollback

### Repair Budget
One focused revision pass if the new release wording makes the default task flow feel heavier.

### Rollback Scope
The new release-batch template and the wording added to templates and guides in this slice.

### Escalation Condition
Stop if supporting release checks would require a new mandatory project layer, a required release artifact for every task, or a new control-surface directory.

## Write-back Needed
No

## Risks / Notes
- The main risk is letting optional release support turn into routine spec overhead.
- The second risk is implying that batch-level release review can replace human release judgment rather than reduce manual collection work.
