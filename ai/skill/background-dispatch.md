# Skill: Background Dispatch

## When to use

Dispatching long-running or slow work (executors, sub-agents, remote jobs) from a loop or hub that must stay responsive.

## Rule

- Long dispatches run in the **background** (`background:true`), never in the foreground — a blocking foreground dispatch hangs the whole hub.
- **Ack first → kick off in the background → report the result when the completion notification lands.**
- Executors can die or stall mid-run. If one stays silent well past its expected horizon:
  1. check its output for staleness,
  2. then re-dispatch or take over.
- Never sit waiting on a dead run.
