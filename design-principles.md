# Menata Design Principles

Version

0.1 Draft

---

# Introduction

Menata is designed around a small set of fundamental principles.

These principles guide the evolution of the language, its specification, and future machine interpreters.

Whenever a design decision conflicts with these principles, the decision should be questioned.

These principles govern the **language** (`specification/000-language-spec.md` §Language Goals restates them in normative form for the language specifically). Menata Runtime — one Machine Interpreter — has its own, related principle set that governs runtime architecture rather than language design: [`001-design-principles.md`](https://github.com/menata-id/menata-runtime/blob/main/001-design-principles.md) in [menata-id/menata-runtime](https://github.com/menata-id/menata-runtime).

---

# Principle 1

## Business First

Business exists independently of technology.

Technology should adapt to Business Knowledge.

Business Knowledge should never be constrained by implementation technology.

---

# Principle 2

## Knowledge First

Business Knowledge is the primary asset of an organization.

Menata exists to express Business Knowledge.

Machine implementations exist to realize it.

The language always prioritizes Business Knowledge over implementation concerns.

---

# Principle 3

## Declarative

Menata describes **what** a business is.

It does not describe **how** machines should implement it.

Implementation is the responsibility of Machine Interpretation.

---

# Principle 4

## Technology Neutral

Menata does not depend on any programming language, framework, database, AI model, runtime, or implementation technology.

Technology will continue to evolve.

Business Knowledge should remain stable.

---

# Principle 5

## Human Readable

Business Knowledge should be understandable by humans.

Business analysts should be able to read it.

Developers should be able to implement it.

Machines should be able to interpret it.

A language should be understandable before it is executable.

---

# Principle 6

## Machine Readable

Menata is designed to be interpreted consistently by machines.

Machine Interpretation may include:

- AI
- Code Generators
- Compilers
- Interpreters
- Runtime Engines
- Future technologies

The language should remain independent from any particular implementation.

---

# Principle 7

## Composable

Complex Business Knowledge should be constructed from smaller concepts.

Each Grammar has one responsibility.

Grammar should compose rather than overlap.

Composition is preferred over complexity.

---

# Principle 8

## Open Specification

The Menata language specification is open.

Anyone can build machine interpreters, tools, editors, validators, or other implementations, provided they conform to the language specification.

An open language encourages innovation.

---

# Principle 9

## Convention over Configuration

The language provides consistent conventions.

Most Business Knowledge should be expressible without excessive configuration.

Conventions improve readability, interoperability, and machine interpretation.

---

# Principle 10

## Long-term Compatibility

Business Knowledge should outlive implementation technology.

The language should evolve carefully.

Whenever possible, new language versions should preserve compatibility with existing Business Knowledge.

Long-term stability is more valuable than short-term convenience.

---

# Summary

Menata separates Business Knowledge from Machine Interpretation.

```text
Business Reality
        │
        ▼
Business Knowledge
        │
        ▼
Menata
        │
        ▼
Machine Interpretation
        │
        ▼
Application
```

Business Reality is where work happens.

Business Knowledge explains that reality.

Menata expresses Business Knowledge.

Machine Interpretation realizes it.

Applications are one possible outcome.

The language remains stable while implementation technology continues to evolve.
