# Skill Registry

| Name | Purpose | Trigger | Inputs | Outputs | Status |
|---|---|---|---|---|---|
| `plan-to-spec` | Convert a plan into narrow task specs | A plan exists but execution still needs task boundaries | plan, current phase context | task specs, affected area, done condition, validation guidance, write-back guidance | active |
| `design-whitebox-tests` | Decide whether and how to add white-box protection | A task touches complex internal logic or regression-sensitive code | task spec, bug context, internal logic details | white-box test decision, protected logic targets, regression guidance | active |
