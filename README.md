# AI Engineering SOP

A minimal SOP for solo + AI collaboration. Its core is a set of constraints for the AI that converge toward my habits through use.

## Layout

Root holds only the shared entry files; every AI-produced artifact lives under `ai/`.

- **`AGENTS.md`** — the collaboration constitution. The single source of truth. Entry point for AI tools.
- **`CLAUDE.md`** — thin adapter that defers to `AGENTS.md` (no second rule system).
- **`ai/PROGRESS.md`** — the AI-maintained live ledger. Overview + active items.
- **`ai/skill/*.md`** — reusable workflows, added only when a workflow actually repeats. Currently: `background-dispatch`.

Design principle: **few hard rules, state kept separate, everything else grows on demand** — nothing is pre-stocked. When a rule doesn't cover a case, the AI confirms first, then codifies the outcome as a new rule (see `AGENTS.md` section 0). Skills appear the same way: only once a workflow has earned its place.
