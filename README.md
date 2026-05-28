# 📊 Tableau Sales & Customer Dashboards

[![Tableau](https://img.shields.io/badge/Tableau-E97627?style=for-the-badge&logo=Tableau&logoColor=white)](https://www.tableau.com/)
[![Dataset](https://img.shields.io/badge/Dataset-Superstore_EU-blue?style=for-the-badge)](https://github.com/)
[![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)](https://github.com/)

Sebuah proyek visualisasi data interaktif menggunakan **Tableau Desktop** yang dirancang untuk menganalisis kinerja penjualan bisnis (*Sales Performance*) dan perilaku pelanggan (*Customer Insights*). Proyek ini dibangun berdasarkan kebutuhan bisnis nyata (User Stories) untuk membantu jajaran eksekutif dan manajer penjualan dalam mengambil keputusan berbasis data.

---

## 📌 Galeri Dashboard (Tangkapan Layar)

> [!TIP]
> *Silakan ambil screenshot dashboard Tableau Anda dan simpan di folder `images/`, lalu perbarui tautan di bawah ini agar gambar tampil secara langsung di halaman utama GitHub Anda.*

| 📈 Sales Performance Dashboard | 👥 Customer Insights Dashboard |
| :---: | :---: |
| ![Sales Dashboard Placeholder](images/Icon%20-%20Sales%20Dashboard(active).png) <br> *(Tambahkan screenshot Sales Dashboard Anda di sini)* | ![Customer Dashboard Placeholder](images/Icon%20-%20Customer%20Dashboard(active).png) <br> *(Tambahkan screenshot Customer Dashboard Anda di sini)* |

---

## 📖 Ringkasan Proyek & Spesifikasi Kebutuhan

Proyek ini mencakup pengembangan **dua dashboard utama** dengan spesifikasi teknis dan visual sebagai berikut:

### 1. Sales Performance Dashboard (Analisis Penjualan)
* **KPI Utama (BANs):** Menampilkan ringkasan total Penjualan (*Sales*), Keuntungan (*Profit*), dan Jumlah Barang Terjual (*Quantity*) untuk tahun berjalan (*Current Year*) vs tahun sebelumnya (*Previous Year*).
* **Tren Penjualan Bulanan:** Menampilkan fluktuasi bulanan untuk setiap KPI utama untuk membandingkan performa Year-over-Year (YoY) serta menyoroti bulan dengan penjualan tertinggi dan terendah secara visual.
* **Perbandingan Subkategori Produk:** Perbandingan performa penjualan dan profitabilitas antar subkategori produk untuk mengidentifikasi produk penyumbang keuntungan terbesar.
* **Tren Mingguan:** Analisis mingguan penjualan dan profit tahun berjalan terhadap rata-rata mingguan untuk memantau performa jangka pendek secara dinamis.

### 2. Customer Insights Dashboard (Analisis Pelanggan)
* **KPI Utama (BANs):** Menampilkan total jumlah pelanggan unik (*Customers*), rata-rata penjualan per pelanggan (*Sales per Customer*), dan total pesanan (*Total Orders*) YoY.
* **Tren Bulanan (Sparklines):** Sparklines bulanan yang ringkas untuk setiap metrik pelanggan guna melihat pergerakan tren sepanjang tahun.
* **Distribusi Pesanan Pelanggan:** Grafik *Bar-in-Bar* untuk memetakan distribusi pelanggan berdasarkan jumlah pesanan yang mereka lakukan guna menganalisis loyalitas pelanggan.
* **Top 10 Customers:** Tabel interaktif yang merinci 10 pelanggan paling menguntungkan lengkap dengan peringkat (*Rank*), jumlah pesanan, total transaksi, total keuntungan, dan tanggal pesanan terakhir.

---

## 🛠️ Desain, Interaktivitas, & Kontainer

Dashboard dirancang secara modular dan responsif menggunakan prinsip desain Tableau terbaik:
* **Struktur Tata Letak Kontainer:** Sesuai dengan panduan dalam `mockup.pdf`, tata letak disusun secara presisi menggunakan **Vertical Container (Main)** di bagian luar, serta kombinasi **Horizontal** dan **Nested Containers** di bagian dalam untuk memastikan kestabilan visual saat dibuka di berbagai resolusi layar.
* **Navigasi Dinamis:** Menggunakan aset gambar kustom di folder `images/` untuk berpindah antardashboard secara mulus menggunakan tombol gambar interaktif (*Image Navigation Buttons*).
* **Filter Global & Interaktif:** 
  * Filter dropdown untuk menyaring data berdasarkan **Kategori/Subkategori Produk**, serta wilayah geografis (**Region, State, City**).
  * Fitur *Use as Filter* diaktifkan pada semua chart untuk memungkinkan eksplorasi data secara dinamis (mengklik elemen grafik akan menyaring grafik lainnya).
  * Filter **Year Selector** dinamis untuk fleksibilitas analisis lintas tahun.

---

## 📂 Struktur Repositori

```text
├── Sales & Customer Dashboards.twbx       <- Berkas utama Tableau Packaged Workbook
├── Problem.pdf                           <- Dokumen persyaratan bisnis & User Stories
├── mockup.pdf                            <- Panduan tata letak kontainer & sketsa visual
├── project_phases.pdf                    <- Dokumentasi tahapan implementasi proyek
├── datasets/
│   └── eu/                               <- Sumber data mentah (format regional Eropa)
│       ├── Customers.csv                 <- Data master pelanggan (793 baris)
│       ├── Location.csv                  <- Data geografis wilayah Eropa (632 baris)
│       ├── Orders.csv                    <- Data transaksi transaksi (9994 baris)
│       └── Products.csv                  <- Data katalog detail produk (1894 baris)
├── images/                               <- Aset ikon & logo untuk dashboard
└── .gitignore                            <- File konfigurasi Git untuk menyaring berkas sampah
```

---

## 📊 Rincian Sumber Data

Data yang digunakan merupakan data penjualan retail Eropa dengan spesifikasi teknis khusus:
* **Delimiter:** Kolom pada seluruh file CSV dipisahkan oleh titik koma (`;`).
* **Format Desimal:** Kolom desimal seperti `Sales` dan `Profit` di file `Orders.csv` menggunakan format desimal Eropa yaitu koma (`,`), contoh: `219,582`.
* **Pengodean Karakter (Encoding):**
  * `Customers.csv` & `Products.csv` menggunakan pengodean `latin1` (ISO-8859-1).
  * `Location.csv` & `Orders.csv` menggunakan pengodean `utf-8`.

> [!IMPORTANT]
> **Catatan Penting saat Menghubungkan Data di Tableau:**
> Jika Anda menyambungkan kembali data mentah secara manual di Tableau, pastikan untuk mengatur **Text File Properties** Anda dengan pemisah kolom (separator) **Semicolon** dan setelan bahasa (*Locale*) ke negara yang mendukung format desimal koma (misalnya *Germany* atau *France*), atau ubah tipe datanya melalui *Custom Locale* di Tableau agar angka terbaca dengan benar sebagai numerik dan bukan teks.

---

## 🚀 Cara Menjalankan Proyek

1. **Prasyarat:** Pastikan Anda telah menginstal **Tableau Desktop** atau **Tableau Reader** di komputer Anda.
2. **Klon Repositori:**
   ```bash
   git clone https://github.com/USERNAME/Sales-Customer-Dashboard-Project.git
   ```
3. **Buka Workbook:**
   * Klik ganda berkas `Sales & Customer Dashboards.twbx` di folder utama.
   * Karena berkas berformat `.twbx` (*Packaged Workbook*), semua data mentah dari folder `datasets/` sudah terkemas di dalamnya secara otomatis, sehingga Anda bisa langsung menjelajahi dashboard tanpa perlu melakukan koneksi data ulang.

---

## 👤 Penulis

* **Keyla Rindani** - *Data Analyst / Tableau Developer*
* LinkedIn: [keylarindani](https://linkedin.com/in/)
* GitHub: [keylarindani](https://github.com/)

---
*Proyek ini merupakan bagian dari Tableau Portfolio Showcase.*
