# Field

Version

0.1 Draft

Status

Draft

---

# Purpose

Field adalah Grammar BDL yang merepresentasikan satu informasi yang dimiliki oleh sebuah Object.

Field merupakan unit informasi terkecil dalam Business Definition Language.

Field bukan kolom database.

Field bukan atribut ORM.

Field bukan variabel pemrograman.

Field merupakan representasi informasi bisnis.

---

# Philosophy

Business memahami suatu Object melalui informasi yang dimilikinya.

Contoh.

Customer

↓

Customer Name

Phone Number

Email Address

Registration Date

Business OS menggunakan Field untuk merepresentasikan informasi tersebut.

Field merupakan "atribut" dari sebuah Object.

---

# Definition

Field adalah representasi formal dari satu informasi bisnis.

Field harus mempunyai arti yang dapat dipahami oleh pengguna bisnis.

Field harus tetap bermakna meskipun teknologi berubah.

Jika suatu informasi tidak mempunyai makna bisnis,

maka informasi tersebut bukan Field.

---

# Core Characteristics

Field:

- mempunyai identitas
- mempunyai Meaning
- dimiliki oleh satu Object
- menggunakan Data Type
- bersifat independen terhadap implementasi
- dapat digunakan oleh Grammar lain

Field tidak mengetahui bagaimana Grammar lain menggunakannya.

---

# Required Properties

Field wajib memiliki.

Name

Code

Meaning

---

# Optional Properties

Description

Display Name

Category

Tags

Localization

Documentation

---

# Grammar Relationships

Field dimiliki oleh.

Object

---

Field menggunakan.

Data Type

---

Field dapat digunakan oleh.

Action

Interaction

Workflow

Rule

View

Dashboard

Automation

Permission

Policy

Application

Field tidak mengetahui bagaimana Grammar tersebut menggunakannya.

---

# Semantics

Field merepresentasikan satu informasi bisnis.

Satu Field hanya mempunyai satu makna.

Contoh.

Customer Name

↓

Nama resmi pelanggan.

---

Phone Number

↓

Nomor telepon utama pelanggan.

---

Expense Amount

↓

Nilai pengeluaran yang diajukan.

---

Inspection Date

↓

Tanggal pelaksanaan inspeksi.

Contoh yang salah.

customer_name_varchar

tbl_customer_name

customer_name_column

phone_string

email_text

---

# Constraints

Field tidak boleh mengetahui.

Database

Table

Column

Primary Key

Foreign Key

ORM

SQL

Go

Python

Java

REST API

GraphQL

HTML

CSS

JavaScript

Docker

Infrastructure

Implementasi Data Type

Field juga tidak mengetahui.

Action

Interaction

Workflow

Rule

View

Dashboard

Automation

Permission

Policy

Field hanya mendeskripsikan informasi bisnis.

---

# Normative Requirements

Field MUST mempunyai Name.

Field MUST mempunyai Code.

Field MUST mempunyai Meaning.

Field MUST dimiliki oleh tepat satu Object.

Field MUST menggunakan satu Data Type.

Field MUST NOT mengetahui implementasi Runtime.

Field MUST NOT mengetahui implementasi Storage.

Field SHOULD menggunakan istilah bisnis.

Field SHOULD merepresentasikan satu informasi.

Field MAY mempunyai Description.

Field MAY mempunyai Category.

---

# Examples

Object

Customer

Field

Customer Name

Meaning

Nama resmi pelanggan.

Data Type

Person Name

---

Object

Expense

Field

Expense Amount

Meaning

Nilai biaya yang diajukan.

Data Type

Money

---

Object

Inspection

Field

Inspection Date

Meaning

Tanggal pelaksanaan inspeksi.

Data Type

Date

---

Object

Asset

Field

Asset Status

Meaning

Status operasional aset.

Data Type

Selection

---

# Non Goals

Field tidak mendeskripsikan.

User Interface.

Validation.

Visibility.

Layout.

Workflow.

Business Rule.

Automation.

Dashboard.

Permission.

Storage.

API.

Runtime.

Field hanya mendeskripsikan informasi bisnis.

---

# Compatibility

Field harus tetap kompatibel terhadap perubahan Runtime.

Runtime dapat berubah.

Storage dapat berubah.

Renderer dapat berubah.

AI dapat berubah.

Definisi Field tetap.

---

# Notes

Field merupakan Grammar yang mendeskripsikan informasi bisnis.

Setiap Field dimiliki oleh tepat satu Object.

Field menggunakan Data Type yang didefinisikan pada Reference Specification.

Implementasi penyimpanan dan validasi ditentukan oleh Runtime.
