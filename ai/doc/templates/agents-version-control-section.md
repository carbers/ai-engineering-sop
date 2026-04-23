# AGENTS.md `## Version control` section template (Plastic SCM)

Paste the content between the fences into the target project's `AGENTS.md` as a new top-level section.
This template is consumed by `ai/skill/init-plastic-scm.md` during project bootstrap.

- Do not add this section to a project that is not on Plastic SCM.
- Do not duplicate this section if one already exists; use `ai/skill/replan-or-escalate.md` instead.
- Keep the section short. Detailed cm usage should live in external references, not here.

```markdown
## Version control

This workspace uses **Unity Version Control** (formerly **Plastic SCM**), not Git.

### Detection

- `.plastic/plastic.selector` is the canonical workspace marker. Treat the workspace as Plastic unless a real `.git/` working tree is also present.
- Before running any status, diff, add, or commit command, confirm the active VCS. Do not run Git commands on a Plastic workspace.

### Command rules

- Prefer Plastic for repository operations: `cm status`, `cm add`, `cm checkin`.
- Do not use `cm diff` in forms that open the Plastic GUI diff window. In terminal workflows, bare file-path or revision-to-revision `cm diff` usage is considered incorrect.
- Only use `cm diff` when it is guaranteed to stay non-interactive, such as branch or changeset comparisons with `--format`, `--repositorypaths`, or `--download`.
- For local workspace review, prefer `cm status` to discover pending changes, then read or diff file content using normal shell reads or other non-interactive text diff tools.

### Ignore rules

- Plastic ignore rules live in `ignore.conf` at the repo root. Do not reintroduce `.gitignore`, `.gitattributes`, or `.gitkeep` as the primary mechanism.
- Cursor indexing exclusions live in `.cursorignore`, separate from `ignore.conf`.
- Do not add `.gitkeep` to pin empty directories. Document required layout under `project/*` or add meaningful placeholder content when a directory must exist in the depot.

### Bootstrap

- If `.plastic/plastic.selector` is present but this section is missing on first entry, run `ai/skill/init-plastic-scm.md` before any implementation work.
```
