# MongoDB Atlas free tier, Better Auth on a single origin

Data lives in one MongoDB Atlas M0 cluster: 512 MB hard cap, shared CPU, roughly
100 operations per second, 32 MB of sort memory. Authentication is Better Auth
using its official MongoDB adapter, served from the same origin as the app, with
Google and Apple as social providers.

Mongo fits because the ring buffer of ADR-0009 makes storage per user constant and
the live Lookups of ADR-0008 mean no food corpus has to be stored at all — the two
things that would have overrun 512 MB are both absent by design. Better Auth was
chosen over Clerk, Auth.js and WorkOS because it issues plain first-party HttpOnly
cookies from the app's own domain, which is the only session model that reliably
survives Safari's tracking prevention; it is also free at any scale, which suits an
app with no revenue. Auth.js was rejected as being in maintenance mode, and Clerk
and WorkOS because both introduce a second auth-owned domain, which is exactly
where browser sessions break.

## Consequences

The 512 MB cap is a hard write failure, not throttling, so growth has to stay
bounded by design rather than by monitoring. The operations-per-second and
sort-memory limits mean reads should hit whole documents rather than aggregate
across many. Auth must stay on one origin — no separate API subdomain — and auth
routes must be excluded from any service worker caching, or login breaks only for
installed users. Better Auth's CLI cannot generate schema for MongoDB, so
collections are defined by hand, and its default collection naming is known to
collide with existing `user` collections. Apple as a provider requires a
regenerated client secret roughly every six months, which is an operational chore
that will silently break sign-in if missed.
