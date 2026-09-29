# History is a 28-slot ring buffer, not a growing collection

Each user document carries a fixed array of 28 Day Slots. Each Slot holds one
Day's Nutrient sums and the Target Set that applied. Today writes to
`dayIndex % 28`; when the app is opened on a new Day the Slot about to be reused
is zeroed first. Entries themselves live only for the current Day and are
discarded into their Slot at rollover. Nothing in a user's record grows over time:
the whole history is roughly 1.1 KB, forever.

The requirement was a fixed footprint with updates in place rather than a new
document per Day. Three per-user counters for daily, weekly and monthly totals
were rejected because a rolling total cannot be maintained by incrementing — when
a Day leaves the window its contribution must be subtracted, and an
increment-only counter has not kept it. That forces calendar-reset buckets, which
ADR-0003 rejected. The ring buffer satisfies the same fixed-size constraint while
keeping trailing Windows intact, and it makes reads cheap: a 28-Day Window is one
document, which matters against a shared-tier database's operation and sort-memory
limits.

## Consequences

The hard ceiling is 28 Days: no history page, no long-term trend, and data older
than 28 Days is gone permanently rather than archived. Only today's Entries can be
edited or removed, so ADR-0007's Entry List is today-only — a mistake noticed
tomorrow can be corrected in the Day Slot's totals but the offending Entry no
longer exists. Because Slots are overwritten in place there is no way to
reconstruct a Day from Entries after rollover, so the rollover write must be
correct the first time and must be idempotent against the app being opened twice.
Day Slots must be zeroed for every Day skipped, not just the one being entered, or
a user returning after a week will read stale Slots as real intake.
