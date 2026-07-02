# 005 — Permission

Version

0.1 Draft

---

# Purpose

A Permission defines who is allowed to perform business actions.

Permissions express business responsibilities and authority.

They describe access to Business Knowledge.

They do not describe security implementation.

---

# Definition

A Permission assigns one or more Actions to a business role.

Examples include:

- Requester may submit a request.
- Designer may accept a request.
- Manager may approve a request.
- Administrator has full access.

Permissions describe business responsibilities.

They do not describe authentication, authorization mechanisms, or security technology.

---

# Roles

Permissions are assigned to business roles.

Examples

```text
Requester

Designer

Reviewer

Manager

Administrator
```

Role names should use business terminology.

They represent responsibilities within the business.

---

# Actions

Each role may perform one or more Actions.

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

- Verify
- Pay
```

Permissions describe business capability.

They do not describe user accounts or identity systems.

---

# Full Access

A role may be granted unrestricted access.

Example

```text
Permissions

Administrator

- Full Access
```

The meaning of Full Access is determined by Machine Interpretation.

---

# Example

```text
Permissions

Requester

- Submit

Designer

- Accept
- Reject
- Start
- Complete

Reviewer

- Approve
- Revision

Administrator

- Full Access
```

---

# Principles

Permissions represent Business Knowledge.

Permissions describe business responsibility.

Permissions remain declarative.

Permissions remain technology neutral.

Permissions should describe who may perform an Action rather than how access is implemented.

---

# Summary

Permissions define which business roles may perform business actions.

They express organizational responsibility while remaining independent from implementation technology.

Machine Interpretation is responsible for enforcing Permissions while preserving their business meaning.
