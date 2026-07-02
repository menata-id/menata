# 004 — Constraint

Version

0.1 Draft

---

# Purpose

A Constraint defines a rule that limits or validates Business Knowledge.

Constraints describe conditions that must be satisfied for a Business Concept to be considered valid.

Constraints represent business rules.

They do not describe implementation logic.

---

# Definition

A Constraint expresses a business requirement.

Examples include:

- Title is required.
- Due Date must be after today.
- Priority is required.
- Amount must be greater than zero.
- A request must have at least one attachment.
- High Priority must be completed within 2 days.

Constraints describe what must be true.

They do not describe how software enforces the rule.

---

# Required Information

A Constraint may require Business Information.

Examples

```text
Constraints

- Title is required.

- Description is required.

- Due Date is required.
```

---

# Value Validation

A Constraint may validate values.

Examples

```text
Constraints

- Amount must be greater than zero.

- Due Date must be after today.

- Quantity must be at least 1.

- Discount must not exceed 20%.
```

---

# Conditional Constraint

A Constraint may apply only under certain conditions.

Examples

```text
Constraints

- Attachment is required
    if Design Type = Banner 2:1
```

Another example

```text
Constraints

- High Priority must be completed within 2 days.
```

Another example

```text
Constraints

- Manager Approval is required
    if Amount exceeds 10,000,000.
```

---

# Business Policy

Constraints may express organizational policies.

Examples

```text
Constraints

- Employees may only submit one leave request per day.

- Overtime requests must be submitted before the end of the working day.

- Purchase Requests above 50,000,000 require Director Approval.
```

Business policies are Business Knowledge.

Their implementation is determined by Machine Interpretation.

---

# Example

```text
Constraints

- Title is required.

- Description is required.

- Due Date is required.

- Due Date must be after today.

- Attachment is required
    if Design Type = Banner 2:1

- High Priority must be completed within 2 days.
```

---

# Principles

Constraints represent Business Knowledge.

Constraints describe business requirements.

Constraints remain declarative.

Constraints remain technology neutral.

Constraints should describe what must be true rather than how software validates it.

---

# Summary

Constraints define the business rules that govern an Object.

They validate Business Knowledge and express organizational policies.

Machine Interpretation is responsible for enforcing Constraints while preserving their business meaning.
