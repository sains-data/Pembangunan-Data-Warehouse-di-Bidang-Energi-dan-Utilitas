# 🏭 Data Warehouse Project - RubicoNergi (Misi 2)

---

## 🎯 1. Ringkasan Kebutuhan

RubicoNergi (RBN) memerlukan data warehouse untuk mengintegrasikan data konsumsi listrik, spasial, pelanggan, gangguan, dan tagihan berbasis kebutuhan bisnis (data-driven decision making).

**Sumber Data:**
- Konsumsi Energi ➔ Sensor per menit (Kaggle dataset)
- Data Geospasial ➔ GIS (lokasi pelanggan & jaringan distribusi)
- Data Pelanggan ➔ CRM/Billing system
- Data Gangguan ➔ Trouble Ticket System
- Data Tagihan ➔ Sistem pembayaran
- Data Petugas Lapangan ➔ Operasional teknisi

**Proses Derivasi Fakta:**
- Energi Aktif (kWh) ➔ dari Global_active_power
- Energi Reaktif ➔ dari Global_reactive_power
- Tegangan ➔ rerata harian Voltage
- Sub-metering ➔ konsumsi per area (dapur, laundry, HVAC)
- Status Gangguan ➔ jumlah & waktu pemulihan gangguan
- Status Tagihan ➔ lunas, tertunda, menunggak

---

## 🗂️ 2. Skema Konseptual Multidimensi

📊 **Star Schema Design:**  
Fakta utama ➔ `Konsumsi_EnergiFact`  
Terkait ke 6 tabel dimensi:
- WaktuDIM
- PelangganDIM
- GeoDIM
- PerangkatDIM
- GangguanDIM
- TagihanDIM

---

## 🧩 3. Komponen Dimensi

### 🕒 WaktuDIM
- Atribut: Full_DateTime, Date, Time, Year, Quarter, Month, Day, Hour, Minute, Weekday_Name, Is_Weekend
- Hierarki: Menit ➔ Jam ➔ Hari ➔ Bulan ➔ Kuartal ➔ Tahun

### 👥 PelangganDIM
- Atribut: Customer_Name, Customer_Type (Rumah Tangga/Komersial), Meter_Type (Smart/Manual), Region_Type (3S/Non-3S), City_District, Province
- Hierarki: Pelanggan ➔ Kota/Kabupaten ➔ Provinsi ➔ Region_Type

### 🌍 GeoDIM
- Atribut: Latitude, Longitude, Village, Subdistrict, District, Province, Urban_Rural, Region_Type
- Hierarki: Koordinat ➔ Desa ➔ Kecamatan ➔ Kab/Kota ➔ Provinsi

### 🏠 PerangkatDIM
- Atribut: Segment_ID, Segment_Name, Device_Category (Dapur, Laundry, HVAC), Typical_Location
- Hierarki: Sub_metering ➔ Kategori Perangkat ➔ Lokasi

### ⚡ GangguanDIM
- Atribut: Gangguan_Type (Pemadaman, Fluktuasi, Kebocoran), Cause_Code (Bencana Alam, Pemeliharaan), Resolution_Method (Otomatis, Manual)
- Hierarki: Jenis Gangguan ➔ Penyebab ➔ Metode Penanganan

### 💸 TagihanDIM
- Atribut: Billing_Period, Amount_Billed, Amount_Paid, Payment_Date, Payment_Method, Outstanding_Amount, Billing_Status
- Hierarki: Periode Tagihan ➔ Status Pembayaran

---

## 🧠 4. Justifikasi Desain

- **Fakta Konsumsi Energi** ➔ pusat analisis, mencerminkan penggunaan aktual
- **Dimensi Waktu** ➔ analisis pola longitudinal & musiman
- **Dimensi Pelanggan** ➔ mendukung segmentasi & kebijakan layanan
- **Dimensi Wilayah (Geo)** ➔ analisis distribusi spasial & klaster konsumsi
- **Dimensi Gangguan** ➔ evaluasi keandalan & respon gangguan
- **Dimensi Tagihan** ➔ mendukung evaluasi performa pembayaran & mitigasi piutang

---

## 🔗 5. Kesesuaian dengan Sumber Data

📦 **Dataset Utama:**  
Household Electric Power Consumption (Kaggle, 2006-2010, CSV format)

**Mapping ke Skema Fakta:**
- Global_active_power ➔ total_kwh_terjual
- Biaya Pemeliharaan ➔ estimasi dari konsumsi & aset
- id_waktu, id_pelanggan, id_wilayah ➔ foreign key dari dimensi terkait

**Mapping ke Dimensi:**
- Waktu ➔ dari kolom Date
- Pelanggan ➔ dari CRM system
- Geo ➔ dari GIS system
- Aset Jaringan ➔ dari sistem inventori

---

## 📈 Output Project
✅ Desain Skema Multidimensi  
✅ Proses Derivasi Fakta & Dimensi  
✅ Mapping Dataset Kaggle ke Star Schema  
✅ Justifikasi Business Requirements Alignment

---