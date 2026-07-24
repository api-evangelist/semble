# Semble (semble)

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
