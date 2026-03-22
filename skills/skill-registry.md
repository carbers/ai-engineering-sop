# Skill Registry

| Name | Purpose | Trigger | Inputs | Outputs | Status |
|---|---|---|---|---|---|
| `plan-to-spec` | Convert a plan or phase slice into one or more narrow task specs | A plan or phase slice exists and work is about to move into implementation | plan or phase slice, current context, constraints, risks | one or more specs with scope, status, checklist, done condition, validation, write-back guidance | active |
| `design-whitebox-tests` | Decide whether and how to add white-box protection | A task touches complex internal logic or regression-sensitive code | task spec, bug context, internal logic details | white-box test decision, protected logic targets, regression guidance | active |
