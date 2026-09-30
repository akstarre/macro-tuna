---
status: narrowed by ADR-0011
---

# Nutrient values come from live AI Lookups, never cached

There is no food database. When an Entry is created the AI performs a Lookup —
searching for that food's nutrition information, including restaurant and brand
pages — and returns the Nutrient values. A Lookup is performed fresh every time
and its result is never reused for a later Entry, even an identical one.

This supersedes ADR-0002, which required a local corpus. Two things drove the
change. First, the corpus that fits a free-tier database (~20K curated generic
foods) cannot answer "the chicken bowl from the place down the street," and
real-world eating is mostly that; the product deliberately trades precision for
ease of logging. Second, caching was rejected explicitly: a reused Lookup serves
whatever was true weeks ago, and restaurant formulations and package sizes change.
A fresh Lookup is the only way the answer reflects the food as it is now.

## Consequences

Every Entry records whether its Lookup found a citation. Sourced Entries carry
the citation; Estimated Entries are the model's own recall and must be visibly
marked and editable — this distinction is the entire trust mechanism now that no
authoritative local source exists. Accepted costs: logging is seconds not
milliseconds, there is an API call per food, the app cannot log offline at all,
and the same food logged twice may return slightly different numbers. All Lookups
sit behind a single interface so a local corpus can be reinstated without
touching anything else.

## Narrowed

ADR-0011 restricts live Search to brand and restaurant foods and resolves generic
foods against a static USDA Food Table instead. The no-caching rule stands
unchanged for Search; the Food Table is not a cache but immutable reference data
fixed at build time.
