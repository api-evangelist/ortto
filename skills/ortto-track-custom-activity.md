---
generated: '2026-08-13'
method: generated
name: Track a custom activity event
description: Send custom activity events into Ortto against a person, respecting the per-contact frequency cap and the backdating window.
api: openapi/ortto-activities-api-openapi.yml
operations: [createActivities, mergePeople]
source: >-
  operationIds verified verbatim in openapi/ortto-activities-api-openapi.yml and
  openapi/ortto-people-api-openapi.yml; limits from
  https://help.ortto.com/a-271-create-a-custom-activity-event-create and
  rate-limits/ortto-rate-limits.yml
---

# Track a custom activity event

Emit product or business events into Ortto so journeys, audiences and reports can trigger on them.

## Auth
- `X-Api-Key: <custom API key>`. See `authentication/ortto-authentication.yml`.

## Prerequisites
- The custom activity **definition** must exist in the account before events can be sent against it (https://help.ortto.com/a-273). Activity attributes are field ids, not names.

## Steps
1. **Resolve the person** — activities attach to a contact. Either send `merge_by` on the activity payload so Ortto resolves the person by field id, or upsert first with `mergePeople` (`POST /person/merge`) and use the returned contact id.
2. **Send the events** — `createActivities` (`POST /activities/create`) with:
   - `activities[]` — each carrying the activity definition id and its attribute map.
   - `merge_by` — the field ids used to resolve the contact each activity belongs to.

## Hard limits
These are enforced, not advisory:
- 100 activities per request.
- 2 MB total payload, 16 kB per individual activity.
- 50 events per custom activity per contact per 24 hours — beyond this the events are dropped, not queued.
- Backdating is allowed up to 90 days, or the account's configured data-retention period, whichever is shorter.

## Idempotency
- **None.** `createActivities` has no merge semantics and no idempotency key. A retried call re-sends the events and they will count twice against the 50-per-contact-per-day cap. Track your own delivery state before retrying.

## Rate limits
- 10 req/s Professional, 30 req/s Business and Enterprise. On `429`, back off for `try-in-seconds` from the response body; there is no `Retry-After` header. See `rate-limits/ortto-rate-limits.yml`.

## Errors
- See `errors/ortto-problem-types.yml`. A `400` most often means an unknown activity definition id or an attribute that is not in the instance schema.

## Notes
- Web and mobile events can also arrive through the tracking runtime (`ap3c.activity()`) or the SDKs rather than this endpoint — see `components/ortto-components.yml` and `packages/ortto-packages.yml`.
