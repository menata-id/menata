# 004 — Constraint

Version

0.1 Draft

---

# Purpose

A Constraint defines a business rule that must always be satisfied.

Constraints express the requirements that govern Business Knowledge.

They describe what must be true.

They do not describe how software enforces those requirements.

Machine Interpretation is responsible for enforcing Constraints while preserving their business meaning.

---

# Definition

A Constraint represents a business requirement.

Examples include:

- Title is required.
- Due Date must be after today.
- Amount must be greater than zero.
- High Priority must be completed within 2 days.
- Purchase Requests above 50,000,000 require Director Approval.

Constraints express Business Knowledge.

They do not describe implementation logic.

---

# Constraint Types

Constraints may express different kinds of business requirements.

Examples include:

Required Information

```text
Title is required.

Description is required.

Due Date is required.
```

Value Rules

```text
Amount must be greater than zero.

Quantity must be at least 1.

Discount must not exceed 20%.
```

Time Rules

```text
High Priority must be completed within 2 days.

Invoices must be paid within 30 days.
```

Business Policies

```text
Employees may submit only one leave request per day.

Purchase Requests above 50,000,000 require Director Approval.
```

---

# Conditional Constraints

A Constraint may apply only under certain conditions.

Conditional Constraints express Business Knowledge.

They do not describe program logic.

Examples

```text
Attachment is required.

    if Design Type = Banner 2:1
```

```text
Manager Approval is required.

    if Amount exceeds 10,000,000.
```

```text
Response must be completed within 24 hours.

    if Priority = High
```

---

# Examples

Design Request

```text
Constraints

- Title is required.

- Description is required.

- Due Date is required.

- Due Date must be after today.

- Attachment is required.

    if Design Type = Banner 2:1
```

Purchase Request

```text
Constraints

- Amount must be greater than zero.

- Purchase Requests above 50,000,000 require Director Approval.

- Requester must not be the Approver.
```

Leave Request

```text
Constraints

- Start Date must be before End Date.

- Employees may submit only one leave request per day.

- Manager Approval is required.

    if Leave Type = Annual Leave
```

---

# Principles

Constraints represent Business Knowledge.

Constraints describe business requirements.

Constraints should use business terminology.

Constraints describe what must always be true.

Constraints remain declarative.

Constraints remain technology neutral.

Constraints should describe business intent rather than implementation.

Machine Interpretation is responsible for enforcing Constraints while preserving their business meaning.

---

# Summary

A Constraint represents a business rule.

Constraints define the requirements that govern an Object.

Constraints express Business Knowledge by describing what must always be true.

They remain independent from implementation technology.

Machine Interpretation is responsible for enforcing Constraints while preserving the intended business meaning.
