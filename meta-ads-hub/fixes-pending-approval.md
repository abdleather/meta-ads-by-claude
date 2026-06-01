# Fixes Pending Approval

_Last updated: 2026-06-01_

Proposed changes waiting for Abdullah's explicit "yes" before anyone executes them. Nothing here is live.

---

## ⏳ 1. Investigate & fix the 0-purchases funnel
- **Proposal:** Do a read-only walk-through of the Shoulder Bag funnel (destination URL → product page → cart → checkout → payment) and cross-check WooCommerce Orders. Then propose ONE specific fix.
- **Why:** Campaign gets clicks but 0 purchases — money in, nothing out.
- **Needs approval for:** any actual change to URL, payment, shipping, product page, or checkout. (Diagnosis itself is read-only and can proceed.)
- **Status:** Awaiting approval to make changes.

## ⏳ 2. Resolve possible duplicate pixel firing
- **Proposal:** Prove duplication via Events Manager + Pixel Helper. If confirmed, disable ONE pixel source (plugin OR sandbox), clear AirLift cache, retest.
- **Why:** Duplicate events distort reporting and optimization.
- **RULE:** No pixel disabled until duplication is PROVEN.
- **Needs approval for:** disabling any pixel source.
- **Status:** Awaiting proof, then approval.

---

## Approval rules (reminder)
No ad, budget, pixel, plugin, website, or checkout change happens without Abdullah's explicit approval. Do NOT:
- Raise the Rs 500/day budget.
- Publish a duplicate or draft ad.
- Disable a pixel on suspicion.

_When approved + done, move to `fixes-applied.md`._
