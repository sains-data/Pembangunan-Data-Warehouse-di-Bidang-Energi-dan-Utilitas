# 🔋 RubicoNergi Data Warehouse — Misi 3

**Project: Data Warehouse untuk Perusahaan Energi & Utilitas (RubicoNergi)**  
Implementasi end-to-end: dimensi, fakta, storage, indexing, partisi, hingga optimasi performa.

---

## 1️⃣ Design & Implement Dimension Tables
- Mendesain 6 tabel dimensi:
  - 🕒 **WaktuDIM** → tren konsumsi energi dari minute ke year.
  - 👥 **PelangganDIM** → segmentasi pelanggan & lokasi.
  - 🌍 **GeoDIM** → data spasial (lat/lon, wilayah 3S).
  - 🏠 **PerangkatDIM** → sub-metering berdasarkan fungsi ruang.
  - ⚡ **GangguanDIM** → jenis & penyebab gangguan listrik.
  - 💳 **TagihanDIM** → status pembayaran & perilaku pelanggan.
- Menggunakan hierarki & atribut deskriptif.
- Skema: ⭐ **Star Schema**.

---

## 2️⃣ Design & Implement Fact Tables
- Tabel Fakta: **Konsumsi_EnergiFact**.
- Atribut utama:
  - ⚡ Energi_aktif, Energi_reaktif, Tegangan_rata2.
  - 🔌 Sub_metering_1, Sub_metering_2.
  - 🚨 Status_gangguan, 💳 Status_tagihan.
- Integrasi dari dataset Kaggle + CRM, GIS, Billing.
- ETL proses: 🐍 **Python (pandas, SQLite3, psycopg2)**.
- Data warehouse: 🐘 **PostgreSQL**.

---

## 3️⃣ Design & Implement Indexes
- 🔗 **Clustered Index**: Time_ID (tabel fakta).
- 🔍 **Non-clustered Index**: Household_ID, Geo_ID, Billing_ID.
- Optimasi kueri: `EXPLAIN ANALYZE`.
- Pemeliharaan: `REBUILD / REORGANIZE`.

---

## 4️⃣ Design Storage for Data Warehouse
- **Hardware**:
  - 💾 SSD RAID 10, 🧠 16-core CPU, 🗄️ 128GB RAM.
- **File Layout**:
  - 📁 MDF (SSD1), LDF (SSD2), TempDB (SSD3 multi-file).
- **Storage Models**:
  - 🗄️ Columnstore Index (Fakta), Rowstore Index (Dimensi).
- **Compression**:
  - 📦 Page Compression (Geo, Pelanggan, Tagihan).
- **Partitioning**:
  - 📅 Year & Month di Konsumsi_EnergiFact.
- **Cloud Option**:
  - ☁️ Azure Synapse dengan hash distribution.

---

## 5️⃣ Partitioned Tables & Indexed Views
- 🗂️ **Partitioning** di Konsumsi_EnergiFact (YearMonth).
- 💡 Indexed Views untuk agregasi energi per provinsi & tahun.
- Strategi maintenance:
  - 🔀 SPLIT, MERGE, SWITCH partition.
  - ⚙️ Automasi via stored procedure & SQL Agent.
- Monitoring performa: 📊 DMV (Dynamic Management Views).

---

## 🛠️ Tools & Technology
- 🐘 PostgreSQL (Data Warehouse)
- 🐍 Python (pandas, SQLite3, SQLAlchemy)
- 📊 Tableau Public (Dashboard & Visualisasi)
- ⚙️ SQL Indexing, Partitioning, DMV Monitoring

---