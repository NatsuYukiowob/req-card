# Template: bugfix

Use for: fixing incorrect behavior.

## Must-clarify (ask, or state as an Assumption)

- Reproduction: exact steps / input that shows the bug today.
- Expected vs actual behavior.
- Root-cause fix wanted, or a contained workaround acceptable?
- Regression safety: what nearby behavior must stay intact?

## Card skeleton

**Goal:** `<one sentence — the wrong behavior to eliminate>`

**Scope:**
- In: `<the fix + a regression test>`
- Out: `<refactors / adjacent cleanups not included>`

**Environment:** `<repo / branch / affected component; where to reproduce>`

**Acceptance (EARS):**
- WHEN `<the reproduction steps run>` THE SYSTEM SHALL `<show the correct behavior>`
- WHEN `<the existing test suite runs>` THE SYSTEM SHALL `<pass with no new failures>`

**No-go:** `<behavior/contracts that must not change>`

**Assumptions:** `<suspected root cause if unconfirmed — mark clearly as hypothesis>`
