---
name: hvac-replacement-copy
description: >-
  Writes HVAC system-replacement copy from verified facts only. Use when drafting
  Google responsive search ads, Google extensions, Local Services Ads descriptions,
  Meta ads (primary text, headlines, video scripts, carousels), SEO service/city/cost/FAQ
  pages, or paid landing pages for AC, furnace, or heat pump replacement.
---

# HVAC replacement copy

Direct, local, homeowner-plain. Name the system, the town, and the next step.
Write like a licensed contractor, not a slogan mill.

Paths are from the project root.

## Steps

1. **Load facts.** Read `facts.yaml`. If it is missing, tell the user to copy `facts.template.yaml` to `facts.yaml` and fill required fields. **Done when** every required key is non-empty: `legal_name`, `phone`, `city`, `license`, `service_area`, `systems_sold`, `address.street`, `address.locality`, `address.region`, `address.postal_code`.

2. **Refuse empty required slots.** If any required field is blank or `systems_sold` is `[]`, stop and list the missing keys. Do not invent values. **Done when** the run either stops with that list or all required keys are filled.

3. **Load claims.** Read `claims.md`. **Done when** the substitute table is in context.

4. **Pick one channel.** Map the user request to exactly one file:
   - Google RSA → `channels/google-rsa.md` → emit JSON valid against `schemas/rsa.schema.json`
   - Google extensions, LSA, or negatives → `channels/google-extensions.md` (plus `lists/negatives-phrase.txt` and `lists/negatives-exact.txt` when negatives are requested)
   - Meta → `channels/meta.md` → `schemas/meta.schema.json`
   - SEO page → `channels/seo-pages.md` → `schemas/seo-page.schema.json`
   - Paid landing page → `channels/landing.md` → JSON object with the section keys in that file
   Load only that channel file. Load `research/benchmarks.md` only to classify keyword intent or when the user asked for strategy — never to pull numbers into copy. **Done when** one channel file is loaded.

5. **Generate.** Substitute filled `facts.yaml` slots only. Omit assets that need empty optionals. Fill leftover RSA/Meta lines from that channel’s allowed fillers. One system type per RSA (`pins.position_1_system_only` must be `true`). Count characters; include `chars` / `first_sentence_chars` in the JSON. **Done when** output validates against the schema (landing: all specified section keys present).

6. **Claims self-check.** Every digit, warranty, badge, dollar amount, APR, rebate, review count, rating, and speed/SLA phrase maps to a `facts.yaml` key. Unmapped claim → fail the run (delete it or stop). List every unused optional key in `omitted_slots`. **Done when** self-check passes and `omitted_slots` is present.

## Channel split

Google captures homeowners already searching for replacement. Meta interrupts homeowners who have not searched yet. Repair queries do not get this copy.
