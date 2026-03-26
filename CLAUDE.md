# CLAUDE.md

This repository uses `AGENTS.md` as the canonical source of repository-level guidance.

## Source of truth

- Use `AGENTS.md` as the primary AI-tool entrypoint for repository-level behavior.
- Use `ai/README.md` for the `ai/*` namespace map and boundary rules.
- Follow `.cursor/rules/*`, `ai/doc/*`, and `ai/skill/*` as referenced by `AGENTS.md`.
- If `CLAUDE.md` and `AGENTS.md` differ, `AGENTS.md` wins.

This file is an adapter entry point, not a second rule system.
