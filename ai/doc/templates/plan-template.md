# Plan Template

Use this template only when a plan should become a durable repo artifact worth re-reading, sharing, or handing off.
If the plan is already clear enough to derive specs, skip this and move directly to task spec creation.
Keep it lightweight. This template should clarify the current target, phase, and next slices, not become a project board.

## Metadata

### Plan Level
Choose one:
- `main_plan`: phase progression, milestones, dependencies, or checkpoints
- `sub_plan`: task decomposition, ordering, validation flow, or failure handling inside the current phase

### Project Target
What stable project-level target is this plan serving?

### Current Target
What narrower target is being advanced now?

### Parent Plan
Optional. If this is a `sub_plan`, which higher-level plan does it narrow?

### Current Phase
Which phase does this plan serve?

## Phase Context

### Purpose
Why does this phase exist?

### Entry Criteria
What must already be true before this phase or slice starts?

### Exit Criteria
What must be true before this phase can be considered complete?

### Deliverables
What reviewable outputs should this phase produce?

### Allowed Actions
What kinds of work are valid inside this phase?

### Forbidden Actions
What should not be done in this phase?

### Gate Checks
What checks decide whether the phase can proceed or close?

## Problem
What problem is being solved?

## Goal
What outcome should this phase achieve?

## Non-goals
What is explicitly not part of this phase?

## Constraints
What technical, product, platform, or process constraints matter?

## Proposed Approach
What is the preferred direction for this phase?

## Risks
What could go wrong or slow this phase down?

## Phase Split / Task Breakdown
If this is a `main_plan`, list the phase split, milestones, dependencies, or checkpoints.
If this is a `sub_plan`, list the task decomposition, ordering, validation flow, or failure-handling path.

## First Slice
What is the first reviewable slice to implement?
