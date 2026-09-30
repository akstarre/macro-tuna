# Next.js on Vercel, single deployment

The app is a Next.js application deployed to Vercel, with the React UI and the API
routes in one project on one origin. MongoDB Atlas is provisioned in the same
region Vercel functions run in (`iad1` / `us-east-1`) to keep round-trips short.

Next.js and Vercel satisfy ADR-0010's hard requirement for free: the UI and
`/api/auth/*` are the same origin by construction, so Better Auth's first-party
session cookies work with no proxying, no subdomain split, and no exposure to
browser tracking prevention. Vercel's Hobby tier allows a 300-second function
duration, which removes any concern that a live Search could exceed the request
budget. The Food Table from ADR-0011 ships inside the deployment bundle — under a
megabyte, against a 250 MB limit — and is read into memory at cold start.

## Consequences

Serverless execution means database connections must be cached on the global
object and reused across invocations; opening a client per request will exhaust
Atlas's connection limit under any real concurrency. Cold starts pay for parsing
the Food Table, so it must be a compact prebuilt format rather than something
assembled at boot. Module-level state cannot be trusted to persist between
requests, which suits the Food Table (immutable, reloadable) but rules out
in-memory session or rate-limit counters — both need to live in Mongo. Hobby runs
functions in a single region, so a user far from `us-east-1` pays latency on every
Entry, and the free tier's monthly request allowance becomes a ceiling on real
usage well before the database does.
