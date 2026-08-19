# HVAC Agent Pack

Agent-ready copy system for **HVAC system replacement** (not repair): Google Ads, Meta ads, SEO pages, and paid landing pages.

Copy is generated only from verified facts in `facts.yaml`. Empty optional fields are omitted — the agent does not invent `$89/mo`, review counts, or warranties.

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
