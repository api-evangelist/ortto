# Ortto (ortto)

Ortto (formerly Autopilot) is a marketing automation, customer data platform (CDP), and analytics product. Its REST API at https://api.ap3api.com/v1 lets applications create and update people/contacts and accounts, send custom activity events, manage tags, retrieve campaign reports, and send transactional email and SMS, all authenticated with a custom API key via the X-Api-Key header.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/ortto/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/ortto/refs/heads/main/apis.yml)

## Tags

- Marketing Automation
- CDP
- Customer Data Platform
- Analytics
- Email

## Timestamps

- **Created:** 2026-06-25
- **Modified:** 2026-06-25

## APIs

### Ortto People / Contacts API

Create or update one or more people (merge), retrieve people by query or by IDs, archive, delete, restore, and manage subscriptions and custom fields, with configurable merge strategies.

- **Human URL:** [https://help.ortto.com/developer/latest/api-reference/people/](https://help.ortto.com/developer/latest/api-reference/people/)
- **Base URL:** `https://api.ap3api.com/v1`

#### Tags

- People
- Contacts
- CDP

#### Properties

- [Documentation](https://help.ortto.com/a-257-create-or-update-one-or-more-people-merge)
- [API Reference](https://help.ortto.com/a-250-api-reference)
- [OpenAPI](openapi/ortto-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/ortto.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/ortto.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Ortto Custom Activities API

Send up to 100 custom activity events per request (2 MB max) and manage activity definitions, optionally creating or updating the associated person via merge_by or person_id.

- **Human URL:** [https://help.ortto.com/a-233-custom-activities-guide](https://help.ortto.com/a-233-custom-activities-guide)
- **Base URL:** `https://api.ap3api.com/v1`

#### Tags

- Activities
- Events
- Tracking

#### Properties

- [Documentation](https://help.ortto.com/a-271-create-a-custom-activity-event-create)
- [API Reference](https://help.ortto.com/a-250-api-reference)
- [OpenAPI](openapi/ortto-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/ortto.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/ortto.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Ortto Campaigns API

Retrieve campaigns by time period (calendar), pull campaign and asset reports, and fetch the HTML or SMS body of email and SMS assets.

- **Human URL:** [https://help.ortto.com/a-686-retrieve-a-campaign-or-asset-report-get](https://help.ortto.com/a-686-retrieve-a-campaign-or-asset-report-get)
- **Base URL:** `https://api.ap3api.com/v1`

#### Tags

- Campaigns
- Reports
- Assets

#### Properties

- [Documentation](https://help.ortto.com/a-887-using-the-api-to-export-campaign-data)
- [API Reference](https://help.ortto.com/a-250-api-reference)
- [OpenAPI](openapi/ortto-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/ortto.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/ortto.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Ortto Tags API

Retrieve the list of tags configured on an account, optionally filtered by a search term; people are tagged and untagged through the people merge endpoint.

- **Human URL:** [https://help.ortto.com/a-263-retrieve-a-list-of-tags-get](https://help.ortto.com/a-263-retrieve-a-list-of-tags-get)
- **Base URL:** `https://api.ap3api.com/v1`

#### Tags

- Tags
- Segmentation

#### Properties

- [Documentation](https://help.ortto.com/a-227-tagging-and-untagging-people)
- [API Reference](https://help.ortto.com/a-250-api-reference)
- [OpenAPI](openapi/ortto-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/ortto.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/ortto.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Ortto Transactional Email API

Send transactional (or, with non_transactional set, marketing) email and SMS via a single POST, with support for up to 5 base64-encoded attachments; the endpoint returns a 202 on acceptance.

- **Human URL:** [https://help.ortto.com/a-242-using-the-api-to-send-emails](https://help.ortto.com/a-242-using-the-api-to-send-emails)
- **Base URL:** `https://api.ap3api.com/v1`

#### Tags

- Transactional
- Email
- Messaging

#### Properties

- [Documentation](https://help.ortto.com/a-827-send-emails-via-api)
- [API Reference](https://help.ortto.com/a-250-api-reference)
- [OpenAPI](openapi/ortto-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/ortto.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/ortto.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Ortto Webhooks

Outbound webhooks delivered from Ortto journeys/playbooks let external systems react to contact and campaign events; configuration is done in the Ortto app rather than through a dedicated public REST resource.

- **Human URL:** [https://help.ortto.com/a-223-developer-guide](https://help.ortto.com/a-223-developer-guide)
- **Base URL:** `https://api.ap3api.com/v1`

#### Tags

- Webhooks
- Events

#### Properties

- [Documentation](https://help.ortto.com/a-223-developer-guide)
- [OpenAPI](openapi/ortto-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/ortto.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/ortto.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [GitHub Organization](https://github.com/autopilot3)
- [LinkedIn](https://www.linkedin.com/company/ortto)
- [Website](https://ortto.com/)
- [Documentation](https://ortto.com/developers/)
- [Plans](plans/ortto-plans-pricing.yml)
- [Rate Limits](rate-limits/ortto-rate-limits.yml)
- [Fin Ops](finops/ortto-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
