# 005 — Permission

Version

0.1 Draft

---

# Purpose

A Permission defines which business roles may perform Events.

Permissions express business responsibilities and authority.

They describe who may perform business activities.

They do not describe authentication, authorization mechanisms, or security implementation.

Machine Interpretation is responsible for enforcing Permissions while preserving their business meaning.

---

# Definition

A Permission assigns one or more Events to a business role.

Permissions describe organizational responsibility.

They do not describe user accounts, identity management, or implementation technology.

Examples include:

- Requester may Submit.
- Designer may Accept.
- Manager may Approve.
- Finance may Verify Payment.

---

# Business Roles

Permissions are assigned to business roles.

Role names should use business terminology.

Examples

```text
Requester

Designer

Reviewer

Manager

Finance

Administrator
```

Business roles represent organizational responsibility.

They do not represent individual users.

---

# Event Permissions

A business role may be permitted to perform one or more Events.

Permissions describe business authority.

They do not describe how authorization is implemented.

Example

```text
Permissions

Requester

- Submit

Designer

- Accept
- Reject
- Start
- Complete
```

Another example

```text
Permissions

Manager

- Approve

Finance

- Verify Payment
- Record Payment
```

A business role may be permitted to perform the same Event as another role.

Example

```text
Permissions

Requester

- View

Manager

- View

Administrator

- View
```

Machine Interpretation determines how Permissions are enforced.

---

# Examples

Design Request

```text
Permissions

Requester

- Submit

Designer

- Accept
- Reject
- Start
- Complete

Manager

- Approve
```

Purchase Request

```text
Permissions

Requester

- Submit

Manager

- Approve

Finance

- Verify Payment

Procurement

- Create Purchase Order
```

Leave Request

```text
Permissions

Employee

- Submit

Manager

- Approve

HR

- Record Leave
```

---

# Principles

Permissions represent Business Knowledge.

Permissions describe organizational responsibility.

Permissions should use business terminology.

Permissions define which business roles may perform Events.

Permissions remain declarative.

Permissions remain technology neutral.

Permissions describe business authority rather than implementation.

Machine Interpretation is responsible for enforcing Permissions while preserving their business meaning.

---

# Summary

A Permission defines which business roles may perform Events.

Permissions express organizational responsibility independently of implementation technology.

They remain focused on Business Knowledge rather than authentication or authorization mechanisms.

Machine Interpretation is responsible for enforcing Permissions while preserving the intended business meaning.
