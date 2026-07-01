# Business Definition Language Specification

Version

0.1 Draft

Status

Draft

---

# Purpose

Business Definition Language (BDL) adalah spesifikasi bahasa deklaratif untuk mendeskripsikan pengetahuan bisnis secara terstruktur.

BDL menyediakan sekumpulan Grammar yang digunakan untuk membangun aplikasi bisnis tanpa bergantung pada teknologi implementasi.

BDL merupakan fondasi dari Business OS.

---

# Scope

BDL mendefinisikan:

- struktur pengetahuan bisnis
- hubungan antar Grammar
- aturan dasar Grammar
- prinsip interoperabilitas
- kontrak antara Business Knowledge dan Runtime

BDL tidak mendefinisikan implementasi.

---

# Design Goals

Business Definition Language dirancang agar.

Satu definisi bisnis dapat digunakan oleh banyak Runtime.

Satu definisi bisnis dapat dijalankan pada Web, Mobile, Desktop, Chat, Voice, maupun AI.

Business dapat berkembang tanpa bergantung pada teknologi.

Business Analyst dapat merancang aplikasi tanpa menulis kode.

AI dapat menghasilkan aplikasi menggunakan metadata BDL.

Runtime dapat berubah tanpa mengubah definisi bisnis.

Renderer dapat berubah tanpa mengubah definisi bisnis.

Storage dapat berubah tanpa mengubah definisi bisnis.

Business Knowledge tetap menjadi aset utama organisasi.

---

# Design Principles

Business First

Keputusan desain selalu didasarkan pada kebutuhan bisnis.

---

Metadata First

Aplikasi dibangun menggunakan metadata.

---

Knowledge Driven

Business Knowledge merupakan sumber utama aplikasi.

---

Declarative

BDL mendeskripsikan apa yang diinginkan.

Runtime menentukan bagaimana cara menjalankannya.

---

Runtime Independent

Grammar tidak bergantung pada Runtime.

---

Storage Independent

Grammar tidak bergantung pada database.

---

Renderer Independent

Grammar tidak bergantung pada User Interface.

---

AI Native

Grammar dirancang agar dapat dipahami dan dihasilkan oleh AI.

---

Composable

Grammar dapat digabungkan menjadi solusi yang lebih besar.

---

Extensible

Grammar dapat dikembangkan tanpa merusak kompatibilitas.

---

Backward Compatible

Perubahan Grammar harus menjaga kompatibilitas sejauh memungkinkan.

---

# Core Grammar

Business Definition Language terdiri dari Grammar berikut.

| Grammar | Tujuan |
|----------|---------|
| Object | Merepresentasikan konsep bisnis. |
| Field | Merepresentasikan informasi bisnis. |
| Relationship | Merepresentasikan hubungan antar Object. |
| Action | Merepresentasikan aktivitas bisnis. |
| Interaction | Merepresentasikan cara Action dijalankan. |
| Workflow | Merepresentasikan perubahan siklus hidup bisnis. |
| Rule | Merepresentasikan aturan bisnis. |
| View | Merepresentasikan penyajian informasi. |
| Dashboard | Merepresentasikan pemantauan kondisi bisnis. |
| Permission | Merepresentasikan hak akses. |
| Automation | Merepresentasikan proses otomatis. |
| Policy | Merepresentasikan kebijakan organisasi. |
| Recipe | Merepresentasikan paket solusi bisnis. |
| Workspace | Merepresentasikan lingkungan kerja. |
| Application | Merepresentasikan komposisi seluruh Grammar. |

---

# Grammar Model

Setiap Grammar mempunyai satu tanggung jawab.

Grammar saling melengkapi.

Tidak saling menggantikan.

```text
Object
    ├── Field
    ├── Relationship
    │
    ├── Action
    │      └── Interaction
    │
    ├── Workflow
    ├── Rule
    ├── View
    ├── Dashboard
    ├── Permission
    ├── Automation
    └── Policy

Recipe
    └── Menggabungkan Grammar menjadi solusi

Workspace
    └── Menjalankan Recipe

Application
    └── Menggabungkan seluruh Grammar
```

---

# Layered Architecture

Business OS terdiri dari beberapa lapisan.

```text
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
Deployment
```

Setiap lapisan berkembang secara independen.

---

# Separation of Concerns

BDL hanya mendeskripsikan pengetahuan bisnis.

Runtime menjalankan Grammar.

Storage menyimpan data.

Renderer menyajikan pengalaman pengguna.

Deployment mengelola lingkungan operasional.

AI membantu menghasilkan dan menyempurnakan BDL.

Setiap lapisan memiliki tanggung jawab yang berbeda.

---

# Normative Requirements

Seluruh Grammar BDL:

MUST mempunyai identitas.

MUST mempunyai tujuan yang jelas.

MUST menggunakan istilah bisnis.

MUST bebas dari implementasi teknis.

MUST dapat dipahami oleh pengguna bisnis.

MUST dapat diproses oleh Runtime.

SHOULD dapat digunakan kembali.

SHOULD menjaga kompatibilitas.

SHOULD dapat dikomposisikan.

MAY diperluas tanpa mengubah definisi dasar.

---

# Non Goals

Business Definition Language tidak mendefinisikan.

Bahasa pemrograman.

Framework.

Database.

ORM.

REST API.

GraphQL.

User Interface.

HTML.

CSS.

JavaScript.

Mobile Framework.

Infrastructure.

Deployment.

Seluruh implementasi tersebut berada di luar ruang lingkup BDL.

---

# Compatibility

Grammar BDL harus tetap stabil terhadap perubahan Runtime.

Grammar BDL harus tetap stabil terhadap perubahan Storage.

Grammar BDL harus tetap stabil terhadap perubahan Renderer.

Grammar BDL harus tetap stabil terhadap perkembangan AI.

Perubahan Grammar harus menjaga kompatibilitas sejauh memungkinkan.

---

# Glossary

Grammar

Unit penyusun Business Definition Language.

Business Knowledge

Pengetahuan yang merepresentasikan cara organisasi bekerja.

Metadata

Representasi deklaratif dari Business Knowledge.

Runtime

Komponen yang menjalankan Grammar.

Storage

Komponen yang menyimpan data.

Renderer

Komponen yang menyajikan informasi kepada pengguna.

---

# Notes

Business Definition Language merupakan fondasi seluruh Business OS.

Seluruh Grammar mengikuti spesifikasi ini.

Dokumen ini menjadi acuan sebelum mempelajari setiap Grammar secara rinci.
