# Menata

> **A language for representing Business Knowledge.**

Business software has been tightly coupled to implementation technologies for decades.

Programming languages evolve.

Frameworks evolve.

Databases evolve.

User interfaces evolve.

Business Knowledge should not.

**Menata** is a declarative language for representing Business Knowledge independently from implementation technology.

Business Knowledge expressed in Menata can be implemented by one or more Runtime implementations into business applications.

---

> ⚠️ **Research Draft**
>
> Menata is currently an active research project.
>
> The language specification is evolving and **breaking changes are expected** before version **1.0**.
>
> The current focus of this repository is the design of the Menata language.
>
> Feedback, discussions, references, and constructive criticism are welcome.

---

## Why Menata?

Business Knowledge is one of the most valuable assets of an organization.

Unfortunately, it is often embedded inside source code, tightly coupled to programming languages, frameworks, databases, and user interfaces.

As technology evolves, organizations repeatedly rewrite software—not because the business has changed, but because the technology has changed.

Menata separates **Business Knowledge** from **implementation**.

Business Knowledge becomes a long-lived organizational asset.

Technology becomes replaceable.

---

## Vision

Menata is built on a simple belief.

> **Business Knowledge should outlive technology.**

Business Knowledge should:

- be implementation independent,
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

Business Reality represents what actually happens inside an organization.

Business Knowledge represents an organization's understanding of that reality.

Menata provides a formal language for expressing Business Knowledge.

Runtime implementations execute Menata.

Applications become an implementation detail.

---

## Design Principles

Menata is designed around a small set of fundamental principles.

- Business First
- Knowledge First
- Declarative
- Runtime Independent
- Human Readable
- AI Native
- Composable
- Open Specification
- Convention over Configuration
- Long-term Compatibility

The complete design rationale is available in **design-principles.md**.

---

## Documentation

The language specification is developed incrementally.

Current specifications are available in the `specification/` directory.

Each document defines one part of the language.

---

## Roadmap

The long-term vision of the Menata ecosystem includes:

- Language Specification
- Runtime Implementations
- Development Tools
- AI-assisted Authoring
- Reference Applications

---

## Contributing

Menata is currently focused on language design.

Ideas, discussions, critiques, academic references, and design proposals are highly appreciated.

A formal RFC (Request for Comments) process will be introduced as the language matures.

---

## License

Licensed under the Apache License 2.0.

See the LICENSE file for details.
