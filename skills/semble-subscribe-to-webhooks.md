---
name: Subscribe to webhooks
description: Register and manage outbound event webhooks for a Semble practice via GraphQL.
api: https://open.semble.io/graphql
operations: [webhooks, createWebhookSubscription, updateWebhookSubscription, deleteWebhookSubscription]
method: generated
generated: '2026-07-24'
source: https://docs.semble.io/docs/API/queries/webhooks/
---

# Subscribe to webhooks (Semble)

Use this to receive event-driven updates (patients, bookings, invoices, etc.) instead of polling.

## 1. Authenticate
Send a role-scoped token in the `x-token` header.

## 2. List existing subscriptions
```graphql
query {
  webhooks {
    data { id url events enabled }
    pageInfo { hasMore }
  }
}
```

## 3. Create a subscription
Register your HTTPS delivery URL and the events you want:

```graphql
mutation {
  createWebhookSubscription(webhookData: {
    url: "https://your-app.example.com/semble/webhook"
    events: ["<event-name>"]
  }) {
    data { id url events }
    error
  }
}
```

The concrete event enum is defined in the (auth-gated) GraphQL schema — introspect it or check the authenticated Webhooks guide to get exact event names.

## 4. Update / delete
Use `updateWebhookSubscription` to change the URL or event set, `deleteWebhookSubscription` to remove one.

## Rules
- Serve the delivery endpoint over HTTPS and respond 2xx quickly.
- Verify authenticity per Semble's documented signing scheme (see the authenticated Webhooks guide; asyncapi/semble-webhooks.yml).
- Handle the GraphQL `errors[]` envelope; respect the 240 req/min management-call ceiling.
