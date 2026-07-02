# 001 — Object

Version

0.1 Draft

---

# Purpose

An Object represents a business concept.

It is the primary unit used to describe Business Knowledge in Menata.

Everything expressed in Menata begins with an Object.

Examples include:

- Customer
- Employee
- Purchase Request
- Design Request
- Incident Report
- Meeting
- Asset
- Training

An Object describes a concept in the business domain.

It does not describe database tables, classes, APIs, or implementation details.

---

# Object Structure

An Object may contain one or more Grammar components.

Typical components include:

- Description
- Field
- Relationship
- Workflow
- Constraint
- Permission
- Page

Not every Object requires every component.

Only the Business Knowledge that exists needs to be described.

---

# Object Name

The Object Name identifies the business concept.

Examples

```text
Customer

Purchase Request

Design Request

Incident Report
```

Object names should use business terminology.

Avoid technical or implementation-oriented names.

Good

```text
Purchase Request

Expense Claim

Meeting
```

Avoid

```text
PurchaseRequestEntity

PurchaseRequestTable

PurchaseRequestDTO
```

---

# Description

An Object may include a Description.

The Description explains the purpose of the business concept.

Example

```text
Description

Request for creating design materials.
```

Descriptions exist to help people understand Business Knowledge.

They do not affect Machine Interpretation.

---

# Composition

Objects are composed from Grammar.

For example,

```text
Design Request

Description

...

Information

...

Workflow

...

Constraints

...

Permissions

...

Pages

...
```

The authoring style above is intended for humans.

Machine Interpretation maps these sections to the corresponding Grammar defined by the language specification.

For example,

| Authoring Style | Grammar |
|-----------------|---------|
| Information | Field |
| Constraints | Constraint |
| Pages | Page |

This allows Business Knowledge to remain natural for humans while remaining consistent for Machine Interpretation.

---

# Principles

An Object represents Business Knowledge.

An Object is technology neutral.

An Object is declarative.

An Object describes the business, not its implementation.

---

# Example

```text
Design Request

Description

Request for creating design materials.

Information

- Requester : User
- Design Type : Poster | Thumbnail | Banner 2:1
- Due Date : Date
- Title : Text
- Description : Rich Text

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

Constraints

- Title is required.
- Due Date must be after today.

Permissions

Requester

- Submit

Designer

- Accept
- Reject
- Start
- Complete

Pages

- Request Form : Form
- My Requests : Card
- All Requests : Table
```

---

# Summary

An Object is the highest-level construct in Menata.

It represents a business concept and serves as the container for Business Knowledge.

Objects are composed from Grammar, while the authoring style remains natural and easy for humans to read.

Machine Interpretation is responsible for mapping the authoring style into the formal language grammar.
