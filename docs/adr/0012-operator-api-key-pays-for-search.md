# The operator's API key pays for Search in v1

Search runs on a single Anthropic API key owned by the operator. There is no
per-user key and no billing in v1. Every Lookup path sits behind one
`NutrientSource` interface so that Search can later be switched off per user or
per tier without touching the logging flow.

An Anthropic subscription cannot serve an application: Pro, Max and Team grant
access to claude.ai and the desktop apps only, provide no API credits or discount,
and only Enterprise touches the API at all — at per-token rates on top of the seat
price. Driving a subscription-authenticated client to serve users would breach the
terms and is not an option.

The cost is bounded by ADR-0011. Search is billed at $10 per 1,000 searches plus
the retrieved page text as input tokens, roughly two cents per searched food. With
generic foods resolving against the Food Table for free, a single user logging ten
times a day costs cents per month. That is affordable for one operator and one
user, and deliberately does not scale — which is the point of putting the interface
in now.

## Consequences

Search cost is linear in users and is the app's dominant variable cost, so a
revenue model has to exist before any significant user base does. The likely
shapes are user-supplied keys or a paid tier; both are enabled by the
`NutrientSource` interface and neither is built now. Anthropic requires that
citations be displayed when search results are shown to end users, so the Sourced
badge is a compliance obligation rather than a nicety. The key is a single point of
failure and a single point of abuse: rate limiting per user is needed before the
app is public, and a spend cap should be set in the console from the start.
