# Macro Tuna

A web app for tracking calories and macronutrients, where all food logging
happens through conversation with an AI rather than through forms or search.

## Language

### Tracking

**Entry**:
One logged act of eating, created from a Message. Holds the food identified, the
quantity, and the resulting Nutrient values.
_Avoid_: meal, item, record, log entry

**Nutrient**:
A single measured quantity attached to an Entry — protein, carbohydrate, fat,
fiber, or sodium. Some are Macros, some are not.
_Avoid_: macro (when speaking generally), nutrition, stat

**Macro**:
One of the three energy-providing Nutrients: protein, carbohydrate, fat. Fiber
and sodium are Nutrients but not Macros. Calories are not a Nutrient at all.
_Avoid_: macronutrient (in code), stat

**Calories**:
Energy, derived from Macro grams (4/4/9), never measured or stored independently.
The reason Calories are displayed on the Tuna and not in a Bubble.
_Avoid_: kcal, energy (in UI copy), calorie count

**Day**:
The window an Entry is counted in. Bounded by the Day Start, not by midnight UTC.
_Avoid_: date, today

**Day Start**:
The per-user local time at which a new Day begins. Defaults to midnight, and is
configurable because late-night eating belongs to the day it felt like.
_Avoid_: cutoff, rollover, reset time

**Window**:
The span the Bubbles aggregate over: the current Day, the last 7 Days, or the
last 28 Days. Always trailing from now, never a calendar week or calendar month.
_Avoid_: period, range, timeframe, tab, view, week, month

**Pace**:
Average Nutrient intake per Day across the selected Window, which is what a
Bubble actually displays. Compared against the daily Target, so a Bubble means
the same thing in all three Windows.
_Avoid_: average, rate, trend

### Logging

**Message**:
One thing the user says in the conversation. May produce zero, one, or several
Entries. Stored, but never displayed back as a scrollable transcript.
_Avoid_: prompt, chat, input, utterance

**Entry List**:
The reviewable record of what the user ate — the only history surface in the app.
Shows Entries, not Messages, each with its quantity editable and itself
removable. Takes the place of a chat transcript.
_Avoid_: history, transcript, log, feed, diary

**Identity**:
The three facts an Entry needs before it can be counted: what the food is, where
it came from (brand or restaurant), and how much of it there was. An Entry
missing any of them is Pending.
_Avoid_: details, metadata, attributes

**Pending**:
The state of an Entry whose Identity is incomplete. Pending Entries are excluded
from Pace and from the Tuna, because a total that includes half-known food is a
lie.
_Avoid_: draft, incomplete, unconfirmed, partial

**Estimated**:
The state of an Entry whose Nutrient values came from the AI rather than a
database match. Always visibly marked, always editable.
_Avoid_: guessed, approximate, inferred

### Interface

**Bubble**:
The display of one tracked Nutrient, floating above the Tuna. Its background fills
in proportion to Pace against that Nutrient's daily Target.
_Avoid_: ring, circle, widget, card

**Tuna**:
The mascot — a buff, friendly tuna fish — which doubles as the Calories display
for the selected Window. Distinct from the Bubbles because Calories are derived.
_Avoid_: mascot (in code), fish, avatar

### The user

**Profile**:
The user's body and activity facts — weight, height, age, sex, body fat
percentage, activity level — from which Targets are calculated.
_Avoid_: settings, account, user data

**Goal**:
The outcome the user is pursuing: weight loss, weight gain, muscle gain, or
maintenance. A Goal transforms a Profile into Targets.
_Avoid_: objective, plan, program, mode

**Target**:
The daily value of one Nutrient a user is aiming for, derived from Profile plus
Goal, and overridable by the user. Always daily, never per-Window.
_Avoid_: goal (reserved above), limit, budget, macro goal

**Target Set**:
The Targets in force from a given moment, stored as an immutable version so a
Window spanning a change is measured against whatever was true on each Day.
_Avoid_: snapshot, revision, version, current targets

**Check-In**:
The periodic prompt asking the user to re-state their Profile. Answering it is
what moves Targets; ignoring it leaves them static. Disableable in settings.
_Avoid_: reminder, nudge, weigh-in, update prompt
