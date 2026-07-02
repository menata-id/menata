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

---

# Event Responses

An Event may produce one or more business responses.

Business responses describe what the business intends to happen after an Event occurs.

Examples include:

- Notify
- Create
- Update
- Generate
- Record
- Assign
- Status Submitted

Menata does not define a fixed set of responses.

Business responses are expressed using natural business language.

Machine Interpretation is responsible for realizing those responses.

---

# Conditions

An Event may execute conditionally.

Conditions describe when a business response should occur.

Example

```text
When Submit

    if Design Type = Poster

        Notify Design Team
```

Another example

```text
Every Day

    if Status = In Progress

    if Due Date < Today

        Notify Requester
```

Conditions describe Business Knowledge.

They do not describe implementation logic.

---

# Examples

Design Request

```text
Events

When Submit

    Status Submitted

    Notify Design Team

    Record Design Request Register

When Accept

    Status Accepted

When Reject

    Status Rejected

When Start

    Status In Progress

When Complete

    Status Completed

    Notify Requester
```

Reminder

```text
Events

Every Day 08:00

    Notify User
```

Invoice

```text
Events

When Payment Received

    Status Paid

    Notify Finance
```

Weekly Report

```text
Events

Every Monday

    Generate Weekly Report
```

