# ignore.conf template (Plastic SCM / Unity Version Control)

Use this template to generate a project's root `ignore.conf`.

- Plastic SCM uses gitignore-like syntax but is not 100% compatible.
  Flag the following cases during translation: `!` negations, bracket character ranges (`[...]`), some folder-only patterns.
- Do not duplicate Cursor indexing rules here. Those belong in `.cursorignore`.
- Do not use `.gitkeep` to pin empty directories. Document required empty layout under `project/*` or replace with meaningful placeholder content.

Copy everything between the fences into `ignore.conf` at the project root, then fill in the project-specific slot.

```text
# Plastic SCM (Unity Version Control) ignore rules.
# Syntax is gitignore-like; edge cases differ (bracket ranges, some folder rules, negations).
# One pattern per line; '#' starts a comment.
# Cursor indexing exclusions live in .cursorignore, not here.

# --- OS & shell ---
Thumbs.db
ehthumbs.db
Desktop.ini
$RECYCLE.BIN/
.DS_Store
.AppleDouble
.LSOverride

# --- Editors & local tool state ---
.idea/
.vs/
.vscode/
*.suo
*.user
*.userosscache
*.sln.docstates

# --- Python ---
__pycache__/
*.py[cod]
*$py.class
.Python
.venv/
venv/
ENV/
env/
*.egg-info/
.eggs/
dist/
build/
*.egg
.pytest_cache/
.mypy_cache/
.ruff_cache/
.coverage
htmlcov/
.tox/
.nox/
.hypothesis/

# --- Node / frontend (when present) ---
node_modules/
npm-debug.log*
yarn-debug.log*
yarn-error.log*
pnpm-debug.log*
.npm/
.pnpm-store/

# --- Secrets & local env (keep templates like .env.example trackable) ---
.env
.env.local
.env.development.local
.env.test.local
.env.production.local

# --- Logs & temp ---
*.log
logs/
tmp/
temp/
.cache/

# --- Jupyter / notebooks ---
.ipynb_checkpoints/

# --- OS-generated junk ---
*~
*.swp
*.swo

# --- Project specific (fill in per project) ---
# Add regenerable run outputs, local credential files, large binaries, or
# project-only scratch trees here. Keep this section small and reviewable.
```

## Translation notes

When an existing `.gitignore` is being merged into this file:

- plain globs and directory globs can be copied directly into the `Project specific` section
- leading `!` negations must be reviewed manually and listed in the init report
- character class ranges such as `[abc]` must be reviewed manually
- `.gitkeep` entries are intentionally dropped; do not translate them
- `.gitattributes` directives are out of scope; leave them for a separate review
