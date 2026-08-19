# SEO pages

Paid landing pages are `channels/landing.md`. This file is organic page types. Generate [`schemas/seo-page.schema.json`](../schemas/seo-page.schema.json).

NAP (`legal_name`, `phone`, street address, `city`) must match `facts.yaml` exactly — same spelling as GBP and LSA.

## Character budgets

| Field | Budget |
|---|---|
| Title | 50–60 characters |
| Meta description | 150–160 characters |
| H1 | One line; include `{{city}}` and the system when those slots exist |

Do not stuff titles with APR, rebates, or review counts. Money belongs in body copy only if facts support it.

## Schema

Emit `schema_type` only. Types:

- Service page: `HVACBusiness` + `Service`
- City page: `HVACBusiness` with `areaServed`
- Cost page: `FAQPage` + `Service`
- Repair vs replace: `FAQPage` + `Article`
- Financing: `FAQPage` (only if financing slots filled)
- FAQ hub: `FAQPage`

JSON-LD values come from `facts.yaml`. Do not use the Apex/Phoenix demo entity.

## Shared FAQ quality

Each answer is a complete paragraph a model can quote: who (`legal_name`), where (`city` / `service_area`), license, and the next step. No orphan one-liners.

---

## 1. System replacement (commercial)

Use for `/ac-replacement`, `/furnace-replacement`, `/heat-pump-installation` matching `systems_sold`.

- **Intent:** commercial — ready to hire a replacement contractor
- **Title:** `{{System}} Replacement in {{city}} | {{legal_name}}` (trim to 60)
- **H1:** `{{System}} Replacement in {{city}}`
- **H2 outline:**
  1. When replacement beats another repair
  2. What we install (`brands` if filled; else “residential {{system}} systems”)
  3. How the job goes (estimate → install → walkthrough)
  4. Coverage (`warranty` split only if filled)
  5. Service area (`service_area`)
  6. Get a quote (`phone`)
- **FAQs (3–5):** How long does replacement take? (`install_sla` only if filled, else “set at the estimate”); Do you pull permits in {{city}}?; What size system do I need? (answered as “we size at the visit,” not a fake tonnage)
- **Internal links:** cost page, city page, FAQ hub, financing if slots filled
- **schema_type:** `HVACBusiness+Service`

## 2. City / service-area (local)

One page per city in `service_area`, or a hub that lists them.

- **Intent:** local — “{{system}} replacement {{city}}”
- **Title:** `HVAC Replacement in {{city}} | {{legal_name}}`
- **H1:** `HVAC Replacement in {{city}}`
- **H2:** Neighborhoods/cities from `service_area` only; license; what systems you sell; quote CTA
- **Do not** invent neighborhoods
- **schema_type:** `HVACBusiness`

## 3. Cost / how much (commercial-investigation)

The GEO-useful page. Answer the question.

- **Intent:** cost research
- **Title:** `{{System}} Replacement Cost in {{city}}`
- **H1:** `What {{System}} Replacement Costs in {{city}}`
- **H2:**
  1. What drives price (size, efficiency, ductwork, electrical — no fake national average unless you add a sourced `facts` note; this template has none, so explain drivers without a dollar average)
  2. What is in our estimate
  3. Financing — only if `financing` filled
  4. Rebates — only if `rebate` filled
  5. How to get a number for *this* house
- **FAQ few-shot — good:**

  Q: How much does AC replacement cost in Madison?

  A: Lakeside Heating & Cooling prices AC replacement after an in-home visit in Madison. Cost depends on system size, efficiency, and ductwork — we do not publish a fake average. License WI-12345. Call {{phone}} for an estimate.

  (Swap in real `facts.yaml`. Do not insert $8,000–$15,000 from `research/benchmarks.md`.)

- **schema_type:** `FAQPage+Service`

## 4. Repair vs replace (mid-funnel)

- **Intent:** decide, not emergency dispatch
- **Title:** `Repair or Replace Your HVAC in {{city}}`
- **H1:** `Repair or Replace?`
- **H2:** Age and repair frequency as *decision questions*, not “if it is over 10 years you must replace” unless you have a facts-backed policy
- **CTA:** replacement estimate — not “24/7 emergency repair”
- **schema_type:** `FAQPage+Article`

## 5. Financing (only if `financing` filled)

If `apr_percent` is null, **do not generate this page**.

- **Title:** `HVAC Replacement Financing in {{city}}`
- **H1 / body:** exact APR, term, down payment; `monthly_example` only with `monthly_example_caveat` on the same section
- **schema_type:** `FAQPage`

## 6. FAQ hub

- **Intent:** extractable answers (People Also Ask / AI answers)
- **H1:** `HVAC Replacement FAQ in {{city}}`
- **Questions:** cost, timeline, brands (if filled), warranty split, service area, license, how to book
- **schema_type:** `FAQPage`
