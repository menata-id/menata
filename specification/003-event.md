# 003 — Event

Version

0.1 Draft

---

# Purpose

An Event defines when Business Knowledge should respond.

Events describe business occurrences that trigger one or more business responses.

Events express business intent rather than implementation.

Machine Interpretation is responsible for determining how Events are realized.

---

# Definition

An Event represents something that happens within Business Reality.

Events may originate from business activities, time, dates, external systems, or other business occurrences.

When an Event occurs, Business Knowledge may produce one or more responses.

Examples include:

- Submit
- Approve
- Reject
- Complete
- Payment Received
- User Registered
- Email Received
- Every Day
- Every Monday
- Due Date

Events describe what happens.

They do not describe how software detects or executes those events.

---

# Event Sources

An Event may originate from different sources.

## Business Activity

```text
When Submit

When Approve

When Reject

When Complete
```

---

## Time

```text
Every Day

Every Monday

Every Month
```

---

## Date

```text
When Due Date

When Due Date - 1 Day

When Due Date + 7 Days
```

---

## External

```text
When Payment Received

When Email Received

When Webhook Received
```

An implementation may support additional Event sources while preserving the same Business Knowledge.

