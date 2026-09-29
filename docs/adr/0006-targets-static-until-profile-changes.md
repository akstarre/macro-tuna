# Targets are static until the user updates their Profile

Targets do not drift on their own. They are recalculated only when the user
changes their Profile, which they are invited to do by a periodic Check-In that
can be switched off in settings. Each recalculation writes a new Target Set
rather than mutating the old one.

Silent drift was rejected: a Bubble the user was comfortably hitting suddenly
reading as missed, with no action on their part to explain it, reads as a bug and
costs trust in every other number. Static-forever was also rejected, because a
user 8 kg into a cut is measuring themselves against a stranger's requirements.
The Check-In puts the change under the user's control while making sure staleness
gets noticed.

## Consequences

Target Sets are immutable and timestamped, and every Pace calculation resolves the
Target Set that applied on each Day rather than reading today's. This is the whole
reason Target Sets are versioned: a 28-Day Window will routinely straddle a
change, and comparing old intake against new Targets would misreport history.
Deleting a Target Set is therefore never safe once Days reference it.
