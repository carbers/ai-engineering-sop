# Example: Adoption Entrypoint Split Slice

> **This is an example spec** showing one complete task slice inside a longer phase-aware chain.
> It is not a real task in this repository.
> Use it when you want to see how a long-task setup still narrows into one small reviewable spec.

## Metadata

### Source Plan / Request
`sub_plan`: Phase 1 adoption clarity pass, Task 1 - split the homepage into `small task` and `long task` entry paths.

### Parent Phase
Phase 1 - adoption clarity pass for copied-project use.

### Parent Plan
`sub_plan`: order the adoption pass into entrypoint split, canonical example, then terminology alignment.

### Status
`done`

### Related Specs
- `20260102-001-example-phase-aware-guide-slice.md` (thin field example)

## Goal
Make the repository homepage show a clear `small task` versus `long task` entry split so first-time adopters can choose the right workflow without reading multiple guides first.

## Phase-Aware Contract

## Inputs
- the current repository entrypoint model
- the default lightweight workflow
- the phase-aware workflow guide
- the copied-project adoption goal for this phase

## Expected Outputs
- a short homepage decision section
- direct links to the default lightweight path and the phase-aware path
- no change to the underlying SOP workflow

## In Scope
- clarify the root `README.md` entrypoint for first-time readers
- route `small task` readers to the default spec-first path
- route `long task` readers to the phase-aware guide and example package

## Out of Scope
- rewriting the full adoption guide
- changing `AGENTS.md` into a long tutorial
- introducing runtime-specific behavior or automation

## Allowed Edits
- `README.md`
- `ai/doc/guides/phase-aware-workflow.md`
- `ai/doc/guides/phase-aware-canonical-example.md`

## Disallowed Edits
- `AGENTS.md` workflow semantics
- namespace roots under `ai/`
- project-management or runtime implementation files

## Affected Area
- repository entry guidance
- phase-aware navigation
- canonical example references

## Task Checklist
- [x] add a visible `small task` versus `long task` decision split near the top of `README.md`
- [x] link each path to the next file a first-time reader should open
- [x] keep the default workflow wording intact
- [x] verify the long-task path points to a closed example chain rather than only concept docs

## Done When
A first-time reader can open the homepage and quickly tell which workflow path fits their current work, where to click next, and that both paths still converge on narrow task specs before implementation.

## Validation

### Black-box Checks
- open `README.md` and confirm the `small task` and `long task` paths are visible near the top
- follow the `small task` link and confirm it leads to spec-first guidance
- follow the `long task` link and confirm it leads to both a phase-aware guide and a closed example chain
- confirm the homepage still describes the default workflow as lightweight rather than mandatory phase-aware planning

### White-box Needed
No

### White-box Trigger
This slice is a documentation navigation change with direct artifact review rather than fragile internal logic.

### Internal Logic To Protect
None.

## Repair / Rollback

### Repair Budget
One bounded wording pass for unclear labels, missing links, or overlong homepage copy found during review.

### Rollback Scope
Revert the new homepage split and example links if the result makes the root README harder to scan.

### Escalation Condition
Stop as `replan_required` or `needs_decision` if clarifying the entrypoint would require redefining the default workflow, adding a new namespace, or turning the repository into a heavyweight process portal.

## Write-back Needed
Yes

If yes, what stable information should be written back, where does it belong, and which type best fits?
Record the resulting long-task example pattern in `ai/doc/facts/golden-cases.md` as a `task_pattern` or `phase_lesson` if it remains a stable reusable adoption reference.

## Risks / Notes
- The main risk is making the phase-aware path look mandatory for every task.
- If the task stops for escalation, keep `Status` on the last accurate steady-state value and report `needs_decision` or `replan_required` here or in the handoff summary.
