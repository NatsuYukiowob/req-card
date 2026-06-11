# Template: feature

Use for: adding new functionality to an existing system.

## Must-clarify (ask, or state as an Assumption)

- Who uses this feature, through what interface (UI / API / CLI)?
- Smallest version that is still useful (the MVP cut)?
- Does anything change for current users / existing behavior?
- What proves it works end to end?

## Card skeleton

**Goal:** `<one sentence>`

**Scope:**
- In: `<the MVP behavior>`
- Out: `<explicitly deferred: nice-to-haves, other interfaces, migrations>`

**Environment:** `<repo / branch / module or service>`

**Acceptance (EARS):**
- WHEN `<user action>` THE SYSTEM SHALL `<new observable behavior>`
- WHEN `<an existing flow not related to the feature runs>` THE SYSTEM SHALL `<return the same response / exit code / output as before the change>`

**No-go:** `<APIs/schemas not to break, files not to touch>`

**Assumptions:** `<inferred choices: naming, placement, defaults, error behavior>`

> New architecture or a big feature? Prefer the L flow, and hand the
> approved card to a brainstorming/design skill as its input.
