# 004 — Constraint

Version

0.1 Draft

---

# Purpose

A Constraint defines a business rule that must always be satisfied.

Constraints express Business Knowledge by describing what must always be true.

They define the rules that govern an Object and its interactions with other Objects.

They do not describe how software enforces those rules.

Machine Interpretation is responsible for enforcing Constraints while preserving their business meaning.

---

# Definition

A Constraint represents a business rule.

Constraints may apply to an Object, its Fields, its Events, or its interaction with other Objects.

Examples include:

- Title is required.

- Amount must be greater than zero.

- Purchase Orders above 50,000,000 require Director Approval.

- Salary must be visible only to HR.

- Medical records must remain confidential.

- High Priority must be completed within 2 days.

- Employees may submit only one leave request per day.

Constraints express Business Knowledge.

They describe business intent rather than implementation.

---

# Conditional Constraints

A Constraint may apply only under certain conditions.

Conditional Constraints express Business Knowledge.

They do not describe program logic.

Examples

```text
Attachment is required.

    if Design Type = Banner
```

```text
Manager Approval is required.

    if Amount exceeds 10,000,000
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

- Due Date must be after today.

- Attachment is required.

    if Design Type = Banner
```

Purchase Request

```text
Constraints

- Amount must be greater than zero.

- Purchase Requests above 50,000,000 require Director Approval.

- Requester must not be the Approver.
```

Employee

```text
Constraints

- Salary must remain confidential.

- Salary must be visible only to HR and the Employee.
```

Medical Record

```text
Constraints

- Medical records must remain confidential.

- Medical records must comply with applicable privacy regulations.
```

Reward Point

```text
Constraints

- Purchase information may be used for reward calculation.

- Purchase details must remain confidential.
```

---

# Principles

Constraints represent Business Knowledge.

Constraints describe business rules.

Constraints should use business terminology.

Constraints describe what must always be true.

Constraints may govern an Object, its Fields, its Events, or its interaction with other Objects.

Constraints remain declarative.

Constraints remain technology neutral.

Constraints describe business intent rather than implementation.

Machine Interpretation is responsible for enforcing Constraints while preserving their business meaning.

---

# Summary

A Constraint represents a business rule.

Constraints express Business Knowledge by defining what must always be true.

They may govern an Object, its Fields, its Events, or its interaction with other Objects.

Constraints remain independent from implementation technology.

Machine Interpretation is responsible for enforcing Constraints while preserving the intended business meaning.
