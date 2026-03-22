# Spec to Executor Prompt Template

Use this template to hand a single task spec to an executor.
This is a prompt scaffold, not a durable project document.

## Input

### Target Spec Path
Which single spec should be executed?

### Allowed Scope
What work inside the spec is allowed?

### Forbidden Scope
What must remain out of scope for this execution pass?

### Validation Expectations
What validation is required before this work can be reported as done?

### Completion Reporting Format
How should the executor report completed work, validation, blockers, and follow-ups?

### Stop / Fallback Conditions
When should the executor stop and hand the work back to the planner / specifier?

## Execution Contract

The executor should:
- consume one spec at a time
- stay inside the current spec boundary
- validate against the spec before reporting completion
- return blockers, ambiguity, and scope pressure to the planner / specifier

The executor should not:
- re-open the high-level design
- merge multiple specs into one execution pass
- rewrite `Goal`, `In Scope`, `Out of Scope`, `Done When`, `Validation`, or `Write-back Needed`

The executor may update only:
- `Status`
- `Task Checklist`
- `Risks / Notes`

If the team does not want executors to edit specs directly, the same updates should be reported back instead.

## Fallback Conditions

Stop and return the work when:
- the spec boundary is unclear
- validation is not strong enough to decide `done`
- the work appears to require broader scope
- the work should be split into multiple reviewable slices
