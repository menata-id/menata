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

