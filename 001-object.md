# Object

Version

0.1 Draft

Status

Draft

---

# Purpose

Object adalah Grammar BDL yang merepresentasikan suatu konsep yang memiliki makna bagi organisasi.

Object merupakan fondasi utama Business Definition Language.

Seluruh aplikasi Business OS dibangun dari kumpulan Object yang saling berhubungan.

Object bukan implementasi teknis.

Object merupakan representasi pengetahuan bisnis.

---

# Philosophy

Business berpikir menggunakan konsep.

Customer

Supplier

Employee

Asset

Inspection

Invoice

Purchase Order

Finding

Knowledge

Course

Lesson

Business OS menggunakan Object untuk merepresentasikan konsep-konsep tersebut.

Object merupakan "kata benda" (noun) dalam Business Definition Language.

---

# Definition

Object adalah representasi formal dari suatu konsep bisnis.

Object harus dapat dipahami oleh pengguna bisnis.

Object harus tetap bermakna meskipun teknologi berubah.

Jika suatu konsep tidak mempunyai makna bisnis,

maka konsep tersebut bukan Object.

---

# Core Characteristics

Object:

- mempunyai identitas
- mempunyai Purpose
- mempunyai satu atau lebih Field
- dapat mempunyai Relationship
- bersifat independen
- dapat digunakan oleh Grammar lain

Object tidak mengetahui bagaimana Grammar lain menggunakannya.

---

# Required Properties

Object wajib memiliki.

Name

Code

Purpose

Version

---

# Optional Properties

Description

Display Name

Category

Icon

Color

Tags

Owner

Localization

Documentation

---

# Grammar Relationships

Object mempunyai.

Field

Relationship

---

Object digunakan oleh.

Action

Interaction

Workflow

Rule

View

Dashboard

Automation

Permission

Policy

Recipe

Workspace

Application

Object tidak mengetahui bagaimana Grammar tersebut menggunakannya.

---

# Semantics

Object harus merepresentasikan konsep yang stabil.

Contoh.

Customer

Supplier

Employee

Invoice

Asset

Inspection

Knowledge

Object tidak dibuat berdasarkan implementasi.

Contoh yang salah.

tbl_customer

customer_model

invoice_service

inspection_controller

customer_api

---

# Constraints

Object tidak boleh mengetahui.

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

Object juga tidak mengetahui.

Action

Interaction

Workflow

Rule

View

Dashboard

Automation

Permission

Policy

Object hanya mengetahui dirinya sendiri.

---

# Normative Requirements

Object MUST mempunyai Name.

Object MUST mempunyai Code.

Object MUST mempunyai Purpose.

Object MUST mempunyai minimal satu Field.

Object MUST NOT mengetahui implementasi Runtime.

Object MUST NOT mengetahui implementasi Storage.

Object SHOULD menggunakan istilah bisnis.

Object SHOULD mempunyai nama yang mudah dipahami.

Object MAY mempunyai Description.

Object MAY mempunyai Icon.

Object MAY mempunyai Category.

---

# Examples

Object

Customer

Purpose

Mengelola informasi pelanggan.

Fields

Customer Name

Phone Number

Email Address

Customer Type

Registration Date

---

Object

Asset
