# Business OS Core Principles

Version 0.1 Draft

---

# Introduction

Business OS dibangun berdasarkan seperangkat prinsip.

Prinsip ini menjadi pedoman dalam setiap keputusan arsitektur.

Jika suatu keputusan bertentangan dengan prinsip ini, maka keputusan tersebut harus dipertanyakan.

---

# Principle 1

## Business First

Business OS dibangun untuk menyelesaikan masalah bisnis.

Bukan untuk mendemonstrasikan teknologi.

Teknologi dapat berubah.

Proses bisnis selalu menjadi fokus utama.

---

# Principle 2

## Metadata First

Semua hal harus terlebih dahulu dipertimbangkan sebagai Metadata.

Jangan menulis Runtime baru apabila Metadata masih mampu merepresentasikan kebutuhan tersebut.

Pertanyaan pertama setiap fitur baru adalah:

> Apakah ini masih dapat dijelaskan sebagai Metadata?

Jika Ya,

jangan tambah kode.

---

# Principle 3

## Runtime is Generic

Runtime tidak mengetahui bisnis user.

Runtime tidak mengetahui CRM.

Runtime tidak mengetahui Accounting.

Runtime tidak mengetahui Inventory.

Runtime hanya mengetahui:

- Metadata
- Runtime Services
- Platform Services

---

# Principle 4

## Everything is an Object

Semua data bisnis direpresentasikan sebagai Business Object.

Contoh:

Customer

Supplier

Invoice

Meeting

Course

Knowledge

Inspection

Employee

Asset

Semuanya memiliki bentuk yang sama.

Object

↓

Fields

↓

Relations

↓

Metadata

---

# Principle 5

## Everything is a View

Data tidak memiliki tampilan bawaan.

Satu Business Object dapat memiliki banyak View.

Contoh:

Table

Card

Kanban

Calendar

Timeline

Chart

Map

Dashboard

Semua View dibuat dari Metadata.

---

# Principle 6

## Everything is a Workflow

Setiap Object dapat memiliki Workflow.

Workflow bukan fitur khusus.

Workflow adalah Metadata.

Contoh:

Draft

↓

Review

↓

Approved

↓

Closed

---

# Principle 7

## Rules are Declarative

Business Rule tidak ditulis menggunakan source code.

Business Rule dijelaskan menggunakan Metadata.

Contoh:

WHEN

Expense Approved

THEN

Create Journal

THEN

Notify Finance

Runtime yang menjalankan Rule.

---

# Principle 8

## UI is Metadata

UI tidak dibuat menggunakan HTML secara manual.

UI dijelaskan menggunakan Metadata.

Runtime memilih Renderer yang sesuai.

Contoh:

Desktop

↓

Table

Mobile

↓

Card

Watch

↓

Compact View

---

# Principle 9

## AI is Optional

Business OS tidak bergantung pada AI tertentu.

User dapat menggunakan:

ChatGPT

Claude

Gemini

DeepSeek

Local LLM

Wizard

Manual Editor

Semuanya menghasilkan Metadata yang sama.

---

# Principle 10

## Open Specification

Spesifikasi Business OS bersifat terbuka.

Siapa pun dapat membuat:

Runtime

CLI

SDK

AI

Recipe

Platform Service

selama mengikuti Specification.

---

# Principle 11

## Convention over Configuration

Business OS menyediakan default.

User hanya mengubah jika diperlukan.

AI selalu menghasilkan konfigurasi yang mengikuti Convention.

---

# Principle 12

## Composition over Customization

Business OS lebih memilih menyusun Object yang sudah ada.

Bukan membuat Runtime baru.

Contoh:

CRM

=

Lead

+

Customer

+

Activity

+

Task

+

Dashboard

Bukan CRM Engine.

---

# Principle 13

## Platform Services are Universal

Platform Service tidak mengetahui domain bisnis.

Platform Service hanya menyediakan kemampuan.

Contoh:

Identity

Storage

Notification

Communication

PDF

Search

AI

GIS

Payment

Realtime

Media

---

# Principle 14

## Recipes are Knowledge

Recipe bukan kode.

Recipe adalah kumpulan Metadata.

Recipe dapat:

dipasang

dibagikan

diperbarui

dikembangkan

oleh komunitas.

---

# Principle 15

## Human Readable

Metadata harus mudah dibaca manusia.

Business Analyst harus dapat memahami Metadata.

AI harus dapat menghasilkan Metadata.

Developer harus dapat mengimplementasikan Runtime.

---

# Principle 16

## Long-term Compatibility

Metadata Version 1 harus tetap dapat dijalankan oleh Runtime di masa depan.

Compatibility lebih penting daripada fitur baru.

---

# Summary

Business OS dibangun berdasarkan empat pilar utama.

Business Knowledge

↓

Metadata

↓

Runtime

↓

Platform Services

Source Code bukan pusat sistem.

Metadata adalah pusat sistem.
