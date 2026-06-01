# Skill: Pixel + CAPI Debugging

_Last updated: 2026-06-01_

How to diagnose Meta Pixel and Conversions API (CAPI) tracking for ABD Leather.

---

## Setup facts
| Item | Value |
|------|-------|
| Pixel ID | 1249598143690399 |
| Pixel file | `wp-content/novamira-sandbox/meta-pixel.php` |
| CAPI file | `wp-content/novamira-sandbox/meta-capi.php` |
| Domain verify file | `wp-content/novamira-sandbox/meta-domain-verify.php` |
| CAPI token | WP option `wc_facebook_capi_integration_access_token` (NEVER copy out) |
| Domain | abdleather.com — verified in Meta |
| Plugin | Meta for WooCommerce (installed + active) |
| Cache | AirLift — clear after any pixel/tracking change |

## Events tracked (Pixel + CAPI)
| Event | Trigger |
|-------|---------|
| PageView | Every page |
| ViewContent | Product pages |
| AddToCart | Item added to cart |
| InitiateCheckout | Checkout page |
| Purchase | Order confirmation (deduped via `_abd_capi_tracked` meta) |
| Search | Site search |

Dedup: browser pixel and CAPI send the same `event_id`. Purchase also guarded by the `_abd_capi_tracked` order meta so it can't double-count.

## CURRENT OPEN ISSUE — duplicate pixel/event firing
- **Symptom:** suspicion that pixel/events may be firing twice.
- **RULE: Get PROOF before disabling anything.** Do NOT remove the plugin pixel or the sandbox pixel until duplication is confirmed with evidence.
- **How to prove:**
  1. Use Meta Events Manager → Test Events / live event log, and the Meta Pixel Helper, to see if a single action produces two events with different `event_id`s.
  2. Check whether BOTH the "Meta for WooCommerce" plugin AND the custom sandbox `meta-pixel.php` are injecting the base pixel (that's the usual cause of doubles).
  3. Confirm CAPI + pixel are sharing `event_id` (correct = dedup, not a true duplicate).
- **If proven:** recommend ONE fix (disable the plugin's pixel OR the sandbox pixel, not both) in `fixes-pending-approval.md`, then wait for approval. Clear AirLift cache after the change.

## Debug checklist
1. Pixel Helper shows how many pixels fire per page.
2. Events Manager → diagnostics for duplicate/redundant warnings.
3. Confirm matching `event_id` between pixel and CAPI = healthy dedup.
4. Verify Purchase fires once per order (check `_abd_capi_tracked`).
5. After any change: clear AirLift cache, retest.

## Related
- `skills/woocommerce-funnel-debugging.md` — for the 0-purchases funnel issue
- `meta-ads-hub/known-problems.md`
