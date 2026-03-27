# Golden Cases

These are stable reference cases for this SOP repository.

## Case 1: Plan to SPEC conversion

### Input
A phase-level plan that includes:
- problem
- goal
- constraints
- risks
- phased direction

### Expected outcome
The plan is converted into one or more narrow task specs that:
- define in-scope vs out-of-scope
- stay small enough to review independently, splitting when one spec would become too large
- define validation clearly
- identify white-box triggers
- identify write-back needs

### Why it matters
This is the main bridge between planning and execution.

---

## Case 2: Bugfix with white-box trigger

### Input
A deterministic bugfix in branch-heavy or stateful logic.

### Expected outcome
The task still uses black-box validation for acceptance, but also adds white-box protection for the internal regression path when appropriate.

### Why it matters
This demonstrates the layered validation model.

---

## Case 3: Selective write-back

### Input
A completed task with both temporary reasoning and one stable new decision.

### Expected outcome
Only the stable, reusable decision is written back. Temporary working notes stay out of facts.

### Why it matters
This protects the repository from documentation sprawl.

---

## Case 4: Phase-aware long-task chain

### Input
A long-running adoption or refactor slice that needs explicit `project_target`, `current_target`, `phase`, plan hierarchy, and failure boundaries before execution starts.

### Expected outcome
The work stays on the same core path, but adds just enough structure to keep the long task legible:
- a visible `project_target`, `current_target`, and `phase`
- a `main_plan` for phase progression and an optional `sub_plan` for task ordering
- one narrow task spec with explicit validation and failure boundaries
- selective write-back after the slice is complete

See `ai/doc/guides/phase-aware-canonical-example.md` and `ai/doc/specs/20260103-001-example-adoption-entrypoint-slice.md`.
For copyable plan artifacts, also see `ai/doc/guides/phase-aware-example-main-plan.md` and `ai/doc/guides/phase-aware-example-sub-plan.md`.

### Why it matters
This shows how to make longer work reviewable without replacing the default lightweight workflow.

---

## Case 5: First copied-project small-task slice

### Input
A copied-project adoption pass where the next reviewable slice is already clear and does not need explicit phase-aware hierarchy.

### Expected outcome
The work stays on the default lightweight path:
- one narrow task spec
- explicit in-scope and out-of-scope boundaries
- black-box validation that a reviewer can inspect quickly
- no extra plan or hierarchy artifacts unless they add real clarity

See `ai/doc/specs/20260104-001-example-first-copied-project-quickstart.md`.

### Why it matters
This shows the smallest practical spec-first path for teams adopting the starter into a real project.
