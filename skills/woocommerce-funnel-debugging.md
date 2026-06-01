# Skill: WooCommerce Funnel Debugging

_Last updated: 2026-06-01_

Why the Shoulder Bag campaign gets clicks but **0 purchases** — how to diagnose the WooCommerce funnel.

---

## Store stack
WordPress 6.9.4 + WooCommerce 10.7.0, Blocksy + Elementor theme, Hostinger, AirLift cache. Full control via Novamira WordPress MCP.

## The funnel to check (in order)
1. **Destination URL** — does the ad link land on the correct, live product page (Handmade Leather Shoulder Bag), not a 404 / homepage / broken slug?
2. **Product page loads** — mobile especially; price visible, Add to Cart works.
3. **Add to Cart → Cart** — item actually adds, cart isn't empty.
4. **Checkout reachable** — guest checkout works (see fix already applied below).
5. **Payment method** — a working method is available at checkout for PK customers.
6. **Order completes** — test/low-value order goes through, Purchase event fires once.

## Fix ALREADY applied ✅
- **Guest checkout enabled and verified.** Customers no longer forced to create an account before buying. (Confirmed working.)

## Likely remaining culprits for 0 purchases
- Destination URL mismatch or slow/broken mobile product page.
- Payment friction (limited or failing payment option for Pakistan).
- Shipping not configured for buyer's city → checkout blocked.
- Pixel Purchase not firing even when sales happen (under-reporting, not zero sales) — cross-check with WooCommerce → Orders.

## How to diagnose safely
- Read-only: inspect the ad's destination URL via Meta MCP; load the product page; walk the cart→checkout flow; check WooCommerce Orders for any real (untracked) orders; check shipping zones + payment settings.
- **Make NO changes** to checkout, payment, shipping, or the product page without approval. Diagnose → recommend in `fixes-pending-approval.md` → wait.

## Reporting
Explain findings in plain English: "People click the ad and reach the page, but [X] stops them from buying. I suggest [Y]. Want me to fix it?"

## Related
- `skills/pixel-capi-debugging.md`
- `meta-ads-hub/known-problems.md`
