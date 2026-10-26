# Webex (webex)

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

Cisco Webex is a comprehensive collaboration platform offering APIs for messaging, meetings, calling, devices, and contact center workflows. The Webex Developer Platform enables developers to build integrations, bots, embedded apps, and automations using REST APIs, SDKs, and webhooks. Webex supports OAuth 2.0 authentication and provides separate API surfaces for messaging, video conferencing, cloud calling, admin management, and more.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/webex/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/webex/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Consumer
- **Access:** 3rd-Party

## Tags

- Calling
- Collaboration
- Communication
- Enterprise
- Messaging
- Video Conferencing

## Timestamps

- **Created:** 2025-02-06
- **Modified:** 2026-05-19

## APIs

### Webex Messaging

Webex Messaging API for creating and managing rooms, messages, attachments, teams, memberships, and real-time collaboration. Supports text, markdown, file sharing, and webhook event subscriptions.

- **Human URL:** [https://developer.webex.com/docs/messaging](https://developer.webex.com/docs/messaging)

#### Tags

- Bots
- Collaboration
- Messaging
- Rooms
- Teams
- Webhooks

#### Properties

- [Documentation](https://developer.webex.com/docs/messaging)
- [OpenAPI](openapi/webex-messaging-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/webex-messaging.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/webex-messaging.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Webex Meetings

Webex Meetings API for scheduling, managing, and reporting on video meetings. Provides endpoints for meeting lifecycle management, invitees, participants, recordings, transcripts, and meeting templates.

- **Human URL:** [https://developer.webex.com/docs/meetings](https://developer.webex.com/docs/meetings)

#### Tags

- Meetings
- Recordings
- Scheduling
- Video Conferencing

#### Properties

- [Documentation](https://developer.webex.com/docs/meetings)
- [OpenAPI](openapi/webex-meeting-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/webex-meeting.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/webex-meeting.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Webex Admin

Webex Admin API for managing organizations, users, licenses, locations, workspaces, devices, and organization settings. Provides administrative control over Webex deployments including PSTN settings and call policies.

- **Human URL:** [https://developer.webex.com/docs/admin](https://developer.webex.com/docs/admin)

#### Tags

- Administration
- Devices
- Licenses
- Organizations
- Users

#### Properties

- [Documentation](https://developer.webex.com/docs/admin)
- [OpenAPI](openapi/webex-admin-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/webex-admin.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/webex-admin.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Webex Cloud Calling

Webex Cloud Calling API with 633 endpoints for managing users, locations, call settings, hunt groups, auto-attendants, voicemail, call queues, and PSTN configurations for cloud-based telephony.

- **Human URL:** [https://developer.webex.com/docs/cloud-calling](https://developer.webex.com/docs/cloud-calling)

#### Tags

- Auto Attendant
- Call Management
- Calling
- Cloud Telephony
- PSTN
- Voicemail

#### Properties

- [Documentation](https://developer.webex.com/docs/cloud-calling)
- [OpenAPI](openapi/webex-cloud-calling-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/webex-cloud-calling.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/webex-cloud-calling.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Webex Contact Center

Webex Contact Center API for managing customer service operations including agents, queues, routing strategies, skills, and reporting. Enables programmatic control of contact center configurations and workflows.

- **Human URL:** [https://developer.webex.com/docs/contact-center](https://developer.webex.com/docs/contact-center)

#### Tags

- Agents
- Contact Center
- Customer Service
- Queues
- Routing

#### Properties

- [Documentation](https://developer.webex.com/docs/contact-center)
- [OpenAPI](openapi/webex-contact-center-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/webex-contact-center.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/webex-contact-center.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Webex Devices

Webex Device API for managing Webex hardware devices, workspaces, and device configurations. Includes endpoints for device inventory, activation, workspace assignments, and device-specific settings.

- **Human URL:** [https://developer.webex.com/docs/devices](https://developer.webex.com/docs/devices)

#### Tags

- Devices
- Hardware
- Workspaces

#### Properties

- [Documentation](https://developer.webex.com/docs/devices)
- [OpenAPI](openapi/webex-device-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/webex-device.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/webex-device.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Webex Broadworks Calling

Webex Broadworks Calling API for managing BroadWorks subscriber provisioning and migration to Webex. Enables service providers to integrate BroadWorks telephony infrastructure with Webex cloud services.

- **Human URL:** [https://developer.webex.com/docs/broadworks](https://developer.webex.com/docs/broadworks)

#### Tags

- BroadWorks
- Calling
- Service Provider
- Telephony

#### Properties

- [Documentation](https://developer.webex.com/docs/broadworks)
- [OpenAPI](openapi/webex-broadworks-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/webex-broadworks.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/webex-broadworks.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Webex for UCM

Webex for Unified CM (UCM) API for managing on-premises Cisco Unified Communications Manager integration with Webex cloud services. Supports hybrid calling configurations.

- **Human URL:** [https://developer.webex.com/docs/ucm](https://developer.webex.com/docs/ucm)

#### Tags

- Calling
- On-Premises
- Unified CM

#### Properties

- [Documentation](https://developer.webex.com/docs/ucm)
- [OpenAPI](openapi/webex-ucm-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/webex-ucm.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/webex-ucm.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Webex Wholesale

Webex Wholesale API for service provider partners to provision and manage Webex Wholesale (RTM) customers and subscriptions at scale. Enables white-label Webex deployment workflows.

- **Human URL:** [https://developer.webex.com/docs/wholesale](https://developer.webex.com/docs/wholesale)

#### Tags

- Partner
- Provisioning
- Service Provider
- Wholesale

#### Properties

- [Documentation](https://developer.webex.com/docs/wholesale)
- [OpenAPI](openapi/webex-wholesale-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/webex-wholesale.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/webex-wholesale.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/webex)
- [Portal](https://developer.webex.com/)
- [Getting Started](https://developer.webex.com/docs/getting-started)
- [Authentication](https://developer.webex.com/docs/authentication)
- [SDK](https://developer.webex.com/docs/sdks)
- [SDK](https://github.com/webex/webex-js-sdk)
- [SDK](https://github.com/webex/webex-ios-sdk)
- [SDK](https://github.com/webex/webex-android-sdk)
- [Blog](https://developer.webex.com/blog)
- [Status Page](https://status.webex.com)
- [Support](https://developer.webex.com/support)
- [Terms of Service](https://www.cisco.com/c/en/us/about/legal/terms-conditions.html)
- [Privacy Policy](https://www.cisco.com/c/en/us/about/legal/privacy-full.html)
- [Rate Limits](https://developer.webex.com/docs/rate-limiting)
- [GitHub Organization](https://github.com/webex)
- [GitHub Repository](https://github.com/webex/webex-openapi-specs)
- [Spectral Rules](rules/webex-spectral-rules.yml)
- [Vocabulary](vocabulary/webex-vocabulary.yml)
- [JSON-LD](json-ld/webex-messaging-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)
- [JSON-LD](json-ld/webex-meeting-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)
- [JSON-LD](json-ld/webex-admin-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)
- [JSON-LD](json-ld/webex-device-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)
- [Features](undefined)
- [Use Cases](undefined)
- [Integrations](undefined)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
