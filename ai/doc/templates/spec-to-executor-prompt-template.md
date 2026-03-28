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

### Escalation Expectations
When should the executor return `needs_decision` or `replan_required` instead of continuing?

### Completion Reporting Format
How should the executor report completed work, validation, blockers, escalation outcomes, and follow-ups?

### Stop / Fallback Conditions
When should the executor stop and hand the work back to the planner / specifier?

## Execution Contract

The executor should:
- consume one spec at a time
- stay inside the current spec boundary
- validate against the spec before reporting completion
- make the spec's write-back and closeout decision explicit before reporting `done`
- return blockers, ambiguity, scope pressure, and escalation outcomes to the planner / specifier

The executor should not:
- re-open the high-level design
- merge multiple specs into one execution pass
- rewrite `Goal`, `In Scope`, `Out of Scope`, `Done When`, `Validation`, or `Write-back Needed`

The executor may update only:
- `Status`
- `Task Checklist`
- `Risks / Notes`

If the team does not want executors to edit specs directly, the same updates should be reported back instead.
If the repository uses `project/*`, completion reporting should state whether `ai/skill/session-closeout.md` was applied and what, if anything, was updated.
If the spec is marked `release_sensitive`, completion reporting should also call out any deployment, migration, config, compatibility, or rollback note that a later release batch review should see.

## Fallback Conditions

Stop and return the work when:
- the spec boundary is unclear
- validation is not strong enough to decide `done`
- the work appears to require broader scope
- the work should be split into multiple reviewable slices
- the task should return as `needs_decision` or `replan_required`
