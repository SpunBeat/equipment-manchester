# AI Usage Policy

Last updated: 2026-02-05

## Purpose
Define how AI tools (ChatGPT, Claude, Cursor, Gemini, etc.) are used in this repository
to increase productivity without sacrificing quality, scope control, or correctness.

AI is an assistant, not an authority.

---

## Scope
This policy applies to:
- Code generation
- Documentation
- Commits and pull requests
- Refactoring and testing
- Analysis and debugging

This policy applies to both human developers and AI-assisted workflows.

---

## Allowed AI Usage
AI MAY be used to:
- Draft documentation following `doc-standards.md`
- Propose commit messages based on `git diff --staged`
- Generate boilerplate code **after contracts are defined**
- Assist with implementation details inside an approved scope
- Suggest refactors with explicit human approval
- Generate unit or integration tests based on existing behavior
- Help analyze logs, errors, and failures
- Assist in writing PR descriptions and review comments

---

## Restricted AI Usage
AI MUST NOT:
- Change or invent scope outside `docs/02-scope.md`
- Modify OpenAPI contracts without explicit intent and PR discussion
- Introduce new architectural patterns without an ADR
- Perform large refactors without approval
- Commit, push, merge, or rebase code autonomously
- Generate or store secrets, credentials, tokens, or production keys
- Bypass branch protection, CI checks, or review processes
- Create new documentation categories without approval

---

## Mandatory Workflow When Using AI
When AI is involved in implementation:

1. Confirm the change is within scope (`docs/02-scope.md`)
2. Update or reference contracts first (if applicable)
3. Use AI to assist implementation
4. Run tests or validations
5. Open a Pull Request with a clear description
6. Human review and merge

AI output is always reviewed before merge.

---

## AI-Assisted Commit Messages

AI may be used to generate commit titles and descriptions under strict rules.

### Source of Truth
- The ONLY allowed input for AI-generated commit messages is:
  `git diff --staged`
- Unstaged changes MUST NOT be used.

### Standard Prompt
When asking AI to generate a commit message, use the following prompt exactly:

```
Act as a Commit Message Generator.

Sources of truth:
- Commit rules, types, scopes, and format are defined in:
  docs/conventional-commits.md

Input:
- The output of `git diff --staged`

Tasks:
1) Read and strictly follow docs/conventional-commits.md.
2) Determine the correct commit type and optional scope based on the diff.
3) Generate a subject line:
   - imperative tense
   - ≤ 72 characters
   - matching the defined format
4) Generate a body with bullet points:
   - What changed (max 5 bullets)
   - Why it changed (1–2 bullets)
   - Risk or impact (if applicable)
5) If the diff introduces breaking changes, include the required footer exactly as defined.

Output format:
- Line 1: <type>(<scope>): <subject>
- Blank line
- Bullet-point body
- Footer (if applicable)

Constraints:
- Do NOT invent commit types or scopes.
- Do NOT describe changes not present in the diff.
- If no valid type applies, default to the closest allowed type and explain briefly in the body.
```

### Human Responsibility
- AI suggestions must be reviewed before committing.
- The final commit is always created by a human.
- If the commit message does not accurately reflect the diff, it must be edited.

---

## AI + Documentation
- AI may draft documentation but must follow `doc-standards.md`
- AI must not expand documentation unnecessarily
- AI must not create new doc types or structures
- All documentation must reflect current reality, not plans

---

## AI + Contracts
- Contracts are authoritative
- AI may generate contract drafts only with explicit intent
- Any contract change must be clearly visible and reviewed in a PR
- Breaking contract changes must be explicitly documented

---

## Security & Privacy
- Never paste secrets into AI tools
- Never upload proprietary customer or user data
- Treat all AI tools as external third parties
- Assume all AI interactions may be logged externally

---

## Enforcement
- This policy is enforced via PR reviews and CI checks
- Violations must be corrected before merge
- Repeated violations require process review

---

## Principle
> AI accelerates execution.  
> Humans own decisions, quality, and responsibility.
