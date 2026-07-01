# BDL Grammar 001

# Business Object

Version

0.1 Draft

Status

Draft

---

# Purpose

Business Object adalah representasi formal dari suatu konsep bisnis.

Business Object bukan tabel database.

Business Object bukan Class.

Business Object bukan Entity Framework.

Business Object adalah representasi pengetahuan bisnis.

Contoh:

Customer

Supplier

Invoice

Meeting

Course

Lesson

Asset

Inspection

Employee

Knowledge

Action

Observation

Business Object adalah fondasi seluruh Business OS.

---

# Philosophy

Business Object merepresentasikan sesuatu yang memiliki makna bagi bisnis.

Jika suatu konsep tidak memiliki makna bisnis,

maka konsep tersebut bukan Business Object.

---

# Characteristics

Business Object:

- memiliki identitas

- memiliki atribut

- dapat memiliki relasi

- dapat memiliki workflow

- dapat memiliki permission

- dapat memiliki view

- dapat memiliki automation

- dapat memiliki dashboard

Business Object tidak memiliki implementasi.

---

# Identity

Setiap Business Object memiliki Identity.

Identity bersifat unik dalam sebuah Workspace.

Contoh.

Customer

Employee

Inspection

Asset

---

# Required Properties

Business Object wajib memiliki.

Name

Code

Description

Version

---

# Optional Properties

Display Name

Icon

Color

Category

Tags

Owner

Recipe

Localization

---

# Children

Business Object dapat memiliki.

Fields

Relationships

Forms

Views

Workflow

Rules

Permissions

Automation

Policies

---

# Example

Business Object

Customer

Description

Data pelanggan.

Fields

Name

Email

Phone

Address

Workflow

Prospect

↓

Customer

↓

Inactive

Views

Table

Card

Dashboard

Customer Summary

---

# Constraints

Business Object tidak boleh mengetahui.

Database

Go

SQL

HTML

REST

GraphQL

Platform Service

Infrastructure

---

# Runtime Responsibility

Runtime bertanggung jawab untuk.

Memuat Object.

Memvalidasi Object.

Menghubungkan Object.

Menampilkan Object.

Menyimpan Object.

Menjalankan Workflow.

Menjalankan Rule.

Business Object tidak mengetahui bagaimana Runtime bekerja.

---

# AI Responsibility

AI bertanggung jawab.

Menghasilkan Business Object.

Memberi nama yang tepat.

Mengusulkan Relationship.

Mengusulkan Workflow.

Mengusulkan View.

Namun AI tidak boleh menghasilkan implementasi Runtime.

---

# Human Responsibility

Business Analyst bertanggung jawab.

Menentukan apakah suatu Object memang memiliki makna bisnis.

Jika tidak,

jangan dibuat.

---

# Design Rules

Nama harus menggunakan istilah bisnis.

Jangan menggunakan istilah teknis.

Contoh.

Benar.

Customer

Invoice

Meeting

Inspection

Salah.

tbl_customer

CustomerModel

CustomerEntity

CustomerRecord

---

# Compatibility

Business Object harus kompatibel dengan seluruh Runtime Business OS.

Runtime boleh berubah.

Business Object tetap.

---

# Future Extension

Business Object dapat diperluas.

Namun definisi dasar tidak boleh berubah.
