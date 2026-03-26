# Add API Request Rate Limiting

> **This is an example spec** demonstrating the task-spec-template filled in for a realistic task.
> It is not a real task in this repository.
> Use it as a reference when writing your own specs.

## Metadata

### Source Plan / Request
Phase 2 hardening plan — "add basic rate limiting before public beta launch."

### Status
`done`

### Related Specs
- `20251215-001-api-auth-middleware.md` (prerequisite, done)
- `20260101-002-rate-limit-dashboard.md` (follow-up, draft)

## Goal
Add per-client request rate limiting to the public API so that no single client can exhaust server resources.

## In Scope
- token-bucket rate limiter middleware for the API gateway
- per-client limits keyed by API key
- 429 response with `Retry-After` header when limit is exceeded
- configurable limit via environment variable

## Out of Scope
- per-endpoint differentiated limits (future phase)
- rate limit analytics dashboard (separate spec)
- authentication changes

## Affected Area
- `src/middleware/rate-limiter.ts` (new)
- `src/middleware/index.ts` (register middleware)
- `src/config/env.ts` (new env var)
- `tests/integration/rate-limiter.test.ts` (new)
- `tests/unit/rate-limiter.test.ts` (new)

## Task Checklist
- [x] implement token-bucket rate limiter middleware
- [x] register middleware in API gateway pipeline
- [x] add `RATE_LIMIT_PER_MINUTE` env var with default
- [x] return 429 with correct `Retry-After` header
- [x] add integration test for rate-limited request
- [x] add unit tests for token-bucket logic

## Done When
A client exceeding the configured rate limit receives a 429 response with a correct `Retry-After` header, and clients below the limit are unaffected.

## Validation

### Black-box Checks
- send requests above the limit → expect 429 with `Retry-After`
- send requests below the limit → expect normal 200
- change `RATE_LIMIT_PER_MINUTE` → confirm new limit takes effect

### White-box Needed
Yes

### White-box Trigger
The token-bucket algorithm has internal state (token count, refill timing) and branch-heavy logic (allow vs deny vs refill). Black-box checks alone cannot reliably verify that the bucket refills correctly at boundary conditions.

### Internal Logic To Protect
- token deduction and refill timing in `TokenBucket` class
- boundary case: request arrives exactly when bucket refills
- boundary case: concurrent requests drain bucket to zero

## Write-back Needed
No

## Risks / Notes
- If the middleware is registered after auth middleware, unauthenticated requests will not be rate-limited. Registration order matters.
