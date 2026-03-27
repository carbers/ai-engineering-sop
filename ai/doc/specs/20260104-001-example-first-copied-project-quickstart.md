# Example: First Copied-Project Quickstart Slice

> **This is an example spec** showing a first-use task on the default lightweight path.
> It is not a real task in this repository.
> Use it when you want a small, copyable spec without phase-aware fields.

## Metadata

### Source Plan / Request
Copied-project adoption request: add one short quickstart section so a first-time team can see how to start using the SOP without reading every guide first.

### Status
`done`

### Related Specs
- `20260103-001-example-adoption-entrypoint-slice.md` (phase-aware contrast example)

## Goal
Add a short copied-project quickstart section that tells a first-time adopter what to keep, whether to start on the small-task or long-task path, and how to get to the first spec quickly.

## In Scope
- add one short quickstart section for copied-project use
- point readers to the minimum files and first next steps
- preserve the existing lightweight workflow wording

## Out of Scope
- rewriting the full adoption guide
- adding a new quickstart file or namespace
- introducing phase-aware hierarchy into the task itself

## Affected Area
- root `README.md`
- copied-project adoption guidance links

## Task Checklist
- [x] add one short copied-project quickstart section
- [x] point to the first spec path rather than expanding the homepage into a tutorial
- [x] confirm the section still keeps the default workflow lightweight

## Done When
A first-time adopter can open the repository, see what to copy into a real project, decide whether the first slice is small-task or long-task work, and get to the first task spec path without reading the entire documentation set first.

## Validation

### Black-box Checks
- open `README.md` and confirm the copied-project quickstart is visible and short
- confirm the quickstart tells readers what to keep on day one
- confirm the quickstart points readers to the spec-first path for the first implementation slice
- confirm the quickstart does not imply every copied project needs a durable plan before the first spec

### White-box Needed
No

### White-box Trigger
This is a documentation clarity task with direct artifact review rather than fragile internal logic.

### Internal Logic To Protect
None.

## Write-back Needed
No

## Risks / Notes
- The main risk is turning the quickstart into a second long-form guide instead of a short entry section.
- If the slice stops feeling small and reviewable, split follow-up changes into a separate spec instead of expanding this one.
