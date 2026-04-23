# New Project SOP

Short human-reading reference for the copied-project first-use path.
The executable path lives in `ai/skill/init-project-from-brief.md`; this guide is the prose companion for readers who prefer to walk the flow manually.

## The Default Path

When you copy this starter into a new project:

1. Run `ai/skill/init-project-from-brief.md` with your project brief.
 The skill personalizes `AGENTS.md` and `README.md`, seeds `project/CURRENT.md`, `project/DOC_MAP.md`, and `ai/doc/facts/project-scope.md`, delegates to `ai/skill/init-plastic-scm.md` when the workspace is Plastic SCM, and hands off to `ai/skill/plan-to-spec.md`.
2. Derive the first task spec with `ai/skill/plan-to-spec.md`.
3. Implement from the spec with `ai/skill/execute-from-spec.md`.
4. Validate explicitly.
5. Close out deliberately with `ai/skill/session-closeout.md` when the result changed current state, memory, decisions, experiments, facts, or skills.

If you do not have a brief yet, the skill will fall back to a structured Q&A for the required fields before editing anything.

## Entrypoints In Copied Projects

Keep the entrypoints split:

- root `README.md` for humans
- `AGENTS.md` and any tool adapters for AI tools
- `ai/README.md` for the `ai/*` namespace

When human readers need a recovery-first current-state view, keep the root-level `project/` control surface and start with `project/CURRENT.md`.
If you adopt that control surface, keep `project/README.md`, `project/decisions/`, `project/experiments/`, the starter memory pages under `project/memory/*`, and `ai/skill/session-closeout.md` so the control surface stays current without duplicating execution artifacts.

## Day-One Minimal Set

The smallest practical copied-project set is:

- `AGENTS.md`
- `ai/README.md`
- `.cursor/rules/*`
- `ai/doc/templates/*`
- `ai/doc/specs/README.md`
- `ai/doc/facts/facts-index.md`
- `ai/skill/init-project-from-brief.md`
- `ai/skill/plan-to-spec.md`
- `ai/skill/execute-from-spec.md`
- `ai/skill/design-whitebox-tests.md`

Add more files only when they solve a real current need.
`ai/skill/autopilot.md` is advanced and on-demand; keep it only when the project explicitly wants bounded autonomous execution.

If the target project runs on Plastic SCM (Unity Version Control), also keep:

- `ai/skill/init-plastic-scm.md`
- `ai/doc/templates/ignore-conf-template.md`
- `ai/doc/templates/cursorignore-template.md`
- `ai/doc/templates/agents-version-control-section.md`

`init-project-from-brief` will call `init-plastic-scm` automatically when `.plastic/plastic.selector` is present. Projects on other backends do not need a VCS bootstrap.

If you want the guided path reference files and optional examples, also keep:

- `ai/doc/guides/new-project-sop.md` (this guide)
- `ai/doc/guides/testing-strategy.md`
- `ai/doc/guides/task-lifecycle-and-escalation.md`
- `ai/skill/replan-or-escalate.md`
- `ai/skill/decision-recording.md`
- `ai/skill/session-closeout.md`
- `ai/doc/templates/release-batch-template.md` when the project will prepare real product releases
- `ai/doc/specs/20260104-001-example-first-copied-project-quickstart.md` as a small-task example
- `ai/doc/guides/phase-aware-workflow.md` when long-task guidance is needed
- `ai/doc/guides/phase-aware-canonical-example.md`, `ai/doc/guides/phase-aware-example-main-plan.md`, `ai/doc/guides/phase-aware-example-sub-plan.md`, and `ai/doc/specs/20260103-001-example-adoption-entrypoint-slice.md` when you want the closed long-task example

## Plan Vs Spec

`init-project-from-brief` produces the project identity and control-surface seeds. It does not produce a plan or a spec.

Write a durable plan under `ai/doc/templates/plan-template.md` only when the phase, handoff, or checkpoint structure is worth re-reading later.
Otherwise move directly to `plan-to-spec` with the brief as plan-level input.

A task spec should shrink the plan into a narrow implementation contract.
See `ai/doc/specs/README.md` for naming, splitting, and lifecycle conventions.
For longer-running work, also use `ai/doc/guides/task-lifecycle-and-escalation.md` and `ai/skill/replan-or-escalate.md` so repair, rollback, replan, and escalation stay explicit.

## Validation

- black-box validation by default
- add white-box validation when triggered by internal complexity or regression sensitivity

See `ai/doc/guides/testing-strategy.md` for the trigger criteria.

## Write-back

After implementation and validation, create or update only what is stable and reusable:

- `project/CURRENT.md` when current operating state or next durable actions changed
- `project/memory/*` when stable project-facing memory should keep influencing later work
- `project/DOC_MAP.md` when the normal reading order or document roles changed
- `project/decisions/*` when a durable project-level choice was frozen (use `ai/skill/decision-recording.md`)
- `project/experiments/*` when a real experiment produced a reusable result
- `ai/doc/facts/project-scope.md` when scope or boundaries became clearer
- `ai/doc/facts/golden-cases.md` when stable reusable validation references are worth preserving
- `ai/skill/*` when a repeated workflow has stabilized

Do not turn every task discussion into permanent docs.

## Phase-Aware Variant

Use the phase-aware variant when one or more of these are true:

- work spans multiple phases or checkpoints
- a `main_plan` and one or more `sub_plan` views are both useful
- task ordering, dependency handling, or failure handling must be made explicit
- multiple people or models will hand the work across boundaries
- repair, rollback, replan, or escalation paths need to be reviewable

See `ai/doc/guides/phase-aware-workflow.md` and `ai/doc/guides/phase-aware-canonical-example.md`.

## Multi-Model Collaboration

If design discussion, planning, spec derivation, and execution are split across different tools or people, see `ai/doc/guides/design-to-spec-handoff.md`.
That guide is an extension of this SOP, not a replacement.
The same core rule still applies: implementation should run from a clear task spec, not directly from a broad design discussion.
