# .cursorignore template

Use this template to generate a project's root `.cursorignore`.

- `.cursorignore` controls what Cursor indexes and loads as codebase context.
- It is not a version control ignore file. SCM ignores live in the project's VCS ignore file (`ignore.conf` for Plastic SCM, `.gitignore` for Git).
- Keep this file focused on excluding large, generated, or noisy trees that do not help the agent.

Copy everything between the fences into `.cursorignore` at the project root, then fill in the project-specific slot.

```text
# Cursor index / codebase context exclusions (gitignore-style).
# SCM ignores live in the project's VCS ignore file (ignore.conf for Plastic SCM,
# .gitignore for Git); this file is only for Cursor.

# --- OS ---
Thumbs.db
ehthumbs.db
Desktop.ini
$RECYCLE.BIN/
.DS_Store

# --- IDE / local tool state ---
.idea/
.vs/

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

# --- Node ---
node_modules/
npm-debug.log*
yarn-debug.log*
yarn-error.log*
pnpm-debug.log*
.npm/
.pnpm-store/

# --- Secrets & local env ---
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

# --- Jupyter ---
.ipynb_checkpoints/

# --- Project specific (uncomment / add when those trees exist) ---
# datasets/
# artifacts/
# checkpoints/
# wandb/
# runs/
```
