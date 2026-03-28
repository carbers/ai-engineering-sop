# Skill Registry

Keep this registry in sync with the files in `ai/skill/`.
When adding, removing, or renaming a skill file, update this registry in the same change.

| Name | Purpose | Trigger | Inputs | Outputs | Status |
|---|---|---|---|---|---|
| `plan-to-spec` | Convert a plan or phase slice into one or more narrow task specs | A plan or phase slice exists and work is about to move into implementation | plan or phase slice, current context, constraints, risks, and for phase-aware work the current target and plan level | one or more specs with scope, status, checklist, done condition, validation, write-back guidance, and when needed parent mapping plus failure-boundary fields | active |
| `design-whitebox-tests` | Decide whether and how to add white-box protection | A task touches complex internal logic or regression-sensitive code | task spec, bug context, internal logic details | white-box test decision, protected logic targets, regression guidance | active |
| `session-closeout` | Decide what durable updates, if any, should happen after a slice completes | A task or slice is finishing and control-surface, fact, or skill write-back may be needed | completed task or slice, current control surface state, any decision or experiment outcome, and candidate reusable context | targeted control-surface updates, optional decision or experiment records, optional fact or skill updates, or an explicit no-write-back outcome | active |
