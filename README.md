# Semble (semble)

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

Semble is a London-headquartered cloud clinical and practice-management platform for United Kingdom private and independent healthcare providers. Its modular EHR unifies patient records, appointment scheduling and online booking, video consultations, e-prescribing, pathology/lab ordering, clinical documentation, invoicing and payments (Semble Pay), and patient communications. Semble exposes a single open, secure public GraphQL API — available to Semble clinics at no extra cost — for reading and writing patients, bookings, availability, consultations, clinical pathways, prescriptions, labs, invoices, tasks, forms, questionnaires, and webhooks.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/semble/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/semble/refs/heads/main/apis.yml)

## Tags

- Healthcare
- United Kingdom
- EHR
- Practice Management
- GraphQL
- Patient Records
- Scheduling
- e-Prescribing
- Interoperability
- Digital Health

## Timestamps

- **Created:** 2026-07-24
- **Modified:** 2026-07-24

## API Posture

- **API style:** GraphQL (single endpoint) — `https://open.semble.io/graphql`
- **Authentication:** API-key / token via the `x-token` header (role-scoped token, 12-hour lifetime); a `signIn(email, password)` mutation can also mint a token. Not SMART-on-FHIR.
- **Rate limit:** 240 requests per minute (documented).
- **FHIR / HL7:** No FHIR CapabilityStatement, `/metadata`, or `/.well-known/smart-configuration` is served — the API is GraphQL-native, not FHIR.
- **Downloadable spec:** None published — the developer portal is a Docusaurus site rendering the GraphQL schema; `docs.semble.io/openapi.json` returns the SPA shell, and schema introspection is gated behind an authenticated token.
- **Availability:** Documented and self-serve to Semble clinics (Settings → API Access), gated by Semble package and role.

## APIs

The Semble public GraphQL API is modeled here by product domain (all sharing the single `https://open.semble.io/graphql` endpoint):

### Semble Patients API

Patients, demographics, phone numbers, relationships, labels, memberships, access groups, allergy records, free-text records, patient documents, and patient communications.

- **Human URL:** [https://docs.semble.io/docs/API/queries/patients/](https://docs.semble.io/docs/API/queries/patients/)
- **Base URL:** `https://open.semble.io/graphql`

### Semble Scheduling & Bookings API

Bookings, availabilities, availability rules/settings/slots, online booking configurations, out-of-office bookings, and booking payments.

- **Human URL:** [https://docs.semble.io/docs/API/queries/bookings/](https://docs.semble.io/docs/API/queries/bookings/)
- **Base URL:** `https://open.semble.io/graphql`

### Semble Clinical API

Consultations, clinical pathways, clinical reports, episodes and episode types, letters, working diagnoses, diagnosis codes, forms, and questionnaires.

- **Human URL:** [https://docs.semble.io/docs/API/queries/consultations/](https://docs.semble.io/docs/API/queries/consultations/)
- **Base URL:** `https://open.semble.io/graphql`

### Semble Prescriptions & Labs API

Prescriptions, repeat prescriptions, and lab / pathology orders and results.

- **Human URL:** [https://docs.semble.io/docs/API/queries/prescriptions/](https://docs.semble.io/docs/API/queries/prescriptions/)
- **Base URL:** `https://open.semble.io/graphql`

### Semble Billing & Payments API

Invoices, invoice payments and line items, account statements, products, price profiles/rules/adjustments, and Semble Pay payment terminals.

- **Human URL:** [https://docs.semble.io/docs/API/queries/invoices/](https://docs.semble.io/docs/API/queries/invoices/)
- **Base URL:** `https://open.semble.io/graphql`

### Semble Practice & Platform API

Practice details, users, contacts, tasks, labels, template documents, integration tokens, and webhooks.

- **Human URL:** [https://docs.semble.io/docs/API/queries/webhooks/](https://docs.semble.io/docs/API/queries/webhooks/)
- **Base URL:** `https://open.semble.io/graphql`

## Common Properties

- [Website](https://www.semble.io/)
- [Developer Portal](https://docs.semble.io/)
- [API Reference](https://docs.semble.io/docs/API/)
- [Getting Started](https://help.semble.io/api-access)
- [Authentication](https://docs.semble.io/docs/authentication/)
- [Status Page](https://status.semble.io/)
- [Security / Trust Centre](https://trust.semble.io/)
- [Blog](https://www.semble.io/blog)
- [Support](https://help.semble.io/)
- [Sign Up / Book a Demo](https://www.semble.io/book-a-demo)
- [Terms of Service](https://www.semble.io/terms-of-service)
- [Privacy Policy](https://www.semble.io/privacy-policy)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
