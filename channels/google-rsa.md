# Google Responsive Search Ads

One RSA per system-type ad group. `systems_sold` in facts is the allowlist. If the user does not name a system, pick the first of `ac_replacement`, `furnace_replacement`, `heat_pump_installation` that appears in `systems_sold`. Never mix two systems in one RSA.

## Limits (official)

- Headlines: 3–15, each ≤30 characters
- Descriptions: 2–4, each ≤90 characters
- Paths: two × ≤15 characters
- Source: [About responsive search ads](https://support.google.com/google-ads/answer/7684791)

Count the visible fallback, not the `{KeyWord:}` wrapper. Spaces count.

## Pinning

- **Position 1:** this system’s keyword line only (one or two variants of the *same* system). Optional DKI: `{KeyWord:{{fallback}}}` where `fallback` is the same system headline ≤30 chars.
- **Position 2:** money lines, only from filled `financing` / `rebate` slots. If none are filled, leave Position 2 unpinned.
- **Position 3:** proof — license (always available), plus reviews/warranty only if filled.
- **Unpinned:** estimate/quote CTAs, city, brands (if filled), install SLA (if filled), remaining fillers.

Do not pin AC, furnace, and heat pump to Position 1 in the same ad.

## DKI

Optional, one headline, Position 1 only. Fallback must read correctly if insertion fails. Character count = fallback length.

## Build order

1. Write Position 1 from the system table below.
2. Add every optional headline whose facts slot is filled and ≤30 chars.
3. Fill remaining headline slots from **Allowed fillers** until 15 unique lines, or stop at fewer if 15 unique lines would repeat. Prefer 15.
4. Write 4 descriptions the same way (money → proof → CTA). Prefer 4; minimum 2.
5. Record unused optional keys in `omitted_slots`.

## System Position 1

Use `{{city}}` when the line stays ≤30 characters; otherwise drop the city.

| `systems_sold` value | Headline options (pick 1–2 for pin 1) |
|---|---|
| `ac_replacement` | `AC Replacement`, `AC Replacement {{city}}`, `Central AC Replacement` |
| `furnace_replacement` | `Furnace Replacement`, `Furnace Replacement {{city}}`, `New Furnace Installation` |
| `heat_pump_installation` | `Heat Pump Installation`, `Heat Pump Install {{city}}`, `Heat Pump Replacement` |

## Optional headlines (skip if slot empty)

Write the line, then count. If it exceeds 30, shorten without adding new facts.

| Slot | Pattern |
|---|---|
| `financing.apr_percent` + `term_months` | `{{apr_percent}}% APR for {{term_months}} Mos` |
| `financing.down_payment` is 0 | `$0 Down Replacement` |
| `financing.monthly_example` | `From ${{monthly_example}}/Month` — only with caveat on a description |
| `rebate.cap_usd` | `Utility Rebates To ${{cap_usd}}` |
| `proof.review_count` + `review_source` | `{{review_count}}+ {{review_source}} Reviews` |
| `warranty.parts_years` + `parts_source` | `{{parts_years}}-Yr Parts Warranty` |
| `warranty.labor_years` + `labor_source` | `{{labor_years}}-Yr Labor Warranty` |
| `install_sla` | `{{install_sla}} Installation` (e.g. `Next-Day Installation`) |
| `brands` (first brand) | `{{brand}} System Installers` |
| `offers_free_estimate` true | `Free In-Home Estimates` |
| `family_owned` true | `Local Family-Owned Installers` |
| `programs.google_guaranteed` true | `Google Guaranteed` |
| `programs.bbb_rating` | `BBB {{bbb_rating}} Rated` |

## Allowed fillers (no optional facts)

Use until you reach 15 unique headlines:

- `{{city}} HVAC Replacement`
- `Licensed {{license}}` (trim if >30: `License {{license}}`)
- `Local Replacement Experts`
- `In-Home System Estimate`
- `Get a Replacement Quote`
- `Residential System Install`
- `{{legal_name}}` (trim to 30)
- `Fully Licensed Installers`
- `Schedule Your Estimate`
- `Replacement Done Right`

## Descriptions (≤90)

Include the system name. Pin Description 1 only if a financing/rebate sentence is filled.

Patterns:

- Financing: `Upgrade to a new {{system}}. {{apr_percent}}% APR for {{term_months}} months{{down clause}}.`
- Age/problem without fake years: `Replace a worn central system with a new {{system}}. Licensed in {{city}} ({{license}}).`
- Proof: `{{review_count}} {{review_source}} reviews. Licensed {{license}}. Schedule an in-home estimate.`
- CTA: `Lower energy use with a new {{system}}. {{cta}}. Serving {{city}}.`

`cta` is `Get a free estimate` only if `offers_free_estimate`; else `Get a replacement quote`.

## Paths

`/Replacement` and `/{{City}}` or `/AC` `/Furnace` `/HeatPump` — each ≤15.

## Few-shot — good (example facts, not runtime)

Example facts used only here: `legal_name` Lakeside Heating & Cooling, `city` Madison, `license` WI-12345, `systems_sold` `[ac_replacement]`, `offers_free_estimate` true. All other optionals empty.

Pin 1: `AC Replacement Madison` (22), `Central AC Replacement` (22)

Unpinned fillers (no fake $89, no fake reviews): `Free In-Home Estimates`, `Licensed WI-12345`, `Local Replacement Experts`, `Get a Replacement Quote`, …

Description: `Replace a worn central system with a new AC. Licensed in Madison (WI-12345).` (76)

## Few-shot — wrong (do not emit)

Pin Position 1: `AC Replacement Service` + `Heat Pump Installation Expert` + `Central HVAC Replacement` in one RSA. Headlines: `500+ 5-Star Local Reviews`, `0% APR Financing For 60 Mos`, `Rates As Low As $89/Month` with no matching facts. This fails the one-system rule and the claims self-check.
