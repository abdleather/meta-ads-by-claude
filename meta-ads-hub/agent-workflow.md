# Agent Workflow

_Last updated: 2026-06-01_

How Claude, Codex, Antigravity 2.0, and ChatGPT work together on ABD Leather Meta Ads without stepping on each other.

---

## Roles
| Agent | Role | Instructions |
|-------|------|--------------|
| ChatGPT | Manager — strategy & decisions | ABD Brand project chat |
| Claude | Execution & reporting (Meta MCP + WordPress MCP) | this repo + `~/.claude/skills/` |
| Codex | Technical execution (code, PHP, JS, CSS, FFmpeg) | `~/.codex/AGENTS.md` |
| Antigravity 2.0 | Visual QA, responsive testing, screenshots | `~/.antigravity-ide/INSTRUCTIONS.md` |

## The standard loop
**Diagnose → Recommend → Ask Approval → Execute → Report.**

1. **Read first.** `current-state.md`, `handoff-for-agents.md`, and the relevant `skills/` file. No exceptions.
2. **Diagnose read-only.** Pull data, inspect, walk the funnel. No changes yet.
3. **Recommend.** Write the proposed fix into `fixes-pending-approval.md`.
4. **Ask approval.** Report to Abdullah in plain English, starting "I am Claude." Wait for an explicit yes.
5. **Execute.** Only the approved change. Clear AirLift cache if pixel/site touched.
6. **Report + log.** Update `current-state.md`, `fixes-applied.md`, `reports.md`. Report result to Abdullah, then wait for the next task.

## Task queue
GitHub Issues on `abdleather/abd-website` and this repo. Issues tagged "FOR CLAUDE" → Claude. Comment ACTIVE when starting, DONE when finished.

## Approval gate (never bypass)
No change to ads, budget, pixel, plugins, website, or checkout — and no publishing a duplicate/draft ad, and no budget increase above Rs 500/day — without Abdullah's explicit approval.

## Security
Never write tokens, passwords, card numbers, or access keys into this repo, a report, or a commit. The CAPI token stays in WordPress only.

## Reporting style
Simple, beginner-friendly English. No jargon. Always: what I checked → what I found → what I suggest → what I need approval for.
