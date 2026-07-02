# Business Definition Language (BDL) Specification

Version

0.1 Draft

Status

Draft

---

# Purpose

Business Definition Language (BDL) adalah spesifikasi bahasa deklaratif untuk merepresentasikan Business Knowledge.

BDL menyediakan sekumpulan Grammar yang digunakan untuk mendefinisikan aplikasi bisnis secara independen dari teknologi implementasi.

BDL merupakan fondasi dari Business OS.

---

# Scope

## In Scope

BDL mendefinisikan:

- Grammar
- Semantics
- Grammar Relationships
- Normative Rules
- Business Metadata

## Out of Scope

BDL tidak mendefinisikan:

- Runtime
- Storage
- Renderer
- Deployment
- Programming Language
- Framework
- Database
- Infrastructure

---

# Design Goals

BDL dirancang agar:

- Business Knowledge menjadi aset utama aplikasi.
- Satu definisi bisnis dapat digunakan oleh banyak Runtime.
- Satu definisi bisnis dapat dijalankan pada berbagai Renderer.
- Definisi bisnis tetap stabil meskipun teknologi berubah.
- Business Analyst dapat merancang aplikasi tanpa menulis kode.
- AI dapat menghasilkan dan menyempurnakan aplikasi menggunakan BDL.
- Grammar dapat digunakan kembali pada berbagai aplikasi.
- Implementasi dapat berubah tanpa mengubah Business Knowledge.

Prinsip utama BDL adalah:

> **One Business Definition. Multiple Runtime.**

---

# Design Principles

## Business First

Keputusan desain selalu didasarkan pada kebutuhan bisnis.

---

## Knowledge Driven

Business Knowledge merupakan sumber utama definisi aplikasi.

---

## Metadata First

Aplikasi dibangun dari metadata, bukan dari kode program.

---

## Declarative

BDL mendeskripsikan apa yang diinginkan.

Cara menjalankannya ditentukan oleh Runtime.

---

## Runtime Independent

Grammar tidak bergantung pada Runtime tertentu.

---

## Storage Independent

Grammar tidak bergantung pada mekanisme penyimpanan data.

---

## Renderer Independent

Grammar tidak bergantung pada media penyajian.

---

## AI Native

Grammar dirancang agar mudah dipahami dan dihasilkan oleh AI.

---

## Composable

Grammar dapat digabungkan menjadi solusi yang lebih besar.

---

## Extensible

Grammar dapat dikembangkan tanpa mengubah definisi dasarnya.

---

## Backward Compatible

Perubahan Grammar harus menjaga kompatibilitas sejauh memungkinkan.

---

# Mental Model

Business OS memisahkan pengetahuan bisnis dari implementasi.

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
Storage
        │
        ▼
Renderer
        │
        ▼
User Experience
```

---

# Standard Grammar Set

Business Definition Language terdiri dari Grammar berikut.

| Grammar | Responsibility |
|----------|----------------|
| Object | Merepresentasikan konsep bisnis. |
| Field | Merepresentasikan informasi bisnis. |
| Relationship | Merepresentasikan hubungan antar Object. |
| Action | Merepresentasikan aktivitas bisnis. |
| Interaction | Merepresentasikan cara menjalankan Action. |
| Workflow | Merepresentasikan perubahan siklus hidup bisnis. |
| Rule | Merepresentasikan aturan bisnis. |
| View | Merepresentasikan penyajian informasi. |
| Dashboard | Merepresentasikan pemantauan informasi. |
| Permission | Merepresentasikan hak akses. |
| Automation | Merepresentasikan proses otomatis. |
| Policy | Merepresentasikan kebijakan organisasi. |
| Recipe | Merepresentasikan paket solusi bisnis. |
| Workspace | Merepresentasikan lingkungan kerja. |
| Application | Merepresentasikan komposisi Grammar menjadi aplikasi. |

Setiap Grammar hanya mempunyai satu tanggung jawab.

---

# Grammar Model

Grammar saling melengkapi.

Tidak ada Grammar yang menggantikan Grammar lain.

```text
Object
Field
Relationship
Action
Interaction
Workflow
Rule
View
Dashboard
Permission
Automation
Policy

        │
        ▼

Recipe

        │
        ▼

Workspace

        │
        ▼

Application
```

---

# Layered Architecture

Business OS terdiri dari lapisan yang terpisah.

```text
Business Reality

↓

Business Knowledge

↓

Business Definition Language

↓

Runtime

↓

Storage

↓

Renderer

↓

Deployment
```

Setiap lapisan mempunyai tanggung jawab yang berbeda.

Perubahan pada satu lapisan tidak mengubah definisi lapisan lainnya.

---

# Separation of Concerns

| Layer | Responsibility |
|--------|----------------|
| Business Reality | Aktivitas nyata organisasi |
| Business Knowledge | Pengetahuan organisasi |
| Business Definition Language | Representasi formal Business Knowledge |
| Runtime | Menjalankan Grammar |
| Storage | Menyimpan data |
| Renderer | Menyajikan informasi |
| Deployment | Menyediakan lingkungan operasional |
| AI | Membantu menghasilkan dan menyempurnakan Grammar |

---

# Conformance

Suatu implementasi dinyatakan sesuai dengan BDL apabila:

- Mengimplementasikan seluruh Grammar yang digunakan.
- Mematuhi seluruh aturan normatif.
- Menjaga makna Business Knowledge.
- Tidak mengubah Semantics Grammar.

Implementasi dapat menggunakan teknologi apa pun.

---

# Normative Requirements

Seluruh Grammar:

- MUST mempunyai satu tanggung jawab utama.
- MUST menggunakan istilah bisnis.
- MUST bebas dari implementasi teknis.
- MUST mempunyai Semantics yang jelas.
- MUST dapat diproses oleh Runtime.
- MUST dapat dipahami oleh pengguna bisnis.
- MUST menjaga konsistensi dengan Grammar lain.
- SHOULD dapat digunakan kembali.
- SHOULD menjaga kompatibilitas.
- SHOULD mudah dipahami oleh AI.
- MAY diperluas tanpa mengubah definisi dasar.

---

# Non Goals

BDL tidak mendefinisikan:

- Bahasa pemrograman.
- Framework.
- Database.
- ORM.
- REST API.
- GraphQL.
- User Interface.
- HTML.
- CSS.
- JavaScript.
- Infrastruktur.
- Deployment.
- Algoritma implementasi.

BDL tidak bertujuan menggantikan bahasa pemrograman.

---

# Compatibility

Perubahan Grammar harus menjaga kompatibilitas sejauh memungkinkan.

Business Knowledge harus tetap stabil meskipun Runtime, Storage, Renderer, maupun teknologi implementasi berubah.

---

# Reference Specifications

BDL dapat menggunakan dokumen referensi pendukung.

Contoh:

- Data Types
- Naming Conventions
- Reserved Keywords
- Glossary
- Best Practices

Dokumen referensi bukan merupakan Grammar.

---

# Glossary

**Business Reality**

Aktivitas nyata yang terjadi dalam organisasi.

**Business Knowledge**

Pengetahuan yang menjelaskan bagaimana organisasi bekerja.

**Grammar**

Unit penyusun Business Definition Language.

**Metadata**

Representasi deklaratif dari Business Knowledge.

**Runtime**

Komponen yang menjalankan Grammar.

**Storage**

Komponen yang menyimpan data.

**Renderer**

Komponen yang menyajikan informasi.

---

# Notes

Business Definition Language merupakan fondasi seluruh Business OS.

Seluruh Grammar mengikuti spesifikasi ini.

Implementasi teknis dijelaskan pada spesifikasi Runtime, Renderer, Storage, AI, dan Reference secara terpisah.
