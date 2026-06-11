---
name: req-card
description: Use when the user requests any hands-on task — changing code, configs, infrastructure or deployments, or creating files/documents. Turns the casual request into an explicit requirement card (goal / scope / environment / acceptance / no-go / assumptions) that the user confirms BEFORE any work starts. Do NOT use for pure questions, status checks, or open discussion.
---

# req-card — Requirement Card Intake

Turn casual requests into unambiguous, confirmed requirement cards before
doing any work. The core anti-hallucination move: every assumption you would
silently make gets written down and shown to the user to veto.

## Hard rules

1. **Language.** ALWAYS interact and write the card in the user's language.
   These skill files are English; your output follows the user.
2. **No work before confirmation.** Do not edit, run, or create anything for
   the task until the user approves the card.
3. **Assumptions is never empty.** If you truly assumed nothing, write
   "none — all fields user-stated".

## Step 1 — Should this run?

Run for any hands-on task (something will be changed or created). Skip for
pure Q&A, status checks, or discussion — answer those normally. The user can
also invoke this skill manually at any time.

## Step 2 — Resolve templates (overlay order)

Look for template directories in this order; for same-named or
same-purpose templates the earlier layer wins:

1. **Project:** `<project root>/.claude/req-card/templates/`
2. **Personal:** `~/.claude/req-card/templates/`
3. **Built-in:** `templates/` inside this skill directory.

List what exists, pick the closest match for the request. No good match →
use built-in `templates/generic.md`.

## Step 3 — Tier the task

- **S (small):** scope clearly bounded — single file / single resource /
  known routine operation — AND you can fill every card field with
  confidence.
- **L (large):** new feature, new component, architecture change,
  cross-system work, OR you are unsure about any card field.

When in doubt → L.

## Step 4-S — Small-task flow (target: ≤30 seconds for the user)

1. Fill the card from the chosen template (schema in Step 5). Read
   `references/ears.md` for the Acceptance field.
2. Confirm with ONE question (use AskUserQuestion if available, plain text
   otherwise), options exactly:
   - **Proceed as carded**
   - **Edit a field** (apply the correction, re-confirm once)
   - **Upgrade to full interview** (switch to Step 4-L)
   - **Cancel** (stop; do not archive)
3. On approval: archive the card (Step 6), then execute the task following
   the card. Treat **No-go** as hard limits and **Acceptance** as the
   definition of done.

## Step 4-L — Large-task flow

1. **Explore first.** Read the relevant files / docs / recent commits before
   asking anything.
2. **Interview** following `references/questioning.md`: one question per
   message, multiple-choice preferred, only non-obvious questions, hard cap
   7. Stop as soon as every card field is solid.
3. Produce the full card; confirm exactly like Step 4-S item 2.
4. On approval: archive (Step 6). If the task is creative work (new
   feature / component / architecture) and a brainstorming or design skill
   is available, hand the approved card to it as its input — the card
   replaces that skill's early requirement-discovery phase. Otherwise
   execute directly.

## Step 5 — Card schema (six fields, all required)

| Field | Content |
|-------|---------|
| **Goal** | One sentence — the outcome the user wants. |
| **Scope** | What is in, AND what is explicitly out. |
| **Environment** | Which system / cluster / host / repo / branch this touches. |
| **Acceptance** | EARS sentences (see `references/ears.md`): `WHEN <trigger> THE SYSTEM SHALL <observable behavior>`. 1–3 criteria for S tier. |
| **No-go** | Files, resources, or operations that must not be touched. |
| **Assumptions** | Everything you inferred rather than was told — shown for the user to veto. Never empty. |

## Step 6 — Archive & sedimentation

- Save the approved card to `~/.claude/req-card/archive/YYYY-MM-DD-<slug>.md`
  (create directories if missing). Cancelled cards are NOT saved.
- When the same request pattern has appeared 2–3 times with no matching
  template, propose creating one — ask whether it belongs in the personal or
  the project overlay. Only create it if the user agrees.

## Edge rules

- Interview cap hit with major unknowns left → don't push; record them in
  Assumptions as explicit risks and let the confirmation gate decide.
- Tier misjudged mid-flow (L turns out trivial) → close the card early and
  say so.
- No template fits → built-in `generic.md`, never skip the card.
