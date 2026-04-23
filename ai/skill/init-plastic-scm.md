# Skill: init-plastic-scm

## Purpose
Bootstrap a copied project that uses Plastic SCM (Unity Version Control) so that AI tools stop defaulting to Git commands, stop opening the Plastic GUI via `cm diff`, and read a project-specific declaration of the active VCS from the project's own `AGENTS.md` and `project/CURRENT.md`.

This skill runs **once** per copied project. It is not a recurring workflow.

## Pre-execution guardrails

These rules apply from the moment this skill starts and continue throughout its execution. They also apply when `ai/skill/init-project-from-brief.md` delegates to this skill before the copied project's own `AGENTS.md` has been updated. They cover the pre-init window when backend-specific rules have not yet been injected into the project's own `AGENTS.md`.

- Do not run Git commands against a Plastic workspace. `.plastic/plastic.selector` is the authoritative marker; if it exists, treat the workspace as Plastic regardless of any leftover `.gitignore` or `.gitkeep`.
- Do not invoke `cm diff` in forms that open the Plastic GUI diff window. Bare file-path or revision-to-revision `cm diff` in a terminal context is considered incorrect. Use `cm diff` only with non-interactive flags such as `--format`, `--repositorypaths`, or `--download`.
- Prefer `cm status` for local review. Read file content with normal text reads. Do not drive `cm diff` as a browsing tool.
- Do not reintroduce `.gitignore`, `.gitattributes`, or `.gitkeep` during repair, rollback, or retry inside this skill; the skill's job is to remove them, not reinstate them.
- These guardrails are runtime rules for the executing agent. Do not copy them into project files; the injection target for project-facing rules is `ai/doc/templates/agents-version-control-section.md`.

## When to use
Use this skill when:
- a project copied from this starter is placed into a Plastic SCM workspace (the marker `.plastic/plastic.selector` is present)
- the project's `AGENTS.md` does not yet declare `Version control`
- `.gitignore` or `.gitkeep` files still exist and conflict with the Plastic `ignore.conf` model

Do not use this skill:
- after the project has already been bootstrapped
- on Git-only workspaces
- on workspaces that legitimately operate a dual Git + Plastic layout (that case requires an explicit decision, not a bootstrap)

## Inputs
- `.plastic/plastic.selector` marker file
- existing `.gitignore` content, if any
- existing `.gitkeep` file locations, if any
- `ai/doc/templates/ignore-conf-template.md`
- `ai/doc/templates/cursorignore-template.md`
- `ai/doc/templates/agents-version-control-section.md`
- the project's `AGENTS.md` and `project/CURRENT.md`, if the project uses the `project/*` control surface

## Outputs
- `ignore.conf` at repo root, generated from the template plus any translatable `.gitignore` rules
- `.cursorignore` at repo root, generated from the template
- a `## Version control` section appended into the project's own `AGENTS.md` that names Plastic SCM as the active backend and lists the non-interactive `cm` command rules
- `project/CURRENT.md` updated with a VCS declaration in `Current source of truth`, when the project uses the `project/*` control surface
- `.gitignore` deleted
- all `.gitkeep` files deleted
- a short init report printed to the user with: files created, files deleted, rules translated, rules flagged as not directly translatable, and a next-step task list (including README and project-description review)

## Non-Goals
- rewriting the project's `README.md` free text or project description
- creating a `project/decisions/DEC-*` record automatically
- converting Git history, branches, or remotes
- running any `cm` command against the live workspace (this skill only produces artifacts)
- handling non-Plastic backends

## Workflow

### 1. Detect the workspace
Confirm `.plastic/plastic.selector` exists at the repo root.
Also check for a real `.git/` working tree.

- If only `.plastic/plastic.selector` exists, proceed.
- If both markers exist, stop and return `needs_decision`. A dual Git + Plastic layout requires an explicit decision about which backend is authoritative; do not silently delete `.gitignore` or `.gitkeep` in that case.
- If only `.git/` exists, stop. This skill does not apply.

### 2. Translate `.gitignore` into `ignore.conf`
Start from `ai/doc/templates/ignore-conf-template.md` as the baseline.
Read the existing `.gitignore`, if any, and merge translatable rules into the project-specific slot at the bottom of the new `ignore.conf`.

Translate conservatively:
- plain file globs and directory globs translate directly
- comments translate directly
- `!`-prefixed negations may not behave identically; list them in the init report as flagged items
- character class ranges (for example `[abc]`) behave differently in Plastic; list them as flagged items
- Git-only mechanisms (`.gitkeep`, `.gitattributes` directives) are not translated

Do not invent new ignore rules beyond what the template and the existing `.gitignore` already cover.

### 3. Generate `.cursorignore`
Write `.cursorignore` at the repo root from `ai/doc/templates/cursorignore-template.md`.
The top comment must make it explicit that SCM ignores live in `ignore.conf`, and that `.cursorignore` is only for Cursor indexing. Do not copy SCM ignore rules into this file.

### 4. Update the project's own `AGENTS.md`
Insert a new `## Version control` section using `ai/doc/templates/agents-version-control-section.md`.
Fill in:
- the backend name (Plastic SCM / Unity Version Control)
- the marker file path (`.plastic/plastic.selector`)
- the ignore file path (`ignore.conf`)
- the required `cm` command rules (non-interactive `cm diff` only, `cm status` for local review, no `.gitkeep`)

If a `## Version control` section already exists, stop and return `needs_decision`. Do not overwrite a pre-existing declaration.

### 5. Update `project/CURRENT.md`
If the project uses the `project/*` control surface, add one line to `Current source of truth`:

```
- Plastic SCM workspace (marker: .plastic/plastic.selector, ignore file: ignore.conf)
```

Do not copy full rules into `project/CURRENT.md`. The control surface is a pointer, not a rule store.

### 6. Remove Git-only artifacts
After steps 1 through 5 succeed:
- delete `.gitignore`
- delete every `.gitkeep`, recording the deleted paths

If any `.gitkeep` deletion would leave a directory empty and the directory is meaningful to the project layout, flag it in the init report. Do not recreate the empty directory with a placeholder in this skill; the project owner decides how to document or replace the empty directory.

### 7. Emit the init report
Produce a short report with these sections:
- `Created`: paths of `ignore.conf`, `.cursorignore`, and any newly added AGENTS.md / CURRENT.md sections
- `Deleted`: `.gitignore` and each `.gitkeep` path
- `Flagged for review`: `.gitignore` rules that could not be translated directly, empty directories left after `.gitkeep` removal
- `Next-step tasks`: short checklist for the project owner, including:
  - review and update the project `README.md` project description and scope if needed
  - confirm the new `## Version control` section wording in the project's `AGENTS.md`
  - review the project-specific slot of `ignore.conf` for project-only patterns
  - decide whether a `DEC-*` decision record is warranted (use `ai/skill/decision-recording.md` only if yes)

## Stop conditions
Return `needs_decision` without editing files when:
- both `.plastic/plastic.selector` and a real `.git/` working tree exist
- the project's `AGENTS.md` already contains a `## Version control` section
- the request indicates the project intends to bootstrap a non-Plastic backend

Return `replan_required` when:
- `ai/doc/templates/ignore-conf-template.md`, `ai/doc/templates/cursorignore-template.md`, or `ai/doc/templates/agents-version-control-section.md` is missing
- the project's `AGENTS.md` is missing (the project has not been initialized from the starter yet)

## Common failure modes
- running the skill twice and doubling the `## Version control` section
- merging `.gitignore` rules without flagging non-translatable patterns
- putting SCM ignore rules into `.cursorignore`
- auto-rewriting the project's `README.md`
- producing a decision record that the user did not ask for
- deleting `.gitignore` on a workspace that still relies on Git history
