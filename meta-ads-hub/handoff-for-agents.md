# Handoff For Agents

_Last updated: 2026-06-01_

This file lets any AI — Claude, Codex, Antigravity 2.0, or ChatGPT — pick up the Meta Ads work from exactly where the last one stopped.

---

## Before you touch anything, read these (in order)
1. `meta-ads-hub/current-state.md` — live status
2. `meta-ads-hub/handoff-for-agents.md` — this file
3. `skills/meta-ads-skill.md`
4. `skills/meta-mcp-usage.md`
5. `skills/pixel-capi-debugging.md`
6. `skills/woocommerce-funnel-debugging.md`
7. `meta-ads-hub/known-problems.md` and `fixes-pending-approval.md`

## Who does what
| Agent | Role |
|-------|------|
| ChatGPT | Strategy + decisions (the manager) |
| Claude | Execution + reporting via Meta MCP + WordPress MCP |
| Codex | Code/scripts/PHP/JS/CSS/FFmpeg execution |
| Antigravity 2.0 | Visual QA, responsive testing, screenshots |

## The one process everyone follows
**Diagnose → Recommend → Ask Approval → Execute → Report.**
No write/spend/publish action happens without Abdullah's explicit yes.

## Current handoff state (2026-06-01)
- Campaign **ABD Leather — Shoulder Bag — Sales — PK Cities** is running at Rs 500/day.
- Problem: clicks but **0 purchases**. Guest checkout already fixed ✅.
- Next diagnostic owner: whoever picks this up — verify destination URL, payment, shipping, and Purchase-event firing (read-only first).
- Second open item: prove/disprove duplicate pixel firing before disabling anything.

## When you finish a task
1. Update `current-state.md`.
2. Log fixes in `fixes-applied.md`, proposals in `fixes-pending-approval.md`.
3. Add a report in `reports.md`.
4. Report to Abdullah in plain English, starting "I am Claude." (or your name).

## Hard limits
- Rs 500/day, Rs 15,000/month cap.
- No secrets in the repo, ever.
- Approval required for ads, budget, pixel, plugins, website, checkout.
