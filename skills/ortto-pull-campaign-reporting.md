---
generated: '2026-08-13'
method: generated
name: Pull campaign reporting
description: List campaigns from the calendar, then fetch the performance report for a campaign or one of its assets.
api: openapi/ortto-campaigns-api-openapi.yml
operations: [getCampaignCalendar, getCampaignReport]
source: >-
  operationIds verified verbatim in openapi/ortto-campaigns-api-openapi.yml;
  behaviour from https://help.ortto.com/a-887-using-the-api-to-export-campaign-data,
  https://help.ortto.com/a-695-retrieve-a-list-of-sent-campaigns-calendar and
  https://help.ortto.com/a-686-retrieve-a-campaign-or-asset-report-get
---

# Pull campaign reporting

Get campaign performance out of Ortto and into a warehouse, dashboard or agent context.

## Auth
- `X-Api-Key: <custom API key>`. See `authentication/ortto-authentication.yml`.

## Steps
1. **List campaigns** — `getCampaignCalendar` (`POST /campaign/calendar`) with:
   - `type` — campaign type (email, SMS, push, journey, playbook).
   - `state` — campaign state filter.
   - `folder_id`, `q` — narrow by folder or search term.
   - `sort_order` — `asc` or `desc`.
   - `limit` — page size.
   Capture each campaign's id.
2. **Fetch the report** — `getCampaignReport` (`POST /campaign/reports/get`) with `campaign_id`, and optionally `asset_id` to scope the report to a single message asset within the campaign.
3. **Iterate** — repeat step 2 per campaign. There is no bulk report endpoint.

## Pagination
- Reads are `POST` bodies, not query strings. Use `limit`, `offset` and `cursor_id`, and follow `has_more` / `next_offset` from the response envelope. See `conventions/ortto-conventions.yml`.

## Rate limits
- 10 req/s Professional, 30 req/s Business and Enterprise. A per-campaign report loop over a large account will hit this — pace the loop and back off for `try-in-seconds` on `429`. See `rate-limits/ortto-rate-limits.yml`.

## Errors
- See `errors/ortto-problem-types.yml`.

## Agent note
If you are an agent rather than a batch job, Ortto's MCP server is the better surface for reporting: `get_campaigns`, `get_email_report`, `get_journey_report`, `get_journey_shape_report`, `get_sms_report`, `get_push_report`, `list_reports` and `get_report` cover more reporting ground than the REST API does, including journey, SMS and push reports that have no REST equivalent. See `mcp/ortto-mcp.yml` and `mcp/ortto-tool-crosswalk.yml`. The reverse is also true: MCP cannot write contacts, emit activities or send messages, so a mixed workflow needs both surfaces.
