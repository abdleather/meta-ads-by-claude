# Pixel & Tracking Status

_Last updated: 2026-06-01_

## Pixel

| Item | Detail |
|------|--------|
| Pixel ID | 1249598143690399 |
| Status | ✅ Active |
| Plugin | Meta for WooCommerce (installed & activated) |
| Pixel file | `wp-content/novamira-sandbox/meta-pixel.php` |

## Conversions API (CAPI)

| Item | Detail |
|------|--------|
| CAPI Status | ✅ Active |
| Access Token | Stored in WP option `wc_facebook_capi_integration_access_token` (never exposed here) |
| CAPI file | `wp-content/novamira-sandbox/meta-capi.php` |
| Deduplication | ✅ Enabled via `_abd_capi_tracked` order meta |

## Events Tracked

| Event | Trigger | Status |
|-------|---------|--------|
| PageView | Every page load | ✅ Active |
| ViewContent | Product pages | ✅ Active |
| AddToCart | Item added to cart | ✅ Active |
| InitiateCheckout | Checkout page | ✅ Active |
| Purchase | Order confirmation | ✅ Active (deduped) |
| Search | Site search | ✅ Active |

## Enhanced Matching (CAPI)

Sends hashed user data for better attribution:
- Email, Phone, First name, Last name
- City, State, ZIP, Country
- External ID, fbp/fbc cookies
- Event ID (for deduplication)

## Domain Verification

| Item | Status |
|------|--------|
| Domain | abdleather.com |
| Verified | ✅ Yes |
| Verify file | `wp-content/novamira-sandbox/meta-domain-verify.php` |

## Known Issues

- None currently. Pixel and CAPI both firing correctly.
- Business verification still pending (unrelated to pixel — affects ad account trust level).
