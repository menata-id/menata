# 003 — Event

Version

0.1 Draft

---

# Purpose

An Event defines when Business Knowledge should respond.

Events describe business occurrences that trigger one or more business actions.

Events may originate from business activities, time, external systems, or other business events.

They describe business intent rather than implementation.

---

# Definition

An Event represents something that happens in the business.

When an Event occurs, one or more business actions may be performed.

An Event may also change the state of an Object.

Examples include:

- Submit
- Approve
- Reject
- Complete
- Every Day
- Every Monday
- Due Date
- Payment Received
- Email Received

Events describe what happens.

They do not describe how software detects or executes them.

---

# Event Sources

An Event may originate from different sources.

Business Activity

```text
When Submit

When Approve

When Reject
```

Time

```text
Every Day

Every Monday

Every Month
```

Date

```text
When Due Date

When Due Date - 1 Day

When Due Date + 7 Days
```

External

```text
When Email Received

When Payment Received

When Webhook Received
```

---

# Behaviors

An Event may perform one or more business behaviors.

Examples include:

- Notify
- Create
- Generate
- Record
- Assign
- Update

Example

```text
When Submit

    Status Submitted

    Notify Design Team

    Record Design Request Register
```

Another example

```text
Every Monday

    Generate Weekly Report
```

Another example

```text
When Due Date - 1 Day

    Notify Requester
```

---

# Conditions

An Event may execute only when one or more conditions are satisfied.

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

Conditions express Business Knowledge.

They do not describe program logic.

---

# State Changes

An Event may change the state of an Object.

Example

```text
When Submit

    Status Submitted
```

Another example

```text
When Approve

    Status Approved
```

State changes are optional.

Not every Event changes the Object.

---

# Object Interaction

An Event may interact with other Objects.

Example

```text
When Approved

    Create Purchase Order
```

Another example

```text
When Completed

    Create Certificate

    Notify Participant
```

Another example

```text
When Payment Received

    Update Invoice

    Notify Finance
```

Events may create, update, or notify other Business Objects.

The implementation is determined by Machine Interpretation.

---

# Examples

Design Request

```text
When Submit

    Status Submitted

    Notify Design Team
        if Design Type = Poster

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

Daily Reminder

```text
Every Day

    if Status = In Progress

    if Due Date < Today

        Notify Requester
```

Weekly Report

```text
Every Monday

    Generate Weekly Report
```

Invoice

```text
When Payment Received

    Status Paid

    Notify Finance
```

---

# Principles

Events represent Business Knowledge.

Events describe when Business Knowledge responds.

Events remain declarative.

Events remain technology neutral.

Events describe business intent rather than implementation.

---

# Summary

An Event represents something that happens in the business.

Events may trigger business behaviors, change the state of an Object, or interact with other Business Objects.

Machine Interpretation is responsible for realizing Events while preserving the Business Knowledge expressed by Menata.
