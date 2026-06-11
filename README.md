# req-card

A Claude Code skill that turns casual requests into **confirmed requirement
cards** — before the agent touches anything.

## Why

When you talk to a coding agent casually, it silently fills the gaps:
which cluster you meant, what "done" means, what it must not touch. Those
silent guesses are where hallucinated actions come from. req-card forces
every guess onto the table:

> **Goal / Scope / Environment / Acceptance (EARS) / No-go / Assumptions**

You veto or approve the card in seconds; only then does work start.

## How it behaves

- **S tier (small task):** the agent picks the closest template, fills the
  card, asks ONE confirmation question. Target cost to you: ~30 seconds.
- **L tier (big task):** the agent explores your repo first, then interviews
  you — one non-obvious question at a time, 7 max — and produces a card that
  can feed a brainstorming/design workflow.
- Acceptance criteria use [EARS syntax](references/ears.md)
  (`WHEN <trigger> THE SYSTEM SHALL <observable behavior>`) so "done" is
  testable, not vibes.
- The skill is English; **interaction follows your language** automatically.

## Install

```bash
git clone https://github.com/NatsuYukiowob/req-card ~/.claude/skills/req-card
```

That's it. Claude Code picks it up as `req-card`. Invoke manually with
`/req-card <request>` or let it trigger automatically on hands-on tasks.

## Customize (overlays)

Same-named (or same-purpose) templates override by layer: **project > personal > built-in**.

| Layer | Path | Lives in |
|-------|------|----------|
| Project | `<repo>/.claude/req-card/templates/` | your project's git |
| Personal | `~/.claude/req-card/templates/` | your machine only |
| Built-in | `templates/` here | this repo |

Personal data lives in `~/.claude/req-card/` — deliberately OUTSIDE this
skill's directory, so `git pull` upgrades never touch your templates or
archive.

Approved cards are archived to `~/.claude/req-card/archive/`. When the same
request pattern keeps showing up, the skill proposes turning it into a new
template.

Built-in templates: `generic`, `feature`, `bugfix`, `ops-change`,
`research`, `doc`.

## License

MIT

---

## 繁體中文

req-card 是一個 Claude Code skill:在 agent 動手之前,把你隨口說的需求變成
一張**需求卡**(目標/範圍/環境/EARS 驗收/禁區/已知假設)讓你確認。核心防
幻覺手段是「已知假設」欄——agent 原本會默默腦補的東西全部攤開給你打臉。

- 小任務(S 級):挑模板、填卡、一次確認,約 30 秒。
- 大任務(L 級):先讀你的 repo,再一次一題訪談(上限 7 題),產出的卡可以
  直接餵給 brainstorming/spec 流程。
- 互動語言自動跟隨使用者(你說中文它就全程中文)。

安裝:`git clone` 本 repo 到 `~/.claude/skills/req-card` 即可。

客製:同名模板覆蓋優先序「專案 > 個人 > 內建」;專案模板放
`<repo>/.claude/req-card/templates/`、個人模板放
`~/.claude/req-card/templates/`;定案的卡會歸檔在
`~/.claude/req-card/archive/`,同類需求出現多次時 skill 會主動提議固化成
新模板。
