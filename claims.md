# Claims

Write only what `facts.yaml` can support. An empty, null, or false slot is a skip, not a prompt to guess.

## Filled slots only

Use a required field (name, phone, city, license, systems, service area, address) in any channel. Use an optional field only when it has a real value. `omitted_slots` lists every optional key you did not use.

## Substitutes

When the tempting claim has no facts key, write the substitute instead.

| If this is empty | Write this |
|---|---|
| `financing.*` | Comfort, efficiency, or a free/paid estimate — not monthly price, APR, or $0 down |
| `rebate.cap_usd` | Efficiency or “ask about local utility programs” — not a dollar amount |
| `proof.review_count` / `rating` | License number and city — not star counts |
| `warranty.parts_years` | “Ask about manufacturer coverage” — not a year count |
| `warranty.labor_years` | “Ask about our labor coverage” — do not merge parts and labor into one line |
| `install_sla` | “Schedule a replacement estimate” — not next-day, same-day, or 24-hour |
| `brands` | “Replacement systems we install” — not Carrier, Trane, Lennox, or “top brands” |
| `programs.google_guaranteed` is false | License + insurance language — not Google Guaranteed |
| `programs.bbb_rating` is empty | License + reviews only if `proof` is filled |
| `offers_free_estimate` is false | “Get a replacement quote” — not “free estimate” |
| `family_owned` is false | Local + licensed — not family-owned |
| `years_in_business` is null | City + license — not a year count |

## Warranty split

Parts and labor are separate sentences, each tied to `parts_source` / `labor_source`. Write “10-year parts and labor” only when both year fields equal 10 and both sources are filled.

## Financing

Use the exact `apr_percent`, `term_months`, and `down_payment` from facts. Write “as low as ${{monthly_example}}/mo” only when `monthly_example` and `monthly_example_caveat` are both filled. Put the caveat on the landing page or description, not as a silent footnote.

## Badges

`google_guaranteed` and `bbb_rating` are binary. False or empty means the phrase does not appear.

## Digits

Every numeral in the output (prices, APR, months, years, review counts, ratings, rebate caps, install timing) maps to a facts key. If you cannot point to the key, delete the numeral.

## Wrong (do not treat as a template)

The source briefing mixed three systems in one RSA Position 1 and used unverified “500+ 5-star reviews”, “$89/month”, “0% APR for 60 months”, “Save $1,200”, “next-day install”, and a fake Phoenix schema entity. Those strings are failures. Replace them with slots or substitutes from the table above.
