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

- Business verification still pending (unrelated to pixel — affects ad account trust level).

---

## Duplicate Event Firing — Full Audit (2026-06-01)

### Every Source Currently Firing Events

| Event | Custom `meta-pixel.php` (Browser JS, no event_id) | Meta WC Plugin (Browser JS, UUID event_id) | Meta WC Plugin built-in CAPI (Server, **same** UUID event_id) | Custom `meta-capi.php` (Server, **different** event_id format) |
|-------|----|----|----|-----|
| PageView | ✅ | ✅ | ✅ | ✅ |
| ViewContent | ❌ | ✅ | ✅ | ✅ |
| AddToCart | ❌ | ✅ | ✅ | ✅ |
| InitiateCheckout | ❌ | ✅ (JS on checkout page) | ✅ | ✅ |
| Purchase | ❌ | ✅ | ✅ | ✅ |
| Search | ❌ | ✅ | ✅ | ✅ |

### How Event IDs Are Generated

| Source | event_id format | Example |
|--------|----------------|---------|
| Meta WC Plugin (browser JS) | UUID v4 via `random_bytes()` | `a3f4b521-7c2e-4f1a-...` |
| Meta WC Plugin (server CAPI) | **Same UUID** as browser | `a3f4b521-7c2e-4f1a-...` ← matches |
| Custom `meta-capi.php` | `EventName_timestamp_rand` | `AddToCart_1780329370_4521` ← never matches |
| Custom `meta-pixel.php` | **No event_id** | — |

### Deduplication Status

| Pair | Deduplicated? | Why |
|------|--------------|-----|
| Meta WC Plugin browser ↔ Meta WC Plugin CAPI | ✅ YES | Same UUID event_id — Meta correctly deduplicates |
| Custom `meta-capi.php` ↔ Meta WC Plugin | ❌ NO | Different event_id formats — never match — counted twice |
| Custom `meta-pixel.php` ↔ anything | ❌ NO | No event_id set — Meta has no basis to deduplicate |

**Net result per event:**
- PageView: fires 4 times → ~2 distinct events (plugin dedup pair) + 1 extra (custom CAPI) + 1 extra (custom pixel, no event_id)
- ViewContent / AddToCart / Purchase / Search: fires 3 times → 1 clean count (plugin dedup pair) + 1 extra (custom CAPI)
- InitiateCheckout: fires 2 times → plugin browser JS + custom CAPI (different event_ids, no dedup)

### Meta WC Plugin Enhanced Matching (PII) Status

| Setting | Current Value |
|---------|--------------|
| Advanced Matching (AAM) enabled | ❌ NOT SET / disabled |
| CAPI integration enabled | ✅ YES |
| CAPI sends hashed PII | ❌ NOT SET / disabled |
| Plugin has PII hashing code | ✅ YES (in Event.php) — just not enabled |

The custom `meta-capi.php` IS sending full hashed PII (email, phone, name, address, fbp, fbc, external_id). The Meta WC Plugin is not, because AAM is disabled.

### Which Setup Is Safest Long-Term?

| Option | Deduplication | Enhanced Matching | Maintenance | Verdict |
|--------|--------------|------------------|-------------|---------|
| Meta WC Plugin only (current state, no changes) | ✅ Browser+CAPI pair deduplicated | ❌ AAM disabled | ✅ Official, auto-updated | Good but missing PII |
| Custom CAPI only (disable plugin tracking) | ❌ No browser partner to dedup against | ✅ Full PII | ⚠️ Custom code, manual upkeep | Weaker — loses official dedup |
| Both with correct deduplication | ✅ Best | ✅ Best | ✅ Best | **Recommended — but needs config** |
| Current state (both, broken dedup) | ❌ Broken | ✅ Custom CAPI has it | — | ❌ Not acceptable long-term |

**Recommendation: Meta WC Plugin as primary + enable its AAM + enable CAPI PII + remove custom sandbox files.**
- Plugin already correctly pairs browser events with server CAPI using matching event_ids.
- Enabling AAM adds hashed email/phone/name to the plugin's own CAPI calls.
- Removing `meta-capi.php` and `meta-pixel.php` eliminates the extra undeduplicatable stream.
- Result: clean, officially maintained, properly deduplicated, enhanced matching enabled.
- Only risk: InitiateCheckout CAPI backup moves from server-PHP-hook to plugin's JS approach — acceptable.

### Exact Changes Needing Approval (no action taken yet)

1. Enable plugin Advanced Matching: `update_option('wc_facebook_use_pii', 'yes')`
2. Enable plugin CAPI PII: `update_option('wc_facebook_capi_integration_send_pii', 'yes')`
3. Disable `meta-pixel.php` (redundant — plugin already loads pixel)
4. Disable `meta-capi.php` (creates undeduplicatable events — plugin's CAPI replaces it)

Steps 1+2 can be done before steps 3+4 — enabling AAM first ensures no data gap.
