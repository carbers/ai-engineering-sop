# Design-to-Spec Handoff

Use this guide when design discussion, planning, spec derivation, and execution are handled by different models or different people.

This is a recommended extension of the default SOP, not a replacement for it.
The core repository rule still applies: when work is ready for implementation, the durable execution artifact should be one or more task specs.

## Role Contracts

### Design Partner
- discuss the high-level design
- clarify goals, non-goals, constraints, and risks
- produce a design summary when the discussion needs to be handed off
- do not implement from the design discussion alone

### Planner / Specifier
- combine the design input with actual repository context
- turn the current design into a clarified plan or phase slice
- decide when the work is implementation-ready
- derive one or more narrow task specs when implementation is ready
- split oversized work before handing it to an executor

### Executor
- implement and validate one spec at a time
- stay within the current spec boundary
- report blockers, ambiguity, and validation gaps back to the planner / specifier
- do not expand scope or invent missing design

## Artifact Policy

- high-level design is temporary by default
- summarize design only when it must be re-read, shared, or handed off
- a written plan is optional and may remain temporary
- the task spec is the default durable execution artifact

## Handoff Gates

### Design -> Planner / Specifier

The planner / specifier may accept:
- a design summary
- a goal and non-goals
- constraints and risks
- relevant repository context
- known open questions

The planner / specifier should not treat a design discussion as implementation-ready by default.

### Planner / Specifier -> Executor

The executor should accept only:
- a single target spec
- allowed scope and forbidden scope
- explicit validation expectations
- clear stop or fallback conditions

The executor should not accept:
- design-only input
- plan-only input
- multiple specs merged into one execution request

If the design is still not converged enough for a safe spec, the planner / specifier may stop at a clarified plan.
When this happens, the planner / specifier should explicitly list the missing decisions and should not fabricate a spec.

## Default Flow

1. Discuss the high-level design and summarize it if handoff is needed.
2. Let the planner / specifier inspect the repository and refine the plan or current phase slice.
3. When the work is implementation-ready, derive one or more narrow specs.
4. Hand one spec at a time to the executor.
5. Validate the completed work against the spec.
6. If boundaries change or blockers appear, return to the planner / specifier to refine or split the spec.

## Iteration Loop

Follow `docs/specs/README.md` for spec refinement, splitting, and lifecycle conventions.
Keep scope changes with the planner / specifier, not the executor.

## Executor Mutation Limits

By default, the executor may update only:
- `Status`
- `Task Checklist`
- `Risks / Notes`

The executor should not rewrite:
- `Goal`
- `In Scope`
- `Out of Scope`
- `Done When`
- `Validation`
- `Write-back Needed`

If a team does not want executors to edit specs at all, these fields can be reported back instead of updated directly.

## Example Mapping

This mapping is illustrative, not required:

- a chat-oriented design model can play the `design partner` role
- a repository-aware planning model can play the `planner / specifier` role
- a lower-cost execution-focused model can play the `executor` role

One common example is:
- `ChatGPT` as `design partner`
- `Codex` as `planner / specifier`
- `Cursor` or `Composer` as `executor`

## Failure Modes

- handing a plan directly to the executor without deriving a spec
- creating one large spec that hides multiple primary outcomes
- letting the executor fill in missing design instead of returning to the planner / specifier
- continuing implementation while blocked and quietly expanding scope
- treating design discussion logs as durable project documentation by default
