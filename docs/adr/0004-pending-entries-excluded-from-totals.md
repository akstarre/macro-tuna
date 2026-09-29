# A Pending Entry does not count toward anything

An Entry needs three facts before it is real: what the food is, where it came
from, and how much of it there was. Until all three are known the Entry is
Pending, and Pending Entries are excluded from Pace, from the Bubbles, and from
the Tuna. The AI collects the missing facts through ordinary conversation rather
than blocking the user behind a form.

Counting a half-identified Entry would be worse than not counting it: "a bagel"
could be 180 or 400 calories, and a total silently built from that spread is
indistinguishable from an accurate one. The user would trust it, act on it, and be
wrong. Excluding Pending Entries means a total is either correct or visibly
incomplete, never quietly false.

## Consequences

The UI must surface the count of Pending Entries prominently, because an excluded
Entry the user has forgotten about makes the day's totals look artificially good.
Entry state is `pending | resolved | estimated`, and every aggregate query filters
on it. Resolution is non-blocking and can happen long after the Message that
created the Entry, so clarification must be addressable to a specific Entry
rather than assuming the most recent one.
