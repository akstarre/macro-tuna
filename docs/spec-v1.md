## Problem Statement

Tracking what you eat is a chore, and the chore is the reason people stop. Every
mainstream calorie tracker asks the same thing of you: open the app, search a
database, scroll a list of near-identical results, pick a serving size from a
dropdown, repeat for every component of the meal. A sandwich is four searches. The
effort is front-loaded onto the moment you are least willing to spend it — mid-meal,
on your phone, hungry. So people log carefully for a week, sporadically for another,
and then not at all, and the app that was supposed to show them a trend has nothing
to show.

The information a tracker needs, meanwhile, is something the user can already say
in one sentence. "Two eggs and toast." "A chicken bowl from the place on the
corner." The gap is not knowledge, it is data entry.

Macro Tuna's user wants to know whether they are eating in a way that serves their
goal — gaining muscle, losing weight, maintaining — and wants to find out without
performing database administration three times a day.

## Solution

You tell Macro Tuna what you ate, in the words you would use with a person, and it
does the rest. An AI reads the Message, works out what the food was, looks up the
Nutrient values, and records an Entry. If what you said was too vague to log, it
asks — conversationally, one thing at a time, the way a person would: what was in
it, where was it from, how much was there.

The main screen is not a list. Five Bubbles — protein, carbohydrate, fat, fiber,
sodium — float above a buff, friendly Tuna that carries the day's Calories. Each
Bubble's background fills as you approach that Nutrient's Target. A glance tells
you where you are. Three Windows — today, the last 7 Days, the last 28 Days —
switch the same five Bubbles between the immediate and the habitual, so a single
bad day reads as a single bad day and a bad fortnight reads as a bad fortnight.

Targets are not guesses. You give Macro Tuna your body and your Goal once, and it
derives them with the current formulas, then leaves them alone until you tell it
something has changed.

## User Stories

### Accounts and onboarding

1. As a new user, I want to sign in with my existing Google or Apple account, so that I can start using the app without inventing another password.
2. As a returning user, I want to still be signed in when I come back, so that logging food is never gated behind a login screen.
3. As a signed-in user, I want to sign out, so that I can leave the app on a shared device.
4. As a new user, I want to enter my weight, height, age and sex, so that my Targets are calculated for my body rather than an average one.
5. As a new user, I want to optionally enter my body fat percentage, so that my Targets use the more accurate formula when I actually know the number.
6. As a new user, I want to pick my activity level from plain descriptions of how much I move, so that I am not guessing at a multiplier.
7. As a new user, I want to choose my Goal from weight loss, weight gain, muscle gain or maintenance, so that my Targets reflect what I am trying to do.
8. As a new user, I want to see my calculated Targets and which formula produced them, so that I can sanity-check the numbers before trusting them.
9. As a user who already knows my numbers, I want to override any Target by hand, so that the app does not argue with a plan I already have.
10. As a new user, I want to be logging food within a minute of signing in, so that onboarding does not become its own chore.

### Logging by conversation

11. As a user, I want to type what I ate in ordinary language, so that logging costs one sentence instead of four searches.
12. As a user, I want one Message to produce several Entries when I describe a whole meal, so that I do not have to log components one at a time.
13. As a user, I want the AI to tell me what it recorded, so that I can catch a misreading immediately.
14. As a user, I want to be asked what the food actually was when I have been too vague, so that the Entry is not silently invented.
15. As a user, I want to be asked where a food came from when the brand or restaurant matters, so that the numbers reflect the thing I really ate.
16. As a user, I want to be asked how much there was when I have not said, so that the quantity is mine rather than an assumed default.
17. As a user, I want to be asked these things one at a time in casual conversation, so that logging does not turn into a form.
18. As a user, I want to keep logging other food while an earlier Entry is still Pending, so that one unanswered question does not block the whole day.
19. As a user, I want to see how many Entries are still Pending, so that I notice when my totals are missing something.
20. As a user, I want Pending Entries excluded from my Bubbles and Tuna, so that a total is either right or visibly incomplete, never quietly wrong.
21. As a user, I want to answer a clarification about an older Pending Entry, so that I can resolve them in any order.
22. As a user, I want to be told when a Message could not be understood as food at all, so that I am not left wondering whether it registered.

### Nutrient values and trust

23. As a user, I want everyday foods resolved instantly, so that logging eggs does not involve waiting.
24. As a user, I want the same everyday food to produce the same numbers every time, so that my history is consistent.
25. As a user, I want branded and restaurant foods looked up fresh, so that a reformulated menu item is not recorded from stale data.
26. As a user, I want to see the source behind an Entry's numbers, so that I can judge how much to trust them.
27. As a user, I want Entries whose values came from the model's own recall clearly marked as Estimated, so that I know which numbers are soft.
28. As a user, I want to correct any Entry's numbers by hand, so that a bad Lookup is a nuisance rather than a corrupted day.
29. As a user, I want to be told when a Lookup failed rather than shown a plausible fabrication, so that the app never lies to me.

### Reviewing and correcting

30. As a user, I want to see today's Entries in a list, so that I can check what the app believes I ate.
31. As a user, I want each Entry to describe itself well enough to recognise, so that I can review without remembering what I typed.
32. As a user, I want to edit an Entry's quantity directly, so that fixing "one slice" to "two" takes one interaction.
33. As a user, I want to remove an Entry entirely, so that a mistake or a food I did not finish does not count.
34. As a user, I want my Bubbles and Tuna to update the moment I edit or remove an Entry, so that the display and the record never disagree.
35. As a user, I want to ask the AI to change an Entry in conversation, so that I can correct things the same way I created them.

### Bubbles, Tuna, and Windows

36. As a user, I want five Bubbles for protein, carbohydrate, fat, fiber and sodium, so that I see the Nutrients I care about at once.
37. As a user, I want each Bubble to fill in proportion to progress toward its Target, so that I can read my state without reading numbers.
38. As a user, I want the exact figure and Target on a Bubble when I want detail, so that the glanceable view does not cost me precision.
39. As a user, I want Calories shown on the Tuna rather than as a sixth Bubble, so that the derived number is visibly a different kind of thing.
40. As a user, I want to switch to the last 7 Days, so that I can see whether today is typical.
41. As a user, I want to switch to the last 28 Days, so that I can see a habit rather than an incident.
42. As a user, I want a Bubble to mean the same thing in every Window, so that switching tabs does not change how I read it.
43. As a user, I want the longer Windows to show my average day against my daily Target, so that Monday morning does not look like failure.
44. As a user, I want Days before I joined excluded from my averages, so that my first week is not dragged down by days that never existed.
45. As a user, I want the Tuna to look like it is doing well when I am on Target, so that the app feels like it is on my side.

### Days and time

46. As a user, I want my Day to end at midnight by default, so that the app behaves the way I expect without configuration.
47. As a user, I want to move my Day Start later, so that a 1am snack counts toward the day it belonged to.
48. As a user, I want my Day boundary to follow my own timezone, so that travelling does not scramble my log.
49. As a user, I want yesterday's totals folded into my history when a new Day starts, so that the record survives the rollover.
50. As a user, I want Days I did not open the app handled correctly, so that a week away does not show as a week of stale intake.

### Profile and Targets over time

51. As a user, I want to update my weight when it changes, so that my Targets keep matching my body.
52. As a user, I want to be reminded periodically to update my stats, so that my Targets do not quietly go stale.
53. As a user, I want to turn that reminder off, so that the app stops nagging me when I do not want it.
54. As a user, I want my Targets to change only when I change something, so that a Bubble I was hitting never silently starts reading as missed.
55. As a user, I want to see how my Targets changed after an update, so that I understand why the numbers moved.
56. As a user, I want past Days measured against the Targets that applied then, so that my history is not rewritten by a change made today.
57. As a user, I want to change my Goal without starting over, so that switching from a cut to a bulk is one decision.

## Implementation Decisions

### Shape

A single Next.js application deployed to Vercel, UI and API routes in one project
on one origin (ADR-0013). MongoDB Atlas free tier in the same region as the
functions (ADR-0010). No separate backend service, no API subdomain — the
single-origin property is what makes first-party session cookies work.

### Authentication

Better Auth with its MongoDB adapter, Google and Apple social providers, sessions
as first-party HttpOnly cookies on the app's own origin (ADR-0010). Collections are
hand-defined because Better Auth's schema CLI does not support MongoDB, and its
default naming is known to collide with an existing `user` collection. Apple's
client secret expires roughly every six months and must be regenerated, which will
break sign-in silently if missed.

### Storage model

One document per user, holding the Profile, settings, the Target Set history, and a
fixed array of 28 Day Slots (ADR-0009). Today's Entries and Messages are separate
and short-lived: Entries exist only for the current Day and are folded into their
Day Slot at rollover, then discarded. A user's stored size is therefore constant
regardless of how long they use the app.

Day Slots are addressed by `dayIndex % 28`. On the first request of a new Day the
rollover writes yesterday's sums into its Slot, zeroes the Slot about to be reused,
and zeroes every Slot for Days skipped since the last visit. This operation must be
idempotent — two requests arriving together must not double-write — and there is no
way to reconstruct a Day from Entries afterward, so it must be correct the first
time.

Calories are never stored. They are computed from Macro grams at read time (4/4/9,
ADR-0001).

### Nutrient resolution

One `NutrientSource` interface with two implementations behind it (ADR-0011,
ADR-0012):

- **Food Table**: a prebuilt USDA-derived file (Foundation, SR Legacy, FNDDS
  prepared dishes) trimmed to the five Nutrients plus portion sizes, roughly 15,000
  foods, shipped in the deployment bundle and read into memory at cold start. Public
  domain, immutable, regenerated only at build time. Resolves generic foods.
- **Search**: a live web lookup through the Anthropic API, used only for brand and
  restaurant foods. Never cached, fresh every time. Costs about a cent per call plus
  retrieved page tokens, on the operator's key.

The AI routes each parsed food to one path or the other. Misrouting produces a
suboptimal answer, never a wrong one. Every Entry records which path resolved it
and any citation, which drives the Sourced / Estimated distinction in the UI and
satisfies Anthropic's requirement to display citations for search results.

### The AI's job

Parsing only, never arithmetic. A Message becomes a list of candidate foods with
quantity and unit, plus a routing decision per food; Nutrient values come from the
`NutrientSource` (ADR-0002 as narrowed by ADR-0011). Structured output, not free
text. The model also generates the clarifying questions for Identity and can be
asked to edit an existing Entry, which means it needs a way to address a specific
Entry rather than only create new ones.

An Entry is Pending until all three parts of Identity are known — what it is, where
it came from, how much — and Pending Entries are excluded from every aggregate
(ADR-0004).

### Target calculation

A pure function from Profile and Goal to a Target Set: Katch-McArdle on lean mass
when body fat percentage is present, Mifflin-St Jeor on total mass otherwise, times
an activity multiplier, then a 20% deficit for weight loss or a 10% surplus for
weight gain and muscle gain. Protein 1.6–2.2 g/kg, fat at 25% of Calories,
carbohydrate taking the remainder (ADR-0005).

Target Sets are immutable and timestamped. A new one is written when the user
changes their Profile or Goal; nothing recalculates on its own (ADR-0006). The Check
-In prompt invites an update on a cadence the user can disable.

### Pace

A pure function from Day Slots, Target Sets and a Window to per-Nutrient fill
fractions. Average intake per Day across the trailing Window, against the daily
Target — so a Bubble means the same thing in all three Windows (ADR-0003). Each Day
resolves the Target Set that applied on that Day, because a 28-Day Window will
routinely straddle a change. Days before the account existed are excluded from the
denominator rather than counted as zero.

### Interface

Five Bubbles above the Tuna, background opacity filling with Pace. Sodium is a
ceiling rather than a floor and its fill shifts toward a warning palette past 100%,
driven by a direction flag per Nutrient. The Tuna carries Calories. A Window
selector switches Day / 7 Days / 28 Days. At the bottom, the Message input with one
line above it for the AI's latest question or reply — no transcript (ADR-0007). The
Entry List is today's Entries, each with an editable quantity and a remove action,
and is the only history surface in the app.

### Serverless discipline

The Mongo client is cached on the global object and reused across invocations;
per-request clients would exhaust Atlas's connection limit. Rate limiting and any
counters live in Mongo, not module scope, because module state does not survive
between invocations. The Food Table is the one exception — immutable and reloadable,
so a cold start simply re-reads it.

## Testing Decisions

A good test here asserts on behaviour the user could observe and says nothing about
how it was produced. "Logging two eggs raises the protein Bubble's fill" is a test.
"`computeProteinTotal` was called once" is not — it fails when the code is
reorganised and passes when the feature is broken.

There is no prior art; this is a greenfield repo, so these seams are the prior art
for everything added later.

**Primary seam: the HTTP API boundary.** Tests send requests and assert on JSON
responses. Logging a Message, resolving a clarification, editing an Entry, reading
Bubbles for a Window, crossing a Day boundary — all exercised through the real
application with real Mongo and real routing. Nothing internal is mocked. This is
the highest available seam and carries most of the suite.

Three ports are injected at that seam because they are nondeterministic, costly, or
both:

- **`NutrientSource`** — stubbed to fixed values, so tests spend nothing on Search
  and produce identical numbers on every run.
- **`Clock`** — required, not optional: Day rollover, the 28-Slot wrap, zeroing
  skipped Days, and a configurable Day Start are untestable without controlling
  time.
- **`Parser`** — stubbed to fixed structured output for deterministic tests. A
  separate, small suite exercises the real model to check parsing quality; it is run
  deliberately, not in CI, because it costs money and is not deterministic.

**Two pure-function seams below the API**, because they are dense arithmetic where a
direct test is far cheaper than an HTTP round-trip:

- **Target calculation**: `(Profile, Goal) → Target Set`. Covers the
  Katch-McArdle / Mifflin-St Jeor branch, activity multipliers, deficit and surplus
  rates, protein bounds, and implausible input.
- **Pace**: `(Day Slots, Target Sets, Window) → fill fractions`. Covers trailing
  windows, ring-buffer wraparound, excluded pre-account Days, per-Day Target Set
  resolution, and Windows straddling a Target change.

Everything else — Mongo access, the Food Table loader, the ring buffer writer, the
rollover — is tested *through* the API seam rather than directly, so internals can
be reorganised without touching tests.

Cases that must be covered because they are where this design breaks: rollover
running twice concurrently; a user returning after more than 28 Days; a Window
containing zero logged Days; an Entry edited after its Day has rolled over (it no
longer exists); a Target change mid-Window; Pending Entries never resolved; and a
Search that returns nothing.

## Out of Scope

- **Barcode scanning.** No scanner, no camera, no WASM decoder. Chat is the only
  input path.
- **Branded and packaged food browsing.** No product catalogue, no UPC database.
  Brands are handled by Search, on demand.
- **History beyond 28 Days.** No history page, no long-term charts, no weight-trend
  graph. Day 29 is gone permanently (ADR-0009).
- **Editing past Days.** Only today's Entries exist and can be corrected.
- **Offline logging.** Every Entry needs a network round-trip.
- **Installable app behaviour.** No manifest work, no service worker, no install
  prompt, no push notifications. A browser page.
- **Native iOS or Android.**
- **Billing, subscriptions, or user-supplied API keys.** Search runs on the
  operator's key (ADR-0012). The interface makes these possible later; none is built.
- **Multi-user features.** No sharing, coaching, social, or export.
- **Exercise and calories burned.** Intake only.
- **Recipes and saved meals.** Every Message is parsed fresh.
- **Micronutrients** beyond the five tracked Nutrients.
- **Water tracking.**

## Further Notes

The whole design rests on one bet: that conversational logging is pleasant enough to
sustain where search-and-scroll is not. Everything else is downstream of that, which
is why chat is the only input path — a manual entry form would let the bet go untested
and quietly become the path everyone uses.

Two constraints are load-bearing and easy to forget. The 28-Slot ring buffer is a
hard ceiling, not a soft one: there is no archive behind it, so a future history page
is a schema change and a data-loss boundary, not a feature addition. And Search cost
is linear in users on a single operator key, so a spend cap and per-user rate limiting
belong in place before the app is ever public.

The Food Table's coverage, not the model's intelligence, is what determines whether
everyday logging feels instant. If it feels slow, the fix is usually more foods in
the table rather than a better prompt.

`week` and `month` are deliberately absent from the vocabulary. The Windows are the
last 7 Days and the last 28 Days, and using calendar language for them reintroduces
exactly the semantics ADR-0003 rejected.
