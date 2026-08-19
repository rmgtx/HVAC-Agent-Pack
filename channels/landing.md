# Paid landing page

Use for Google/Meta replacement traffic. Do not use this layout as the SEO service page (`channels/seo-pages.md`).

Send replacement clicks here, not to a generic homepage.

## Section order

Emit a JSON object with these keys. Skip a section’s *claim lines* when slots are empty; keep the section if it still has non-claim content.

### sticky_header

- `phone` from facts (required)
- License number
- Review badge only if `proof` is filled
- “24/7 dispatch” only if you add that boolean later — it is **not** in `facts.yaml`, so do not write it

### hero_headline

Prefer financing only when filled:

- With APR+term: `Replace Your {{system}} with {{apr_percent}}% APR for {{term_months}} Months`
- Else: `{{system}} Replacement in {{city}}`

### hero_subhead

Combine install SLA (if filled) + warranty (if filled) + license. If those are empty: `Licensed replacement in {{city}} ({{license}}). Get a quote.`

### form

- Label: `Check rebate & financing eligibility` only if rebate or financing is filled
- Else: `Get a replacement quote`
- Short fields (name, phone, ZIP, system). Do not promise instant approval.

### trust_strip

- Brands only from `brands`
- `Google Guaranteed` / BBB only when booleans/rating are set
- Always-ok: `Licensed {{license}}`

### calculator

Include a monthly slider **only** if `monthly_example` is filled; bound it with `monthly_example_caveat`. Otherwise omit the calculator.

### proof

Local photos and testimonials are production assets. Copy caption: city + system. Star counts only from `proof`.

## Voice

Same as the skill: direct, local, homeowner-plain. Hero is one offer, not three stacked slogans.
