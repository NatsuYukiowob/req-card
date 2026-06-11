# Template: doc

Use for: writing or updating documentation.

## Must-clarify (ask, or state as an Assumption)

- Audience, and their prior knowledge?
- Tier/tone: detailed technical, technical summary, or plain-language? One
  version or several?
- Source of truth the doc must match (code, spec, live system)?
- Format and destination (md / docx, repo path).

## Card skeleton

**Goal:** `<one sentence>`

**Scope:**
- In: `<sections/topics covered>`
- Out: `<topics explicitly out>`

**Environment:** `<file path(s) and format>`

**Acceptance (EARS):**
- WHEN a target reader reads the doc THE SYSTEM SHALL `<enable them to do/understand X without other sources>`
- WHEN claims in the doc are checked against `<source of truth>` THE SYSTEM SHALL `<match it>`

**No-go:** `<docs not to modify; secrets/internal info not to include>`

**Assumptions:** `<inferred audience, tier, structure>`
