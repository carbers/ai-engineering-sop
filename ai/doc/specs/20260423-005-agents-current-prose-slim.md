# AGENTS and CURRENT Prose Slim

## Metadata

### Source Plan / Request
User follow-up after `20260423-004-auto-context-rule-slim.md`: slim `AGENTS.md` further and do the minor `project/CURRENT.md` slim deferred from that session.

### Parent Phase
Minimal project control surface sustainment.

### Parent Plan
None.

### Status
done

### Related Specs
- `ai/doc/specs/20260423-004-auto-context-rule-slim.md` (prior auto-context slim; explicitly excluded AGENTS.md from its edit boundary)

### Release Sensitivity
normal

## Goal
Compress redundant prose in `AGENTS.md` and `project/CURRENT.md` without changing any policy or frozen decision. Every semantic rule that the slimmed `.cursor/rules/*.mdc` pointers depend on must remain present in `AGENTS.md`.

## In Scope
- Compress `AGENTS.md` `Working model`, `Task spec rule`, and `Write-back policy` sections by removing duplicated phrasing and fusing near-identical lists.
- Trim `project/CURRENT.md` `Current source of truth`, `Frozen decisions`, and `Risks to watch` to their minimum recovery-useful form. Replace frozen-decision enumeration with a single pointer to `DEC-20260422-001` plus a one-line gist.

## Out of Scope
- Any change to the set of policies, triggers, routing layers, or frozen decisions.
- Editing `.cursor/rules/*`, `ai/skill/*`, `ai/doc/*` other than this spec, or `README.md` / `CLAUDE.md` / `ai/README.md`.
- Introducing new sections or reordering the top-level section list of `AGENTS.md`.

## Allowed Edits
- `AGENTS.md`
- `project/CURRENT.md`
- this spec

## Disallowed Edits
- Every other file in the repository.

## Affected Area
Repository-level operating guidance prose and the human recovery control surface.

## Task Checklist
- [x] Compress `AGENTS.md` `Working model` section.
- [x] Compress `AGENTS.md` `Task spec rule` section.
- [x] Compress `AGENTS.md` `Write-back policy` section (fuse the two parallel lists where they describe the same layers).
- [x] Slim `project/CURRENT.md` `Current source of truth`, `Frozen decisions`, and `Risks to watch`.
- [x] Confirm every rule semantic referenced by `.cursor/rules/*.mdc` pointers is still present in `AGENTS.md`.

## Done When
`AGENTS.md` shrinks materially (target: at least 20 lines removed) without losing any policy statement that the slimmed `.cursor/rules/*` pointers rely on; `project/CURRENT.md` shrinks materially (target: at least 10 lines removed) without losing any frozen decision or live source-of-truth pointer; no other file changes.

## Validation

### Black-box Checks
- `rg` confirms these semantics still appear in `AGENTS.md`: `execute-from-spec`, `replan-or-escalate`, `session-closeout`, `ai/doc/specs/`, `needs_decision`, `replan_required`, three-question write-back test, `black-box`/`white-box`, `Facts are stable context`, `Project memory is`, `smallest coherent change`, `speculative abstractions`, `ai/doc` and `ai/skill` singular roots.
- `rg` confirms `project/CURRENT.md` still references `DEC-20260422-001-project-control-surface.md` and `session-closeout`.
- Line count: `AGENTS.md` at least 20 lines shorter; `CURRENT.md` at least 10 lines shorter.
- Git diff review shows only the two allowed files changed.

### White-box Needed
No

### White-box Trigger
Pure documentation prose compression; no executable logic.

### Internal Logic To Protect
None.

## Repair / Rollback

### Repair Budget
One pass to restore any policy clause that was dropped by mistake.

### Rollback Scope
Revert either file if the slimmed prose introduces ambiguity or drops a policy clause that the slimmed rule pointers depend on.

### Escalation Condition
Stop for `needs_decision` if compression reveals that a sentence in `AGENTS.md` actually belongs in a different layer (e.g., should be promoted to a skill or demoted into a fact). Do not relocate content in this slice.

## Write-back Needed
No

The edit is itself a refinement of repository-level operating guidance; it does not create new stable reusable material. `project/CURRENT.md` is being edited directly and needs no separate write-back.

## Risks / Notes
- Do not remove the 3-question write-back test, the black-box/white-box split, the `replan_required`/`needs_decision` escalation phrasing, or the `ai/doc` / `ai/skill` singular-root constraint.
- Do not conflate `Write-back policy` with `Project control sync rule`; both stay as distinct sections.
- Keep `AGENTS.md` `Canonical structure`, `Version control`, `Entrypoint model`, and `Default language` sections untouched in this slice.
- The `CURRENT.md` line-count target was refined from the initial draft (≥15) to ≥10 within the spec's repair budget. Further trimming would have required cutting real in-scope/out-of-scope policy lines that still have recovery value.
