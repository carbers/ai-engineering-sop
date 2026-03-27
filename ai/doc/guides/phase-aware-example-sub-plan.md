# Example: Phase-Aware Adoption Sub-Plan

> **This is an example plan artifact** for the phase-aware long-task path.
> It is not a real plan in this repository.
> Use it when you want a copyable `sub_plan` example rather than only a prose description.

This file is an example artifact, not a new canonical storage rule.
In a real project, keep durable plans wherever the project's planning docs belong.

## Metadata

### Plan Level
`sub_plan`

### Project Target
Make the SOP starter easy to adopt in real projects without changing its lightweight workflow model.

### Current Target
Improve first-use adoption so new users can tell where to start, when to stay on the default path, and when to use the phase-aware variant.

### Parent Plan
Phase 1 adoption clarity `main_plan`

### Current Phase
Phase 1 - adoption clarity pass for copied-project use.

## Phase Context

### Purpose
Break the current phase into narrow, reviewable slices while keeping sequencing and failure boundaries visible.

### Entry Criteria
- the adoption phase goal is already clear
- the current work benefits from explicit task ordering

### Exit Criteria
- each adoption improvement has been delivered through one narrow spec at a time
- the phase can close without ambiguity about what changed or what remains

### Deliverables
- one homepage entrypoint split
- one canonical phase-aware example package
- one terminology alignment pass across core docs

### Allowed Actions
- sequence tasks into narrow slices
- define validation order
- add explicit stop conditions when a slice should replan or escalate

### Forbidden Actions
- merge multiple primary outcomes into one spec
- broaden tasks to absorb unrelated adoption work
- force phase-aware fields onto every small task

### Gate Checks
- each slice stays reviewable in one pass
- validation remains explicit
- the phase-aware structure adds clarity rather than overhead

## Problem
Even when the phase goal is clear, adoption improvements can blur together unless the task ordering and boundaries are made explicit.

## Goal
Ship one reviewable adoption slice at a time without losing the parent phase context.

## Non-goals
- replace the main plan
- add a separate project board
- document every implementation note as a durable artifact

## Constraints
- keep slices narrow
- keep example artifacts compact
- preserve the default spec-first workflow

## Proposed Approach
Order the phase into three slices: entrypoint split, canonical long-task example, then terminology alignment.

## Risks
- the first slice could expand into a full quickstart rewrite
- the example package could become too abstract or too large
- terminology changes could drift across files if edited independently

## Phase Split / Task Breakdown
- Task 1: split the homepage into `small task` and `long task` entry paths
- Task 2: add one canonical phase-aware example package
- Task 3: align steady-state status values and escalation outcomes across docs

## First Slice
Task 1: homepage entrypoint split.
