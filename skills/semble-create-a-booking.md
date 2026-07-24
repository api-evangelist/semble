---
name: Create a booking
description: Check availability and create a patient appointment (booking) via the Semble GraphQL API.
api: https://open.semble.io/graphql
operations: [availabilities, bookings, createBooking]
method: generated
generated: '2026-07-24'
source: https://docs.semble.io/docs/API/mutations/create-booking/
---

# Create a booking (Semble)

Use this to schedule an appointment for a patient.

## 1. Authenticate
Send a role-scoped token in the `x-token` header (see semble-authenticate-and-query-patients).

## 2. Find open slots
Query available times for the doctor/appointment type before booking:

```graphql
query {
  availabilities(pagination: { page: 1, pageSize: 50 }) {
    data { id start end doctor { id } }
    pageInfo { hasMore }
  }
}
```

## 3. Create the booking
```graphql
mutation {
  createBooking(bookingData: {
    patient: "PATIENT_ID"
    doctor: "DOCTOR_ID"
    start: "2026-08-01T09:00:00Z"
    end: "2026-08-01T09:30:00Z"
    appointmentId: "APPOINTMENT_TYPE_ID"
  }) {
    data { id start end }
    error
  }
}
```

## 4. Confirm
Re-read with `bookings` (paginated) to verify the appointment landed.

## Rules
- Semble does not document idempotency keys — guard against double-submitting the same booking (conventions/semble-conventions.yml).
- Respect the 240 req/min ceiling.
- Field names may vary by schema version; confirm exact input fields against the authenticated schema / release notes before writing.
- Handle the GraphQL `errors[]` envelope and any `error` field on the mutation payload.
