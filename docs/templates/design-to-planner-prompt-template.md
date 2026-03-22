# Design to Planner Prompt Template

Use this template to hand design input to a planner / specifier.
This is a prompt scaffold, not a durable project document.

## Input

### Design Summary
Summarize the current high-level design discussion.

### Goal
What outcome should this phase or slice achieve?

### Non-goals
What is explicitly out of scope?

### Constraints
What technical, product, platform, or process constraints matter?

### Risks
What could go wrong or remain ambiguous?

### Relevant Repo Context
What repository context, files, modules, or facts should be considered?

### Known Open Questions
What decisions are still unresolved?

### Desired Next Step
What should the planner / specifier do next?
Examples:
- refine the plan
- derive one or more specs
- identify missing decisions before spec creation

## Output Contract

The planner / specifier should:
- inspect the repository context before finalizing the planning output
- clarify the current plan or phase slice
- derive one or more narrow specs when the work is implementation-ready
- name validation paths, write-back suggestions, and spec split triggers
- stop at a clarified plan when the work is not ready for safe spec creation
- explicitly list `why not yet` and the missing decisions when no spec should be produced yet

## Constraints

The planner / specifier should not:
- implement directly
- copy temporary design discussion into repository docs by default
- skip spec-first when implementation is ready
- combine multiple primary outcomes into one spec
