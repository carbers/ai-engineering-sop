# Project Memory

This directory holds longer-lived project memory that should stay easy to recover without turning into a task log.
Use it for repeated agreements, recurring patterns, and reminders that will likely matter again in this same project.

Start here after `../CURRENT.md` when you need context that is broader than one task but not the same as current status.

## Memory Snapshot

- The recovery path is `project/CURRENT.md` first, then `project/memory/*`, then the active spec or repository rules.
- `project/memory/*` is for project-facing repeated memory, not frozen decisions, not task-local notes, and not `ai/doc/facts/*`.
- Update memory mainly during closeout through `../../ai/skill/session-closeout.md`; mid-slice edits are allowed only for already-stable repeated memory.
- Keep memory dense and actionable. Prefer short bullet entries with concrete triggers, responses, and links.
- Merge with existing entries instead of appending a new near-duplicate.

## Read Order

1. `working-agreements.md` for long-lived constraints, preferences, and collaboration rules.
2. `recurring-patterns.md` for repeated pitfalls, decision triggers, and stable local tactics.

## What Good Memory Looks Like

Good memory should help a returning reader answer questions such as:

- What do we repeatedly do in this project?
- What repeatedly goes wrong here?
- Which constraints or habits will affect my next slice?
- Which reminders are stable enough that I should know them before editing?

Keep entries short enough to scan in one pass.
If an entry becomes long, split details into a dedicated project-facing page and keep only the summary and pointer here.

## Update Discipline

Default to updating project memory during closeout through `../../ai/skill/session-closeout.md`.
Mid-slice updates are allowed only when the memory is already stable, repeated, and likely to affect later execution before closeout.

Before adding a new entry:

1. check whether the idea already exists
2. merge into the existing entry when it does
3. add a new entry only when the memory is genuinely new

Prefer updating the existing note over appending a near-duplicate.

## Store Here

- long-lived project-specific working agreements
- durable constraints or reminders that keep reappearing
- recurring project patterns, pitfalls, and local tactics
- short pointers to related decisions, facts, or active specs when that helps recovery

## Do Not Store Here

- step-by-step progress updates
- task-local implementation notes
- validation transcripts
- frozen project decisions that belong in `../decisions/*`
- reusable AI-oriented facts that belong in `../../ai/doc/facts/*`
- generic workflows that should become skills
- chronological session history

## Split Rule

Create a new memory page only when a topic has enough stable repeated content that one of these becomes true:

- the summary page is no longer easy to scan
- the topic needs its own recurring entries, tables, or curated links
- the topic is project-facing but too detailed for `working-agreements.md` or `recurring-patterns.md`

When splitting, keep a short summary and pointer in this index.

## Routing Guide

- Use `../CURRENT.md` for current phase, active slice, next actions, and current source of truth.
- Use `../decisions/*` for frozen project-level decisions.
- Use `../../ai/doc/facts/*` for stable reusable AI-oriented context.
- Use `../../ai/skill/*` for repeatable workflows.
