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

Menata is the foundation for **Knowledge-Defined Software**.

---

> ⚠️ **Research Project**
>
> Menata is currently in the **Research Draft** stage.
>
> The language specification is under active development and **breaking changes are expected** before version **1.0**.
>
> The current focus of this repository is **language design**, not runtime implementation.
>
> Feedback, discussions, references, and constructive criticism are welcome.

---

# Why Menata?

Business Knowledge is one of the most valuable assets of an organization.

Unfortunately, Business Knowledge is often tightly coupled to programming languages, frameworks, databases, and user interfaces.

As technology evolves, organizations repeatedly rewrite applications—not because the business has changed, but because the technology has changed.

Menata separates **Business Knowledge** from **implementation**.

Business Knowledge becomes a long-lived asset.

Technology becomes replaceable.

---

# Vision

Business Knowledge should outlive technology.

Business Knowledge should be understandable by both humans and AI.

Business Knowledge should be reusable.

Business Knowledge should be implementation independent.

Business Knowledge should become a first-class engineering artifact.

---

# Core Philosophy

Menata follows several fundamental principles.

- Business First
- Knowledge Driven
- Declarative
- Runtime Independent
- Storage Independent
- Renderer Independent
- AI Native
- Composable
- Extensible
- Backward Compatible

---

# Architecture

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
        │
        ▼
User Experience
```

Business Reality represents what actually happens inside an organization.

Business Knowledge represents organizational understanding of that reality.

Menata provides a formal language for representing Business Knowledge.

Runtime implementations execute Menata definitions.

Applications are generated or implemented from Menata.

---

# Language

Menata represents Business Knowledge using a collection of Core Grammar.

Current Core Grammar:

- Object
- Field
- Relationship
- Action
- Interaction
- Workflow
- Rule
- View
- Dashboard
- Permission
- Automation
- Policy

Each Grammar has a single responsibility.

Together they describe Business Knowledge.

---

# Ecosystem

The Menata ecosystem is expected to evolve into several specifications and implementations.

## Language Specification

Defines the Menata language.

Current repository focus.

---

## Composition Specification *(Planned)*

Defines how Business Knowledge is composed into complete business solutions.

Planned concepts include:

- Recipe
- Workspace
- Application

---

## Runtime Specification *(Planned)*

Defines how Menata is executed.

Multiple Runtime implementations are expected.

Examples:

- Go Runtime
- Java Runtime
- Python Runtime

---

## Reference Specification *(Planned)*

Defines shared vocabularies used across the language.

Examples:

- Data Types
- Naming Conventions
- Reserved Keywords
- Glossary
- Best Practices

---

# Design Goals

Menata is designed so that:

- Business Knowledge becomes the primary organizational asset.
- One Business Definition can be implemented by multiple Runtime implementations.
- Business Knowledge remains stable while technology evolves.
- Business analysts can describe business systems without writing source code.
- AI can understand, generate, validate, and improve Business Knowledge.
- Runtime implementations remain replaceable.

The fundamental principle is:

> **One Business Definition. Multiple Runtime.**

---

# Repository Structure

```
README.md

manifesto.md

design-principles.md

specification/

    language/

        000-language-spec.md

        001-object.md

        002-field.md

        003-relationship.md

        004-action.md

        ...
```

The repository structure will evolve together with the language.

---

# Current Status

Current stage:

**Research Draft**

The language specification is actively evolving.

Breaking changes are expected until version **1.0**.

The current goal is to design a stable language before building production-grade Runtime implementations.

---

# Roadmap

## Phase 1

Language Specification

- Foundation
- Core Grammar
- Reference Specification

---

## Phase 2

Composition Specification

- Recipe
- Workspace
- Application

---

## Phase 3

Runtime Specification

- Runtime
- Storage
- Renderer
- AI Integration

---

## Phase 4

Reference Runtime

- Go Runtime
- Web Runtime
- AI Authoring
- CLI
- Playground

---

## Phase 5

Reference Applications

- Business OS
- Sustainability Management
- Learning Management
- Knowledge Management
- Asset Management
- Project Management

---

# Contributing

Menata is currently focused on language design.

Discussions, ideas, references, critiques, and design proposals are highly appreciated.

A formal RFC (Request for Comments) process is planned as the language matures.

---

# License

Licensed under the Apache License 2.0.

See the LICENSE file for details.
