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

