# meta-ads-by-claude

**Abd's Meta Ads Management Hub**

> ChatGPT = Strategy & Decisions | Claude = Execution & Reporting

---

## Purpose

This repo is the single source of truth for Abd's Meta Ads account.  
ChatGPT acts as the strategy/manager layer. Claude acts as the execution and reporting agent via Meta MCP.

No tokens, passwords, or access keys are ever stored here.

---

## Repo Structure

| File | Purpose |
|------|---------|
| `meta-ads-hub/brand-rules.md` | Abd's brand voice, visual rules, and ad content guidelines |
| `meta-ads-hub/account-status.md` | Current Meta Ads account health, limits, pixel status |
| `meta-ads-hub/campaigns.md` | Active and paused campaign summary |
| `meta-ads-hub/tasks.md` | Task queue — synced with GitHub Issues |
| `meta-ads-hub/reports.md` | Performance reports from Claude |
| `meta-ads-hub/decisions.md` | Decision log — what was approved and why |
| `meta-ads-hub/experiments.md` | A/B tests, ad experiments, results |
| `meta-ads-hub/pixel-tracking.md` | Pixel events, CAPI setup, tracking status |
| `meta-ads-hub/sop.md` | Standard operating procedures for this workflow |

---

## Workflow Rules

1. **Never save or expose** Meta tokens, passwords, access keys, or private credentials anywhere in this repo.
2. **GitHub Issues = task queue.** All tasks go through Issues.
3. Issues starting with **"FOR CLAUDE"** → Claude executes or investigates.
4. After every important task, Claude reports back in the **dedicated Claude chat in ChatGPT**.
5. Claude **must not** make budget, campaign, ad set, ad, pixel, or website changes without approval first.
6. Claude's process: **Diagnose → Recommend → Ask Approval → Execute → Report.**
7. All reports must be **simple and beginner-friendly** — no jargon.

---

## Accounts

- **Ad Account:** Abd's meta ad account no 1
- **Facebook Page:** Abd's
- **Instagram:** @abdleather
- **Website:** abdleather.com
- **Currency:** PKR | **Timezone:** Asia/Karachi (UTC+5)

---

## Quick Links

- [Account Status](meta-ads-hub/account-status.md)
- [Active Campaigns](meta-ads-hub/campaigns.md)
- [Task Queue](meta-ads-hub/tasks.md)
- [Latest Report](meta-ads-hub/reports.md)
- [SOPs](meta-ads-hub/sop.md)
