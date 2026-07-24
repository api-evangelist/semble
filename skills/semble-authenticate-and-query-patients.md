---
name: Authenticate and query patients
description: Obtain a Semble x-token and read patient records over the GraphQL API with page-number pagination.
api: https://open.semble.io/graphql
operations: [signIn, patients, patient]
method: generated
generated: '2026-07-24'
source: https://docs.semble.io/docs/authentication/
---

# Authenticate and query patients (Semble)

Use this to authenticate against the Semble public GraphQL API and read patient records.

## 1. Get a token
Either use a long-lived API token created in the Semble app (Settings > API Access > New, with a role assigned), OR call the `signIn` mutation with email/password to get a JWT valid for 12 hours:

```graphql
mutation { signIn(email: "you@clinic.com", password: "***") { token } }
```

Send the token on every request as the `x-token` HTTP header. A missing/invalid token returns `errors[0].extensions.code = UNAUTHENTICATED` ("Missing token.").

## 2. Query patients (paginated)
Semble uses page-number pagination: pass `pagination: { page, pageSize }`, read `data` and `pageInfo.hasMore`.

```graphql
query {
  patients(pagination: { page: 1, pageSize: 25 }) {
    data { id firstName lastName email }
    pageInfo { hasMore }
  }
}
```

Increment `page` until `pageInfo.hasMore` is false.

## 3. Fetch one patient
```graphql
query { patient(id: "PATIENT_ID") { id firstName lastName dateOfBirth } }
```

## Rules
- Stay under 240 requests/minute (rate-limits/semble-rate-limits.yml).
- The token's role scopes which queries/data are reachable; a `FORBIDDEN`/scope error means the role lacks access.
- Re-authenticate at least daily (signIn JWTs expire after 12 hours).
- Handle the GraphQL `errors[]` envelope (errors/semble-error-codes.yml).
