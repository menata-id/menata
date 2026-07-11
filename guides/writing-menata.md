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

Setiap file `.menata` mendeskripsikan satu **Object** (nanti direalisasikan sebagai satu Machine),
disusun dari sampai lima bagian berikut, dalam urutan tetap kalau dipakai — pakai ini sebagai lembar
acuan cepat, langkah-langkah lengkapnya ada di bawah:

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

**Tidak semua bagian wajib ada.** Object cukup memuat bagian yang benar-benar dibutuhkan untuk
mengekspresikan Business Knowledge-nya — kalau sebuah Object tidak punya kejadian yang mengubah
keadaannya (misalnya data master seperti `Chart of Account`, atau Object gabungan seperti `Follow`
pada relasi many-to-many), bagian **Events** boleh dilewati sepenuhnya. Di antara puluhan contoh
`.menata` nyata di `prototype/go/docs/examples/` (menata-runtime), hampir separuhnya tidak punya
bagian Events sama sekali.

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

`File` juga dipakai untuk dokumen yang **dihasilkan** sistem dari sebuah template (misalnya
sertifikat kelulusan), bukan hanya yang diunggah pengguna — dari sisi Business Knowledge keduanya
sama-sama "sebuah file", bedanya siapa yang menghasilkannya adalah detail Machine Interpretation.

### Daftar baris dalam satu Field

Kadang satu Field sebenarnya adalah **daftar baris**, bukan satu nilai — misalnya baris-baris item
dalam sebuah dokumen (pesanan, jurnal akuntansi, daftar konversi satuan). Belum ada grammar formal
untuk ini di Menata Language, tapi polanya sudah dipakai berulang di banyak contoh nyata. Tulis saja
nama kolom-kolomnya di dalam kurung:

```
- Lines : Table of (Account, Debit Amount, Credit Amount, Line Memo)
```

Ini notasi sementara, bukan keputusan final — cukup sampaikan maksud bisnisnya ("baris-baris ini
yang perlu dicatat"), developer yang menerjemahkan tahu cara merealisasikannya di Runtime Metadata.
Jangan khawatir memikirkan bagaimana daftar ini akan disimpan.

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

Menata **tidak membatasi respon pada daftar tertutup** — tulis dengan bahasa bisnis apa pun yang
paling pas untuk menjelaskan apa yang terjadi. Pola-pola berikut sudah terbukti berulang di banyak
Object nyata, jadi pakai sebagai titik awal, bukan daftar lengkap:

| Respon | Arti | Contoh |
|--------|------|--------|
| `Status <Nilai>` | Ubah status menjadi nilai tersebut | `Status Approved` |
| `Notify <Siapa>` | Kirim notifikasi | `Notify Design Team`, `Notify Assignee` |
| `<Field> <Nilai>` | Set field ke sebuah nilai | `Approved By Current User`, `Posting Date Today` |
| `Create <Object>` | Buat record baru di Object lain | `Create Loan`, `Create Order` |
| `Record <Nama>` | Catat ke log atau register | `Record Design Request Register` |
| `Generate <Sesuatu>` | Hasilkan serangkaian record dari satu formula | `Generate Repayment Schedule` |
| `Issue <Object>` | Terbitkan sesuatu (mis. dokumen hasil generate) | `Issue Certificate` |
| `<Field> plus/minus <Nilai>` | Tambah/kurangi nilai sebuah field | `Post Like Count plus 1` |
| `<Field lain lewat rujukan>` | Ubah field milik Object yang dirujuk | `Invoice Status Paid` (dari Payment ke Invoice yang dirujuknya) |

### Baris penjaga (guard) di dalam Event

Sebuah Event boleh menuliskan syarat yang harus benar sebelum ia boleh berlanjut, ditulis sebagai
kalimat aturan biasa — bukan `if`, karena ini bukan cabang kondisional, tapi syarat mutlak:

```
When Post

    Posting Date Today

    Posted By Current User

    Sum of Lines Debit Amount must equal sum of Lines Credit Amount

    Fiscal Period must not be Closed

    Status Posted
```

Aturan yang sama biasanya juga dituliskan ulang di bagian **Constraints** sebagai aturan Object yang
berlaku selalu — dua tempat ini boleh tumpang tindih, karena menjawab dua pertanyaan berbeda: Event
menjawab "apa syarat sebelum aksi ini boleh terjadi", Constraint menjawab "apa yang harus selalu
benar pada Object ini" (lihat Langkah 4).

### Kondisi di dalam Event — `if`

```
Every Day 07:00

    if Next Due Date < Today
    if Status = Due

        Notify Assignee
```

Baris `if <syarat>` membuat aksi di bawahnya (diindentasi lebih dalam) hanya berjalan kalau syaratnya
benar. Dua baris `if` yang ditumpuk pada indentasi yang sama berarti keduanya harus benar sekaligus
(AND). Syarat boleh ditulis dengan berbagai perbandingan bisnis, bukan cuma `=`:

```
if Status = Resolved
if Next Due Date < Today
if Due Date is before Today
if Progress is greater than or equal to 100
if sum of Point Ledger Entry Points for this Member is greater than or equal to 100
if Provider Event ID already exists among Payment Webhook Event
```

Baris terakhir di atas adalah pola pengecekan "sudah pernah terjadi belum" — berguna untuk kejadian
dari luar sistem yang mungkin terkirim dua kali (mis. webhook pembayaran), supaya tidak diproses ulang.

### Event berjadwal — `Every Day <Jam>`

Selain `When <Nama Event>` (dipicu aksi bisnis) dan `Every Day <Jam>` (dipicu jadwal harian), bahasa
ini juga mengizinkan pemicu waktu lain seperti `Every Monday` atau `Every Month`, serta pemicu
berbasis tanggal seperti `When Due Date` atau `When Due Date - 1 Day`. Dalam praktik saat ini,
kebutuhan seperti itu paling sering diekspresikan lewat `Every Day` dikombinasikan dengan `if`:

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

### Pola Constraint lain yang sering muncul

Constraint tidak selalu sesederhana "field ini wajib diisi". Pola-pola berikut sudah terbukti
berulang di banyak Object nyata:

```
# Lintas record dalam satu Object (agregat)
- Sum of Lines Debit Amount must equal sum of Lines Credit Amount.

# Keunikan — mencegah baris duplikat pada relasi many-to-many
- A Follower may follow a given Followee only once.

# Lintas Object, lewat rujukan Field
- Fund Current Balance must be greater than or equal to Amount.

# Terhadap keadaan Object lain
- Fiscal Period must not be Closed.

# Kerahasiaan / siapa boleh melihat
- Salary must be visible only to HR and the Employee.
```

Constraint keunikan ("...only once", "hanya boleh satu X per Y") sangat umum untuk Object relasi
many-to-many (`Follow`, `Like`, `Membership`, `Enrollment`) — kalau Object Anda punya Field yang
merujuk ke dua Object lain sekaligus tanpa satu pun "memiliki" barisnya, kemungkinan besar Anda
butuh constraint semacam ini.

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

### Dua Role khusus

**`System`** — dipakai kalau yang menjalankan Event bukan manusia, melainkan runtime itu sendiri
(mis. Event yang dipicu jadwal, atau webhook dari luar):

```
Permissions

System

- Receive
```

**`Visitor`** — dipakai kalau sebuah View atau Event memang harus bisa diakses tanpa login sama
sekali (mis. halaman blog publik). `Visitor` bukan role dalam organisasi — ia menandai *ketiadaan*
sesi login, bukan salah satu jenisnya:

```
Permissions

Visitor

- Read Published
```

### Tips menulis Permission

- Role = jabatan atau fungsi bisnis, bukan nama user: `Employee`, `Manager`, `Finance`, `HR`
- Satu Role boleh punya banyak Event
- Satu Event boleh dimiliki lebih dari satu Role (misalnya `View` bisa dimiliki semua role)
- Jika sebuah Event tidak ada di Permissions, tidak ada yang bisa memicunya — setiap Event yang ada
  di **Events** harus disebutkan di sini untuk setidaknya satu role (kecuali yang memang ditujukan
  untuk `System`)

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

Sama seperti respon Event, tipe View **bukan daftar tertutup** — pilih kata yang paling menjelaskan
maksud bisnisnya. `Form`, `List`, dan `Detail` adalah trio yang hampir selalu dibutuhkan; sisanya
dipakai sesuai kebutuhan:

| Tipe | Kegunaan |
|------|----------|
| `Form` | Input untuk membuat atau mengubah record |
| `List` | Daftar banyak record |
| `Detail` | Tampilan lengkap satu record |
| `Report` | Ringkasan/agregat lintas banyak record (mis. Trial Balance, Leaderboard) |
| `Calendar` | Tampilan berbasis tanggal (mis. jadwal janji temu) |
| `Summary` | Ringkasan singkat |
| `Dashboard` | Metrik dan grafik |
| `Timeline` | Tampilan kronologis |
| `Map` | Tampilan berbasis lokasi |

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

**6. Rujukan nilai di `if` yang ambigu**

Menata itu human-first — Anda **boleh** merujuk sebuah pilihan dengan sebutan natural yang manusia
pakai sehari-hari, tidak harus persis sama huruf demi huruf dengan yang dideklarasikan di Fields.
Contoh nyata dari `design-request.menata`, yang justru sudah diterjemahkan dengan benar oleh
developer di `design-request.yaml`:

```
Fields

- Design Type : Poster | Thumbnail | Banner 2:1

Constraints

- Attachment is required.

    if Design Type = Banner
```

"Banner" di sini jelas merujuk ke `Banner 2:1` bagi siapa pun yang membacanya — meresolusi rujukan
seperti ini ke nilai yang presisi adalah pekerjaan Machine Interpretation, bukan tanggung jawab Anda
saat menulis Business Knowledge.

Yang perlu dihindari bukan singkatan, tapi **ambiguitas** — kalau ada dua pilihan yang sama-sama bisa
cocok dengan sebutan yang Anda tulis:

```
❌ Fields
   - Design Type : Banner 2:1 | Banner 3:2

   if Design Type = Banner        ← yang mana? bisa dua-duanya

✅ Fields
   - Design Type : Banner 2:1 | Banner 3:2

   if Design Type = Banner 2:1    ← jelas, tidak ada pilihan lain yang mirip
```

Tulis serinci yang dibutuhkan supaya seorang pembaca manusia tidak ragu — tidak lebih, tidak kurang.

---

## Checklist Sebelum Menyerahkan ke Developer

- [ ] Nama Object jelas dan singular (`Leave Request`, bukan `Leave Requests`)
- [ ] Setiap field punya tipe yang jelas — kalau ragu antara pilihan tertutup vs rujukan, lihat
      §"Tips memilih tipe" di Langkah 2
- [ ] Ada field `Status` dengan daftar keadaan lengkap, nilai pertama = keadaan awal
- [ ] Setiap Event mengubah `Status` (atau menjelaskan kenapa tidak perlu)
- [ ] Setiap Event yang ada di **Events** juga muncul di **Permissions**, minimal untuk satu role
- [ ] Constraint ditulis sebagai kalimat lengkap, bukan pseudocode
- [ ] Setiap nilai yang dirujuk di `if` (Events maupun Constraints) jelas menunjuk ke satu pilihan
      di Fields tanpa ambigu — boleh singkatan natural, asal tidak bisa disalahartikan
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
