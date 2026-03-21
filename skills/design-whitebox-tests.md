# Skill: design-whitebox-tests

## Purpose
Determine whether white-box validation is needed and identify the right internal logic to protect.

This skill complements black-box acceptance. It does not replace it.

## When to use
Use this skill when a task:
- changes branch-heavy logic
- changes internal state transitions
- fixes a deterministic bug
- changes caches, parsers, schedulers, rules engines, traces, analyzers
- changes important internal contracts that black-box checks alone may not protect

## Inputs
- task spec
- relevant bug or regression context
- affected internal logic
- current black-box validation plan

## Outputs
- whether white-box validation is needed
- what internal logic should be protected
- what not to assert
- suggested regression protection direction

## What to protect
Prefer protecting:
- branch selection
- state transitions
- error handling paths
- rollback behavior
- cache invalidation rules
- intermediate invariants
- deterministic regression paths

## What not to assert
Avoid overfitting to:
- helper call order with no business meaning
- local implementation trivia
- brittle details likely to change during harmless refactors
- irrelevant internal naming

## Bugfix guidance
When a task fixes a deterministic bug, prefer converting the root cause into a regression-protecting test when appropriate. This is a strong trigger for white-box protection.

## Common failure modes
- adding white-box checks where black-box acceptance is already sufficient
- asserting incidental implementation details
- chasing coverage percentages instead of protecting risk
- failing to lock the known regression path
