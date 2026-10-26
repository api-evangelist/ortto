# Ortto (ortto)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
