# Panduan Menulis Menata Language

Panduan ini menjelaskan cara menulis Business Knowledge dalam Menata Language — dari nol sampai selesai.

**Untuk siapa:** Domain expert, business analyst, siapapun yang memahami cara kerja bisnis.
**Tidak dibutuhkan:** Pengetahuan pemrograman.

Referensi formal: `specification/` — panduan ini adalah versi praktisnya.

**Langkah setelah ini:** panduan developer menerjemahkan `.menata` menjadi Runtime Metadata (YAML → SQL) —
[`guides/writing-runtime-metadata.md`](https://github.com/menata-id/menata-runtime/blob/main/guides/writing-runtime-metadata.md)
di [menata-id/menata-runtime](https://github.com/menata-id/menata-runtime).

---

## Posisi `.menata` dalam Arsitektur

```
Business Reality
        │
        ▼
Business Knowledge (.menata)   ← Anda di sini
        │
        ▼
Runtime Metadata (YAML → SQL)
        │
        ▼
Menata Runtime (Go prototype)
        │
        ▼
Application
```

`.menata` mendeskripsikan **apa yang bisnis tahu** — objek apa saja yang ada, field apa saja yang
dimiliki, kejadian apa saja yang bisa terjadi, aturan apa yang berlaku, siapa boleh melakukan apa,
dan tampilan apa saja yang dibutuhkan. Tidak lebih dari itu.

`.menata` **tidak** menyebutkan: tabel database, tipe kolom SQL, endpoint API, atau detail teknis
lain. Kalau sebuah kalimat butuh pengetahuan tentang cara runtime bekerja untuk ditulis, itu bukan
Business Knowledge lagi — itu sudah masuk Runtime Metadata, dan bukan tempatnya di sini.

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

## Struktur Satu Object (ringkasan)

Setiap file `.menata` mendeskripsikan satu **Object** (nanti direalisasikan sebagai satu Machine).
Strukturnya selalu lima bagian, urutan tetap — pakai ini sebagai lembar acuan cepat, langkah-langkah
lengkapnya ada di bawah:

```
<Nama Object>

Fields

- <Nama Field> : <Tipe>
...

Events

When <Nama Event>

    <aksi>
    <aksi>

Constraints

- <aturan>.

Permissions

<Role>

- <Event yang boleh dijalankan>

Views

- <Nama View> : <Tipe View>
```

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
- Leave Type : Annual Leave | Sick Leave | Emergency Leave | Unpaid Leave
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

`User` dan `File` ditulis seperti tipe biasa, tapi sebenarnya adalah **rujukan** ke sesuatu yang
punya identitasnya sendiri (siapa penggunanya, file yang mana) — Anda tidak perlu tahu detail ini
saat menulis `.menata`, cukup tulis tipenya.

### Tips memilih tipe

Ini heuristik, bukan aturan wajib. Kalau ragu, jangan macet di sini — tulis tebakan terbaik Anda dan
lanjutkan; presisi tipe field bukan tanggung jawab Business Knowledge, dan boleh dipertajam nanti saat
diterjemahkan ke Runtime Metadata.

- Satu Field = satu informasi. Jangan gabungkan dua informasi dalam satu Field.
- Siapa yang mengajukan/bertanggung jawab → `User`

Kalau ragu antara pilihan tetap (`A | B | C`) dan referensi ke Object lain, dua pertanyaan ini bisa
membantu — tapi hasilnya tetap tebakan bisnis, bukan keputusan teknis final:

1. Apakah nilai ini menamai sesuatu yang terasa punya "kehidupan sendiri" bagi bisnis (dipakai ulang
   di tempat lain, dikelola terpisah, punya riwayat) — atau cuma label yang menempel pada baris ini?
2. Kalau cuma label: apakah himpunan pilihannya kecil dan jarang berubah? Kalau ya, `A | B | C`
   biasanya cukup. Kalau nilai itu sebetulnya konsep bisnis sendiri, tulis saja nama Object-nya
   sebagai tipe (lihat "Object References" di `specification/002-field.md`) — tidak masalah kalau
   ternyata developer nanti memilih merealisasikannya secara berbeda.

Bagi yang ingin kajian lebih dalam (opsional, sudah masuk wilayah Machine Interpretation):
[`benchmarks/005-field-modeling-decision-framework.md`](https://github.com/menata-id/menata-runtime/blob/main/benchmarks/005-field-modeling-decision-framework.md)
di [menata-id/menata-runtime](https://github.com/menata-id/menata-runtime).

### Field Status

Field `Status` boleh ditulis jika organisasi perlu mendefinisikan nilai-nilainya secara eksplisit:

```
- Status : Draft | Submitted | Approved | Rejected | Cancelled
```

Nilai pertama dalam daftar adalah keadaan awal record saat dibuat. `Status` **tidak pernah** diisi
langsung oleh user lewat form — nilainya selalu diset oleh Events. Nilai Status yang muncul di
Events harus konsisten dengan daftar ini — lihat Langkah 3.

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
| `<Field> <Nilai>` | Set field lain ke sebuah nilai (mis. `Approved By Current User`) |

### Kondisi di dalam Event — `if`

```
Every Day 07:00

    if Next Due Date = Today

        Status Due

        Notify Assignee
```

Baris `if <Field> = <Nilai>` membuat aksi di bawahnya (diindentasi lebih dalam) hanya berjalan kalau
kondisinya benar. Dua baris `if` yang ditumpuk berarti keduanya harus benar sekaligus (AND).

### Event berjadwal — `Every Day <Jam>`

Selain `When <Nama Event>` (dipicu aksi user), Event juga bisa dipicu jadwal:

```
Every Day 08:00

    if Due Date is before Today

        Status Overdue
```

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

Artinya: `Attachment` wajib diisi, tapi hanya kalau `Design Type` adalah `Banner`. Baris `if` harus
diindentasi dengan 4 spasi, diletakkan setelah baris constraint dengan satu baris kosong di antara
keduanya.

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
- Jika sebuah Event tidak ada di Permissions, tidak ada yang bisa memicunya — setiap Event yang ada
  di **Events** harus disebutkan di sini untuk setidaknya satu role

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
| `Report` | Ringkasan/agregat lintas banyak record |

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

## Checklist Sebelum Menyerahkan ke Developer

- [ ] Nama Object jelas dan singular (`Leave Request`, bukan `Leave Requests`)
- [ ] Setiap field punya tipe yang jelas — kalau ragu antara pilihan tertutup vs rujukan, lihat
      §"Tips memilih tipe" di Langkah 2
- [ ] Ada field `Status` dengan daftar keadaan lengkap, nilai pertama = keadaan awal
- [ ] Setiap Event mengubah `Status` (atau menjelaskan kenapa tidak perlu)
- [ ] Setiap Event yang ada di **Events** juga muncul di **Permissions**, minimal untuk satu role
- [ ] Constraint ditulis sebagai kalimat lengkap, bukan pseudocode
- [ ] View minimal punya satu Form (input) dan satu Detail (tampilan lengkap)

---

## Referensi

Untuk definisi formal setiap Grammar, baca `specification/`:

- `specification/001-object.md` — Object
- `specification/002-field.md` — Field
- `specification/003-event.md` — Event
- `specification/004-constraint.md` — Constraint
- `specification/005-permission.md` — Permission
- `specification/006-view.md` — View

Untuk langkah setelah `.menata` — menerjemahkannya ke Runtime Metadata dan menjalankannya — lihat
[menata-id/menata-runtime](https://github.com/menata-id/menata-runtime):

- [`guides/writing-runtime-metadata.md`](https://github.com/menata-id/menata-runtime/blob/main/guides/writing-runtime-metadata.md) — cara developer menerjemahkan `.menata` menjadi Runtime Metadata (YAML → SQL)
- [`runtime-metadata-schema.md`](https://github.com/menata-id/menata-runtime/blob/main/runtime-metadata-schema.md) — daftar lengkap tipe field dan konfigurasinya
- [`benchmarks/005-field-modeling-decision-framework.md`](https://github.com/menata-id/menata-runtime/blob/main/benchmarks/005-field-modeling-decision-framework.md) — kerangka lengkap memilih tipe field, termasuk kenapa `Money`/`User`/`File` adalah "reference sugar"
- [`prototype/go/docs/examples/`](https://github.com/menata-id/menata-runtime/tree/main/prototype/go/docs/examples) — puluhan contoh `.menata` nyata lintas domain (HR, akuntansi, inventori, media sosial, rumah sakit, dan lainnya) — cara tercepat belajar polanya
