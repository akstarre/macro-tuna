# Bubbles show Pace over a trailing Window, not cumulative totals

The three views are the current Day, the last 7 Days, and the last 28 Days —
trailing windows, not calendar weeks or months. Each Bubble fills according to
average intake per Day across the window, measured against the same daily Target
in all three.

The alternative was a cumulative total against a multiplied target (7 × daily).
That was rejected because it makes a Bubble mean something different in each
view: on a Monday morning the weekly Bubble would sit near empty no matter how
well the user has eaten, reading as failure when they are exactly on pace.
A view that punishes you for the calendar cannot support accountability, which is
the reason these views exist. Trailing windows also mean a Sunday-night binge
stays visible into the following week instead of being erased by a calendar
boundary.

## Consequences

Targets are stored per-day only; no per-window target exists anywhere in the
model. Windows of 7 and 28 days are both whole multiples of a week, so neither
over-weights weekends. Days before the account existed are excluded from the
average rather than counted as zero, otherwise a new user's Bubbles read as
failure on day one.
