# 003 — Workflow

Version

0.1 Draft

---

# Purpose

A Workflow describes how a Business Concept progresses through its lifecycle.

It defines the business process by expressing states, transitions, and business behaviors.

Workflow represents how work is performed.

It does not describe how software executes the process.

---

# Definition

A Workflow is composed of one or more States.

Each State may define one or more transitions to another State.

A transition is triggered by an Action.

A transition may also perform one or more business behaviors.

Example

```text
Workflow

Draft

    Submit -> Submitted

Submitted

    Accept -> Accepted

    Reject -> Rejected

Accepted

    Start -> In Progress

In Progress

    Complete -> Completed

Completed

Rejected
```

---

# State

A State represents the current condition of a Business Concept.

Examples

```text
Draft

Submitted

Approved

Rejected

Completed

Cancelled
```

State names should use business terminology.

State names describe business conditions.

They do not describe implementation status.

---

# Transition

A Transition moves an Object from one State to another.

Example

```text
Submit -> Submitted
```

Another example

```text
Approve -> Approved
```

A Transition always belongs to the current State.

Transitions describe business behavior rather than implementation logic.

---

# Behaviors

A Transition may perform one or more business behaviors.

Examples include:

- Notify
- Record
- Generate
- Assign
- Create
- Update

Example

```text
Draft

    Submit -> Submitted

        Notify Design Team

        Record Design Request Register
```

Another example

```text
Review

    Approve -> Completed

        Generate Certificate

        Notify Participant
```

Behaviors describe business intent.

They do not prescribe implementation technology.

---

# Conditions

A Transition may be conditional.

Example

```text
Draft

    Submit -> Submitted

        Notify Design Team
            if Design Type = Poster
```

Conditions describe Business Knowledge.

They do not describe program logic.

---

# Example

```text
Workflow

Draft

    Submit -> Submitted

        Notify Design Team
            if Design Type = Poster

        Record Design Request Register

Submitted

    Accept -> Accepted

    Reject -> Rejected

        Notify Requester

Accepted

    Start -> In Progress

In Progress

    Complete -> Completed

        Notify Requester

Completed

Rejected
```

---

# Principles

A Workflow represents Business Knowledge.

Workflow should describe the business process.

Workflow should remain declarative.

Workflow should remain technology neutral.

Workflow should describe what happens rather than how it is implemented.

---

# Summary

A Workflow defines how a Business Concept progresses through its lifecycle.

It is composed of States, Transitions, Conditions, and Behaviors.

Machine Interpretation is responsible for realizing the Workflow while preserving the Business Knowledge expressed by Menata.
