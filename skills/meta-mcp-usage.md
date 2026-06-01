# Skill: Meta MCP Usage

_Last updated: 2026-06-01_

How to operate the Meta Ads account safely through the Meta Marketing API / Meta MCP.

---

## Golden rule
**Read freely, write only with approval.** Pulling stats, campaign lists, insights, and pixel diagnostics is always allowed. Anything that creates, edits, pauses, or spends requires Abdullah's explicit yes first.

## Safe read actions (no approval needed)
- List campaigns, ad sets, ads and their status
- Pull insights (spend, reach, clicks, CTR, purchases, CPP, ROAS)
- Check pixel/event activity and diagnostics
- Inspect ad creative, targeting, placements, destination URLs
- Check account spend vs. limit

## Write actions (approval REQUIRED every time)
- Create/edit/duplicate a campaign, ad set, or ad
- Publish a draft ad
- Change budget (esp. raising above Rs 500/day)
- Pause or resume anything
- Change targeting, placements, or destination URL
- Touch the pixel, plugins, website, or checkout

## Identifiers to use
- Ad Account ID: `1256975159584845`
- Page ID: `1100224009829899`
- Pixel ID: `1249598143690399`

## Spend guardrails
- Daily budget per campaign: Rs 500
- Monthly cap: Rs 15,000 (resets on the 1st)
- Before any spend-affecting change, check month-to-date spend so the cap isn't blown.

## Secrets
The CAPI access token lives in WP option `wc_facebook_capi_integration_access_token`. **Never** read it into this repo, a report, or a commit. If a task needs it, use it in place via the WordPress MCP and never echo it.

## Workflow each time
1. Read `meta-ads-hub/current-state.md` and `handoff-for-agents.md`.
2. Do read-only checks first.
3. Diagnose → write recommendation to `fixes-pending-approval.md`.
4. Wait for approval.
5. Execute, then log in `fixes-applied.md` and `reports.md`.
