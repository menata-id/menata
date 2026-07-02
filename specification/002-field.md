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

