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

