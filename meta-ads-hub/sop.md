# Standard Operating Procedures (SOPs)

_How Claude and ChatGPT work together on Abd's Meta Ads._

---

## Core Principle

> **Diagnose → Recommend → Get Approval → Execute → Report**

Claude never makes a move without approval first. ChatGPT gives the green light. Abd owns the final say on any money spent.

---

## SOP 1: Starting a New Session

1. Claude checks GitHub Issues for any open `FOR CLAUDE` tasks.
2. Claude pulls current account status via Meta MCP.
3. Claude reports current status in the ChatGPT Claude chat: "I am Claude. [status summary]"
4. Claude waits for instructions from ChatGPT.

---

## SOP 2: Launching a New Campaign

1. ChatGPT creates a GitHub Issue: `FOR CLAUDE — Launch campaign: [name]`
2. Claude reviews the brief in the Issue.
3. Claude diagnoses: audience, budget, creative needed.
4. Claude recommends a campaign setup (objective, targeting, budget, ad format).
5. Claude posts recommendation as a comment on the Issue.
6. ChatGPT approves (comments "APPROVED") or requests changes.
7. Claude executes via Meta MCP.
8. Claude reports: spend, reach, performance after 24–48 hours.

---

## SOP 3: Reporting Performance

1. Claude pulls data via Meta MCP (weekly or after each campaign).
2. Claude writes a simple report: what ran, what it cost, what happened.
3. Claude posts to `reports.md` and comments on any related GitHub Issue.
4. Claude sends report summary to ChatGPT Claude chat: "I am Claude. [report]"
5. ChatGPT decides next action.

---

## SOP 4: Handling a Problem

1. Claude detects an issue (disapproved ad, pixel not firing, overspend, etc.).
2. Claude immediately flags it: GitHub Issue titled `FOR CHATGPT — Problem: [description]`
3. Claude diagnoses the root cause.
4. Claude recommends a fix.
5. Claude does NOT fix anything until ChatGPT approves.
6. After fix: Claude confirms resolved and closes the Issue.

---

## SOP 5: Updating This Repo

- `account-status.md` — update weekly or after any account change.
- `campaigns.md` — update after every campaign launch or pause.
- `reports.md` — update after every performance pull.
- `decisions.md` — update after every major decision.
- `experiments.md` — update after every test result.

---

## What Claude CANNOT Do Without Approval

- Spend money / change budgets
- Launch, pause, or delete campaigns
- Change pixel code on the website
- Change ad creatives
- Change audience targeting
- Make any website changes
