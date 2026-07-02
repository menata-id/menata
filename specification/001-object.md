# 001 — Object

Version

0.1 Draft

---

# Purpose

An Object represents a Business Concept.

Objects are the primary building blocks of Business Knowledge.

Everything expressed in Menata belongs to an Object.

---

# Definition

An Object represents something that exists within a Business Reality.

An Object is not limited to documents or database entities.

An Object may represent any Business Concept that is meaningful to an organization.

Examples include:

- User
- Customer
- Employee
- Department
- Asset
- Project
- Purchase Request
- Design Request
- Meeting
- Holiday
- Currency
- Reminder
- Schedule

Objects describe the business, not the implementation.

---

# Identity

Every Object has a unique name.

Object names should use business terminology.

Good examples

```text
Purchase Request

Design Request

Employee

Meeting

Holiday
```

Avoid implementation-oriented names.

```text
TblEmployee

UserEntity

RequestModel

DesignDTO
```

---

# Responsibility

Each Object has one primary responsibility.

An Object should represent one Business Concept.

If an Object attempts to represent multiple concepts, it should be divided into smaller Objects.

Good

```text
Employee

Department

Project
```

Avoid

```text
EmployeeDepartmentProject
```

---

# Composition

An Object may contain one or more of the following language components.

- Fields
- Events
- Constraints
- Permissions
- Views

Only the components required to express the Business Knowledge should be defined.

Not every Object requires every component.

Examples

A simple Object

```text
Holiday

Fields

- Name : Text
- Date : Date
```

A business process

```text
Purchase Request

Fields

- Request Number : Text
- Requester : User
- Amount : Money

Events

When Submit

    Status Submitted

When Approve

    Status Approved

Constraints

- Amount must be greater than zero.

Permissions

Requester

- Submit

Manager

- Approve

Views

- Request Form : Form
- My Requests : Card
```

---

# Relationships

Objects may reference other Objects through Fields.

Example

```text
Purchase Request

Fields

- Requester : User
- Department : Department
```

Relationships are expressed naturally through Fields.

No separate relationship definition is required.

---

# Principles

An Object represents one Business Concept.

An Object should use business terminology.

An Object should remain independent from implementation technology.

An Object should contain only the language components necessary to express its Business Knowledge.

---

# Summary

An Object is the primary unit of Business Knowledge in Menata.

Objects represent Business Concepts.

They are composed of language components such as Fields, Events, Constraints, Permissions, and Views.

Machine Interpretation is responsible for realizing Objects while preserving the Business Knowledge expressed by Menata.
