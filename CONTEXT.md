# Macro Tuna

A mobile web app for tracking calories and macronutrients, where all food logging
happens through conversation with an AI rather than through forms or search.

## Language

### Tracking

**Entry**:
One logged act of eating, created from a Message. Holds the food identified, the
quantity, and the resulting Nutrient values.
_Avoid_: meal, item, record, log entry

**Nutrient**:
A single measured quantity attached to an Entry — protein, carbohydrate, fat,
fiber, sodium, or energy. Some are Macros, some are not.
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

**Period**:
The span a view aggregates over: Day, Week, or Month. Selecting a Period changes
both the Bubbles' fill and the Targets they are measured against.
_Avoid_: range, timeframe, tab, view

### Interface

**Bubble**:
The display of one tracked Nutrient, floating above the Tuna. Its background fills
in proportion to progress against that Nutrient's Target for the selected Period.
_Avoid_: ring, circle, widget, card

**Tuna**:
The mascot — a buff, friendly tuna fish — which doubles as the Calories display
for the selected Period. Distinct from the Bubbles because Calories are derived.
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
The value of one Nutrient a user is aiming for over one Period, derived from
Profile plus Goal, and overridable by the user.
_Avoid_: goal (reserved above), limit, budget, macro goal
