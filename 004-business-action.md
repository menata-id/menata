# Business Action

Version

0.1 Draft

Status

Draft

---

# Purpose

Business Action adalah Grammar BDL yang mendeskripsikan suatu tindakan bisnis yang mempunyai makna bagi organisasi.

Business Action bukan tombol.

Business Action bukan HTTP Method.

Business Action bukan fungsi program.

Business Action merupakan representasi dari aktivitas bisnis.

---

# Philosophy

Business tidak mengenal.

POST

PUT

DELETE

Business mengenal.

Approve Expense

Register Customer

Borrow Asset

Complete Inspection

Assign Task

Issue Permit

Business Action menjelaskan apa yang dilakukan oleh bisnis.

Runtime menentukan bagaimana tindakan tersebut dijalankan.

---

# Definition

Business Action adalah Grammar yang mendeskripsikan satu aktivitas bisnis terhadap satu atau lebih Business Object.

Business Action harus mempunyai tujuan bisnis yang jelas.

Jika suatu tindakan tidak mempunyai makna bisnis,

maka tindakan tersebut bukan Business Action.

---

# Characteristics

Business Action:

- mempunyai tujuan bisnis
- menggunakan satu atau lebih Business Object
- dapat dijalankan oleh Actor
- dapat memiliki Preconditions
- dapat memiliki Postconditions
- dapat memicu Workflow
- dapat memicu Rule
- dapat menghasilkan Event

Business Action tidak menentukan implementasi teknis.

---

# Identity

Setiap Business Action mempunyai Identity.

Identity bersifat unik dalam satu Workspace.

Contoh.

Register Customer

Approve Expense

Borrow Asset

Return Asset

Complete Inspection

Issue Certificate

---

# Required Properties

Business Action wajib memiliki.

Name

Code

Purpose

Minimal satu Business Object

---

# Optional Properties

Description

Category

Tags

Priority

Localization

Version

---

# Business Objects

Business Action dapat menggunakan satu atau lebih Business Object.

Contoh.

Borrow Asset

menggunakan.

Employee

Asset

Approval

---

Issue Purchase Order

menggunakan.

Supplier

Purchase Order

Purchase Item

Approval

---

Business Action tidak dimiliki oleh Business Object.

Business Action menggunakan Business Object.

---

# Actor

Business Action dijalankan oleh Actor.

Actor dapat berupa.

Person

Team

Department

System

AI Agent

External System

IoT Device

Runtime menentukan identitas Actor.

Business Action hanya mengetahui peran bisnisnya.

---

# Preconditions

Business Action dapat memiliki syarat sebelum dijalankan.

Contoh.

Expense telah dibuat.

Asset tersedia.

Customer aktif.

Inspection belum selesai.

Jika Preconditions tidak terpenuhi,

Business Action tidak boleh dijalankan.

---

# Postconditions

Business Action dapat menghasilkan kondisi baru.

Contoh.

Expense menjadi Approved.

Asset menjadi Borrowed.

Inspection menjadi Completed.

Customer menjadi Active.

Postcondition menjelaskan hasil bisnis.

Bukan implementasi.

---

# Produced Events

Business Action dapat menghasilkan Event.

Contoh.

CustomerRegistered

ExpenseApproved

InspectionCompleted

AssetBorrowed

PurchaseOrderIssued

Event dapat digunakan oleh Workflow, Rule, Automation, maupun sistem lain.

---

# Workflow

Business Action dapat memicu perubahan Workflow.

Contoh.

Approve Expense

↓

Expense Status

Draft

↓

Approved

Business Action tidak mendefinisikan Workflow.

Workflow merupakan Grammar tersendiri.

---

# Rules

Business Action dapat menggunakan Rule.

Contoh.

Expense Approved

↓

Create Journal

↓

Notify Finance

↓

Update Budget

Business Action tidak mendefinisikan Rule.

Rule merupakan Grammar tersendiri.

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

Menjalankan Business Action.

Menghasilkan Event.

Memperbarui Workflow.

Menjalankan Rule.

Menyimpan perubahan pada Business Object.

Runtime tidak mengetahui tujuan bisnis Business Action.

---

# AI Responsibility

AI bertanggung jawab.

Mengusulkan Business Action.

Mengusulkan Business Object yang digunakan.

Mengusulkan Preconditions.

Mengusulkan Postconditions.

Mengusulkan Workflow.

Mengusulkan Rule.

AI tidak menentukan implementasi Runtime.

---

# Human Responsibility

Business Analyst bertanggung jawab.

Menentukan apakah Business Action memang mempunyai makna bisnis.

Menentukan tujuan.

Menentukan Actor.

Menentukan hasil yang diharapkan.

---

# Validation Rules

Runtime harus memastikan.

Name tidak kosong.

Code unik.

Minimal satu Business Object digunakan.

Purpose tersedia.

Preconditions valid.

Postconditions valid.

---

# Constraints

Business Action tidak boleh mengetahui.

HTML

CSS

JavaScript

React

Vue

Flutter

Go

Python

SQL

Database

REST API

GraphQL

Docker

Infrastructure

Seluruh implementasi merupakan tanggung jawab Runtime.

---

# Compatibility

Perubahan berikut kompatibel.

Mengubah Description.

Menambah Tags.

Menambah Documentation.

Perubahan berikut memerlukan analisis.

Mengubah Business Object.

Mengubah Preconditions.

Mengubah Postconditions.

Menghapus Business Action.

---

# Versioning

Business Action mengikuti versi Business Definition Language.

Runtime harus menjaga kompatibilitas.

---

# Example

Business Action

Register Customer

Purpose

Mendaftarkan pelanggan baru.

Business Objects

Customer

Address

Agreement

Actor

Customer Service

Produces Event

CustomerRegistered

---

Business Action

Approve Expense

Purpose

Menyetujui pengajuan biaya.

Business Objects

Expense

Approval

Actor

Manager

Produces Event

ExpenseApproved

---

Business Action

Borrow Asset

Purpose

Meminjam aset perusahaan.

Business Objects

Employee

Asset

Actor

Employee

Produces Event

AssetBorrowed

---

# Notes

Business Action merupakan representasi aktivitas bisnis.

Business Action tidak menjelaskan implementasi.

Business Action tidak menjelaskan UI.

Business Action tidak menjelaskan API.

Business Action tidak menjelaskan Database.

Business Action hanya menjelaskan tindakan bisnis.

---

# Future Extension

Composite Action

Long Running Action

Distributed Action

Scheduled Action

Collaborative Action

AI Generated Action

Saga Action

Compensating Action

Tanpa mengubah definisi dasar bahwa Business Action adalah representasi tindakan bisnis.
