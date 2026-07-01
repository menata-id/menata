# BDL Grammar 002

# Field

Version

0.1 Draft

Status

Draft

---

# Purpose

Field adalah representasi formal dari satu informasi yang dimiliki oleh sebuah Business Object.

Field bukan kolom database.

Field bukan variabel pemrograman.

Field bukan atribut ORM.

Field merupakan representasi dari informasi yang memiliki makna bagi bisnis.

---

# Philosophy

Business Object merepresentasikan suatu konsep bisnis.

Field merepresentasikan informasi yang menjelaskan konsep tersebut.

Contoh.

Customer

↓

Customer Name

Phone Number

Email Address

Registration Date

Business mengenal informasi.

Runtime menentukan bagaimana informasi tersebut disimpan.

---

# Definition

Field adalah Grammar BDL yang mendeskripsikan satu atribut dari Business Object.

Field harus mempunyai arti yang jelas bagi bisnis.

Jika suatu informasi tidak mempunyai makna bisnis,

maka informasi tersebut bukan Field.

---

# Characteristics

Field:

- dimiliki oleh tepat satu Business Object

- memiliki Identity

- memiliki Value Type

- dapat digunakan oleh Form

- dapat digunakan oleh View

- dapat digunakan oleh Workflow

- dapat digunakan oleh Rule

- dapat digunakan oleh Dashboard

- dapat digunakan oleh Automation

---

# Identity

Setiap Field mempunyai Identity.

Identity bersifat unik dalam satu Business Object.

Contoh.

Customer Name

Phone Number

Email Address

---

# Required Properties

Field wajib memiliki.

Name

Code

Value Type

---

# Optional Properties

Description

Label

Placeholder

Required

Read Only

Hidden

Default Value

Help Text

Unique

Searchable

Filterable

Sortable

Display Order

Category

Tags

Localization

---

# Value Type

Business OS menggunakan Value Type.

Bukan Database Type.

Contoh.

Person Name

Organization Name

Phone Number

Email Address

Money

Percentage

Quantity

Date

Date Time

Duration

Boolean

Address

Location

Document

Image

URL

Rich Text

Selection

Reference

Runtime menentukan bagaimana Value Type dipetakan ke Storage.

---

# Children

Field tidak mempunyai Child Grammar.

Field merupakan Grammar atomik.

---

# Relationships

Field dimiliki oleh satu Business Object.

Field dapat digunakan oleh.

Form

View

Workflow

Rule

Dashboard

Automation

---

# Lifecycle

Draft

↓

Active

↓

Deprecated

↓

Removed

Runtime harus menjaga kompatibilitas terhadap data yang sudah menggunakan Field tersebut.

---

# Runtime Responsibility

Runtime bertanggung jawab untuk.

Memvalidasi Field.

Menyimpan nilai.

Mengambil nilai.

Memberikan nilai kepada Renderer.

Memberikan nilai kepada Workflow.

Memberikan nilai kepada Rule.

Runtime tidak mengetahui arti bisnis Field.

---

# AI Responsibility

AI bertanggung jawab.

Mengusulkan Field.

Memberikan nama yang konsisten.

Mengusulkan Value Type.

Mengusulkan Validasi.

Mengusulkan Default Value apabila diperlukan.

AI tidak boleh membuat Field yang tidak memiliki makna bisnis.

---

# Human Responsibility

Business Analyst bertanggung jawab.

Menentukan apakah Field memang dibutuhkan.

Menentukan arti bisnis.

Menentukan nama.

Menentukan apakah wajib diisi.

---

# Validation Rules

Runtime harus memastikan.

Name tidak kosong.

Code unik.

Value Type valid.

Default Value sesuai dengan Value Type.

---

# Constraints

Field
