# 002 — Field

Version

0.1 Draft

---

# Purpose

A Field represents a single piece of Business Information.

Fields describe the information required to understand, perform, or record a Business Concept.

Every Field contributes one piece of Business Knowledge.

---

# Definition

A Field represents one business value.

Examples include:

- Customer Name
- Due Date
- Title
- Description
- Quantity
- Price
- Status

A Field describes business information.

It does not describe database columns.

It does not describe programming variables.

It does not describe implementation details.

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

---

# Field Type

A Field may define a type.

Common types include:

```text
Text

Rich Text

Number

Boolean

Date

Date Time

Duration

Currency

Percentage

Email

Phone

URL

User

File

Image

Location
```

The language may evolve to support additional types.

---

# Value Lists

Some Fields contain a predefined set of values.

Example

```text
Design Type

- Poster
- Thumbnail
- Banner 2:1
```

Another example

```text
Priority

- Low
- Normal
- High
- Urgent
```

---

# Optional Information

A Field may be optional.

Example

```text
Attachment : File (Optional)
```

If omitted, a Field is interpreted according to the rules defined by the Object.

---

# Examples

```text
Information

- Requester : User

- Design Type

    - Poster
    - Thumbnail
    - Banner 2:1

- Due Date : Date

- Title : Text

- Description : Rich Text

- Attachment : File (Optional)
```

Another example

```text
Information

- Employee : User

- Leave Type

    - Annual Leave
    - Sick Leave
    - Marriage Leave

- Start Date : Date

- End Date : Date

- Reason : Rich Text
```

---

# Principles

A Field represents Business Information.

Field names should use business terminology.

Field definitions should remain technology neutral.

Fields describe information, not implementation.

---

# Summary

A Field represents a single piece of Business Information.

Fields are combined to describe the information required by a Business Concept.

Together, Fields form the information model of an Object while remaining independent from implementation technology.
