# AGENTS.md — Collaboration Constitution

This file is the single source of truth for this repository.
It constrains how AI tools (Claude Code / Cursor / etc.) behave here.
Rules are few and hard. State does not live here — it lives in `ai/PROGRESS.md`.

## 0. Meta-rule: how rules grow

1. **Where a rule exists → follow it exactly.** No improvising, no unrequested "improvements".
2. **Where no rule covers the case, or it's ambiguous → stop and confirm with me first.** Do not decide on your own.
3. **After we confirm → if the outcome is a reusable rule (not a one-off approval), write it** under `## 5. Specific rules`.
4. Goal: the ruleset **converges toward my habits through use**. An uncovered case is not a defect — it's the signal to add a rule.

Amendment process: on hitting a gap, propose **one draft rule**; write it into this file only after I approve.

### Precedence & conflicts

- A more specific rule refines a more general one; read them together, the narrower scope wins. This is normal interpretation, not a conflict.
- **A genuine contradiction between two rules is a stop-and-confirm event, never auto-resolved.** Surface the conflicting rules to me and let me decide; then resolve by editing or removing a rule (supersede in place) so the ruleset stays internally consistent (git keeps the history). Never silently pick a winner and proceed.

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

- AI maintains `ai/PROGRESS.md`; **it does not depend on me updating it by hand**.
- Refresh two sections at the end of each reviewable slice:
  - **Overview**: current goal / done / in progress / next
  - **Active items**: for each — status, what changed, whether validated, what's left
- Move an item out of "in progress" once done. Keep the ledger lean — not a running log.

## 4. Self-verification

Before marking a slice done — and before any commit — silently check the work against §1–§3. Write to `ai/PROGRESS.md` only when a check fails or the slice changed durable state (per §3), never one line per commit. The checks:

- Did any change hit a "confirm first" case (§1) without confirming?
- Did any file land outside its predetermined home, or a temp file enter the repo (§2)?
- Is the ledger refreshed (§3), and was any new/ambiguous case codified or any conflict surfaced (§0)?

If a check fails, fix it before proceeding; if the fix needs a decision, stop and confirm.

## 5. Specific rules

> Starts empty. Each time the amendment loop in `## 0` fires, append one rule here.
> Keep each to roughly one line, executable, non-redundant with the above.

- AI-produced document artifacts live under `ai/` (e.g. `ai/PROGRESS.md`), isolated from human-facing files. The repo root holds only shared/human entry files: `README.md`, `AGENTS.md`, `CLAUDE.md`.
- Stay attentive to performance. On clearly poor performance, fix the bottleneck before (re-)running — don't idly wait out a known-slow run.
