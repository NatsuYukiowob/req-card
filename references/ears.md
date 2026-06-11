# EARS — Acceptance Criteria Syntax

EARS (Easy Approach to Requirements Syntax) forces every acceptance
criterion into an unambiguous, testable sentence. Use it for the card's
**Acceptance** field. Write criteria in the user's language; keep the
structural keywords (WHEN / WHILE / IF...THEN / WHERE / SHALL) — translating
them is fine as long as the structure stays.

## Patterns

| Pattern | Form | Use for |
|---------|------|---------|
| Ubiquitous | THE SYSTEM SHALL `<behavior>` | always-true properties |
| Event-driven | WHEN `<trigger>` THE SYSTEM SHALL `<behavior>` | most cases — use this by default |
| State-driven | WHILE `<state>` THE SYSTEM SHALL `<behavior>` | mode-dependent behavior |
| Unwanted behavior | IF `<bad thing>`, THEN THE SYSTEM SHALL `<response>` | error handling, rollback paths |
| Optional feature | WHERE `<feature present>` THE SYSTEM SHALL `<behavior>` | config-dependent behavior |

## Rules

- `<behavior>` must be **observable**: a command output, an HTTP status, a
  file existing, a pod state — something a third party could check.
- One criterion = one behavior. Split compound sentences.
- An S-tier card needs 1–3 criteria. More only if genuinely needed.

## Examples

Bad (not observable):
> WHEN deployed THE SYSTEM SHALL work properly.

Good:
> WHEN `kubectl -n litellm get pods` runs THE SYSTEM SHALL show `1/1 Running`
> with `0 restarts` sustained for 10 minutes.

Good (unwanted behavior):
> IF the new config makes the pod crash, THEN THE SYSTEM SHALL be revertible
> by re-applying the previous manifest saved before the change.
