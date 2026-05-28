# Dokumentasi Proyek: Tableau Sales & Customer Dashboards

Dokumen ini berisi spesifikasi teknis dan dokumentasi lengkap dari proyek **Tableau Sales & Customer Dashboards**. Proyek ini dirancang untuk memberikan wawasan berbasis data kepada para pemangku kepentingan (seperti eksekutif dan manajer penjualan) dalam menganalisis kinerja penjualan dan perilaku pelanggan.

---

## 1. Pendahuluan

Tujuan dari proyek ini adalah membangun dua buah dashboard interaktif di Tableau Desktop yang berfungsi untuk melacak *Key Performance Indicators* (KPI) terkait pendapatan, profitabilitas, serta tren historis. Dashboard ini memungkinkan penelusuran data yang lebih dalam (*drill-down*) berdasarkan hierarki produk dan wilayah geografis.

---

## 2. Spesifikasi Kebutuhan Dashboard (Requirements)

Pengembangan dashboard didasarkan pada *User Stories* berikut:

### 2.1. Sales Performance Dashboard
Fokus utama dari dashboard ini adalah menyajikan metrik kinerja penjualan untuk memfasilitasi analisis *Year-over-Year* (YoY).
* **KPI Utama (BANs):** Menampilkan ringkasan metrik Total Penjualan, Total Keuntungan, dan Jumlah Kuantitas untuk tahun berjalan dan tahun sebelumnya.
* **Tren Penjualan (Bulanan):** Menampilkan pergerakan metrik secara bulanan (YoY) serta menonjolkan bulan-bulan dengan performa tertinggi dan terendah agar mudah dikenali.
* **Perbandingan Subkategori Produk:** Menyoroti perbandingan antara hasil penjualan dan tingkat keuntungan (profit) pada setiap subkategori produk.
* **Tren Mingguan:** Menyajikan data mingguan pada tahun berjalan, menampilkan garis rata-rata mingguan, serta menyoroti titik-titik data (minggu) yang berada di atas atau di bawah batas rata-rata.

### 2.2. Customer Insights Dashboard
Fokus utama dari dashboard ini adalah analitik profil pelanggan dan loyalitas pesanan.
* **KPI Utama (BANs):** Menampilkan Total Pelanggan, Penjualan per Pelanggan, dan Total Pesanan untuk tahun berjalan dan sebelumnya.
* **Tren Pelanggan (Sparklines):** Representasi visual yang ringkas mengenai tren pelanggan per bulan.
* **Distribusi Pesanan Pelanggan (Bar-in-Bar):** Representasi sebaran pelanggan berdasarkan jumlah pesanan yang mereka lakukan untuk menganalisis keterikatan (*engagement*).
* **Top 10 Customers (Berdasarkan Profit):** Menyajikan data 10 besar pelanggan yang menyumbang keuntungan tertinggi, lengkap dengan jumlah pesanan, total penjualan, total profit, dan tanggal transaksi terakhir.

---

## 3. Arsitektur dan Skema Dataset

Dataset yang digunakan berfokus pada wilayah Eropa dengan spesifikasi (*formatting*) khusus yang perlu diperhatikan saat melakukan integrasi data:

* **Format Pemisah (Delimiter):** Semicolon (`;`)
* **Format Desimal:** Koma (`,`) (Standar Eropa)

### Skema Tabel

1. **Orders.csv** (`utf-8`) - *Data Transaksi (9.994 baris)*
   * Kolom: `Row ID`, `Order ID`, `Order Date`, `Ship Date`, `Ship Mode`, `Customer ID`, `Segment`, `Postal Code`, `Product ID`, `Sales`, `Quantity`, `Discount`, `Profit`.
2. **Customers.csv** (`latin1`) - *Data Master Pelanggan (793 baris)*
   * Kolom: `Customer ID`, `Customer Name`.
3. **Products.csv** (`latin1`) - *Data Katalog Produk (1.894 baris)*
   * Kolom: `Product ID`, `Category`, `Sub-Category`, `Product Name`.
4. **Location.csv** (`utf-8`) - *Data Geografis (632 baris)*
   * Kolom: `Postal Code`, `City`, `State`, `Region`, `Country/Region`.

---

## 4. Arsitektur Desain Antarmuka (UI/UX)

Dashboard dibangun dengan memanfaatkan hierarki **Container** yang ketat di Tableau untuk memastikan tata letak yang proporsional pada berbagai perangkat:

1. **Main Vertical Container:** Bertindak sebagai pembungkus (*wrapper*) utama seluruh elemen dashboard.
2. **Horizontal Container (KPI):** Terletak di bagian atas untuk menampung elemen-elemen metrik kunci (BANs).
3. **Horizontal & Nested Vertical Container (Charts):** Terletak di bawah KPI untuk menempatkan diagram interaktif. Grafik-grafik pendamping (*secondary charts*) disusun secara bersarang di sebelah grafik utama (*primary chart*).
4. **Interaktivitas (*Actions & Navigation*):**
   * Menggunakan tombol navigasi (*Image Button*) kustom yang diletakkan melalui folder `images/` untuk berpindah antardashboard.
   * Filter silang (*Cross-filtering*) otomatis dengan menjadikan setiap grafik sebagai pemicu filter bagi komponen lainnya.
   * *Parameter/Filter* interaktif untuk filter kategori, subkategori, serta wilayah secara dinamis, termasuk penyesuaian Tahun (*Year*).

---

## 5. Panduan Penggunaan (*Deployment Guide*)

1. **Membuka Proyek:** Buka berkas `Sales & Customer Dashboards.twbx` menggunakan aplikasi **Tableau Desktop** (versi yang relevan) atau **Tableau Reader**.
2. **Koneksi Data:** Karena berkas tersebut bertipe *Packaged Workbook* (`.twbx`), semua *extract* data (`datasets/`) dan aset gambar (`images/`) telah terkompresi bersama. Anda tidak perlu menyambungkan ulang jalur *database* atau file lokal, kecuali jika Anda ingin melakukan pembaruan data secara langsung (*live connection* / *refresh extract*).
3. **Pembaruan Data:** Jika struktur data CSV berubah, pastikan *Text File Properties* Tableau diatur untuk membaca pemisah berupa titik koma (`;`) dan *Locale* diatur ke negara dengan format desimal koma (misal: *Germany*).

---
*Dokumentasi ini dibuat untuk melengkapi dan memandu fase implementasi dari Keyla's Tableau Project.*
