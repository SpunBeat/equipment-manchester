# Conventional Commits

Last updated: 2026-02-05

Purpose:
Make commit history readable, enable automated changelogs/versioning, and keep AI outputs consistent.

## Format
<type>(optional scope): <short summary>

Examples:
- feat(auth): add refresh token rotation
- feat(inventory): add equipment availability endpoint
- fix(payments): make webhook handler idempotent
- docs: add branch strategy
- chore: setup repo governance (phase 1)
- ci: add lint and test workflow
- refactor(api): extract rental pricing service
- test(api): add contract tests for inventory

## Types
- feat: new feature
- fix: bug fix
- docs: documentation only changes
- style: formatting only (no code logic changes)
- refactor: code change that neither fixes a bug nor adds a feature
- perf: performance improvement
- test: adding or updating tests
- build: build system or dependencies
- ci: CI configuration changes
- chore: repo maintenance (no production code change)
- revert: revert a previous commit

## Scopes (recommended, optional)
Use a scope when it helps:
- auth
- inventory
- contracts
- rentals
- payments
- permissions
- mobile
- web
- api
- db
- ci
- docs

## Rules
- Use imperative present tense ("add", "fix", "update"), not past tense.
- Keep the summary under ~72 characters.
- One purpose per commit. Avoid mixed changes.

## When to use BREAKING CHANGE
If a change breaks compatibility (especially contracts):
- Use a footer:
  BREAKING CHANGE: <what changed and why>

Example:
feat(contracts): rename equipmentId to assetId

BREAKING CHANGE: equipmentId renamed to assetId in inventory endpoints.