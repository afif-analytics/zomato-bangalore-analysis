# 🍽️ Zomato Bangalore: Data Wrangling & Business Analytics

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Excel](https://img.shields.io/badge/Microsoft_Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)
![Academic](https://img.shields.io/badge/Academic-UAS_Data_Science-green?style=for-the-badge)

> **Tentang Proyek:** Repositori ini berisi penyelesaian *end-to-end* tugas Ujian Akhir Semester (UAS) mata kuliah Data Wrangling untuk program studi Sains Data (Semester 2). Proyek ini berfokus pada alur kerja lintas aplikasi: menggunakan Python untuk mengolah ~51.000 data mentah menjadi metrik bisnis, lalu divisualisasikan menggunakan Microsoft Excel untuk ekstraksi intelijen bisnis industri F&B di Bangalore.

---

## 🛠️ Sorotan Teknis: Alur Data Wrangling
Proyek ini mendemonstrasikan teknik pembersihan dan rekayasa data tingkat lanjut menggunakan **Pandas**, mereduksi dataset dari 51.717 baris kotor menjadi 41.505 baris berkualitas tinggi yang siap saji:

1. **General Cleaning & Dimensionality Reduction:**
   - Menghapus duplikasi data dan melakukan *drop* pada kolom yang tidak relevan dengan metrik bisnis (`url`, `reviews_list`, dll) untuk efisiensi komputasi.

2. **Specific Cleaning & Imputation:**
   - **Ekstraksi Numerik:** Membersihkan format teks anomali pada kolom `rate` menjadi tipe `float`.
   - **Robust Imputation:** Menggunakan metode **imputasi median** pada *missing values* untuk menjaga distribusi data dari pengaruh *outliers*.
   - **Entity Resolution:** Menstandarisasi berbagai penulisan sub-lokasi menjadi satu entitas konsisten menggunakan metode operasi *string*.

3. **Feature Engineering (Rekayasa Fitur):**
   - **`cost_category`:** Melakukan *binning* harga menjadi 3 kelompok proporsional (Murah, Sedang, Mahal) menggunakan fungsi `pd.qcut`.
   - **`popularity_score`:** Membuat metrik buatan dengan mengalikan *rating* dan **logaritma natural dari jumlah *votes*** (`np.log1p(votes)`) untuk meredam ketimpangan nilai ekstrem.

4. **Data Aggregation (Business Use Case Generation):**
   - Menerapkan konsep *Split-Apply-Combine* menggunakan fungsi `.groupby()` dan `.agg()`. Data yang sudah bersih dipilah berdasarkan kategori (lokasi, harga, status online) untuk dihitung rata-rata skor popularitas dan total *votes*-nya. Hasil agregasi ini kemudian di-*export* ke dalam format `Excel` secara otomatis.

---

## 📈 Ekstraksi Insight Bisnis
*(Catatan: Proses komputasi angka dan tabel agregasi dieksekusi menggunakan Python/Pandas, sementara pembuatan grafik visual di bawah ini di-generate secara manual menggunakan **Microsoft Excel** berdasarkan data hasil export).*

### 1. Analisis Lokasi (*Location Strategy*)
Area **Koramangala** secara absolut mendominasi interaksi pasar Bangalore dengan total >4,2 juta *votes*, menjadikannya episentrum F&B yang paling menjanjikan untuk ekspansi cabang baru.
![Insight Lokasi](Image/bussinescase1.png)

### 2. Segmentasi Harga (*Pricing Strategy*)
Kategori harga **"Mahal"** mengungguli kategori lain dengan rata-rata *rating* 3.93/5, membuktikan bahwa demografi pasar lebih mengutamakan pengalaman kualitas premium dibandingkan sekadar harga yang murah.
![Insight Harga](Image/bussinescase2.png)

### 3. Dampak Digitalisasi (*Online Order Impact*)
Restoran yang mengintegrasikan layanan **Pemesanan Online** memiliki Rata-Rata Skor Popularitas yang jauh lebih tinggi (17.55) dibandingkan restoran murni *offline* (15.63). Go-digital terbukti secara kuantitatif dalam memperluas jangkauan pasar.
![Insight Digital](Image/bussinescase3.png)

---

## 📂 Struktur Repositori

```text
├── Data/
│   ├── Raw/            # Dataset asli (zomato.csv)
│   └── processed/      # Data bersih multi-sheet (Zomato_Final_Analysis.xlsx)
├── Image/              # Visualisasi hasil analisis (.png)
└── Notebook/           # Source code utama (Afif Febrian_Restaurant.ipynb)
