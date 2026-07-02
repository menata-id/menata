# 006 — View

Version

0.1 Draft

---

# Purpose

A View defines how Business Knowledge is organized and presented for a particular business purpose.

Views help people understand and interact with Business Knowledge.

Views describe presentation intent.

They do not describe user interface implementation.

Machine Interpretation is responsible for realizing Views while preserving their business meaning.

---

# Definition

A View represents one way of presenting an Object.

An Object may define one or more Views.

Each View serves a different business purpose.

Examples include:

- Request Form
- My Requests
- All Requests
- Review Queue
- Calendar
- Dashboard

Views describe what people need to see.

They do not describe how software renders or implements the presentation.

---

# View Name

Every View has a name.

View names should use business terminology.

View names should describe the business purpose rather than the presentation technology.

Good

```text
Request Form

My Requests

Purchase Requests

Employee Directory

Meeting Calendar

Review Queue
```

Avoid

```text
Page01

DashboardComponent

RequestScreen

ListView1
```

---

# Presentation

A View may define its preferred presentation.

Presentation describes how Business Knowledge is intended to be organized.

Examples include:

```text
Form

List

Detail

Summary

Calendar

Timeline

Dashboard

Map
```

Presentation expresses business intent.

Machine Interpretation determines how the presentation is realized.

---

# Multiple Views

An Object may define multiple Views.

Each View may present the same Business Knowledge differently depending on its business purpose.

Example

```text
Views

- Request Form : Form

- My Requests : List

- Request Details : Detail

- Dashboard : Dashboard
```

Different Views may present the same Object without changing its Business Knowledge.

---

# Examples

Design Request

```text
Views

- Request Form : Form

- My Requests : List

- Request Details : Detail

- Dashboard : Dashboard
```

Employee

```text
Views

- Employee Directory : List

- Employee Profile : Detail

- Organization Chart : Dashboard
```

Project

```text
Views

- Project Summary : Summary

- Project Timeline : Timeline

- Project Calendar : Calendar

- Project Location : Map
```

---

# Principles

Views represent Business Knowledge.

Views describe presentation intent.

Views should use business terminology.

Views describe what people need to see.

Views remain declarative.

Views remain technology neutral.

Views should describe business purpose rather than presentation technology.

Machine Interpretation is responsible for realizing Views while preserving their business meaning.

---

# Summary

A View defines how Business Knowledge is organized and presented for a particular business purpose.

An Object may define multiple Views, each serving a different business purpose.

Views remain independent from implementation technology.

Machine Interpretation is responsible for realizing each View while preserving the intended Business Knowledge.
