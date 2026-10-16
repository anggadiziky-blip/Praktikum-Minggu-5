# Tugas Pendahuluan Modul 5 Pemrograman Web: Bootstrap

Ganjil 2026/2027

| | |
|---|---|
| **Nama** | Angga Farhat Diziky |
| **NIM** | 103092400060 |
| **Versi Bootstrap** | 5.3.8 |

---

## 1. Pengertian Bootstrap

Bootstrap adalah *framework front-end* open source yang berisi kumpulan CSS, JavaScript, dan komponen siap pakai untuk membangun tampilan website yang responsif. Bootstrap dibuat oleh tim Twitter dan sekarang dikembangkan oleh komunitas.

Kegunaan Bootstrap:

- Mempercepat pembuatan tampilan karena komponen seperti navbar, tombol, form, kartu, dan modal sudah tersedia.
- Membuat website responsif yang menyesuaikan ukuran layar desktop, tablet, maupun ponsel (pendekatan *mobile-first*).
- Menjaga konsistensi desain di seluruh halaman dan di berbagai peramban.
- Mengurangi penulisan CSS manual karena pengaturan jarak, warna, dan tata letak cukup memakai *utility class*.

## 2. Memasang Bootstrap

1. **CDN (Content Delivery Network).** Menautkan file CSS di `<head>` dan JS di akhir `<body>` langsung dari server CDN, misalnya jsDelivr. Tidak perlu mengunduh file apa pun, tetapi membutuhkan koneksi internet.

   ```html
   <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.8/dist/css/bootstrap.min.css" rel="stylesheet">
   <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.8/dist/js/bootstrap.bundle.min.js"></script>
   ```

2. **Mengunduh file Bootstrap (compiled CSS dan JS).** File diunduh dari situs resmi, disimpan di folder project, lalu ditautkan secara lokal sehingga bisa dipakai tanpa internet.
3. **Package manager.** Memasang lewat npm (`npm install bootstrap@5.3.8`), yarn, pnpm, bun, atau Composer (`composer require twbs/bootstrap:5.3.8`), lalu mengimpornya ke project.
4. **Source files (Sass).** Mengunduh kode sumber Bootstrap agar variabel Sass dapat diubah dan dikompilasi sendiri untuk kustomisasi tema.

## 3. Grid dan Breakpoint

**Class grid.** Sistem grid Bootstrap berbasis flexbox dengan 12 kolom. Strukturnya terdiri dari tiga lapis class:

- `.container` / `.container-fluid`: pembungkus (lebar tetap per breakpoint atau penuh 100%).
- `.row`: baris yang membungkus kolom-kolom.
- `.col`, `.col-*`, `.col-{breakpoint}-*`: kolom dengan lebar 1–12 bagian. Contoh `col-12 col-md-6` berarti satu kolom penuh di layar kecil dan setengah lebar mulai layar medium. Total kolom dalam satu baris yang melebihi 12 akan turun ke baris berikutnya.

**Kegunaan breakpoint.** Breakpoint adalah batas lebar layar tempat tata letak berubah, sehingga satu halaman dapat tampil berbeda pada tiap ukuran perangkat tanpa membuat halaman terpisah. Breakpoint bawaan Bootstrap 5:

| Breakpoint | Awalan class | Lebar layar |
|---|---|---|
| Extra small | (tanpa awalan) | < 576px |
| Small | `sm` | ≥ 576px |
| Medium | `md` | ≥ 768px |
| Large | `lg` | ≥ 992px |
| Extra large | `xl` | ≥ 1200px |
| Extra extra large | `xxl` | ≥ 1400px |

## 4. Class Bootstrap

| Class | Kegunaan |
|---|---|
| `container` | Membungkus konten agar berada di tengah dengan lebar maksimum sesuai breakpoint. |
| `btn btn-primary` | Membuat tombol bergaya Bootstrap dengan warna primer. |
| `text-center` | Meratakan teks ke tengah. |
| `d-flex` | Mengubah elemen menjadi flex container untuk mengatur tata letak anak elemen. |
| `shadow` | Memberi bayangan pada elemen. |
| `mb-3`, `p-4` | Mengatur margin dan padding (angka 0–5 menentukan besar jarak). |
| `form-control` | Memberi gaya pada input teks, password, dan textarea agar lebar penuh dan rapi. |
| `navbar` | Membuat bilah navigasi di bagian atas halaman. |

## 5. Gambar Responsif

Gunakan class `.img-fluid` pada tag `<img>`. Class ini menerapkan `max-width: 100%` dan `height: auto`, sehingga gambar mengecil mengikuti lebar elemen pembungkusnya dan proporsinya tetap terjaga, tetapi tidak membesar melebihi ukuran aslinya.

```html
<img src="foto.jpg" class="img-fluid" alt="Deskripsi gambar">
```

Gambar dapat dipusatkan dengan `d-block mx-auto`, dan bila ingin berbeda gambar per ukuran layar dapat memakai elemen `<picture>`. Gambar juga dapat ditempatkan di dalam kolom grid (`col-*`) agar ukurannya ikut menyesuaikan.

## 6. Membuat Tampilan dengan Bootstrap

Halaman login **Ruang Baca** dibuat pada file [`index.html`](index.html) dengan Bootstrap 5.3.8 lewat CDN, bertema sistem ERP perpustakaan. Cukup buka `index.html` di browser (membutuhkan koneksi internet untuk memuat Bootstrap dan font).

### Komponen yang dibuat

- **Navbar:** nama **Ruang Baca** di kiri, menu **Beranda**, **Tentang**, dan **Bantuan** di kanan. Di layar kecil menu menjadi tombol *hamburger*.
- **Form login:** judul, input **Username**, input **Password** (dengan tombol lihat/sembunyikan), checkbox **Ingat saya**, tombol **Masuk**, dan tautan **Lupa password?**.
- **Panel ringkasan modul:** tabel status modul perpustakaan (Katalog buku, Sirkulasi, Keanggotaan, Pengadaan, Laporan) yang hanya tampil di layar besar.

### Class Bootstrap yang dipakai

| Bagian | Class |
|---|---|
| Navbar | `navbar navbar-expand-sm bg-white border-bottom`, `navbar-brand`, `navbar-toggler`, `navbar-nav ms-auto`, `nav-link` |
| Grid responsif | `container-fluid`, `row g-0`, `col-12 col-lg-6`, `d-none d-lg-flex` |
| Tabel status | `table align-middle`, `badge rounded-pill text-bg-success` |
| Kartu login | `card shadow rounded-2`, `card-body p-4 p-md-5`, `card-footer text-center` |
| Form | `form-label`, `form-control`, `input-group`, `input-group-text`, `form-check`, `form-check-input` |
| Tombol | `btn btn-primary btn-lg`, `btn btn-outline-secondary`, `d-grid` |
| Tata letak dan teks | `d-flex`, `align-items-center`, `mx-auto`, `w-100`, `mb-3`, `px-md-5`, `fw-semibold`, `text-secondary` |

### Responsif

- **Desktop (≥ 992px):** dua kolom sama lebar, ringkasan modul di kiri dan form login di kanan.
- **Ponsel (< 992px):** panel kiri disembunyikan, form tampil satu kolom penuh, dan menu navbar menjadi hamburger.

Sesuai soal, halaman ini hanya berfokus pada tampilan. Tidak ada autentikasi akun, penyimpanan data login, atau pemulihan password.
