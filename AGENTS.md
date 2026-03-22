# AGENTS.md

## Repository purpose

This repository is a reusable SOP starter for AI-assisted engineering work.

Its purpose is to provide a practical operating model for:

- plan-first engineering
- task-spec-driven execution
- explicit validation
- stable fact write-back
- reusable skill promotion

This repository is workflow-oriented and tool-neutral. It is not tied to a specific application stack.

## Canonical structure

Use the repository layers as follows:

- `README.md`
  Repository entry point and adoption guide.

- `AGENTS.md`
  Canonical repository-level operating rules.

- `CLAUDE.md`
  Lightweight adapter that defers to `AGENTS.md`.

- `.cursor/rules/*`  
  Execution guardrails for Cursor.

- `docs/guides/*`  
  Practical workflow guidance.

- `docs/templates/*`  
  Reusable document skeletons used during work.

- `docs/specs/*`
  Task specs that bridge plans and implementation.

- `docs/facts/*`  
  Stable context worth re-reading later.

- `skills/*`  
  Reusable workflows that reduce repeated cognitive work.

## Working model

Follow this operating sequence by default:

1. start from a plan, a phase slice, or a clearly scoped existing task request
2. derive or refine one or more narrow task specs before implementation
3. implement the smallest coherent change
4. validate explicitly
5. write back stable facts when justified
6. promote repeated workflows into skills when they stabilize

When a plan or phase slice exists, the default execution path is `plan -> one or more task specs -> implementation -> validation`.
A plan may come from an interactive planning session or a written plan document.
Use `docs/templates/plan-template.md` only when the plan should become a durable repo artifact worth re-reading, sharing, or handing off.
Plans may remain temporary. The task spec is the default durable execution artifact for implementation and iteration.
If iterating within the same reviewable slice, refine the existing spec.
If the primary outcome, boundary, or validation path changes, create a new dated spec first.
Only tiny task requests that are already effectively spec-complete and trivially narrow may skip spec creation.

Use change summaries for task-local delivery notes. Do not turn them into permanent facts.

## Boundaries

- Prefer the smallest coherent change.
- Do not add speculative abstractions.
- Do not expand a task because a broader redesign seems attractive.
- Do not turn temporary reasoning into permanent documentation.
- Do not duplicate the same explanation across many files.
- Do not let facts become an archive of every conversation.

## Write-back policy

Write back only when the information is both stable and reusable.

Good write-back targets include:

- current project scope and boundaries
- stable validation references
- stable workflow rules
- reusable decision patterns
- repeatable skills

Route write-back to the right layer:

- `docs/facts/*` for stable reusable project context
- `skills/*` for repeatable workflows
- `AGENTS.md` or `.cursor/rules/*` only for repository-wide operating guidance

Do not write back:

- temporary debugging chatter
- unstable exploration
- one-off implementation details
- task-local reasoning with no future reuse value

Use this rule before writing back:

1. Will this still matter later?
2. Can this be reused later?
3. Does it have a clear destination file?

If the answer is not clearly yes, do not write it back.

Facts are stable context, not an archive.

## Skill promotion rule

Promote a workflow into `skills/*` when:

- it repeats across tasks
- its inputs and outputs are recognizable
- its value is not tied to a single one-off task
- it reduces repeated reasoning effort
- it can be described clearly enough to reuse

Do not create a new skill for every useful prompt.

## Validation expectations

- Black-box validation is the default acceptance mechanism.
- White-box validation is conditional.
- Add white-box validation when logic is regression-sensitive, stateful, branch-heavy, internally fragile, or protected by an important internal contract.
- A deterministic bugfix regression path is a strong trigger for white-box protection when black-box checks alone will not reliably hold the fix in place.
- White-box validation should protect meaningful logic, not incidental implementation trivia.
- Validation must be concrete enough to review.
- Do not turn validation into a coverage-chasing workflow.

## Editing expectations

When changing this repository itself:

- keep changes narrow
- keep terminology consistent
- reinforce the right layer instead of repeating the same rule everywhere
- update the right layer instead of appending notes everywhere
- prefer refinement over expansion
