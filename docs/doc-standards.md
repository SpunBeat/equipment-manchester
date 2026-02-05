# Documentation Standards (doc-standards)

Purpose:
Keep documentation minimal, current, and useful. Prevent duplication, stale docs, and AI-generated noise.

## Golden Rules
1. Documentation must reflect reality (what exists), not plans.
2. Contracts and code are the source of truth for behavior. Docs explain intent, scope, and decisions.
3. If a document is not referenced by a workflow (PR, release, incident), it should not exist.
4. Keep docs short: prefer links to source-of-truth artifacts over long explanations.

## Documentation Types

### 1) Living Docs (few, updated over time)
Definition:
Documents that describe current processes, scope, and operational guidance.

Examples:
- docs/00-problem.md
- docs/01-domain.md
- docs/02-scope.md
- docs/ai-usage.md
- docs/release.md
- docs/rollback.md
- docs/observability.md
- docs/runbook.md

Rules:
- Must stay under ~2 pages each.
- Update only when the underlying process or scope changes.
- Avoid feature-by-feature logging here.

### 2) Event-Based Docs (many, immutable)
Definition:
One file per event/decision/incident. These are records and should not be rewritten.

Examples:
- docs/adr/YYYYMMDD-<decision>.md
- docs/incident/log/YYYY-MM-DD-<incident>.md
- docs/features/YYYY-MM-DD-<feature>.md (only when required)

Rules:
- One event per file.
- After "Accepted" (ADR) or "Closed" (Incident), do not edit. Add a new record instead.
- Use dates in filenames.

### 3) Technical Artifacts (not narrative docs)
Definition:
Versioned artifacts that are already source-of-truth.

Examples:
- contracts/*.openapi.yaml
- database migrations
- CI workflows
- generated clients/types

Rules:
- Do not duplicate these in docs.
- Describe how to use them only when needed (short pointers in runbook).

## ADR Policy
Create an ADR only if the decision is:
- hard to reverse,
- affects multiple layers (API/DB/Frontend),
- has long-term impact,
- and has reasonable alternatives.

ADR format (max 1 page):
- Context
- Decision
- Consequences
- Status (Proposed/Accepted/Superseded)

Location:
- docs/adr/YYYYMMDD-<short-title>.md

## Feature Documentation Policy
Default: no extra docs per feature.

Create a feature brief only if:
- touches multiple modules,
- is high risk (security/payments/data),
- or is business-critical and easy to misunderstand later.

Location:
- docs/features/YYYY-MM-DD-<feature>.md

Max length:
- 1 page.

## Ownership & Freshness
- Each living doc must have a "Last updated" line at the top.
- If a living doc is outdated, it must be updated as part of the next relevant PR.

## Anti-Patterns (avoid)
- Duplicating OpenAPI details in prose.
- Writing docs for screens/components.
- Writing speculative roadmaps inside docs.
- Allowing AI to create new doc types without approval.

## AI Interaction Rules (documentation)
- AI may draft docs but must follow this standard.
- AI must not create new documentation categories.
- AI must not expand docs unnecessarily; prefer concise updates.