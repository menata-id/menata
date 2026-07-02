# Business OS

> **Business Knowledge as a Language**

Business OS adalah pendekatan **Knowledge-Defined Software** yang memandang **Business Knowledge** sebagai aset utama organisasi.

Business OS menyediakan **Business Definition Language (BDL)** untuk merepresentasikan Business Knowledge secara formal.

Business Knowledge yang direpresentasikan menggunakan BDL dapat diimplementasikan oleh satu atau lebih Runtime menjadi aplikasi bisnis.

Business OS bukan framework.

Business OS bukan runtime.

Business OS adalah spesifikasi.

---

# Vision

Business Knowledge harus dapat dipisahkan dari teknologi implementasi.

Perubahan Runtime, bahasa pemrograman, database, maupun User Interface tidak boleh mengubah Business Knowledge organisasi.

Business Knowledge harus tetap menjadi aset yang stabil sepanjang evolusi teknologi.

---

# Architecture

```text
Business Reality
        │
        ▼
Business Knowledge
        │
        ▼
Business Definition Language
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

Business OS memisahkan pengetahuan bisnis dari implementasi teknis.

---

# Repository Structure

Saat ini repository dikembangkan menggunakan pendekatan **Specification First**.

```text
business-os/

README.md

manifesto.md

design-principles.md

business-definition-language.md

core-concepts.md

bdl/

    000-bdl-spec.md

    001-object.md

    002-field.md

    003-relationship.md

    004-action.md

    ...
```

Struktur repository akan berkembang seiring perkembangan spesifikasi.

---

# Current Architecture

Business OS terdiri dari beberapa spesifikasi.

## Business Definition Language (BDL)

Business Definition Language merupakan bahasa formal untuk merepresentasikan Business Knowledge.

Grammar yang saat ini dirancang.

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

---

## Composition Specification *(Planned)*

Composition Specification akan mendefinisikan bagaimana Grammar dikomposisikan menjadi solusi bisnis.

Dokumen yang direncanakan.

- Recipe
- Workspace
- Application

---

## Runtime Specification *(Planned)*

Runtime Specification akan mendefinisikan bagaimana Business Definition Language diimplementasikan menjadi aplikasi.

Runtime bukan bagian dari Business Definition Language.

---

## Reference Specification *(Planned)*

Reference Specification akan mendefinisikan vocabulary bersama yang digunakan oleh seluruh Grammar.

Contohnya.

- Data Types
- Naming Conventions
- Reserved Keywords
- Glossary
- Best Practices

---

# Design Principles

Business OS dibangun menggunakan prinsip berikut.

- Business First
- Knowledge Driven
- Metadata First
- Declarative
- Runtime Independent
- Storage Independent
- Renderer Independent
- AI Native
- Composable
- Extensible
- Backward Compatible

---

# Design Philosophy

Business OS tidak bertujuan menggantikan bahasa pemrograman.

Business OS tidak bertujuan menggantikan framework.

Business OS tidak bertujuan menggantikan Runtime.

Business OS menyediakan bahasa formal untuk merepresentasikan Business Knowledge.

Runtime bertanggung jawab mengimplementasikan bahasa tersebut menjadi aplikasi.

---

# Roadmap

## Phase 1

Business Definition Language Specification

- [x] Foundation
- [ ] Core Grammar
- [ ] Reference Specification

---

## Phase 2

Composition Specification

- [ ] Recipe
- [ ] Workspace
- [ ] Application

---

## Phase 3

Runtime Specification

- [ ] Runtime
- [ ] Storage
- [ ] Renderer
- [ ] AI Integration

---

## Phase 4

Reference Runtime

- [ ] Go Runtime
- [ ] Web Renderer
- [ ] AI Authoring

---

## Phase 5

Proof of Concept Applications

- Portal GA
- Sustainability Management
- Learning Management
- Knowledge Management
- Asset Management
- Project Management

---

# Status

Current Status

**Draft**

Repository ini sedang digunakan untuk merancang spesifikasi Business Definition Language dan arsitektur Business OS.

Spesifikasi dapat berubah hingga versi 1.0 dipublikasikan.

---

# License

TBD
