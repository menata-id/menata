# Menata

> **A language for representing Business Knowledge.**

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

Business Knowledge expressed in Menata can be implemented by one or more Runtime implementations into business applications.

---

> ⚠️ **Research Draft**
>
> Menata is currently an active research project.
>
> The language specification is evolving and **breaking changes are expected** before version **1.0**.
>
> The current focus of this repository is language design.
>
> Feedback, discussions, references, and constructive criticism are welcome.

---

## Why Menata?

Software development is expensive.

Business change is continuous.

Organizations constantly make difficult decisions about which applications deserve to be built.

Core business systems usually come first.

Other business functions often wait.

Sometimes forever.

Yet every business activity already contains Business Knowledge.

If people know how to perform the work, the knowledge already exists.

The problem is no longer creating Business Knowledge.

The problem is turning Business Knowledge into software.

Menata aims to make that transformation significantly simpler.

---

## Vision

We believe that every Business Knowledge deserves software.

Business Knowledge should:

- be independent from implementation technology,
- be understandable by both humans and AI,
- be reusable across applications,
- evolve independently from runtime implementations,
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
Runtime
        │
        ▼
Application
```

Business Reality is where work actually happens.

Business Knowledge explains how that work is performed.

Menata provides a formal language for expressing that knowledge.

Runtime implementations transform the language into executable applications.

Applications become an implementation detail.

---

## Design Principles

Menata is built around several fundamental principles.

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

A complete explanation of these principles is available in **design-principles.md**.

---

## Documentation

The language specification is developed incrementally.

Each document defines one concept of the language.

The current specification is available in the `specification/` directory.

---

## Long-term Vision

The Menata ecosystem is expected to include:

- Language Specification
- Runtime Implementations
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
