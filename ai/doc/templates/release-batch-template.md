# Release Batch Template

Use this template only when preparing a real product release, deploy batch, or coordinated rollout.
This is a project-facing release record. Store the filled artifact in the project's chosen release docs location, for example `project/releases/REL-YYYYMMDD-NNN.md` or another release-docs path the project already uses.
Do not create one for every task spec.

Use it to aggregate the few release-sensitive specs in the batch and the checks a human still needs to review before release.

## Batch
What is this release batch called, when is it planned, and who owns the final go/no-go call?

## Included Specs
Which spec paths, change summaries, or other reviewed slices are included in this batch?

## Release-Sensitive Changes
Which included specs are marked `release_sensitive`, and why?

## Automated Checks
Which automated or repeatable checks passed for this batch?

## Manual Checks
What still requires human confirmation before release?

## Deployment / Migration / Config Notes
What sequence, migration, feature flag, environment, or configuration steps matter?

## Rollback Notes
How would this batch be rolled back if needed?

## Post-Release Checks
Which dashboards, smoke checks, alerts, or business signals should be watched after release?

## Release Decision
Choose one:
- `ready`
- `ready_with_risk`
- `hold`

## Residual Risks
What risk remains, and who is accepting it?
