# Business OS Core Concepts

Version 0.1

---

Business OS dibangun dari sejumlah konsep dasar.

Semua fitur di dalam platform harus dapat dijelaskan menggunakan konsep-konsep berikut.

Jika suatu fitur tidak dapat dijelaskan menggunakan konsep ini, maka konsep tersebut harus ditambahkan terlebih dahulu sebelum Runtime dikembangkan.

---

# Concept 1

Business Object

Business Object adalah representasi dari sesuatu yang memiliki makna bisnis.

Contoh:

Customer

Invoice

Asset

Employee

Meeting

Task

Course

Knowledge

Inspection

Observation

Business Object bukan tabel database.

Business Object adalah konsep bisnis.

---

# Concept 2

Field

Business Object terdiri dari Field.

Field merepresentasikan atribut.

Contoh:

Customer

- Name

- Email

- Phone

- Address

---

# Concept 3

Relationship

Business Object dapat saling berhubungan.

Contoh:

Customer

↓

Invoice

↓

Payment

Relationship dijelaskan menggunakan Metadata.

---

# Concept 4

Form

Form adalah cara membuat atau mengubah Object.

Form tidak mengetahui database.

Form hanya mengetahui Metadata.

---

# Concept 5

Workflow

Workflow menjelaskan perubahan Status.

Draft

↓

Review

↓

Approved

↓

Closed

Workflow tidak mengetahui bisnis.

Workflow hanya mengetahui State.

---

# Concept 6

Rule

Rule menjelaskan perilaku sistem.

WHEN

Expense Approved

THEN

Create Journal

THEN

Notify Manager

Rule bersifat deklaratif.

---

# Concept 7

View

View menjelaskan bagaimana Object ditampilkan.

Contoh:

Table

Card

Grid

Kanban

Timeline

Calendar

Map

Chart

Tree

Gallery

Dashboard

Object tidak memiliki tampilan tetap.

View dapat berubah.

---

# Concept 8

Dashboard

Dashboard adalah kumpulan View.

Dashboard tidak memiliki Data.

Dashboard hanya mengatur Layout.

---

# Concept 9

Recipe

Recipe adalah kumpulan Metadata.

Recipe dapat diinstal.

Recipe dapat dihapus.

Recipe dapat diperbarui.

Recipe dapat dibagikan.

---

# Concept 10

Workspace

Workspace adalah kumpulan Recipe.

Contoh:

General Affairs

↓

Safety

↓

Inspection

↓

Asset

↓

Learning

↓

Dashboard

Workspace menjadi batas kolaborasi.

---

# Concept 11

Platform Service

Platform Service menyediakan kemampuan teknis.

Contoh:

Authentication

Storage

Notification

Communication

Search

PDF

AI

GIS

Realtime

Media

Platform Service tidak mengetahui domain bisnis.

---

# Concept 12

Runtime

Runtime adalah mesin yang menjalankan Metadata.

Runtime tidak mengetahui bisnis.

Runtime hanya mengetahui:

Metadata

Renderer

Workflow

Rule

Platform Service

---

# Concept 13

Metadata

Metadata adalah representasi formal dari Pengetahuan Bisnis.

Metadata merupakan Source of Truth.

Runtime berjalan berdasarkan Metadata.

AI menghasilkan Metadata.

Developer mengembangkan Runtime.

---

Business OS bukan Runtime.

Business OS adalah Metadata.

Runtime hanyalah implementasi.
