# Field

Version

0.1 Draft

Status

Draft

---

# Purpose

Field adalah Grammar BDL yang merepresentasikan satu informasi mengenai sebuah Object.

Field merupakan unit informasi terkecil dalam Business Definition Language.

Field mendeskripsikan apa yang diketahui mengenai suatu Object.

---

# Definition

Field adalah representasi formal dari satu informasi bisnis.

Field harus mempunyai arti yang jelas bagi pengguna bisnis.

Field harus tetap mempunyai makna meskipun implementasi teknis berubah.

Field bukan representasi implementasi teknis.

---

# Philosophy

Business memahami suatu Object melalui informasi yang dimilikinya.

Contoh.

Customer

↓

Customer Name

Email Address

Phone Number

Birth Date

Business OS menggunakan Field untuk merepresentasikan informasi tersebut.

Field merupakan atribut dari sebuah Object.

---

# Core Characteristics

Field:

- Merepresentasikan satu informasi bisnis.
- Dimiliki oleh tepat satu Object.
- Mempunyai Meaning.
- Menggunakan Data Type.
- Bersifat independen terhadap implementasi.
- Dapat digunakan oleh Grammar lain.

---

# Required Properties

Field MUST mempunyai:

- Name
- Code
- Meaning
- Data Type

---

# Optional Properties

Field MAY mempunyai:

- Description
- Display Name
- Category
- Tags
- Documentation
- Localization

---

# Grammar Relationships

Field dimiliki oleh satu Object.

Field menggunakan satu Data Type.

Field dapat digunakan oleh:

- Action
- Interaction
- Workflow
- Rule
- View
- Dashboard
- Permission
- Automation
- Policy

Grammar lain tidak mengubah definisi Field.

---

# Semantics

Field merepresentasikan satu informasi bisnis.

Satu Field hanya mempunyai satu makna.

Contoh.

Customer Name

Meaning

Nama resmi pelanggan.

---

Phone Number

Meaning

Nomor telepon utama pelanggan.

---

Expense Amount

Meaning

Nilai biaya yang diajukan.

---

Inspection Date

Meaning

Tanggal pelaksanaan inspeksi.

Contoh yang bukan Field.

customer_name_varchar

tbl_customer_name

customer_name_column

customer_api

phone_string

---

# Normative Requirements

Field:

- MUST mempunyai Name.
- MUST mempunyai Code.
- MUST mempunyai Meaning.
- MUST menggunakan Data Type.
- MUST dimiliki oleh tepat satu Object.
- MUST merepresentasikan satu informasi bisnis.
- MUST menggunakan istilah bisnis.
- MUST bebas dari implementasi teknis.
- SHOULD dapat digunakan kembali.
- SHOULD mempunyai Description apabila diperlukan.
- MAY mempunyai metadata tambahan.

---

# Constraints

Field tidak mengetahui implementasi teknis.

Field tidak mengetahui Runtime.

Field tidak mengetahui Storage.

Field tidak mengetahui Renderer.

Field tidak mengetahui Database.

Field tidak mengetahui Framework.

Field tidak mengetahui bahasa pemrograman.

Field juga tidak mengetahui implementasi Grammar lain.

---

# Examples

## Customer Name

Meaning

Nama resmi pelanggan.

Data Type

Person Name

---

## Expense Amount

Meaning

Nilai biaya yang diajukan.

Data Type

Money

---

## Inspection Date

Meaning

Tanggal pelaksanaan inspeksi.

Data Type

Date

---

## Asset Status

Meaning

Status operasional aset.

Data Type

Selection

---

# Non Goals

Field tidak mendeskripsikan:

- User Interface
- Layout
- Validation
- Workflow
- Rule
- Permission
- Automation
- Runtime
- Storage
- API

Field hanya mendeskripsikan satu informasi bisnis.

---

# Compatibility

Perubahan Field harus menjaga makna bisnis.

Perubahan Runtime, Storage, maupun Renderer tidak boleh mengubah definisi Field.

---

# Notes

Field merupakan Grammar yang mendeskripsikan satu informasi bisnis.

Setiap Field dimiliki oleh tepat satu Object.

Data Type didefinisikan pada Reference Specification.

Implementasi validasi, penyimpanan, maupun penyajian ditentukan oleh Grammar dan Runtime yang menggunakannya.
