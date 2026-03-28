# Facts Index

Facts are stable context worth reading again later.

Use facts for information that is:
- stable enough to keep
- reusable across tasks
- useful to future readers or AI runs

Facts are not an archive of every discussion.

## File map

- `project-scope.md`
  - stable project target
  - stable current target
  - stable phase goal
  - stable scope boundaries
  - current assumptions
  - open risks worth tracking

- `golden-cases.md`
  - stable validation references
  - reusable example cases
  - representative workflows or outcomes worth preserving

## Do not store in facts

Do not put these into facts:

- temporary notes
- raw debugging chatter
- one-off task reasoning
- unstable exploration
- content that belongs only in a change summary
- current project dashboard content that belongs in `project/CURRENT.md`
- project-level decision or experiment ledgers that belong in `project/*`

## Routing rule

Follow the write-back policy in `AGENTS.md` before adding content here.
Treat `project-scope.md` as slower-moving scope context, not as the live current-status layer.

When a task or plan names a write-back type, use it as a routing hint rather than a reason to create a new file type:

- `facts_update`: stable project context or validation references under `ai/doc/facts/*`
- `skill_promotion`: reusable workflow updates under `ai/skill/*`
- `decision_rationale`: only when the decision is stable and reusable; otherwise leave it in task-local artifacts
- `phase_lesson`: only when the lesson should influence later phases or future runs
- `task_pattern`: reusable execution pattern worth preserving, usually in an existing fact file unless it matures into a skill
- `anti_pattern`: repeated pitfall worth preserving, not one-off frustration

These labels are a routing taxonomy, not a requirement to create one file per label.

## Maintenance rule

When adding, removing, or renaming fact files in this directory, update this index in the same change.
