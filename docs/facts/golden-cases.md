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
