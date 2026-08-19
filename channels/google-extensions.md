# Google extensions and Local Services Ads

Load this file for sitelinks, callouts, structured snippets, LSA description, or negative keywords. RSA headlines live in `channels/google-rsa.md`.

NAP on every asset must match `facts.yaml` (`legal_name`, `phone`, `address`, `city`).

## Sitelinks

**official:** sitelink text ≤25 characters; two optional description lines ≤35 each. [Sitelink assets](https://support.google.com/google-ads/answer/2375416)

Each sitelink needs a real destination on the site. Skip any sitelink whose page does not exist.

| Text (≤25) | When | Description line 1 / 2 (≤35) |
|---|---|---|
| `AC Replacement` | `ac_replacement` in `systems_sold` | `New central AC systems` / `Installed in {{city}}` |
| `Furnace Replacement` | `furnace_replacement` | `New furnace installation` / `Licensed {{license}}` |
| `Heat Pump Install` | `heat_pump_installation` | `Heat pump replacements` / `Serving {{city}}` |
| `Replacement Cost` | cost page exists | `What a new system costs` / `Get an in-home quote` |
| `Financing` | `financing.apr_percent` filled | Use exact APR/term — no “as low as” without `monthly_example` |
| `Service Area` | `service_area` has cities | Name two cities from the list |
| `Free Estimates` | `offers_free_estimate` true | `In-home replacement quote` / `Call {{phone}}` |
| `Get a Quote` | always | `Talk to {{legal_name}}` / `{{city}} replacement` |

## Callouts

**official:** ≤25 characters. [Callout assets](https://support.google.com/google-ads/answer/6079510)

Always-ok: `Licensed {{license}}` (trim), `{{city}} Installers`, `Residential Replacement`.

Slot-gated: `{{apr_percent}}% APR Financing`, `$0 Down Available` (down_payment is 0), `{{parts_years}}-Yr Parts Warranty`, `{{review_source}} Reviewed`, `Google Guaranteed` (boolean true), `Free In-Home Estimates`.

## Structured snippets

Header: **Types** or **Services** (Google’s preset list). 3–10 values, each ≤25 characters, drawn only from `systems_sold` plus real pages:

- `AC Replacement`
- `Furnace Replacement`
- `Heat Pump Installation`
- `System Replacement`

Do not add Repair, Tune-Up, or Window Units to a replacement campaign snippet.

## Local Services Ads description

Keep NAP identical to GBP and the website. **indicative** length: up to ~750 characters; use the space, do not pad with unverified claims.

Structure:

1. `{{legal_name}} replaces {{systems}} in {{city}} and {{service_area}}.`
2. License sentence with `{{license}}`.
3. Optional proof/warranty/financing sentences only from filled slots.
4. Close: `Call {{phone}}` + estimate/quote line.

Do not write Google Guaranteed unless `programs.google_guaranteed` is true (LSA enrollment is separate; still require the facts boolean).

## Negatives

Replacement campaigns load [`lists/negatives-phrase.txt`](../lists/negatives-phrase.txt) and [`lists/negatives-exact.txt`](../lists/negatives-exact.txt). Add terms; do not remove the DIY, jobs, repair, window/portable, or bargain buckets without a human override.
