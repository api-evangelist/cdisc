# cdisc (cdisc)

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

CDISC Library uses linked data and a REST API to deliver CDISC standards metadata to software applications that automate standards-based processes. CDISC Library provides access to new relationships between standards as well as a substantially increased number of versioned CDISC standards and controlled terminology packages.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/cdisc/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/cdisc/refs/heads/main/apis.yml)

## Timestamps

- **Modified:** 2026-05-19

## APIs

### CDISC Library API

The CDISC Library API is a REST API that delivers CDISC standards metadata to software applications that automate standards-based processes. It uses linked data to provide access to SDTM, ADaM, and other clinical data standards. Responses are available in JSON, XML, ODM, CSV, and Excel formats. Access requires a CDISC Library account and an API key obtained from the CDISC Library API Management (APIM) Developer Portal.

- **Human URL:** [https://www.cdisc.org/cdisc-library](https://www.cdisc.org/cdisc-library)
- **Base URL:** `https://library.cdisc.org/api`

#### Tags

- ADaM
- Clinical Trials
- Metadata
- ODM
- Pharma
- SDTM
- Standards

#### Properties

- [Documentation](https://www.cdisc.org/cdisc-library/api-documentation)
- [Reference](https://api.developer.library.cdisc.org/api-details)
- [Getting Started](https://www.cdisc.org/cdisc-library/getting-started)
- [Portal](https://api.developer.library.cdisc.org/)
- [Knowledge Base](https://wiki.cdisc.org/display/LIBSUPRT/How-to+articles)
- [Changelog](https://wiki.cdisc.org/display/LIBSUPRT/Release+Notes)
- [Support](https://jira.cdisc.org/servicedesk/customer/portal/2)
- [Explorer](https://library.cdisc.org/browser)
- [OpenAPI](https://raw.githubusercontent.com/api-evangelist/cdisc/refs/heads/main/openapi/cdisc-library-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/cdisc-library.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/cdisc-library.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### CDISC CORE (Checks and Rules Engine) API

CDISC CORE (Checks and Rules Engine) is an open-source rules engine for validating clinical data against CDISC conformance rules. It enables automated validation of SDTM, ADaM, and other study data artifacts against published CDISC standards.

- **Human URL:** [https://www.cdisc.org/core](https://www.cdisc.org/core)
- **Base URL:** `https://library.cdisc.org/api`

#### Tags

- Clinical Trials
- Conformance
- Pharma
- Rules
- Validation

#### Properties

- [Documentation](https://www.cdisc.org/core)
- [Postman Collection](collections/cdisc-library.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/cdisc-library.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [GitHub Organization](https://github.com/cdisc-org)
- [LinkedIn](https://www.linkedin.com/company/cdisc)
- [Website](https://www.cdisc.org/)
- [OpenAPI](https://raw.githubusercontent.com/api-evangelist/cdisc/refs/heads/main/openapi/cdisc-library-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [JSON Schema](https://raw.githubusercontent.com/api-evangelist/cdisc/refs/heads/main/json-schema/cdisc-dataset-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [J S O N L D Context](https://raw.githubusercontent.com/api-evangelist/cdisc/refs/heads/main/json-ld/cdisc-context.jsonld)
- [Portal](https://www.cdisc.org/cdisc-library)
- [Getting Started](https://www.cdisc.org/cdisc-library/getting-started)
- [Documentation](https://www.cdisc.org/cdisc-library/api-documentation)
- [Authentication](https://api.developer.library.cdisc.org/)
- [Support](https://jira.cdisc.org/servicedesk/customer/portal/2)
- [Changelog](https://wiki.cdisc.org/display/LIBSUPRT/Release+Notes)
- [Sign Up](https://www.cdisc.org/cdisc-library/api-account-request)
- [Integrations](https://www.cdisc.org/partners)

## Maintainers

**Email:** kin@apievangelist.com
