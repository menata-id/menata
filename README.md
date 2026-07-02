# Menata

> **A language that defines the boundary between Business Knowledge and Machine Interpretation.**

Every organization runs on Business Knowledge.

People know how work gets done.

They know the rules.

They know the decisions.

They know the workflows.

They know the exceptions.

The knowledge already exists.

Yet only a small portion of that knowledge ever becomes software.

Not because the business is unimportant.

But because software is expensive to build, difficult to change, and tightly coupled to implementation technology.

**Menata exists to change that.**

Menata is a declarative language for expressing Business Knowledge independently from programming languages, frameworks, databases, and user interfaces.

Business Knowledge expressed in Menata can be interpreted by machines and transformed into business applications.

---

> ⚠️ **Research Draft**
>
> Menata is an active research project.
>
> The language specification is evolving and **breaking changes are expected** before version **1.0**.
>
> The current focus of this repository is language design.
>
> Feedback, discussions, critiques, and academic references are highly appreciated.

---

## Why Menata?

Every business activity contains Business Knowledge.

If people know how to perform the work, the knowledge already exists.

Unfortunately, turning that knowledge into software is still expensive, slow, and highly dependent on implementation technology.

As a result, organizations are forced to prioritize.

Core systems are built first.

Many other business functions wait.

Sometimes forever.

The problem is not the lack of Business Knowledge.

The problem is the gap between Business Knowledge and software.

Menata aims to bridge that gap.

---

## Vision

We believe that every Business Knowledge deserves implementation.

Business Knowledge should:

- be independent from implementation technology,
- be understandable by both humans and machines,
- be reusable across applications,
- evolve independently from implementation technology,
- remain a long-term organizational asset.

Software should evolve because Business Knowledge evolves.

Not because technology changes.

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
Machine Interpretation
        │
        ▼
Application
```

Business Reality is where work actually happens.

Business Knowledge explains how that work is performed.

Menata provides a formal language for expressing that knowledge.

Machine Interpretation transforms Menata into executable systems.

Applications become one possible realization of Business Knowledge.

---

## Design Principles

Menata is designed around several fundamental principles.

- Business First
- Knowledge First
- Declarative
- Runtime Independent
- Human Readable
- Technology Neutral
- Composable
- Open Specification
- Convention over Configuration
- Long-term Compatibility

The complete rationale is available in `design-principles.md`.

---

## Documentation

The language specification is developed incrementally.

Each document defines one concept of the language.

See the `specification/` directory for the complete specification.

---

## Long-term Vision

The Menata ecosystem is expected to include:

- Language Specification
- Machine Interpreters
- Development Tools
- AI-assisted Authoring
- Reference Applications

The language comes first.

Everything else is built on top of it.

---

## Contributing

Menata is currently focused on language design.

Ideas, discussions, critiques, academic references, and design proposals are highly appreciated.

A formal RFC (Request for Comments) process will be introduced as the language matures.

---

## License

Licensed under the Apache License 2.0.

See the LICENSE file for details.
