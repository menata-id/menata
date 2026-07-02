# 006 — View

Version

0.1 Draft

---

# Purpose

A View defines how Business Knowledge is organized and presented for a particular business purpose.

Views help people interact with Business Knowledge.

They describe presentation intent.

They do not describe user interface implementation.

---

# Definition

A View represents a way of presenting an Object.

An Object may have one or more Views.

Each View serves a different business purpose.

Examples include:

- Request Form
- My Requests
- All Requests
- Dashboard
- Calendar
- Review Queue

Views describe what people need to see.

They do not describe how software renders the interface.

---

# View Name

Every View has a name.

View names should use business terminology.

Examples

```text
Request Form

My Requests

All Requests

Dashboard

Review Queue
```

Avoid implementation-oriented names.

Good

```text
Employee Directory

Purchase Requests

Asset Dashboard

Meeting Calendar
```

Avoid

```text
Page01

DashboardComponent

RequestScreen

ListView1
```

---

# View Type

A View may define its preferred presentation.

Common View Types include:

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

The View Type expresses business intent.

Machine Interpretation determines how it is realized.

---

# Multiple Views

An Object may define multiple Views.

Each View may present the same Business Knowledge differently depending on its purpose.

Example

```text
Views

- Request Form : Form

- My Requests : Card

- All Requests : Table

- Dashboard : Dashboard
```

---

# Examples

Example 1

```text
Views

- Request Form : Form

- My Requests : Card

- All Requests : Table

- Dashboard : Dashboard
```

Example 2

```text
Views

- Employee Directory : Table

- Employee Profile : Form

- Organization Structure : Chart
```

Example 3

```text
Views

- Project Timeline : Timeline

- Project Dashboard : Dashboard

- Project Location : Map
```

---

# Principles

A View represents Business Knowledge.

A View describes presentation intent.

A View remains declarative.

A View remains technology neutral.

A View should describe what users need to see rather than how interfaces are implemented.

---

# Summary

A View defines how Business Knowledge is organized and presented for a particular business purpose.

Multiple Views may exist for the same Object.

Machine Interpretation is responsible for realizing each View while preserving the Business Knowledge expressed by Menata.
