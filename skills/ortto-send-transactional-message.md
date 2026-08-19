---
generated: '2026-08-13'
method: generated
name: Send a transactional email or SMS
description: Send a transactional message to resolved recipients via Ortto, with attachments and merge data, and understand what the 202 does and does not guarantee.
api: openapi/ortto-transactional-api-openapi.yml
operations: [sendTransactionalEmail, sendTransactionalSms, mergePeople]
source: >-
  operationIds verified verbatim in openapi/ortto-transactional-api-openapi.yml;
  behaviour from https://help.ortto.com/a-827-send-emails-via-api and
  https://help.ortto.com/a-243-using-the-api-to-send-sms-messages
---

# Send a transactional email or SMS

Deliver a one-to-one message — receipt, password reset, order update — through Ortto's transactional endpoints.

## Auth
- `X-Api-Key: <custom API key>`. See `authentication/ortto-authentication.yml`.
- Transactional sending requires a supporting plan; email sending may need enabling by Ortto support before the endpoint will deliver.

## Steps
1. **Have the asset ready** — a transactional email asset (or SMS asset) is created in the Ortto app and referenced by id. There is no REST operation to create one.
2. **Send email** — `sendTransactionalEmail` (`POST /transactional/send`) with:
   - `email_id` — the transactional email asset id.
   - `people[]` and `merge_by[]` — recipients and the field ids used to resolve them.
   - `subject` / `html_body` — override the asset content when needed.
   - `attachments[]` — up to 5, base64-encoded.
   - `non_transactional: true` only if the message should be treated as marketing (this changes subscription/unsubscribe handling).
3. **Send SMS** — `sendTransactionalSms` (`POST /transactional/send-sms`) with `sms_id`, `people[]` and `merge_by[]`.

## What 202 means
Both operations return **202 Accepted**: the request has been received and queued for delivery. It is not a delivery confirmation. Delivery and engagement outcomes surface as activities and campaign reports, not in this response.

## Idempotency
- **None.** There is no idempotency key and no de-duplication on the send path. A retried call sends the message again. Record the send against your own state before retrying a timeout.

## Rate limits
- Plan-based: 10 req/s Professional, 30 req/s Business and Enterprise. On `429`, sleep for `try-in-seconds` from the body. See `rate-limits/ortto-rate-limits.yml`.

## Errors
- See `errors/ortto-problem-types.yml`. `403` on a send usually means the plan does not include transactional messaging or the account has not been approved for it.

## Notes
- Structured merge data can be passed as a JSON object and referenced with Liquid in the template — https://help.ortto.com/a-286-passing-json-object-data-in-a-transactional-email-via-api.
- Recipients on the account's email suppression list will not receive the message; the suppression list is managed at https://help.ortto.com/a-836-managing-the-email-suppression-list-via-api.
