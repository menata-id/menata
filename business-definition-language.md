# Business Definition Language (BDL)

Version 0.1 Draft

---

# Introduction

Business Definition Language (BDL) adalah bahasa deklaratif yang digunakan untuk mendeskripsikan aplikasi bisnis.

BDL bukan bahasa pemrograman.

BDL tidak menjelaskan bagaimana aplikasi dijalankan.

BDL hanya menjelaskan apa yang diketahui oleh bisnis.

Runtime bertanggung jawab menerjemahkan BDL menjadi aplikasi yang berjalan.

AI bertanggung jawab membantu menghasilkan BDL.

Business Analyst bertanggung jawab mendeskripsikan proses bisnis.

---

# Philosophy

Traditional Software

Business

↓

Source Code

↓

Application

Business OS

Business

↓

BDL

↓

Runtime

↓

Application

Source Code bukan Source of Truth.

BDL adalah Source of Truth.

---

# Design Goals

BDL harus:

- mudah dibaca manusia

- mudah ditulis AI

- mudah divalidasi

- mudah dibandingkan (diff)

- mudah di-versioning

- mudah di-review

- independen terhadap Runtime

- independen terhadap Database

- independen terhadap Framework UI

---

# What BDL Describes

BDL hanya menjelaskan pengetahuan bisnis.

BDL tidak menjelaskan implementasi teknis.

---

BDL menjelaskan:

Business Objects

Fields

Relationships

Workflow

Rules

Permissions

Views

Dashboard

Automation

Localization

Policies

Recipes

Workspace

---

BDL tidak menjelaskan:

Go

Python

JavaScript

SQL

HTML

CSS

REST API

Database Index

Docker

Redis

Kubernetes

Infrastructure

---

# Example

Application

Customer Management

↓

Object

Customer

↓

Fields

Name

Phone

Address

↓

Workflow

Prospect

↓

Customer

↓

Inactive

↓

View

Table

↓

Dashboard

Customer Summary

---

Semua informasi tersebut merupakan BDL.

Runtime menentukan bagaimana aplikasi dijalankan.

---

# Fundamental Principle

Business Knowledge

↓

BDL

↓

Runtime

↓

Application

---

# Core Building Blocks

Business OS hanya mengenal sejumlah Building Block.

Application

Workspace

Recipe

Business Object

Field

Relationship

Form

Workflow

Rule

View

Dashboard

Permission

Automation

Policy

Platform Service

---

Semua aplikasi harus dapat dijelaskan menggunakan Building Block tersebut.

---

# Declarative

BDL bersifat deklaratif.

BDL menjelaskan:

WHAT

bukan

HOW

Contoh.

WHEN

Expense Approved

THEN

Create Journal

BDL tidak menjelaskan algoritma.

Runtime menentukan implementasi.

---
