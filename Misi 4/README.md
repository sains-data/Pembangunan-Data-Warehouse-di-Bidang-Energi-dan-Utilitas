# ⚡ Data Warehouse Energi & Utilitas – Kelompok 11 🚀

Laporan ini menyajikan perancangan dan implementasi sistem **Data Warehouse** bagi perusahaan energi RubicoNergi (RBN) guna mengintegrasikan data konsumsi listrik rumah tangga serta mendukung analisis spasial dan temporal untuk wilayah 3S.

---

## 📌 1. Ringkasan & Latar Belakang
- RBN menghadapi tantangan integrasi data dari sistem terpisah (CRM, billing, GIS).
- Proyek ini membangun DW untuk mengintegrasikan data, mempercepat pelaporan, dan mendukung pengambilan keputusan.
- Wilayah 3S jadi fokus utama untuk ekspansi data-driven.

---

## 🎯 2. Tujuan & Ruang Lingkup
- Integrasi data operasional dan pelanggan.
- Perancangan model multidimensi.
- Proses ETL (Extract, Transform, Load).
- Mendukung analitik spasial, prediktif, dan pelaporan.

---

## 🧩 3. Metodologi
- Analisis kebutuhan → desain skema (star schema) → ETL → evaluasi.
- Fokus pada pemetaan stakeholder dan kebutuhan bisnis.
- Penggunaan skema bintang dengan dimensi waktu, pelanggan, wilayah, perangkat, gangguan, dan tagihan.

---

## 🧠 4. Analisis Kebutuhan
- Identifikasi 6 stakeholder utama dan 5 tujuan bisnis, seperti efisiensi ekspansi wilayah 3S dan peningkatan pelayanan pelanggan.
- Studi kasus pada ketidakterpaduan sistem yang menghambat ekspansi dan pelayanan.

---

## 📐 5. Desain Data Warehouse
- **Skema multidimensi** dengan tabel fakta dan 6 tabel dimensi.
- Tabel fakta menyimpan konsumsi energi dan biaya pemeliharaan.
- Dimensi mendukung analisis waktu, pelanggan, spasial, perangkat, gangguan, dan tagihan.
- Disesuaikan dengan dataset *Household Electric Power Consumption* dari Kaggle.

---

## 🛠️ 6. Implementasi Medallion Architecture
- **Bronze Layer**: menyimpan data mentah dari file CSV.
- **Silver Layer**: data dibersihkan dan ditransformasi.
- **Gold Layer**: data diagregasi untuk pelaporan harian dan bulanan.
- Penggunaan SQL Server dengan indexing, partisi, dan optimalisasi performa.

---

## 📊 7. Hasil Implementasi
- Skema star schema dengan hubungan antar tabel di SQL Server.
- Hasil kueri:
  - Total konsumsi harian (Wh).
  - Pola konsumsi rata-rata per jam.
  - Kontribusi sub-metering per hari.
  - Hari dengan konsumsi tertinggi dan terendah.

---

## ✅ 8. Evaluasi
- Validasi integritas data, pengujian kueri analitik, dan dokumentasi teknis diselesaikan.
- Sistem mampu menyajikan laporan dan analisis yang cepat dan akurat.

---

## 🔭 9. Rencana Pengembangan
- Integrasi data real-time.
- Visualisasi interaktif (dashboard).
- Prediksi beban puncak dan analitik lanjutan dengan AI/ML.

---

## 👥 10. Tim Proyek
- Kelompok 11 – Sains Data ITERA 2025:
  - Muhammad Zaki Abdillah
  - Deva Anjani Khayyuninafsyah
  - Patricia Leondrea Diajeng Putri
  - Syadza Puspadari Azhar
  - Dea Mutia Risani
  - Amalia Melani Putri

---

📁 Dataset: [Kaggle – Household Power Consumption](https://www.kaggle.com/datasets/uciml/electric-power-consumption-data-set)