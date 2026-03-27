# Example: Phase-Aware Adoption Main Plan

> **This is an example plan artifact** for the phase-aware long-task path.
> It is not a real plan in this repository.
> Use it when you want a copyable `main_plan` example rather than only a prose description.

This file is an example artifact, not a new canonical storage rule.
In a real project, keep durable plans wherever the project's planning docs belong.

## Metadata

### Plan Level
`main_plan`

### Project Target
Make the SOP starter easy to adopt in real projects without changing its lightweight workflow model.

### Current Target
Improve first-use adoption so new users can tell where to start, when to stay on the default path, and when to use the phase-aware variant.

### Parent Plan
None.

### Current Phase
Phase 1 - adoption clarity pass for copied-project use.

## Phase Context

### Purpose
Make the first-use path easier to understand without changing the repository's default workflow.

### Entry Criteria
- the repository already has a stable lightweight workflow
- adoption friction has been identified around entrypoints, examples, or terminology

### Exit Criteria
- the homepage clearly splits the small-task and long-task entry paths
- at least one closed phase-aware example chain exists
- status and escalation wording are aligned across core guidance

### Deliverables
- updated repository entry guidance
- one closed phase-aware example chain
- aligned terminology across the specs guide, lifecycle guide, and task spec template

### Allowed Actions
- refine README and guidance wording
- add compact example artifacts
- tighten terminology across existing docs and templates

### Forbidden Actions
- replace the default lightweight workflow
- introduce runtime automation or orchestration
- add a new namespace or heavyweight planning layer

### Gate Checks
- first-time readers can tell which path to follow
- long-task examples remain small and copyable
- small-task workflow remains the default

## Problem
First-time adopters can understand the repository purpose, but they still need to infer when to stay on the lightweight path versus when to use the phase-aware variant.

## Goal
Make adoption clearer, faster, and more copyable without adding method sprawl.

## Non-goals
- build runtime behavior
- redesign the SOP workflow
- turn the starter into a project-management system

## Constraints
- keep the repository lightweight
- prefer refining existing files over adding many new ones
- preserve the spec-first execution model

## Proposed Approach
Improve the top-level entrypoints, add one closed long-task example chain, and align status/escalation terminology across the core docs.

## Risks
- the long-task path could look mandatory if over-explained
- the homepage could become too long if quickstart content expands too far
- example artifacts could drift from the actual template conventions

## Phase Split / Task Breakdown
- Checkpoint 1: split the homepage into small-task and long-task entry paths
- Checkpoint 2: add a compact closed phase-aware example chain
- Checkpoint 3: align steady-state status values and escalation outcomes across docs

## First Slice
Add the homepage decision split and route each path to the next most useful document.
