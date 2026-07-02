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

