---
generated: '2026-08-13'
method: generated
name: Sync contacts into Ortto
description: Upsert people into the Ortto CDP in batches, matching existing records on a merge key rather than creating duplicates.
api: openapi/ortto-people-api-openapi.yml
operations: [mergePeople, getPeople]
source: >-
  operationIds verified verbatim in openapi/ortto-people-api-openapi.yml;
  semantics from conventions/ortto-conventions.yml,
  rate-limits/ortto-rate-limits.yml and
  https://help.ortto.com/a-257-create-or-update-one-or-more-people-merge
---

# Sync contacts into Ortto

Push a batch of people (contacts) into Ortto so they land on the right existing record instead of creating duplicates.

## Auth
- `X-Api-Key: <custom API key>` on every request. One key per Ortto account; no scopes, no test mode. See `authentication/ortto-authentication.yml`.
- Call the endpoint matching the account's region: `https://api.ap3api.com/v1` (default), `https://api.eu.ap3api.com/v1`, `https://api.au.ap3api.com/v1`.

## Idempotency
- There is **no** `Idempotency-Key` header. Repeat-safety comes from the merge key: `mergePeople` matches an existing person on the field ids in `merge_by` and updates in place. Send the same `merge_by` on every sync or you will fork records. See `conventions/ortto-conventions.yml`.

## Steps
1. **Batch the payload** — no more than 100 people per call and no more than 2 MB total. Split larger sets.
2. **Upsert** — `mergePeople` (`POST /person/merge`) with:
   - `people[]` — each entry a `fields` map keyed by Ortto field id, plus optional `location`, `tags`, `unset_tags`.
   - `merge_by` — up to 3 field ids used to identify the existing record (typically the email field id).
   - `merge_strategy` — `1` append only, `2` overwrite existing, `3` ignore.
   - `find_strategy` — `0` any, `1` sequential, `2` all.
   - `async: true` on large batches so Ortto queues processing instead of handling it inline.
   - `skip_non_existing: true` when the sync should only update people who already exist.
3. **Verify** — `getPeople` (`POST /person/get`) with a `filter` on the merge field to confirm the records landed. Page with `limit` (default 50, max 500), `offset` or `cursor_id`; read `has_more` and `next_offset` from the response.

## Rate limits
- 10 requests/second on Professional, 30 on Business and Enterprise; 2,000 requests per 10s and 6,000 per 60s per IP.
- On `429` there are **no** `RateLimit-*` headers and no `Retry-After`. Parse `try-in-seconds` out of the JSON body and sleep for that long. See `rate-limits/ortto-rate-limits.yml`.
- 15 malformed requests in 15 seconds gets the IP banned for 15 seconds — validate payloads before sending.

## Errors
- Vendor JSON, not RFC 9457. Live bodies carry `request_id`, `code` and `error`; quote `request_id` to support. Full status table in `errors/ortto-problem-types.yml`.
- `507 Insufficient Storage` means the account's contact limit has been exceeded — stop and escalate rather than retrying.

## Notes
- Field ids, not field names, are the keys of the `fields` map, and they are account-specific. Retrieve the instance schema before mapping a new source: https://help.ortto.com/a-797-retrieve-account-instance-schema-via-api.
- Every operation is a `POST`, including the reads.
