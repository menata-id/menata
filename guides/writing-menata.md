# Panduan Menulis Menata Language

Panduan ini menjelaskan cara menulis Business Knowledge dalam Menata Language — dari nol sampai selesai.

**Untuk siapa:** Domain expert, business analyst, siapapun yang memahami cara kerja bisnis.  
**Tidak dibutuhkan:** Pengetahuan pemrograman.

Referensi formal: `specification/` — panduan ini adalah versi praktisnya.

---

## Prinsip Dasar

Sebelum mulai menulis, ingat satu prinsip ini:

> **Tulis apa yang bisnis tahu. Bukan bagaimana software bekerja.**

Menata Language mendeskripsikan Business Knowledge — pengetahuan organisasi tentang cara kerja bisnis. Bukan database, bukan kode program, bukan UI.

Pertanyaan yang benar:
- "Informasi apa yang dibutuhkan untuk memproses cuti?"
- "Siapa yang boleh menyetujui pengajuan ini?"
- "Aturan bisnis apa yang selalu harus dipenuhi?"

Pertanyaan yang salah:
- "Kolom apa yang perlu ditambahkan ke tabel?"
- "Bagaimana form ini akan terlihat di browser?"
- "Query apa yang akan dijalankan?"

---

## Langkah 1 — Kenali Object

**Object = satu konsep bisnis yang bermakna bagi organisasi.**

Mulai dengan bertanya: *"Apa yang sedang dikelola atau diproses di sini?"*

Nama Object ditulis dalam bahasa bisnis, bukan teknis.

```
✅ Leave Request
✅ Purchase Order
✅ Design Request
✅ Customer Complaint

❌ LeaveRequestModel
❌ tbl_purchase
❌ RequestDTO
```

Satu Object = satu tanggung jawab. Jika terasa terlalu besar, pecah menjadi dua Object.

---

## Langkah 2 — Tentukan Fields

**Fields = informasi apa yang dibutuhkan untuk mendeskripsikan Object ini.**

Tanya: *"Apa saja yang perlu dicatat atau diketahui tentang [Object] ini?"*

```
Leave Request

Fields

- Employee : User
- Leave Type : Annual Leave | Sick Leave | Emergency Leave
- Start Date : Date
- End Date : Date
- Reason : Rich Text
```

### Tipe Field

| Tulis | Artinya |
|-------|---------|
| `Text` | Teks pendek (nama, judul, kode) |
| `Rich Text` | Teks panjang (deskripsi, catatan, alasan) |
| `Number` | Angka (kuantitas, nilai) |
| `Money` | Nilai uang |
| `Date` | Tanggal |
| `Time` | Waktu |
| `Date Time` | Tanggal dan waktu |
| `Duration` | Rentang waktu |
| `Boolean` | Ya / Tidak |
| `User` | Referensi ke pengguna dalam sistem |
| `File` | Lampiran (dokumen, foto) |
| `A \| B \| C` | Pilihan dari daftar tetap |
| `NamaObject` | Referensi ke Object lain |

### Tips memilih tipe

- Satu Field = satu informasi. Jangan gabungkan dua informasi dalam satu Field.
- Siapa yang mengajukan/bertanggung jawab → `User`

Untuk memilih antara pilihan tetap (`A | B | C`) dan referensi ke Object lain, tanyakan berurutan:

1. **Apakah nilai ini menamai sesuatu yang punya identitas sendiri** (bisa dipakai ulang, punya riwayat), atau cuma label yang menempel pada baris ini?
   - Cuma label yang menempel → lanjut ke langkah 2.
   - Punya identitas sendiri → seharusnya jadi Object tersendiri, dirujuk lewat Field bertipe nama Object itu (lihat "Object References" di atas).
2. **Apakah pilihannya kecil, tetap, dan tidak akan bertambah tanpa mengubah dokumen ini?**
   - Ya → `A | B | C`
   - Tidak (akan bertambah lewat admin, dipakai berulang di tempat lain) → seharusnya Object tersendiri.

Kajian lengkap beserta pohon keputusan formal dan contoh penerapannya: `runtime/benchmarks/005-field-modeling-decision-framework.md`.

### Field Status

Field `Status` boleh ditulis jika organisasi perlu mendefinisikan nilai-nilainya secara eksplisit. Nilai Status biasanya muncul dari Events — lihat Langkah 3.

---

## Langkah 3 — Definisikan Events

**Events = sesuatu yang terjadi dalam bisnis yang mengubah keadaan Object.**

Tanya: *"Apa saja yang bisa terjadi pada [Object] ini? Apa yang dilakukan orang terhadapnya?"*

```
Events

When Submit

    Status Submitted

When Approve

    Status Approved

    Notify Employee

When Reject

    Status Rejected

    Notify Employee

When Cancel

    Status Cancelled
```

### Format Event

```
When <Nama Event>

    <Respon bisnis>
    <Respon bisnis>
```

### Respon yang umum dipakai

| Respon | Arti |
|--------|------|
| `Status <Nilai>` | Ubah status menjadi nilai tersebut |
| `Notify <Role>` | Kirim notifikasi ke role |
| `Record <Nama>` | Catat ke log atau register |
| `Create <Object>` | Buat record di Object lain |

### Tips menulis Event

- Nama Event = kata kerja bisnis singkat: `Submit`, `Approve`, `Reject`, `Complete`
- Respon ditulis dalam bahasa bisnis, bukan kode. "Notify Manager" bukan "send_email()"
- Satu Event boleh punya lebih dari satu respon
- Urutan Event dalam dokumen tidak menentukan urutan eksekusi — Events berdiri sendiri

---

## Langkah 4 — Tuliskan Constraints

**Constraints = aturan bisnis yang harus SELALU dipenuhi.**

Tanya: *"Aturan apa yang tidak boleh dilanggar? Kapan pengajuan ini tidak valid?"*

```
Constraints

- Reason is required.
- Start Date must be after today.
- End Date must be after Start Date.
```

### Format Constraint

```
- <Kalimat aturan bisnis.>
```

Kalimat diakhiri tanda titik. Ditulis dalam bahasa bisnis yang jelas.

### Constraint kondisional

Constraint boleh hanya berlaku dalam kondisi tertentu:

```
- Attachment is required.

    if Design Type = Banner
```

Baris `if` harus diindentasi dengan 4 spasi, diletakkan setelah baris constraint dengan satu baris kosong di antara keduanya.

### Tips menulis Constraint

- Tulis aturan sebagaimana orang bisnis akan menjelaskannya: "Amount must be greater than zero."
- Jangan tulis cara enforcenya: ❌ "Validasi bahwa field amount tidak boleh kosong atau nol"
- Constraint yang selalu berlaku (bukan hanya saat event tertentu) lebih kuat sebagai Constraint daripada sebagai kondisi Event

---

## Langkah 5 — Tetapkan Permissions

**Permissions = siapa (role bisnis) boleh melakukan Event apa.**

Tanya: *"Siapa yang bertanggung jawab melakukan setiap Event ini?"*

```
Permissions

Employee

- Submit
- Cancel

Manager

- Approve
- Reject
```

### Format Permission

```
<Nama Role>

- <Event>
- <Event>
```

### Tips menulis Permission

- Role = jabatan atau fungsi bisnis, bukan nama user: `Employee`, `Manager`, `Finance`, `HR`
- Satu Role boleh punya banyak Event
- Satu Event boleh dimiliki lebih dari satu Role (misalnya `View` bisa dimiliki semua role)
- Jika sebuah Event tidak ada di Permissions, tidak ada yang bisa memicunya

---

## Langkah 6 — Tentukan Views

**Views = bagaimana Object ini perlu dilihat dan digunakan.**

Tanya: *"Tampilan apa yang dibutuhkan orang yang bekerja dengan Object ini?"*

```
Views

- Leave Request Form : Form
- My Requests : List
- Pending Approvals : List
- Leave Request Detail : Detail
```

### Tipe View

| Tipe | Kegunaan |
|------|----------|
| `Form` | Input untuk membuat atau mengubah record |
| `List` | Daftar banyak record |
| `Detail` | Tampilan lengkap satu record |
| `Summary` | Ringkasan |
| `Dashboard` | Metrik dan grafik |
| `Calendar` | Tampilan berbasis tanggal |
| `Timeline` | Tampilan kronologis |

### Tips menulis View

- Nama View = nama yang orang bisnis pakai: "My Requests", "Pending Approvals", "Design Queue"
- Buat View sebanyak kebutuhan bisnis, tidak perlu dibatasi
- Detail konfigurasi View (kolom apa yang tampil, urutan, filter) ditentukan di Runtime Metadata — bukan di sini

---

## Contoh Lengkap: Leave Request

Berikut dokumen Leave Request lengkap, ditulis mengikuti langkah-langkah di atas.

```
Leave Request

Fields

- Employee : User
- Leave Type : Annual Leave | Sick Leave | Emergency Leave | Unpaid Leave
- Start Date : Date
- End Date : Date
- Reason : Rich Text

Events

When Submit

    Status Submitted

When Approve

    Status Approved

    Notify Employee

When Reject

    Status Rejected

    Notify Employee

When Cancel

    Status Cancelled

Constraints

- Reason is required.
- Start Date must be after today.

Permissions

Employee

- Submit
- Cancel

Manager

- Approve
- Reject

Views

- Leave Request Form : Form
- My Requests : List
- Pending Approvals : List
- Leave Request Detail : Detail
```

---

## Kesalahan Umum

**1. Menulis nama teknis**
```
❌ Fields
   - leave_type_id : Integer
   - created_by_user_id : UUID

✅ Fields
   - Leave Type : Annual Leave | Sick Leave
   - Employee : User
```

**2. Menulis cara implementasi di Constraints**
```
❌ - Validasi bahwa field Reason tidak kosong sebelum menyimpan ke database.

✅ - Reason is required.
```

**3. Event terlalu granular (tingkat kode, bukan bisnis)**
```
❌ When save_draft_to_database
❌ When validate_form

✅ When Submit
✅ When Approve
```

**4. Satu Object terlalu besar**

Jika satu Object punya lebih dari 10 Field atau 8 Event, pertimbangkan untuk memecahnya. Biasanya ada dua konsep bisnis yang digabungkan.

**5. Field Status ditulis dengan nilai yang tidak konsisten dengan Events**

Nilai Status yang muncul di Events harus konsisten. Jika `When Submit` → `Status Submitted`, maka nilai `Submitted` ada di daftar Status.

---

## Referensi

Untuk definisi formal setiap Grammar, baca `specification/`:

- `specification/001-object.md` — Object
- `specification/002-field.md` — Field
- `specification/003-event.md` — Event
- `specification/004-constraint.md` — Constraint
- `specification/005-permission.md` — Permission
- `specification/006-view.md` — View
