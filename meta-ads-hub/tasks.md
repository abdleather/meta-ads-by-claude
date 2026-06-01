# Tasks

> All tasks are tracked via **GitHub Issues** on this repo.  
> Issues labeled **FOR CLAUDE** are queued for Claude to execute.  
> Issues labeled **FOR CHATGPT** are strategy/decision tasks for ChatGPT.  
> Issues labeled **FOR ABD** require the account owner's manual action.

---

## How to Use

1. Create a GitHub Issue for any new task.
2. Start the title with `FOR CLAUDE`, `FOR CHATGPT`, or `FOR ABD`.
3. Claude checks Issues at the start of each session and reports status.
4. Claude comments `ACTIVE` when starting, `DONE` when complete.

---

## Current Task Queue

_See GitHub Issues tab for live task list._

---

## Recurring Tasks (Claude runs these regularly)

| Task | Frequency | Notes |
|------|-----------|-------|
| Pull campaign performance report | Weekly | Post to reports.md |
| Check pixel firing status | Weekly | Confirm all events firing |
| Check account health | Weekly | Disabled? Payment issue? |
| Review ad spend vs budget | Weekly | Ensure within Rs 15,000/month |
| Check for disapproved ads | As needed | Flag to ChatGPT immediately |

---

## Open Tasks

| # | Issue Title | Assigned To | Status |
|---|-------------|-------------|--------|
| 1 | FOR CLAUDE — Fix active Shoulder Bag campaign destination and verify funnel | Claude | 🔲 Pending diagnosis |

### Task 1 Detail: FOR CLAUDE — Fix active Shoulder Bag campaign destination and verify funnel

**Campaign:** ABD Leather — Shoulder Bag — Sales — PK Cities  
**Problem:** Clicks coming in but 0 purchases recorded.  
**Claude must diagnose (before any changes):**
1. What URL does the ad currently link to? Is it correct and loading properly?
2. Is the product page (Handmade Leather Shoulder Bag) functional — can a user actually add to cart and complete checkout?
3. Is the Purchase pixel event firing on the order confirmation page for this product?
4. Is there any redirect issue, 404 error, or WooCommerce cart/checkout problem?

**Claude must NOT:**
- Change the destination URL without approval
- Edit any pixel code without approval
- Pause or modify the campaign without approval

**Claude reports findings to ChatGPT, then awaits approval before any fix.**

---

## Completed Tasks

| Date | Task | Result |
|------|------|--------|
| 2026-06-01 | Set up meta-ads-by-claude GitHub repo | ✅ Done — repo live at github.com/abdleather/meta-ads-by-claude |
| 2026-06-01 | Correct repo — add real active Shoulder Bag campaign | ✅ Done — all files updated |
