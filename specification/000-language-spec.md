# Menata Language Specification

Version

0.1 Draft

Status

Draft

---

# Introduction

**Menata** is a declarative language for expressing Business Knowledge.

The purpose of Menata is to provide a stable, human-readable, and machine-interpretable representation of Business Knowledge.

Menata separates **Business Knowledge** from **Machine Interpretation**, allowing organizations to preserve their Business Knowledge independently of implementation technology.

The language defines **what** a business knows.

It does not define **how** machines should implement or execute that knowledge.

Implementation is the responsibility of Machine Interpretation.

This specification defines the Menata language.

It does not define Machine Interpretation.

---

# Language Identity

Menata is a **Business Knowledge Representation Language**.

The language exists to express Business Knowledge independently of implementation technology.

Business Knowledge is the primary artifact.

Machine Interpretation is an implementation concern.

The same Business Knowledge may be realized through different Machine Interpretations while preserving its meaning.

Menata defines the boundary between Business Knowledge and Machine Interpretation.

The language should remain stable while implementation technologies continue to evolve.

---

# Purpose

The purpose of Menata is to establish a common language for expressing Business Knowledge.

The language is intended to:

- express Business Knowledge consistently,
- preserve Business Knowledge independently of implementation technology,
- support collaboration between business experts, developers, and AI,
- enable multiple Machine Interpretations,
- reduce dependency on implementation technology.

Business Knowledge is treated as a long-term organizational asset.

---

# Scope

## In Scope

This specification defines:

- the language,
- language grammar,
- language semantics,
- grammar composition,
- conformance requirements,
- compatibility requirements.

---

## Out of Scope

This specification does not define:

- programming languages,
- source code,
- databases,
- frameworks,
- runtime engines,
- AI models,
- deployment,
- infrastructure,
- user interfaces,
- Machine Interpretation.

These concerns belong to their respective implementation technologies.

# Language Goals

Menata is designed with the following goals.

These goals are the normative restatement, for this specification, of the fuller rationale in `design-principles.md` — read that document for the reasoning behind each goal.

## Business Knowledge First

Business Knowledge is the primary artifact of the language.

Implementation technology is secondary.

A change in implementation should not require redefining Business Knowledge.

---

## Implementation Independence

Business Knowledge should remain stable while implementation technologies continue to evolve.

The same Business Knowledge may be realized through different Machine Interpretations.

---

## Human Readability

Business Knowledge should be understandable by business professionals.

The language should be readable without requiring programming knowledge.

---

## Machine Interpretability

Business Knowledge should be interpretable consistently by machines.

Different Machine Interpretations should preserve the same meaning.

---

## Composability

Complex Business Knowledge should be constructed from smaller language components.

Each language component should have one primary responsibility.

---

## Extensibility

The language should evolve carefully.

New language components may be introduced without unnecessarily breaking existing Business Knowledge.

---

## Long-term Stability

Business Knowledge should outlive implementation technology.

Long-term compatibility is preferred over short-term convenience.

---

# Core Concepts

Menata is built upon a small number of fundamental concepts.

These concepts define the boundary between Business Knowledge and Machine Interpretation.

Every language component ultimately exists to express one or more of these concepts.

---

## Business Reality

Business Reality is the real world in which an organization operates.

It includes:

- people,
- organizations,
- physical objects,
- activities,
- events,
- policies,
- regulations,
- decisions,
- and every observable aspect of business.

Business Reality exists independently of software.

The purpose of Menata is to represent Business Reality through Business Knowledge.

---

## Business Knowledge

Business Knowledge is an organization's understanding of Business Reality.

It explains:

- what exists,
- what happens,
- what rules apply,
- who is responsible,
- how work is performed,
- and how the organization operates.

Business Knowledge belongs to the organization.

It exists independently of software.

Software is one possible realization of Business Knowledge.

---

## Menata

Menata is a declarative language for expressing Business Knowledge.

The language provides a consistent way to represent Business Knowledge independently of implementation technology.

Menata describes Business Knowledge.

It does not describe implementation.

---

## Machine Interpretation

Machine Interpretation is the process of realizing Business Knowledge expressed in Menata.

Machine Interpretation is intentionally outside the scope of the language.

Possible Machine Interpretations include, but are not limited to:

- AI,
- code generators,
- compilers,
- interpreters,
- runtime engines,
- automation platforms,
- future technologies.

Different Machine Interpretations should preserve the same Business Knowledge.

---

## Application

An Application is one possible realization of Business Knowledge.

Applications are implementation artifacts produced through Machine Interpretation.

Different applications may realize the same Business Knowledge while preserving its meaning.

---

## Object and Machine

An Object, as defined in this specification, is a Business Concept.

Menata Runtime — one specific Machine Interpreter — realizes each Object as a **Machine**: the primary runtime realization unit, holding the Object's Fields, Events, Constraints, Permissions, and Views as executable Runtime Metadata.

Object and Machine name the same Business Concept from two sides of the language boundary. Object is how the concept is expressed. Machine is how one particular runtime realizes it. Other Machine Interpreters may name their realization differently while preserving the same Object.

# Conceptual Model

The relationship between the core concepts is illustrated below.

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

Each layer has a distinct responsibility.

| Layer | Responsibility |
|--------|----------------|
| Business Reality | The real world in which organizations operate. |
| Business Knowledge | Understanding and describing Business Reality. |
| Menata | Expressing Business Knowledge using a formal language. |
| Machine Interpretation | Realizing Business Knowledge through implementation technologies. |
| Application | One possible implementation of Business Knowledge. |

Business Knowledge remains independent from implementation technology.

Machine Interpretation is responsible for realizing the language while preserving its meaning.

---

# Language Grammar

Menata expresses Business Knowledge through a small set of language grammar.

Each Grammar has one primary responsibility.

Grammar complement one another.

No Grammar should duplicate the responsibility of another Grammar.

Together, the Grammar form the vocabulary of the Menata language.

---

# Standard Grammar

The core language consists of the following Grammar.

| Grammar | Responsibility |
|----------|----------------|
| Object | Represents Business Concepts. |
| Field | Represents Business Information. |
| Event | Represents Business Behaviors triggered by business occurrences. |
| Constraint | Represents Business Rules that must always be satisfied. |
| Permission | Represents Business Responsibilities and Authorizations. |
| View | Represents how Business Knowledge is organized and presented. |

Each Grammar is defined in its own specification document.

---

# Grammar Composition

Business Knowledge is expressed by combining multiple Grammar.

An Object may contain one or more language components.

Only the components necessary to express the Business Knowledge should be defined.

Example

```text
Design Request

Fields

- Requester : User
- Design Type : Poster | Thumbnail | Banner 2:1
- Due Date : Date
- Title : Text
- Description : Rich Text

Events

When Submit

    Status Submitted

    Notify Design Team

When Complete

    Status Completed

    Notify Requester

Constraints

- Title is required.
- Due Date must be after today.

Permissions

Requester

- Submit

Designer

- Complete

Views

- Request Form : Form
- My Requests : Card
- All Requests : Table
```

The same Business Knowledge may be realized by different Machine Interpretations while preserving its meaning.

---

# Grammar Independence

Each Grammar should be understandable independently.

However, Grammar are designed to work together to express complete Business Knowledge.

Learning one Grammar should not require understanding every other Grammar.

This enables Business Knowledge to evolve incrementally while remaining consistent.

---

# Extensibility

The Menata language is designed to evolve.

New Grammar may be introduced in future versions when they represent new Business Knowledge that cannot be expressed by existing Grammar.

Additional Grammar should:

- have one primary responsibility,
- remain consistent with the language principles,
- avoid overlapping responsibilities,
- preserve Business Knowledge semantics,
- maintain compatibility whenever reasonably possible.

Language evolution should prioritize simplicity over completeness.

---

# Conformance

A Machine Interpreter conforms to the Menata Language Specification if it:

- correctly interprets the Grammar it supports,
- preserves the semantics defined by this specification,
- produces behavior consistent with the expressed Business Knowledge,
- clearly identifies unsupported Grammar.

A Machine Interpreter may support only a subset of the language.

Unsupported Grammar should be reported explicitly.

Machine Interpretation must not change the meaning of Business Knowledge.

---

# Compatibility

Business Knowledge should remain stable over time.

New language versions should preserve compatibility whenever reasonably possible.

Machine Interpreters should support Business Knowledge created by earlier language versions.

If compatibility cannot be preserved, the incompatibility should be explicitly documented.

Long-term compatibility is preferred over unnecessary language changes.

---

# Normative Requirements

The following keywords are interpreted as described in RFC 2119.

- MUST
- MUST NOT
- SHOULD
- SHOULD NOT
- MAY

---

## Language

The language:

- MUST express Business Knowledge.
- MUST remain implementation independent.
- MUST define clear semantics.
- MUST be human readable.
- MUST be machine interpretable.
- SHOULD remain simple.
- SHOULD evolve incrementally.
- MAY be extended through additional Grammar.

---

## Grammar

Each Grammar:

- MUST have one primary responsibility.
- MUST define clear semantics.
- MUST remain consistent with other Grammar.
- MUST avoid overlapping responsibilities.
- SHOULD be independently understandable.
- SHOULD be composable.

---

## Business Knowledge

Business Knowledge:

- MUST remain independent from implementation technology.
- MUST preserve its meaning across Machine Interpretations.
- SHOULD remain stable over time.
- SHOULD evolve without unnecessary disruption.

---

## Machine Interpretation

Machine Interpretation:

- MUST preserve the semantics of Business Knowledge.
- MUST NOT redefine the meaning of the language.
- SHOULD produce consistent results.
- MAY generate applications, source code, configurations, automation, AI agents, or other implementation artifacts.

---

# Non-goals

The Menata Language Specification intentionally does not define:

- programming languages,
- source code,
- databases,
- frameworks,
- APIs,
- user interfaces,
- deployment,
- infrastructure,
- runtime architectures,
- implementation strategies,
- AI models.

These concerns belong to Machine Interpretation rather than the language itself.

---

# Versioning

The Menata Language evolves through published specification versions.

Each version defines:

- language grammar,
- language semantics,
- normative requirements,
- compatibility expectations.

Machine Interpreters should declare the language version they support.

Business Knowledge should specify the language version it conforms to.

---

# Glossary

## Business Reality

The real-world environment in which an organization operates.

---

## Business Knowledge

An organization's understanding of Business Reality.

---

## Menata

A declarative language for expressing Business Knowledge.

---

## Grammar

A language construct used to express one aspect of Business Knowledge.

---

## Machine Interpretation

The process of realizing Business Knowledge expressed in Menata.

---

## Machine Interpreter

A technology that performs Machine Interpretation.

---

## Application

One possible realization of Business Knowledge.

---

# Document Status

This document is a Draft Specification.

The language may continue to evolve before version 1.0.

The goal of the current phase is conceptual stability rather than implementation completeness.
