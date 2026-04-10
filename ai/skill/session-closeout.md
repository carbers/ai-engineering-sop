# Skill: session-closeout

## Purpose
Close out a completed slice without turning the control surface, project memory, facts, or skills into an archive of task chatter.

This skill keeps the human-facing control surface current while preserving the existing `ai/*` execution model.
Use it after required validation and before reporting a task or slice as fully done when the repository uses `project/*`.

## When to use
Use this skill when a task or slice is finishing and you need to decide what, if anything, should be updated after validation.

Typical triggers:
- the active slice changed or completed
- the current phase or current target shifted
- repeated project memory should be recorded for later recovery
- a project-level decision was frozen
- an experiment produced a readable result worth re-reading later
- stable reusable context emerged and may belong in facts or a skill

## Inputs
- current task spec or completed slice
- current `project/CURRENT.md`
- current `project/memory/*`, if the repository uses project memory
- any new decision or experiment outcome
- any candidate fact or reusable workflow learning

## Outputs
- updated `project/CURRENT.md` when current operating state changed
- updated `project/memory/*` when longer-lived project memory should be preserved
- updated `project/DOC_MAP.md` only when document roles or reading order changed
- a decision record under `project/decisions/*` when a durable project-level choice was frozen
- an experiment record under `project/experiments/*` when an experiment outcome is worth re-reading later
- a fact or skill update only when the information is stable and reusable
- no write-back when nothing durable changed

## Workflow

### 1. Start with the control surface
Ask whether a returning human would be misled if `project/CURRENT.md` stayed unchanged.
If yes, update it.
If no, leave it alone.

Update `project/CURRENT.md` only when at least one of these changed:
- current phase
- current target
- active slice
- current source of truth
- frozen decision in force
- next durable actions
- top risk that could make the control surface misleading

Do not update `project/CURRENT.md` for:
- step-by-step task progress
- validation logs
- implementation notes that already live in the spec
- file inventories or commit-style changelogs

Ask whether a returning human would be slowed down if `project/memory/*` stayed unchanged.
If yes, update the relevant memory page.
If no, leave it alone.

Update `project/memory/*` only when at least one of these changed:
- a project-level working agreement or durable constraint is now explicit
- a recurring project pattern or repeated pitfall is now clear
- a repeated reminder should remain easy to recover in later work

Do not update `project/memory/*` for:
- one-off task notes
- validation transcripts
- temporary debugging observations
- frozen decisions that belong in `project/decisions/*`
- reusable AI-oriented facts that belong in `ai/doc/facts/*`

Mid-slice updates are allowed only when the memory is already stable, repeated, and likely to affect later execution before the slice closes.
Otherwise keep it in the active spec, change summary, or task conversation until closeout.

Update `project/DOC_MAP.md` only when at least one of these changed:
- normal start order for a returning reader
- which document family answers which question
- the priority rule when documents overlap

Do not update `project/DOC_MAP.md` just because:
- a new spec was created
- a decision record was added
- an experiment directory exists
- more files now live in the repository

### 2. Separate project-level decisions from task choices
Create a decision record only when the choice changes the project's durable direction, scope boundary, control model, or repeatable operating rule.
Do not record ordinary implementation choices as project decisions.

### 3. Record experiments only when they are real experiments
Use `project/experiments/*` only when the work included explicit experiment setup, results, and a next decision worth re-reading later.
Do not treat ordinary validation runs as experiments.

### 4. Route stable reusable context deliberately
If the outcome is project-facing long-lived memory for this project, route it to `project/memory/*`.
If the outcome is stable reusable context for future AI runs, route it to `ai/doc/facts/*`.
If the outcome is a repeatable workflow, route it to `ai/skill/*`.
Do not use the control surface as a substitute for facts or skills.

### 5. Prefer no write-back over noisy write-back
If the outcome is task-local, temporary, or obvious from the active spec, leave it out of `project/*`, facts, and skills.

## Common failure modes
- updating `project/CURRENT.md` like a running task log
- turning `project/memory/*` into a running log or a second facts directory
- creating decision records for normal implementation choices
- storing ordinary validation runs as experiments
- writing task-local reasoning into facts
- promoting one-off tactics into a skill
- updating multiple layers with the same explanation instead of routing it once
