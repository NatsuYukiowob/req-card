# Template: ops-change

Use for: environment, configuration, infrastructure, or deployment changes.

## Must-clarify (ask, or state as an Assumption)

- Exactly which environment (cluster / host / namespace / stage)? Shared or
  production-like?
- Change path: direct apply, or via GitOps / config repo?
- Rollback: how to undo if it goes wrong?
- Blast radius: what else consumes this config/resource?

## Card skeleton

**Goal:** `<one sentence>`

**Scope:**
- In: `<resources/config to change>`
- Out: `<environments or resources explicitly untouched>`

**Environment:** `<cluster + namespace / host / config repo + branch>`

**Acceptance (EARS):**
- WHEN `<the change is applied>` THE SYSTEM SHALL `<observable healthy state, e.g. pod 1/1 Running, endpoint returns 200>`
- IF `<the change misbehaves>`, THEN THE SYSTEM SHALL `<restore the previous state via a concrete action, e.g. re-applying the saved pre-change manifest>`

**No-go:** `<resources / namespaces / secrets that must not be touched>`

**Assumptions:** `<inferred environment details, credentials, change windows>`
