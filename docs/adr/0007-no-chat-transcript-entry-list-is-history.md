# No chat transcript; the Entry List is the only history surface

Messages are stored but never rendered back as a scrollable conversation. What the
user reviews is the Entry List: the Entries themselves, each with an editable
quantity and a remove action. The conversation area shows only the current
exchange — the AI's latest question or reply above the input.

A transcript and an Entry List are two records of the same thing, and they drift:
an Entry edited to 200g while the Message above it still reads "a small handful"
leaves the user unsure which the app believes. Keeping one authoritative surface
removes the question. It also keeps the interface honest about what the app is —
a food log, not a chat app — and keeps the main screen built around the Bubbles
and the Tuna rather than a growing wall of text.

## Consequences

Messages are retained for auditing a suspicious number and for improving parsing,
but there is no UI that depends on them, so their storage format is free to change.
Entries must be editable both directly (the quantity control) and conversationally
(asking the AI to fix one), which means the AI needs a way to address a specific
existing Entry, not just create new ones. Since the user cannot scroll back to see
what they said, every Entry must be self-describing enough to recognise without
its originating Message.
