# Lookups split by volatility: static table for generic foods, Search for brands

Generic foods resolve against the Food Table — a USDA-derived file (Foundation,
SR Legacy, FNDDS prepared dishes, roughly 15,000 foods trimmed to the five
Nutrients plus portion sizes) shipped as a static asset and held in memory. Brand
and restaurant foods resolve through a live Search. The AI decides which path a
parsed food takes.

This narrows ADR-0008, which sent everything through live Search. The reason is
that the two kinds of food have opposite volatility. An egg's protein content has
not changed in decades and USDA will not revise it, so searching the web for it
pays roughly a cent and several seconds for an answer that was already fixed.
Chipotle's recipe and a protein bar's package size genuinely do change, and for
those a fresh Search is the only correct answer. Splitting on volatility keeps the
freshness guarantee exactly where it means something and stops paying for it where
it doesn't.

The Food Table also costs nothing structurally: it is under a megabyte gzipped, it
lives in the application bundle rather than the database, so it does not consume
any of the 512 MB from ADR-0010, and USDA data is public domain (CC0), carrying
none of the attribution or share-alike obligations that OpenNutrition and Open
Food Facts would have imposed.

## Consequences

Generic Entries resolve in milliseconds at no marginal cost and are deterministic —
the same food logged twice yields identical numbers, which live Search alone could
not promise. Latency and cost now vary by food type, so the interface must tolerate
one Entry appearing instantly and the next taking seconds. Routing is a judgement
the AI makes and it will sometimes be wrong, sending a branded item to the table or
a generic one to Search; both failure modes are recoverable and neither produces a
wrong number, only a suboptimal one. The Food Table is regenerated only at build
time, so a USDA release requires a deploy. Both paths sit behind one interface, so
a food's origin is recorded on the Entry and the routing rule can change without
touching anything else.
