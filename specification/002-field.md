# 002 — Field

Version

0.1 Draft

---

# Purpose

A Field represents a single piece of Business Information.

Fields describe the information required to understand, perform, or record a Business Concept.

Each Field contributes one piece of Business Knowledge.

Together, Fields describe the information of an Object.

---

# Definition

A Field represents one business value.

Examples include:

- Customer Name
- Employee
- Due Date
- Title
- Description
- Quantity
- Price
- Status

Fields describe Business Information.

They do not describe database columns.

They do not describe programming variables.

They do not describe implementation details.

Fields belong to an Object.

An Object may contain one or more Fields.

---

# Field Name

Every Field has a name.

Field names should use business terminology.

Good

```text
Customer Name

Due Date

Design Type

Title

Description
```

Avoid

```text
customer_name

txtCustomer

fld001

design_type_id
```

Field names should describe the Business Information rather than implementation details.

---

# Field Type

A Field may define a type.

Types describe the kind of Business Information represented by the Field.

Common types include:

```text
Text

Rich Text

Number

Money

Boolean

Date

Time

Date Time

Duration

User

File
```

The language may evolve to support additional types.

---

# Object References

A Field may reference another Object.

Object references describe relationships naturally as part of Business Information.

No separate Relationship Grammar is required.

Examples

```text
Requester : User

Manager : User

Department : Department

Company : Organization
```

The referenced Object remains an independent Business Concept.

Machine Interpretation determines how Object references are realized.

---

# Value Lists

Some Fields contain a predefined set of business values.

Example

```text
Design Type : Poster | Thumbnail | Banner 2:1
```

Another example

```text
Priority : Low | Normal | High | Urgent
```

Value Lists describe Business Knowledge.

They do not prescribe how values are stored or implemented.

---

# Examples

Example 1

```text
Fields

- Requester : User

- Design Type : Poster | Thumbnail | Banner 2:1

- Due Date : Date

- Title : Text

- Description : Rich Text

- Attachment : File
```

Example 2

```text
Fields

- Employee : User

- Department : Department

- Leave Type : Annual Leave | Sick Leave | Marriage Leave

- Start Date : Date

- End Date : Date

- Reason : Rich Text
```

---

# Principles

A Field represents one piece of Business Information.

Field names should use business terminology.

Fields should describe Business Information rather than implementation.

Fields should remain technology neutral.

Fields may reference other Objects.

Fields should not describe business behavior.

Business behavior belongs to Events.

Business rules belong to Constraints.

---

# Summary

A Field represents a single piece of Business Information.

Fields describe the information required by an Object.

Fields may represent simple values, predefined value lists, or references to other Objects.

Together, Fields describe the Business Information of an Object while remaining independent from implementation technology.
