# 📊 Data Warehouse Project - Misi 1: RubicoNergi (RBN)

## 📁 Profil Industri

RubicoNergi (RBN) adalah perusahaan yang bergerak di bidang energi listrik, beroperasi di berbagai wilayah Indonesia, termasuk area 3S (Sulit dijangkau, Sulit diawasi, dan Sulit dimonitor). Dengan demikian, diperlukan suatu gudang data yang dapat membantu RBN dalam mengintegrasikan data-data operasional, melakukan optimalisasi pemeliharaan jaringan, menyediakan dashboard otomatis, meningkatkan kemampuannya dalam melakukan prediksi, sehingga meningkatkan pelayanan terhadap pelanggan.

---

## 🎯 Tujuan Bisnis

1. **Efisiensi Ekspansi ke Wilayah 3S**  
   Menggunakan data terintegrasi untuk menyusun strategi ekspansi yang hemat biaya dan tepat sasaran.

2. **Mengurangi Gangguan & Kebocoran Daya**  
   Mendeteksi pola gangguan dan kebocoran daya dengan lebih cepat menggunakan data historis.

3. **Meningkatkan Integrasi Data & Pelaporan**  
   Menyatukan sistem terpisah (pelanggan, gangguan, billing) ke dalam satu platform terpusat.

4. **Pemantauan Konsumsi & Perencanaan Peak-Load**  
   Melakukan prediksi beban puncak dan mengoptimalkan distribusi daya dengan riwayat konsumsi yang lengkap.

5. **Peningkatan Pelayanan Pelanggan**  
   Menghadirkan dashboard prediktif dan sistem tanggap keluhan berbasis data real-time.

---

## 👥 Stakeholders

| Jabatan                    | Peran                                                  |
|---------------------------|---------------------------------------------------------|
| Manajer Operasional       | Monitoring distribusi dan pemeliharaan jaringan         |
| Tim Perencanaan Jaringan  | Strategi ekspansi berdasarkan data konsumsi & wilayah   |
| Tim IT/Data Engineer      | Pengembangan infrastruktur dan integrasi gudang data    |
| Customer Service & Billing| Penanganan keluhan dan sinkronisasi sistem tagihan      |
| Analis Keuangan           | Analisis efisiensi dan dukungan keputusan investasi     |
| Tim Monitoring Gangguan   | Deteksi gangguan dan kebocoran daya real-time           |

---

## 📚 Studi Kasus

Permasalahan utama RBN adalah keterpisahan data pelanggan, konsumsi, gangguan, dan billing yang menghambat efisiensi operasional, perencanaan ekspansi, serta pemantauan gangguan. Oleh karena itu, diperlukan sistem gudang data yang dapat mengintegrasikan seluruh informasi ke dalam satu platform analitik terpusat.

---

## 📦 Star Schema Design

### 🧱 Tabel Fakta: `fakta_konsumsi_listrik`
Merekam konsumsi energi dan aktivitas terkait:

| Atribut               | Deskripsi                                    |
|-----------------------|----------------------------------------------|
| `id_waktu`            | FK ke `dimensi_waktu`                        |
| `id_pelanggan`        | FK ke `dimensi_pelanggan`                    |
| `id_wilayah`          | FK ke `dimensi_wilayah`                      |
| `id_aset_jaringan`    | FK ke `dimensi_aset_jaringan`                |
| `total_kwh_terjual`   | Total energi yang dikonsumsi (kWh)           |
| `biaya_pemeliharaan`  | Estimasi biaya berdasarkan konsumsi & kondisi|

### 🗂️ Tabel Dimensi

- **dimensi_waktu**: tanggal, bulan, tahun
- **dimensi_pelanggan**: nama, tipe pelanggan, provinsi
- **dimensi_wilayah**: status 3S, akses jaringan
- **dimensi_aset_jaringan**: jenis aset, kondisi, tahun pemasangan

---

## 🗂️ Sumber Data

- **Dataset**: [Household Electric Power Consumption (Kaggle)](https://www.kaggle.com/datasets/uciml/electric-power-consumption-data-set)
- **Format**: CSV (.txt)
- **Periode**: Desember 2006 – Desember 2010
- **Atribut penting**: Global_active_power, Voltage, Sub_metering_1/2/3, Date, Time

---

## 🧪 Metadata Utama

| Kolom                 | Tipe Data | Deskripsi                                          |
|-----------------------|-----------|----------------------------------------------------|
| Date, Time            | String    | Tanggal dan waktu pencatatan konsumsi              |
| Global_active_power   | Float     | Daya aktif (kW)                                    |
| Global_reactive_power | Float     | Daya reaktif (kW)                                  |
| Voltage               | Float     | Tegangan (Volt)                                    |
| Sub_metering_1/2/3    | Float     | Penggunaan energi berdasarkan zona peralatan rumah|

---

## 🔧 Teknologi yang Digunakan

- **Bahasa Pemrograman**: Python (pandas, numpy)
- **Database Target**: PostgreSQL (untuk star schema)
- **Visualisasi**: Tableau
- **Sumber data utama**: Kaggle (statis)

---
