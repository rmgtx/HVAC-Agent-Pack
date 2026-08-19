# Meta ads

Google captures searchers. Meta interrupts. Problem-first creative; financing and rebates only from filled slots. Do not put ages, homeowner targeting, or ZIP radii in ad text — those are targeting settings.

## Limits

Write to **visible** length, not API max.

| Field | Budget | Notes |
|---|---|---|
| Primary text first sentence | ≤125 characters | Mobile Feed “See more” truncation |
| Headline | ≤40; prefer ≤27 for Facebook Feed | |
| Link description | ≤27 | Often hidden on Feed/Reels |
| Overlay | 5–7 words | No paragraph |
| CTA button | From the allowlist below | |

## Combinator

Pick **one hook + one offer + one proof + one CTA**. Do not invent a fifth offer. If the chosen offer or proof needs an empty slot, pick another row that facts support.

### Hooks (visual + first line)

1. Aging outdoor unit / noisy condenser
2. High summer or winter utility bill
3. Uneven rooms / thermostat at an extreme set point
4. Repeat repair visits on the same system
5. Homeowner comfort (sleep, upstairs heat)
6. Install-day timelapse (crew, new unit set)
7. Technician at the old unit, talking to camera
8. Before/after of the pad and line set

### Offers (copy)

| ID | Requires | Line pattern |
|---|---|---|
| `quote` | (none) | Get a replacement quote in {{city}} |
| `free_estimate` | `offers_free_estimate` | Free in-home replacement estimate |
| `financing` | `apr_percent` + `term_months` | {{apr_percent}}% APR for {{term_months}} months |
| `monthly` | `monthly_example` + `monthly_example_caveat` | From ${{monthly_example}}/mo (caveat in primary or LP, not overlay) |
| `rebate` | `rebate.cap_usd` + `rebate.source` | Ask about {{source}} rebates up to ${{cap_usd}} |
| `warranty_parts` | `parts_years` | {{parts_years}}-year parts coverage ({{parts_source}}) |

If financing/monthly/rebate/warranty are all empty, use `quote` or `free_estimate` only. Do not add a new offer.

### Proofs

| ID | Requires | Line |
|---|---|---|
| `license` | `license` | Licensed {{license}} in {{city}} |
| `reviews` | `review_count` + `review_source` | {{review_count}} {{review_source}} reviews |
| `brands` | `brands` nonempty | We install {{brand list}} |
| `local` | `city` | Serving {{city}} and nearby towns in `service_area` |

Always legal to pick `license` or `local`.

### CTA buttons (allowlist)

`Get Quote` · `Learn More` · `Book Now` · `Apply Now` (Apply Now only if `financing` is filled)

Primary-text CTA verb: “Get a quote” or “Book an estimate” — not “Apply now” unless financing is filled.

## Primary text

3–5 variants per run. Each variant’s **first sentence is ≤125 characters** and is a complete thought (hook + offer or hook + proof). Further sentences may follow for users who tap See more; they still obey claims.md.

### Few-shot — good (example facts only)

Facts: `city` Madison, `license` WI-12345, `offers_free_estimate` true. No financing, no reviews.

Variant A (count the first sentence):  
`If your AC is loud, tired, and expensive to run, replace it — don’t keep repairing it.` (86)  
`Lakeside Heating & Cooling is licensed in Madison (WI-12345). Get a free in-home replacement estimate.`

## Headlines (≤40 / prefer ≤27)

Build from combinator pieces, e.g. `Replace Your Old AC` (19), `{{city}} AC Replacement`, `{{apr_percent}}% APR {{term_months}} Months` only if filled.

## Link description (≤27)

`Licensed {{city}} Install` or `Get a Replacement Quote`. No dollar amounts unless the slot fits in 27 characters **and** is filled.

## Carousel (4–5 cards)

| Card | Overlay 5–7 words | Supporting line |
|---|---|---|
| 1 Problem | `Tired of repair bills?` | Hook from the list |
| 2 Install day | `Installed in your home` | Crew / new system — no SLA unless `install_sla` filled |
| 3 Money | Skip this card if no financing/rebate/monthly | Else the filled offer line |
| 4 Proof | `Licensed local replacement` | license or reviews |
| 5 CTA | `Get your replacement quote` | Phone from facts only if you also show it on the LP |

## Static overlay

5–7 words. Examples that need no optionals: `Replace the system, not parts`, `New AC for {{city}} homes`. Money overlays only from filled slots.

## 30-second script (one few-shot, slotted)

Salvage beat sheet. Substitute facts; skip a beat’s money line if those slots are empty and use quote/license instead.

| Time | Phase | Visual | Voiceover |
|---|---|---|---|
| 0:00–0:03 | Hook | Close-up of a worn outdoor unit | `If your {{system}} is old and costly to keep alive, stop pouring money into repairs.` |
| 0:03–0:08 | Pain | Bill or uncomfortable room | `Old equipment works harder and still leaves the house uneven.` |
| 0:08–0:18 | Install | Timelapse of the crew setting a new unit | `{{legal_name}} installs replacement systems in {{city}}. License {{license}}.` |
| 0:18–0:24 | Offer | Graphic only if slots exist | Financing/monthly/rebate from facts — else `Get a replacement quote with no made-up monthly price.` |
| 0:24–0:30 | CTA | Logo + `Get Quote` | `Tap Get Quote. {{phone}}.` |

Do not use the briefing’s “$0 Down, 0% APR, $89/Month, 10 years old, 10-year warranty” unless those keys are filled.
