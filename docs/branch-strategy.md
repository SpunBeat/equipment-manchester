# Branch Strategy

Last updated: 2026-02-05

Purpose:
Keep a predictable, low-risk workflow that works for solo development and scales to a team.

## Branches
- main: always stable, production-ready.
- (optional) dev: integration branch for staging environments. Only use if you actually deploy staging.

Default recommendation:
Use main + short-lived feature branches. Add dev only if needed.

## Branch Naming
Use the following prefixes:
- feat/<short-description>      (new feature)
- fix/<short-description>       (bug fix)
- docs/<short-description>      (documentation)
- refactor/<short-description>  (refactoring, no behavior change intended)
- chore/<short-description>     (tooling, repo maintenance)
- ci/<short-description>        (CI/CD changes)
- test/<short-description>      (test-only changes)

Examples:
- feat/equipment-inventory
- feat/rental-contracts
- fix/payment-retry-idempotency
- docs/update-scope
- chore/phase-1-governance

## Pull Requests
All changes to main must go through a PR.

PR rules:
- Keep PRs small and focused.
- One logical change per PR whenever possible.
- If a change affects contracts, contract changes must be explicit and reviewed.

## Merge Strategy
Preferred:
- Squash merge (keeps history clean and PR-based).
Alternative:
- Rebase merge (if you prefer linear history).

Avoid:
- Merge commits for every PR (unless required by your org policy).

## What requires a PR (always)
- Any change to contracts/*
- Any change to CI workflows
- Any change that touches auth, payments, permissions
- Any change that modifies docs scope or architecture decisions

## Hotfix Flow (if needed)
- Branch from main: fix/<issue>
- PR back to main
- Tag release if you use versioning
- Document incident if it impacted users