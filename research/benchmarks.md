# Benchmarks — not for copy

Do not put numbers from this file into ads or pages. Copy comes from `facts.yaml` only.

Labels:

- **official** — platform help docs; use as format limits, not as claims
- **indicative** — industry writeups; strategy only
- **do-not-use-in-copy** — vendor-recycled or mutated stats

## Dual-engine (strategy)

Google Search intercepts homeowners already looking for replacement. Meta interrupts homeowners who have not searched. Repair and replacement do not share a campaign, ad group, RSA, or landing page. Ticket size and acceptable CPA differ by orders of magnitude.

**indicative:** Full residential replacements often invoice in a wide band around $8,000–$15,000 depending on system, efficiency, ductwork, and market (home-services trade writeups, 2026). Use `facts.yaml` job values if you have them; do not print this band in ads.

**indicative:** Competitive-metro replacement keywords are frequently quoted in the $40–$80+ CPC range; blended HVAC CPC (repair + install + branded) is much lower. Treat $80 as peak install auction, not “HVAC CPC.”

## Format limits (official)

Use these as generation budgets.

| Surface | Limit | Source |
|---|---|---|
| RSA headline | 30 characters; 3–15 headlines | [About responsive search ads](https://support.google.com/google-ads/answer/7684791) |
| RSA description | 90 characters; 2–4 descriptions | same |
| RSA path | 15 characters each | same |
| Sitelink text | 25 characters | [Sitelink assets](https://support.google.com/google-ads/answer/2375416) |
| Sitelink description line | 35 characters (two optional lines) | same + 2026 character-limit roundups citing Google Ads |
| Callout | 25 characters | [Callout assets](https://support.google.com/google-ads/answer/6079510) |
| Structured snippet value | 25 characters; 3–10 values | Google Ads asset specs |
| Meta primary text | ~125 characters before “See more” on mobile Feed (API max is thousands) | Meta truncation convention; write the first 125 as a complete sentence |
| Meta headline | ~27 visible on Facebook Feed; ~40 recommended on Instagram | Meta placement truncation, not API max (255) |
| Meta link description | ~27–30 characters; hidden on most Feed/Stories/Reels | same |
| LSA business name | 100 characters | [LSA profile feed](https://developers.google.com/local-services-ads/guides/profile-feed) |
| LSA description | Treat 750 characters as **indicative** unless Google Help states otherwise | contractor LSA guides, not a confirmed Help Center limit |

## GEO stats (do-not-use-in-copy)

A prior briefing stated generative engines were 9.2% of search, 87% of HVAC contractors had zero AI citation share, and AI citations drove a 38% organic CTR lift and a 39% lift in **paid search conversion rates**.

Those figures circulate on contractor-marketing blogs. The 39% figure appears in vendor copy as a lift in **paid-ad clicks**, not conversion rate. Do not quote 9.2%, 87%, 38%, or 39% in ads, landing pages, or SEO body copy.

GEO work that *does* belong in copy: consistent NAP from `facts.yaml`, complete answers on cost and service pages, FAQ chunks a model can extract. See `channels/seo-pages.md`.

## Negative example (do-not-use-in-copy)

Do not paste the briefing’s “Apex Climate Solutions” Phoenix JSON-LD (fake address, fake 4.9/482 reviews, $8,000 offer). Schema is generated from `facts.yaml` only.

## Intent map

Classify the query before writing. Replacement copy is only for replacement intent.

| Intent | Signals | Copy this pack writes |
|---|---|---|
| Replacement | replace, replacement, new AC, new furnace, heat pump installation, install central air | Yes — Google RSA, Meta, SEO replacement pages, replacement LP |
| Cost-research | how much, cost, price, estimate for new system | Yes — SEO cost page; Google only if the ad group is replacement-cost, not repair |
| Repair / diagnostic | fix, repair, not cooling, no heat, leak, error code, capacitor, Freon, troubleshooting | **No.** Different campaign. Do not use this pack’s RSAs or LP. |
| DIY | how to, YouTube, schematic, parts, Home Depot | **No.** Negative keyword. |
| Jobs | hiring, salary, apprenticeship, union | **No.** Negative keyword. |
| Wrong hardware | window unit, portable AC, space heater, RV AC, refrigerator | **No.** Negative keyword. |
| Bargain / used | cheap, used HVAC, wholesale, salvage | **No** for high-ticket replacement campaigns. |

**Checkable split:** if the query implies restoring the current machine, it does not get replacement copy. If it implies a new system, it does.
