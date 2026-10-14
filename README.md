# HVAC Agent Pack

Agent-ready copy system for **HVAC system replacement** (not repair): Google Ads, Meta ads, SEO pages, and paid landing pages.

Copy is generated only from verified facts in `facts.yaml`. Empty optional fields are omitted — the agent does not invent `$89/mo`, review counts, or warranties.

## Why this exists

Ask a general-purpose model for HVAC ads and it invents the details that sell:
financing, star ratings, install speed, warranties. Those claims can be false, and
false advertising is a liability for the contractor. This pack makes the agent write
only from `facts.yaml`. Every claim maps to a filled field, and an empty field is
skipped or replaced with a safe substitute from [`claims.md`](claims.md), never guessed.

### Example (fictional business)

`facts.yaml`: Example Heating & Air · Madison, WI · license HVAC-0000 · systems: AC
replacement · free estimates: yes · financing, reviews, rebates, warranty: empty

| Unguarded model output | With this pack | Why |
|---|---|---|
| `$89/Month Financing` | — | `financing` is empty |
| `500+ 5-Star Reviews` | `Lic. HVAC-0000 · Madison` | No `proof.review_count`; license number and city substitute |
| `Next-Day Install` | `Schedule Your Estimate` | No `install_sla` |
| `Save $1,200 Today` | `Ask About Utility Programs` | No `rebate.cap_usd` |
| `AC Replacement Madison` | `AC Replacement Madison` | `systems_sold` + `city` |
| — | `Free Replacement Estimate` | `offers_free_estimate: true` |

The unguarded strings aren't made up for this example. They're the failures
`claims.md` lists from a real briefing. Each output records the optional fields it
skipped in `omitted_slots`, so a reviewer can see what was left out and why.

## Setup

1. Copy [`facts.template.yaml`](facts.template.yaml) over [`facts.yaml`](facts.yaml) (or edit `facts.yaml` in place).
2. Fill every required field: business name, phone, city, license, service area, systems sold, address.
3. Fill optional slots only when they are true (APR, rebates, reviews, warranties, Google Guaranteed, etc.).
4. In Cursor, open this repo and ask the agent to draft Google RSAs, Meta ads, an SEO cost page, or a replacement landing page.

The skill lives at [`.cursor/skills/hvac-replacement-copy/SKILL.md`](.cursor/skills/hvac-replacement-copy/SKILL.md).

## Layout

| Path | Role |
|---|---|
| `facts.yaml` | Runtime facts (fill this) |
| `claims.md` | What may be written; substitutes when a slot is empty |
| `channels/` | Google RSA, extensions/LSA, Meta, SEO pages, paid LP |
| `lists/` | Negative keywords for replacement campaigns |
| `schemas/` | JSON the agent must emit |
| `research/benchmarks.md` | Strategy and limits — **not** for ad/page copy |

## Channel split

Google captures homeowners already searching for replacement. Meta interrupts those who have not searched. Repair queries do not use this pack.
