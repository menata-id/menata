# Menata

> **A language for representing Business Knowledge.**

Business software has been tightly coupled to implementation technologies for decades.

Programming languages evolve.

Frameworks evolve.

Databases evolve.

User interfaces evolve.

Business Knowledge should not.

**Menata** is a declarative language for representing Business Knowledge independently from implementation technology.

Business Knowledge written in Menata can be implemented by one or more Runtime implementations into business applications.

---

> ⚠️ **Research Project**
>
> Menata is currently in the **Research Draft** stage.
>
> The language specification is under active development and **breaking changes are expected** before version **1.0**.
>
> The current focus of this repository is **language design**.
>
> Feedback, discussion, references, and constructive criticism are welcome.

---

## Why Menata?

Business Knowledge is one of the most valuable assets of an organization.

Unfortunately, it is often tightly coupled to programming languages, frameworks, databases, and user interfaces.

As technology evolves, organizations repeatedly rewrite software—not because the business has changed, but because the technology has changed.

Menata separates **Business Knowledge** from **implementation**.

Business Knowledge becomes a long-lived asset.

Technology becomes replaceable.

---

## Vision

Menata is built on a simple belief.

> **Business Knowledge should outlive technology.**

Business Knowledge should:

- remain implementation independent,
- be understandable by both humans and AI,
- be reusable across applications,
- evolve independently from runtime technology.

---

## Architecture

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
Runtime
        │
        ▼
Application
```

Menata represents Business Knowledge.

Runtime implementations execute it.

Applications become an implementation detail.

---

## Design Principles

- Business First
- Knowledge Driven
- Declarative
- Runtime Independent
- AI Native

---

## Documentation

The language specification is available in the `specification/` directory.

The specification is developed incrementally through individual grammar documents.

Current work includes the language foundation and core grammar.

---

## Roadmap

- Language Specification
- Runtime
- Tooling
- Reference Applications

---

## Contributing

Menata is currently focused on language design.

Ideas, discussions, critiques, academic references, and design proposals are highly appreciated.

---

## License

Licensed under the Apache License 2.0.
