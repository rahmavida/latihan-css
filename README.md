# Latihan-css
## Studi Kasus: Student Management UI (HTML & CSS)

---

## 1. Deskripsi Umum

Website ini adalah tampilan antarmuka (UI) untuk sistem manajemen data mahasiswa, dibangun menggunakan **HTML** sebagai struktur dan **CSS** sebagai pengatur tampilan, layout, dan responsivitas. Sesuai studi kasus, website terdiri dari dua bagian utama dalam satu halaman: **Form Student** (untuk input data) dan **Data Mahasiswa** (tabel menampilkan data dalam bentuk list).

Teknologi yang digunakan hanya **HTML + CSS**, belum menggunakan JavaScript, sesuai tahapan pembelajaran modul, di mana JavaScript baru ditambahkan pada tahap selanjutnya untuk fungsi CRUD (Create, Read, Update, Delete) dan Fetch API

---

## 2. Struktur File

```
student-management/
│
├── index.html      (struktur & konten halaman)
└── style.css        (pengaturan tampilan/layout)
```

`index.html` terhubung ke `style.css` melalui tag:
```html
<link rel="stylesheet" href="style.css">
```
Kedua file ini harus berada di folder yang sama agar koneksi stylesheet-nya berfungsi.

---

## 3. Penjelasan Fitur & Komponen

### a. CSS Reset & Variables
Di awal `style.css`, selector universal `*` digunakan untuk menghilangkan margin/padding bawaan browser dan menetapkan `box-sizing: border-box`. Lalu, blok `:root { ... }` mendefinisikan **CSS Variables** (custom properties) seperti `--primary`, `--danger`, `--secondary`, `--border-color`, dan `--radius-*`. Teknik ini membuat skema warna (soft sky blue, pastel pink, slate gray) dan ukuran radius dapat dipakai berulang di banyak komponen tanpa menulis ulang nilainya.

### b. Navbar (Flexbox)
Navbar dibangun dengan `display: flex` dan `justify-content: space-between`, membagi tiga elemen: logo + ikon topi toga (kiri), menu navigasi Home/Students/About (tengah), dan ikon avatar user (kanan). Ikon-ikon pada navbar memakai **SVG inline** (bukan file gambar terpisah), sehingga ringan dan tetap tajam di ukuran layar berapa pun.

### c. Layout Utama (CSS Grid)
Elemen `.container` memakai `display: grid` dengan `grid-template-columns: 340px 1fr`, membagi halaman jadi dua kolom: kolom kiri berukuran tetap 340px untuk Form Student, kolom kanan mengisi sisa ruang (`1fr`) untuk Data Mahasiswa.

### d. Card Component
Form dan tabel masing-masing dibungkus `.card`, kombinasi `background`, `border`, `border-radius`, dan `box-shadow` yang menghasilkan efek panel/kartu melayang, dipakai berulang untuk dua elemen berbeda (reusable component).

### e. Form Student
Input NIM, Nama Lengkap, Jurusan (dropdown `<select>`), dan Email dibuat dengan `width: 100%` agar mengisi penuh kolom. Setiap input dibungkus `.form-group` agar label dan input-nya terkelompok rapi.

Saat input diklik/difokuskan, pseudo-class `:focus` mengubah warna border jadi biru dan menambahkan `box-shadow` tipis sebagai umpan balik visual bahwa user sedang mengisi field tersebut.

### f. Button Component
Tombol dibangun dari class dasar `.btn` lalu divariasikan lewat `.btn-primary` (Simpan, biru), `.btn-secondary` (Batal, abu-abu), dan `.btn-danger` (Reset, pink). Ini konsep *reusable class*, satu style dasar, beberapa varian warna sesuai fungsi. Tombol Simpan dan Reset juga dilengkapi ikon SVG supaya lebih komunikatif.

### g. Search Box (Flexbox)
Input pencarian dan tombol kaca pembesar diletakkan berdampingan menggunakan `display: flex`, dengan sudut border yang disatukan (`border-radius` hanya di sisi luar) sehingga terlihat seperti satu komponen utuh.

### h. Tabel Data Mahasiswa
Tabel memakai `border-collapse: separate` dan `border-spacing: 0` supaya radius sudut pada header tabel (`th:first-child`, `th:last-child`) bisa tampil rapi. Header tabel diberi warna solid (`background: var(--primary)`), dan `tbody tr:hover` memberi highlight warna lembut saat kursor diarahkan ke salah satu baris.

### i. Action Buttons (Edit & Delete)
Dua tombol aksi kecil per baris data, Edit (biru) dan Delete (pink), disusun berdampingan dengan `display: flex` di dalam `.actions`, masing-masing berisi ikon SVG pensil dan tempat sampah.

### j. Pagination
Navigasi halaman (`«`, `‹`, 1, 2, 3, `›`, `»`) disusun rata kanan dengan `justify-content: flex-end`, dan halaman aktif ditandai lewat class `.active` yang mengubah warna background jadi solid.

### k. Responsive Design (Media Query)
Dua breakpoint diterapkan:
- **Layar ≤ 900px**: `grid-template-columns` berubah jadi `1fr`, membuat Form dan Data Mahasiswa bertumpuk vertikal (1 kolom), bukan 2 kolom berdampingan.
- **Layar ≤ 600px**: menu navbar disembunyikan (`display: none`) dan search box melebar penuh (`width: 100%`) agar tetap nyaman dilihat di layar HP.

---

## 4. Kenapa Tombol-Tombol di Website Ini Belum Bisa Diklik/Berfungsi

Ini **bukan kesalahan/bug**, Alasannya:

1. **HTML hanya mendefinisikan struktur**, seperti elemen `<button>`, `<input>`, atau `<table>` itu ada dan terlihat di halaman.
2. **CSS hanya mengatur tampilan visual**, warna, ukuran, posisi, efek hover. CSS *bisa* mengubah tampilan tombol saat disentuh kursor (`:hover`, `:active`), tapi **tidak bisa menjalankan aksi** seperti menyimpan data, menghapus baris tabel, atau memvalidasi form.
3. Supaya tombol "Simpan" benar-benar menyimpan data baru ke tabel, tombol "Delete" benar-benar menghapus baris, atau kotak pencarian benar-benar memfilter data, dibutuhkan **JavaScript**, yang berfungsi menangani *event* (klik, input, submit) dan mengubah isi halaman secara dinamis (DOM manipulation)

```
HTML + CSS  →  UI Student Management (tampilan statis, seperti sekarang)
     ↓
JavaScript  →  Add Student, Edit Student, Delete Student, Search
     ↓
Fetch API   →  GET, POST, PUT, DELETE
     ↓
Backend + Database
```

Jadi tahap HTML + CSS ini hanya berfokus di **tampilan (UI)**, layout, warna, dan responsivitasnya. Fungsi interaktif (CRUD) adalah tahap pembelajaran berikutnya

---

## 5. Kesimpulan

Website Student Management ini berhasil menerapkan konsep-konsep inti CSS modern sesuai materi: **CSS Variables** untuk konsistensi warna, **Flexbox** untuk navbar/search/action buttons (susunan satu dimensi), **CSS Grid** untuk layout dua kolom, **Box Model** untuk card dan spacing, **pseudo-class** (`:hover`, `:focus`) untuk interaksi visual, serta **Media Query** untuk tampilan responsif di berbagai ukuran layar. Tombol dan elemen interaktif lainnya sudah tampil dan merespons visual (hover/focus), namun belum memiliki fungsi nyata karena fungsionalitas tersebut akan ditambahkan pada tahap JavaScript berikutnya
