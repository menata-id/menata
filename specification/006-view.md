# 006 — Page

Version

0.1 Draft

---

# Purpose

A Page defines how Business Knowledge is presented to users.

Pages organize Business Information for different business activities.

They describe presentation intent.

They do not describe user interface implementation.

---

# Definition

A Page represents a business-facing screen.

Examples include:

- Request Form
- My Requests
- Dashboard
- Review Queue
- Employee Directory
- Purchase History

Pages describe what users need to see.

They do not describe how software renders the interface.

---

# Page Name

Every Page has a name.

Page names should use business terminology.

Examples

```text
Request Form

My Requests

Dashboard

Review Queue

Design Queue
```

Avoid implementation-oriented names.

Good

```text
Employee Directory

Purchase Requests

Asset Dashboard
```

Avoid

```text
Page01

DashboardComponent

RequestScreen

tbl_request
```

---

# Presentation

A Page may define its preferred presentation.

Common presentations include:

```text
Form

Card

Table

Dashboard

Chart

Calendar

Timeline

Map
```

Presentation expresses business intent.

Machine Interpretation determines how it is implemented.

---

# Examples

```text
Pages

- Request Form : Form

- My Requests : Card

- All Requests : Table

- Dashboard : Dashboard
```

Another example

```text
Pages

- Employee Directory : Table

- Organization Chart : Chart

- Company Calendar : Calendar
```

---

# Multiple Pages

An Object may have multiple Pages.

Each Page serves a different business purpose.

Example

```text
Pages

- Request Form : Form

- My Requests : Card

- All Requests : Table

- Dashboard : Dashboard

- Request Trend : Chart
```

---

# Principles

Pages represent Business Knowledge.

Pages describe presentation intent.

Pages remain declarative.

Pages remain technology neutral.

Pages should describe what users need rather than how interfaces are built.

---

# Summary

Pages define how Business Knowledge is presented to users.

They organize Business Information according to business needs while remaining independent from implementation technology.

Machine Interpretation is responsible for realizing Pages using appropriate technologies.
