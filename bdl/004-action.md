# Action

Version

0.1 Draft

Status

Draft

---

# Purpose

Action adalah Grammar BDL yang mendeskripsikan suatu kemampuan atau aktivitas yang dapat dilakukan terhadap satu atau lebih Object.

Action merepresentasikan maksud bisnis.

Action bukan tombol.

Action bukan endpoint API.

Action bukan fungsi program.

Action bukan operasi CRUD.

Runtime menentukan bagaimana Action dijalankan.

---

# Philosophy

Business tidak berpikir dalam istilah:

Create

Update

Delete

Business berpikir dalam istilah:

Approve

Reject

Borrow

Return

Transfer

Assign

Complete

Verify

Publish

Close

Suspend

Activate

Action merepresentasikan bahasa bisnis.

---

# Definition

Action adalah Grammar yang mendeskripsikan satu aktivitas bisnis.

Action selalu mempunyai tujuan bisnis.

Action dapat dijalankan oleh manusia, sistem, maupun AI.

Action tidak menentukan implementasi teknis.

---

# Characteristics

Action:

- mempunyai tujuan bisnis
- menggunakan satu atau lebih Object
- dapat dijalankan oleh Actor
- dapat memiliki Preconditions
- dapat memiliki Postconditions
- dapat menghasilkan Event
- dapat memicu Workflow
- dapat menggunakan Rule

---

# Identity

Setiap Action mempunyai Identity.

Identity bersifat unik dalam satu Workspace.

Contoh.

Approve

Reject

Borrow

Return

Transfer

Assign

Verify

Publish

Close

Archive

---

# Required Properties

Action wajib memiliki.

Name

Code

Purpose

Minimal satu Object

---

# Optional Properties

Description

Category

Tags

Localization

Priority

Version

---

# Objects

Action menggunakan satu atau lebih Object.

Contoh.

Borrow

Objects

Employee

Asset

---

Approve

Objects

Expense

Approval

---

Issue

Objects

Purchase Order

Supplier

Purchase Item

---

Action tidak dimiliki oleh Object.

Action menggunakan Object.

---

# Actor

Action dapat dijalankan oleh.

Person

Team

Department

System

AI Agent

External System

IoT Device

Runtime menentukan identitas Actor.

BDL hanya mendeskripsikan peran bisnis.

---

# Preconditions

Action dapat mempunyai syarat.

Contoh.

Expense masih Draft.

Asset tersedia.

Customer aktif.

Inspection belum selesai.

Jika Preconditions tidak terpenuhi,

Action tidak boleh dijalankan.

---

# Postconditions

Action dapat menghasilkan kondisi baru.

Contoh.

Expense menjadi Approved.

Asset menjadi Borrowed.

Inspection menjadi Completed.

Customer menjadi Active.

Postconditions menjelaskan hasil bisnis.

---

# Produced Events

Action dapat menghasilkan Event.

Contoh.

ExpenseApproved

AssetBorrowed

InspectionCompleted

CustomerActivated

PurchaseOrderIssued

Runtime menerbitkan Event.

Grammar lain dapat menggunakannya.

---

# Workflow

Action dapat memicu perubahan Workflow.

Contoh.

Approve

↓

Draft

↓

Approved

Workflow tetap merupakan Grammar yang terpisah.

---

# Rules

Action dapat menggunakan Rule.

Contoh.

Expense Approved

↓

Create Journal

↓

Notify Finance

↓

Update Budget

Rule menentukan perilaku sistem.

Action hanya mendeskripsikan aktivitas bisnis.

---

# Lifecycle

Draft

↓

Published

↓

Deprecated

↓

Removed

---

# Runtime Responsibility

Runtime bertanggung jawab.

Memvalidasi Preconditions.

Menjalankan Action.

Memperbarui Object.

Menghasilkan Event.

Memicu Workflow.

Menjalankan Rule.

Runtime tidak menentukan tujuan bisnis Action.

---

# AI Responsibility

AI bertanggung jawab.

Mengusulkan Action.

Mengusulkan Object.

Mengusulkan Preconditions.

Mengusulkan Postconditions.

Mengusulkan Event.

AI tidak menentukan implementasi Runtime.

---

# Human Responsibility

Business Analyst bertanggung jawab.

Menentukan apakah Action benar-benar mempunyai makna bisnis.

Menentukan tujuan.

Menentukan hasil yang diharapkan.

Menentukan kapan Action boleh dijalankan.

---

# Validation Rules

Runtime harus memastikan.

Name tersedia.

Code unik.

Minimal satu Object digunakan.

Purpose tersedia.

Preconditions valid.

Postconditions valid.

---

# Constraints

Action tidak boleh mengetahui.

Go

Python

Java

SQL

Database

REST API

GraphQL

HTML

CSS

JavaScript

Docker

Infrastructure

Seluruh implementasi merupakan tanggung jawab Runtime.

---

# Compatibility

Perubahan berikut kompatibel.

Mengubah Description.

Menambah Tags.

Menambah Dokumentasi.

Perubahan berikut memerlukan analisis.

Mengubah Object.

Mengubah Preconditions.

Mengubah Postconditions.

Menghapus Action.

---

# Versioning

Action mengikuti versi BDL.

Runtime harus menjaga kompatibilitas.

---

# Example

Action

Borrow

Purpose

Meminjam aset perusahaan.

Objects

Employee

Asset

Produces Event

AssetBorrowed

---

Action

Approve

Purpose

Menyetujui pengajuan biaya.

Objects

Expense

Approval

Produces Event

ExpenseApproved

---

Action

Complete

Purpose

Menyelesaikan inspeksi.

Objects

Inspection

Finding

Produces Event

InspectionCompleted

---

# Notes

Action mendeskripsikan aktivitas bisnis.

Action tidak mendeskripsikan tampilan.

Action tidak mendeskripsikan API.

Action tidak mendeskripsikan penyimpanan.

Runtime menentukan implementasinya.

---

# Future Extension

Composite Action

Long Running Action

Scheduled Action

Collaborative Action

Distributed Action

Saga Action

Compensating Action

AI Generated Action

Tanpa mengubah definisi dasar bahwa Action merupakan representasi aktivitas bisnis.
