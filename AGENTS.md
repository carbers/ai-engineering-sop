# AGENTS.md — Collaboration Constitution

This file is the single source of truth for this repository.
It constrains how AI tools (Claude Code / Cursor / etc.) behave here.
Rules are few and hard. State does not live here — it lives in `PROGRESS.md`.

## 0. Meta-rule: how rules grow

1. **Where a rule exists → follow it exactly.** No improvising, no unrequested "improvements".
2. **Where no rule covers the case, or it's ambiguous → stop and confirm with me first.** Do not decide on your own.
3. **After we confirm → immediately write the outcome as a new rule** under `## 4. Specific rules`.
4. Goal: the ruleset **converges toward my habits through use**. An uncovered case is not a defect — it's the signal to add a rule.

Amendment process: on hitting a gap, propose **one draft rule**; write it into this file only after I approve.

## 1. When to stop and confirm (threshold)

- **Just do it**: local, reversible, small changes.
- **Confirm first** when any of these apply:
  - creating a file / creating a directory / deciding where a class of file belongs
  - changes spanning multiple modules or files
  - deleting or rewriting existing artifacts
  - introducing a new pattern, dependency, abstraction, or tool

When in doubt, treat it as "confirm first".

## 2. File discipline

- Every file has a **predetermined home**. Never invent ad-hoc paths or directories.
- **Temporary / intermediate artifacts**: if it fits in context, **don't write it to disk**; when a file is genuinely needed, it goes only to the environment's scratchpad directory — **never into this repository**.
- Only **final deliverables** enter the repo, and they go into the established engineering structure (if the structure is undefined, confirm first per `## 1`).
- Do not produce random, one-off, unowned scattered files.

## 3. Progress ledger

- AI maintains `PROGRESS.md`; **it does not depend on me updating it by hand**.
- Refresh two sections at the end of each reviewable slice:
  - **Overview**: current goal / done / in progress / next
  - **Active items**: for each — status, what changed, whether validated, what's left
- Move an item out of "in progress" once done. Keep the ledger lean — not a running log.

## 4. Specific rules

> Starts empty. Each time the amendment loop in `## 0` fires, append one rule here with its date.
> Keep each to roughly one line, executable, non-redundant with the above.

- (none yet)
