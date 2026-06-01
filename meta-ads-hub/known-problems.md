# Known Problems

_Last updated: 2026-06-01_

Open issues with the Meta Ads + store funnel. Update as they're proven or solved.

---

## 1. Clicks but 0 purchases 🔴 (highest priority)
- **Where:** ABD Leather — Shoulder Bag — Sales — PK Cities campaign.
- **Symptom:** Ad gets clicks, **zero purchases** recorded.
- **Possible causes (unconfirmed):** wrong/broken destination URL, slow or broken mobile product page, payment friction for Pakistan, shipping not set for buyer's city, or Purchase pixel not firing (under-reporting real sales).
- **Already ruled-in fix:** guest checkout was a blocker → now enabled ✅.
- **Next step:** read-only funnel walk-through (URL → product page → cart → checkout → payment), cross-check WooCommerce Orders for untracked sales. Diagnose only; propose fix for approval.
- See `skills/woocommerce-funnel-debugging.md`.

## 2. Possible duplicate pixel / event firing 🟠
- **Symptom:** suspicion that pixel/events fire twice.
- **RULE:** **PROOF REQUIRED before disabling anything.** Do not remove the plugin pixel or sandbox pixel on suspicion alone.
- **Likely cause:** both "Meta for WooCommerce" plugin and custom `meta-pixel.php` injecting the base pixel.
- **Note:** pixel + CAPI sharing the same `event_id` is correct dedup, NOT a duplicate.
- **Next step:** confirm via Events Manager Test Events + Pixel Helper, then propose a single fix for approval.
- See `skills/pixel-capi-debugging.md`.

## 3. Business not verified ⚪
- Meta business verification not yet done — needs document upload by Abdullah. Not blocking current campaign but limits some features.

---

_When a problem is proven and fixed, move the resolution to `fixes-applied.md` and update `current-state.md`._
