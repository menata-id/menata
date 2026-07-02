# 001 — Object

Version

0.1 Draft

---

# Purpose

An Object represents a Business Concept.

Everything expressed in Menata begins with an Object.

An Object provides the context for organizing Business Knowledge.

It is the highest-level construct of the language.

---

# Definition

An Object describes something that exists in a business.

Examples include:

- Customer
- Employee
- Supplier
- Product
- Asset
- Purchase Request
- Design Request
- Incident Report
- Training
- Meeting

An Object describes the business.

It does not describe software.

It does not describe databases.

It does not describe programming languages.

It does not describe user interfaces.

---

# Object Name

Every Object has a name.

The Object Name should use the terminology naturally used by the business.

Examples

```text
Customer

Purchase Request

Design Request

Incident Report
```

Avoid implementation-oriented names.

Good

```text
Customer

Meeting

Expense Claim

Purchase Request
```

Avoid

```text
CustomerEntity

PurchaseRequestTable

PurchaseRequestDTO

tbl_customer
```

---

# Description

An Object may include a Description.

The Description explains the purpose of the Business Concept.

Example

```text
Description

Request for creating design materials.
```

Descriptions improve readability.

They do not change the meaning of Business Knowledge.

---

# Composition

An Object is composed from smaller language constructs.

Typical constructs include:

- Field
- Relationship
- Workflow
- Constraint
- Permission
- Page

An Object only contains the constructs necessary to describe its Business Knowledge.

Simple business concepts may require only a few constructs.

More complex business concepts may require many.

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

        Notify Design Team
            if Design Type = Poster

        Record Design Request Register

Submitted

    Accept -> Accepted

    Reject -> Rejected

Accepted

    Start -> In Progress

In Progress

    Complete -> Completed

        Notify Requester

Completed

Rejected

Constraints

- Title is required.
- Description is required.
- Due Date is required.
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
- Dashboard : Dashboard
```

The example above represents one Object.

It describes a complete Business Concept independently from implementation technology.

---

# Principles

An Object represents Business Knowledge.

An Object should use business terminology.

An Object should remain declarative.

An Object should remain technology neutral.

An Object should describe the business rather than its implementation.

---

# Summary

An Object is the primary building block of Menata.

Every Business Concept is represented as an Object.

Business Knowledge is organized through Objects.

Objects are later composed into complete Business Knowledge using the language constructs defined by the Menata Specification.
