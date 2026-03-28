# Testing Strategy

This SOP uses layered validation.

## 1. Black-box validation

Black-box validation is the default.

Use it to verify:
- externally visible behavior
- user-facing outcomes
- integration behavior
- stable acceptance cases

Black-box validation is the main path for task acceptance.

## 2. White-box validation

White-box validation is conditional. It complements black-box acceptance when internal logic needs direct protection.

Add it when the task changes:
- branch-heavy logic
- internal state transitions
- deterministic bugfix root causes
- caches, parsers, schedulers, rules engines, traces, analyzers
- internal contracts that black-box checks alone will not reliably protect

## What white-box validation should protect

Good targets include:
- branch selection
- state transitions
- error handling
- rollback behavior
- cache invalidation rules
- intermediate invariants
- deterministic regression paths

## What white-box validation should avoid

Do not overfit tests to:
- irrelevant helper call order
- local variable names
- brittle internal trivia
- implementation details likely to change during harmless refactors

## Bugfix-first rule

When fixing a deterministic bug, prefer turning the root cause into a regression-protecting test when appropriate. This is one of the strongest reasons to add white-box protection.

## What not to optimize for

Do not make raw coverage percentage the main goal.
Prefer protecting:
- critical internal contracts
- fragile stateful behavior
- regression-prone paths
- high-risk branches

## 3. Batch-level release checks

Do not turn every task spec into a release checklist.
For real product releases, do release-readiness review at the batch level.

A lightweight batch review should aggregate:
- included specs or change summaries
- any specs marked `release_sensitive`
- validation outcomes already completed during task execution
- deployment, migration, config, compatibility, and rollback notes
- post-release checks that still need human review

This reduces human collection work, but it does not replace human release judgment.
Use `ai/doc/templates/release-batch-template.md` when the project wants a lightweight release record.
