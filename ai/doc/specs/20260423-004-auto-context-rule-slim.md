# Auto-Context Rule Slim

## Metadata

### Source Plan / Request
User asked whether the default auto-loaded context is bloated, then approved the recommendation to slim `.cursor/rules/*` into thin pointers to `AGENTS.md` and merge `boundaries.mdc` with `scope-control.mdc`.

### Parent Phase
Minimal project control surface sustainment.

### Parent Plan
None. This narrows the default-context audit into one reviewable rules-layer slice.

### Status
done

### Related Specs
- `ai/doc/specs/20260422-001-sop-execution-link-hardening.md` (prior workflow-rule refinement)

### Release Sensitivity
normal

## Goal
Eliminate the duplication between `.cursor/rules/*.mdc` and `AGENTS.md` on the per-turn auto-loaded layer, without changing any execution contract.

## In Scope
- Slim `.cursor/rules/workflow.mdc`, `writeback.mdc`, `validation.mdc` to thin pointers at AGENTS.md sections plus a short list of execution-critical reminders.
- Merge `.cursor/rules/scope-control.mdc` into `.cursor/rules/boundaries.mdc` and delete `scope-control.mdc`.
- Preserve every existing `alwaysApply: true` frontmatter and each rule's `description` intent.

## Out of Scope
- Any edit to `AGENTS.md` itself (it is the canonical source of truth for these topics).
- Changes to `ai/doc/*`, `ai/skill/*`, `project/*`, or `README.md`.
- Introducing new rule files or a new rule category.

## Allowed Edits
- `.cursor/rules/workflow.mdc`
- `.cursor/rules/writeback.mdc`
- `.cursor/rules/validation.mdc`
- `.cursor/rules/boundaries.mdc`
- `.cursor/rules/scope-control.mdc` (deletion)
- this spec

## Disallowed Edits
- `AGENTS.md`, `CLAUDE.md`, `ai/README.md`
- `ai/skill/*`, `ai/doc/*` other than this spec
- `project/*`

## Affected Area
`.cursor/rules/*` auto-loaded guardrails.

## Task Checklist
- [x] Slim `workflow.mdc` to a pointer plus execution-critical reminders.
- [x] Slim `writeback.mdc` to a pointer plus execution-critical reminders.
- [x] Slim `validation.mdc` to a pointer plus execution-critical reminders.
- [x] Fold `scope-control.mdc` into `boundaries.mdc` and delete `scope-control.mdc`.
- [x] Confirm no dangling references to `scope-control.mdc` in the repo.

## Done When
Each remaining `.cursor/rules/*.mdc` file is a short pointer to an `AGENTS.md` section plus a handful of execution-critical reminders; `scope-control.mdc` no longer exists; references to `.cursor/rules/workflow.mdc` and `.cursor/rules/*` elsewhere in the repo still resolve; AGENTS.md is unchanged.

## Validation

### Black-box Checks
- `rg scope-control` returns no remaining references.
- `rg workflow.mdc` still resolves to the slimmed file.
- Each slimmed rule file retains `alwaysApply: true` frontmatter.
- Total line count across `.cursor/rules/*.mdc` is materially lower than before (target: roughly halved).

### White-box Needed
No

### White-box Trigger
Documentation guardrails only; no executable branches.

### Internal Logic To Protect
None.

## Repair / Rollback

### Repair Budget
One pass to fix wording drift or dangling references.

### Rollback Scope
Revert only the five rule files if the slimmed layer loses an execution-critical guardrail that AGENTS.md does not already carry.

### Escalation Condition
Stop for `needs_decision` if slimming reveals a rule that has no equivalent in AGENTS.md and should instead be promoted there.

## Write-back Needed
No

The edit itself is the write-back (refinement of repository-level operating guidance). No `project/*`, facts, or skill updates are triggered by this slice.

## Risks / Notes
- Keep each slimmed file self-explanatory enough that a Cursor session without AGENTS.md still gets the top-level shape of the rule.
- Do not drop the pointers to `ai/skill/execute-from-spec.md` and `ai/skill/replan-or-escalate.md` from the workflow rule; those are the two skill references that execution flow actively depends on.
