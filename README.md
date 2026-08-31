# Data Preprocessing Praktik: dari Missing Value sampai PCA

Notebook latihan hands-on untuk enam teknik inti data preprocessing sebelum data masuk ke model Machine Learning: missing values, outlier detection (IQR), feature engineering (encoding), text preprocessing (BoW/TF-IDF), dimensionality reduction (PCA), dan konsep data versioning.

Notebook ini sudah dijalankan end-to-end (`nbconvert --execute`) sebelum di-commit — semua output cell, angka, dan chart di dalamnya adalah hasil eksekusi asli, bisa dicek ulang langsung tanpa perlu percaya begitu saja pada komentar di kode.

## Isi

| Teknik | Yang Dipelajari |
|---|---|
| Missing Values | `dropna()` vs `fillna()` (mean/median), cek dulu sebelum asumsi kotor |
| Outlier Detection | Metode IQR (Interquartile Range) + visualisasi boxplot |
| Feature Engineering | Label Encoding vs One Hot Encoding |
| Text Preprocessing | Bag of Words (BoW) vs TF-IDF |
| Dimensionality Reduction | PCA (Principal Component Analysis) |
| Data Versioning | Konsep menyimpan riwayat versi dataset |

## Hasil Eksekusi Terverifikasi

| Bagian | Hasil |
|---|---|
| Dataset pelanggan (`customers-10000.csv`) | 10.000 baris × 12 kolom, missing value **0%** di semua kolom |
| Data sintetis (missing value demo) | `umur` 40% kosong (2/5), `gaji` 20% kosong (1/5) |
| Deteksi outlier IQR (1.000 data gaji + 1 outlier sengaja) | **9 dari 1.001** baris terdeteksi outlier — 4 di bawah batas bawah (~Rp1,76–2,38 juta), 4 di atas batas atas (~Rp7,63–8,85 juta), 1 disisipkan sengaja (Rp50 juta) |
| Data bersih setelah outlier dibuang | 992 dari 1.001 baris |
| PCA pada dataset Iris | 4 fitur → 2 fitur, informasi terjaga **97,8%** (PC1 92,5% + PC2 5,3%) |

## Struktur Folder

```
.
├── notebook/
│   └── Data_Handling_and_Preprocessing_Tutorial.ipynb   # notebook utama, sudah dieksekusi penuh
├── data/
│   └── customers-10000.csv                              # dataset publik (lihat kredit di bawah)
├── documentation/
│   ├── boxplot-gaji-outlier.png                         # chart hasil eksekusi cell boxplot
│   └── pca-scatter-iris.png                              # chart hasil eksekusi cell PCA
├── requirements.txt
└── README.md
```

## Cara Menjalankan

```bash
git clone https://github.com/arielshakaramiro/data-preprocessing-praktik-arielshakaramiro.git
cd data-preprocessing-praktik-arielshakaramiro
pip install -r requirements.txt
jupyter notebook notebook/Data_Handling_and_Preprocessing_Tutorial.ipynb
```

Baris load dataset di notebook sudah diarahkan ke `data/customers-10000.csv` (path lokal di repo ini), bukan lagi ke link Google Drive pribadi — isinya identik, tinggal clone dan jalankan tanpa setup tambahan.

## Kredit Dataset

`customers-10000.csv` adalah dataset sampel publik dari [Datablist](https://www.datablist.com/learn/csv/download-sample-csv-files) — data sintetis yang dibuat dengan Faker untuk keperluan latihan/testing, bukan data pelanggan sungguhan.

## Catatan

Repo ini adalah materi latihan (practice notebook), bukan pipeline production — jadi tidak ada CI/test suite seperti pada [repo pipeline data engineering](https://github.com/arielshakaramiro/assignment-data-pipeline-arielshakaramiro) sebelumnya. Tulisan lengkapnya (dengan penjelasan interaktif, quiz, dan cheat sheet) dipublikasikan di seri **AI Notes & Engineering**.

---
*Bagian dari rangkaian catatan belajar AI Engineering — rubythalib.ai AI Engineer Bootcamp.*
