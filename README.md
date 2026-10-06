# Laporan CSS 
## Studi Kasus: Student Management UI (HTML & CSS)

---

## 1. Deskripsi Umum

Website ini adalah tampilan antarmuka (UI) untuk sistem manajemen data mahasiswa, dibangun menggunakan HTML sebagai struktur dan CSS sebagai pengatur tampilan, layout, dan responsivitas. Website terdiri dari dua bagian utama dalam satu halaman: Form Student untuk input data, dan Data Mahasiswa yang menampilkan data dalam bentuk tabel.

Bahasa yang digunakan hanya HTML dan CSS, belum menggunakan JavaScript

---

## 2. Struktur File

```
student-management/
│
├── index.html      (struktur dan konten halaman)
└── style.css        (pengaturan tampilan/layout)
```

`index.html` terhubung ke `style.css` melalui tag:
```html
<link rel="stylesheet" href="style.css">
```
Kedua file ini harus berada di folder yang sama agar koneksi stylesheet-nya berfungsi

---

## 3. Penjelasan Fitur & Komponen

### a. Pengaturan Warna dan Ukuran
Di awal `style.css`, selector universal `*` digunakan untuk menghilangkan margin dan padding bawaan browser, serta menetapkan `box-sizing: border-box`. Lalu, blok `:root { ... }` mendefinisikan variabel warna seperti `--primary`, `--danger`, `--secondary`, `--border-color`, dan ukuran radius. Dengan cara ini, skema warna (soft sky blue, pastel pink, slate gray) dan ukuran radius bisa dipakai berulang di banyak komponen tanpa menulis ulang nilainya satu per satu.

### b. Navbar
Navbar dibangun dengan `display: flex` dan `justify-content: space-between`, membagi tiga elemen: logo dengan ikon topi toga di kiri, menu navigasi Home, Students, About di tengah, dan ikon avatar user di kanan. Ikon-ikon pada navbar memakai SVG inline (bukan file gambar terpisah), sehingga ringan dan tetap tajam di ukuran layar berapa pun.

### c. Layout Utama
Elemen `.container` memakai `display: grid` dengan dua kolom: kolom kiri berukuran tetap 340px untuk Form Student, kolom kanan mengisi sisa ruang untuk Data Mahasiswa.

### d. Card
Form dan tabel masing-masing dibungkus dengan kartu putih (`background`, `border`, `border-radius`, dan `box-shadow`) yang menghasilkan efek panel melayang. Style ini dipakai berulang untuk dua elemen berbeda, jadi tidak perlu nulis ulang.

### e. Form Student
Input NIM, Nama Lengkap, Jurusan (dropdown), dan Email dibuat dengan lebar penuh agar mengisi kolom. Setiap input dibungkus dalam satu grup bersama labelnya, biar rapi.

Saat input diklik atau difokuskan, border-nya berubah warna jadi biru dan muncul bayangan tipis di sekitarnya, sebagai tanda visual bahwa user sedang mengisi field itu.

### f. Tombol
Tombol dibangun dari satu style dasar lalu divariasikan jadi beberapa warna sesuai fungsinya: Simpan berwarna biru, Batal abu-abu, Reset pink. Tombol Simpan dan Reset juga dilengkapi ikon SVG supaya lebih jelas fungsinya.

### g. Kotak Pencarian
Input pencarian dan tombol kaca pembesar diletakkan berdampingan menggunakan flexbox, dengan sudut yang disatukan sehingga terlihat seperti satu komponen utuh.

### h. Tabel Data Mahasiswa
Header tabel diberi warna solid dengan sudut melengkung di kiri dan kanan. Saat kursor diarahkan ke salah satu baris, baris itu akan berubah warna jadi lebih terang sebagai highlight.

### i. Tombol Aksi (Edit & Delete)
Dua tombol kecil di setiap baris data, Edit berwarna biru dan Delete berwarna pink, disusun berdampingan menggunakan flexbox. Masing-masing berisi ikon SVG pensil dan tempat sampah.

### j. Pagination
Navigasi halaman disusun rata kanan, dan halaman yang sedang aktif ditandai dengan warna background solid supaya langsung keliatan.

### k. Tampilan Responsif
Ada dua ukuran layar yang disesuaikan. Di layar sedang (misalnya tablet), layout dua kolom berubah jadi satu kolom, Form dan Data Mahasiswa bertumpuk ke bawah. Di layar kecil (HP), menu navbar disembunyikan dan kotak pencarian melebar penuh biar tetap nyaman dilihat.

---

## 4. Kenapa Tombol-Tombol di Website Ini Belum Bisa Berfungsi

Ini bukan kesalahan atau bug, Alasannya:

HTML hanya mendefinisikan struktur, misalnya elemen tombol, input, atau tabel itu ada dan terlihat di halaman. CSS hanya mengatur tampilan visual: warna, ukuran, posisi, efek hover. CSS bisa mengubah tampilan tombol saat disentuh kursor, tapi tidak bisa menjalankan aksi seperti menyimpan data, menghapus baris tabel, atau memvalidasi form.

Supaya tombol Simpan benar-benar menyimpan data baru ke tabel, tombol Delete benar-benar menghapus baris, atau kotak pencarian benar-benar memfilter data, dibutuhkan JavaScript. JavaScript yang menangani event seperti klik, input, atau submit, lalu mengubah isi halaman secara dinamis.

Jadi untuk sekarang, website ini hanya berfokus di tampilan, layout, warna, dan responsivitasnya. Fungsi interaktif seperti simpan, edit, hapus, dan cari baru akan ditambahkan di tahap berikutnya pakai JavaScript.

---

## 5. Kesimpulan

Website Student Management ini sudah menerapkan konsep-konsep dasar CSS: penggunaan variabel warna untuk konsistensi tampilan, flexbox untuk navbar, search box, dan tombol aksi, grid untuk layout dua kolom, card untuk membungkus konten, serta pseudo-class dan media query untuk interaksi visual dan tampilan responsif di berbagai ukuran layar. Tombol dan elemen interaktif lainnya sudah tampil dan merespons secara visual, namun belum memiliki fungsi nyata karena fungsionalitas tersebut akan ditambahkan pada tahap JavaScript selanjutnya
