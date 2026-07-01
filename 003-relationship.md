# Relationship

Version

0.1 Draft

Status

Draft

---

# Purpose

Relationship mendeskripsikan hubungan antara dua atau lebih Business Object.

Relationship merupakan representasi hubungan bisnis.

Relationship bukan Foreign Key.

Relationship bukan Join Database.

Relationship bukan ORM Association.

Relationship merupakan pengetahuan bisnis mengenai keterkaitan antar Business Object.

---

# Philosophy

Business tidak mengenal Foreign Key.

Business mengenal hubungan.

Contoh.

Customer

membuat

Invoice

Employee

bertanggung jawab terhadap

Asset

Course

terdiri dari

Lesson

Relationship menjelaskan hubungan tersebut.

Runtime menentukan bagaimana hubungan tersebut diimplementasikan.

---

# Definition

Relationship adalah Grammar BDL yang mendeskripsikan hubungan antara Business Object.

Relationship menjelaskan bagaimana suatu Object berinteraksi dengan Object lainnya.

Relationship tidak menjelaskan implementasi teknis.

---

# Characteristics

Relationship:

- menghubungkan minimal dua Business Object
- mempunyai nama
- mempunyai arah
- mempunyai Cardinality
- dapat memiliki aturan
- dapat digunakan oleh View
- dapat digunakan oleh Rule
- dapat digunakan oleh Workflow
- dapat digunakan oleh Permission

---

# Identity

Setiap Relationship memiliki Identity.

Identity bersifat unik dalam satu Workspace.

Contoh.

Customer Invoice

Employee Asset

Course Lesson

Inspection Finding

---

# Required Properties

Relationship wajib memiliki.

Name

Code

Source Object

Target Object

Cardinality

---

# Optional Properties

Description

Label

Inverse Name

Cascade Policy

Ownership

Required

Read Only

Tags

Category

Localization

---

# Cardinality

Business OS mendukung Cardinality berikut.

One to One

One to Many

Many to One

Many to Many

Cardinality merupakan konsep bisnis.

Runtime menentukan implementasinya.

---

# Direction

Relationship memiliki arah.

Contoh.

Customer

↓

Invoice

atau

Course

↓

Lesson

Relationship juga dapat bersifat dua arah apabila diperlukan.

---

# Ownership

Relationship dapat memiliki Owner.

Contoh.

Invoice dimiliki Customer.

Lesson dimiliki Course.

Ownership membantu Runtime menentukan siklus hidup Object.

---

# Children

Relationship tidak memiliki Child Grammar.

Relationship merupakan Grammar atomik.

---

# Lifecycle

Draft

↓

Active

↓

Deprecated

↓

Removed

Runtime harus menjaga integritas Relationship terhadap data yang sudah ada.

---

# Runtime Responsibility

Runtime bertanggung jawab untuk.

Memvalidasi Relationship.

Menjaga integritas data.

Menyediakan navigasi antar Object.

Menyediakan Relationship kepada View.

Menyediakan Relationship kepada Rule.

Menyediakan Relationship kepada Workflow.

Runtime tidak menentukan arti bisnis Relationship.

---

# AI Responsibility

AI bertanggung jawab.

Mengusulkan Relationship.

Mengusulkan Cardinality.

Mengusulkan Ownership.

Mengusulkan Inverse Relationship apabila diperlukan.

AI tidak boleh membuat Relationship yang tidak memiliki makna bisnis.

---

# Human Responsibility

Business Analyst bertanggung jawab.

Menentukan apakah dua Business Object memang memiliki hubungan.

Menentukan arah Relationship.

Menentukan Cardinality.

Menentukan Ownership.

---

# Validation Rules

Runtime harus memastikan.

Source Object ada.

Target Object ada.

Relationship Name tidak kosong.

Code unik.

Cardinality valid.

Relationship tidak membentuk siklus yang tidak diperbolehkan.

---

# Constraints

Relationship tidak boleh mengetahui.

Foreign Key.

Primary Key.

Join Table.

Database.

SQL.

ORM.

Go.

HTML.

REST.

GraphQL.

Docker.

Infrastructure.

Relationship hanya mengetahui hubungan bisnis.

---

# Compatibility

Perubahan berikut kompatibel.

Mengubah Description.

Mengubah Label.

Menambah
