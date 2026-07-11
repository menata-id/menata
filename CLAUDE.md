# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

Menata is a **language specification project**, not a software project. There is no build, lint, or test tooling — the repository consists entirely of Markdown documents that define a declarative language for expressing Business Knowledge independently of implementation technology. "Working in this repo" means writing and editing specification prose, not code.

The current phase is focused on language design, not implementation. Breaking changes to the language are expected before v1.0.

## Repository structure

- `README.md` — project pitch, vision, and the documentation map (table of "I want to... / Go to...").
- `design-principles.md` — the 10 design principles (Business First, Knowledge First, Declarative, Technology Neutral, Human Readable, Machine Readable, Composable, Open Specification, Convention over Configuration, Long-term Compatibility). Any design decision that conflicts with these principles should be questioned.
- `specification/` — the normative language spec, numbered `NNN-topic.md`:
  - `000-language-spec.md` — core concepts, conceptual model, Standard Grammar table, conformance/compatibility rules, RFC 2119 keywords.
  - `001-object.md` … `006-view.md` — one document per Grammar: Object, Field, Event, Constraint, Permission, View.
- `guides/writing-menata.md` — a practical, example-driven, **Bahasa Indonesia** guide for authoring `.menata` files (walks through Fields → Events → Constraints → Permissions → Views, with a full worked example and a pre-handoff checklist).

Runtime/implementation concerns (translating `.menata` into executable metadata, the reference interpreter) live in a **separate repository**, [menata-id/menata-runtime](https://github.com/menata-id/menata-runtime). Do not add runtime/implementation content here — this repo is language-only. If you find stray references to a local `runtime/` directory, they are stale (it was moved out; see git history around `fa82111`).

## Core conceptual model

```
Business Reality → Business Knowledge → Menata → Machine Interpretation → Application
```

Menata expresses Business Knowledge and stays declarative (**what**, not **how**). Machine Interpretation (compilers, AI, runtime engines, etc.) is explicitly out of scope of the language spec — implementation details, storage, UI, and infra never belong in `specification/` or `design-principles.md`.

The language is built from six composable Grammar, each with **one** responsibility (never overlapping):

| Grammar | Responsibility |
|---|---|
| Object | Business Concept (the container; may hold Fields/Events/Constraints/Permissions/Views) |
| Field | Business Information (a value, value-list, or reference to another Object) |
| Event | Business Behavior triggered by an occurrence (activity, time, date, external) |
| Constraint | Business Rule that must always hold (may be conditional via `if`) |
| Permission | Business Role → Events it may perform |
| View | How Business Knowledge is organized/presented (Form, List, Detail, Calendar, …) |

Note the **Object/Machine** distinction in `000-language-spec.md`: "Object" is the Business Concept as expressed in Menata; "Machine" is Menata Runtime's specific realization of it. Other interpreters may realize the same Object differently.

## Conventions when editing spec content

- Language is normative: use RFC 2119 keywords (MUST/MUST NOT/SHOULD/SHOULD NOT/MAY) deliberately in `specification/`, as defined in `000-language-spec.md`.
- Business terminology only — avoid implementation-flavored names in examples (e.g. write `Purchase Request`, not `TblPurchaseRequest`; `Design Type`, not `design_type_id`).
- Each numbered spec doc follows the same skeleton: Purpose → Definition → (topic-specific sections) → Examples → Principles → Summary.
- `specification/000-language-spec.md`'s "Language Goals" section is a normative restatement of `design-principles.md` — keep the two in sync if principles change.
- `guides/writing-menata.md` is written in Bahasa Indonesia and is derivative of the spec plus real examples; keep terminology consistent with the English spec terms (Object, Field, Event, Constraint, Permission, View stay untranslated).
- Commit messages in this repo follow `docs: <what changed>` (occasionally `docs(runtime): …` for historical runtime-related docs, `chore: …` for repo moves). Keep messages in the same terse, descriptive style seen in `git log`.
