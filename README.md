# 💧 Water Quality Analysis - Exploratory Data Analysis & Preprocessing

Analisis kualitas air dan preprocessing data untuk memprediksi apakah air **layak minum (potable)** atau **tidak layak minum (not potable)** berdasarkan parameter fisikokimia air.

---

## 📋 Daftar Isi

- [Tentang Proyek](#-tentang-proyek)
- [Dataset](#-dataset)
- [Tujuan](#-tujuan)
- [Struktur Proyek](#-struktur-proyek)
- [Teknologi & Library](#-teknologi--library)
- [Metodologi](#-metodologi)
- [Hasil Analisis](#-hasil-analisis)
- [Cara Menjalankan](#-cara-menjalankan)
- [Struktur Notebook](#-struktur-notebook)
- [Kontributor](#-kontributor)
- [Lisensi](#-lisensi)

---

## 📖 Tentang Proyek

Proyek ini merupakan bagian dari tugas mata kuliah **Pembelajaran Mesin** yang berfokus pada tahap **Exploratory Data Analysis (EDA)** dan **Preprocessing** data kualitas air. 

Analisis ini penting untuk memahami karakteristik data sebelum membangun model machine learning untuk klasifikasi kelayakan air minum.

---

## 📊 Dataset

Dataset yang digunakan adalah **Water Potability Dataset** dari Kaggle.

| Informasi | Detail |
|-----------|--------|
| **Sumber** | [Kaggle - Water Potability](https://www.kaggle.com/datasets/adityakadiwal/water-potability) |
| **Jumlah Sampel** | 3.276 baris |
| **Jumlah Fitur** | 9 parameter + 1 target |
| **Target Variable** | `Potability` (0 = Tidak Layak, 1 = Layak Minum) |

### 🔬 Parameter Kualitas Air

| Kolom | Deskripsi | Satuan |
|-------|-----------|--------|
| `ph` | Tingkat keasaman air | pH scale |
| `Hardness` | Kekerasan air (kandungan kalsium & magnesium) | mg/L |
| `Solids` | Total padatan terlarut | mg/L |
| `Chloramines` | Senyawa klorin untuk desinfeksi | mg/L |
| `Sulfate` | Kandungan sulfat | mg/L |
| `Conductivity` | Konduktivitas listrik air | μS/cm |
| `Organic_carbon` | Karbon organik total | mg/L |
| `Trihalomethanes` | Senyawa kimia hasil klorinasi | μg/L |
| `Turbidity` | Kekeruhan air | NTU |
| `Potability` | **Target**: Kelayakan air minum | 0/1 |

---

## 🎯 Tujuan

1. **Memahami karakteristik data** kualitas air melalui analisis statistik deskriptif
2. **Mengidentifikasi missing values** dan menentukan strategi penanganan yang tepat
3. **Menganalisis distribusi kelas target** untuk mendeteksi class imbalance
4. **Melakukan preprocessing data** untuk menyiapkan data sebelum modeling
5. **Visualisasi data** untuk insight yang lebih mudah dipahami

---

## 📁 Struktur Proyek

```
project/
├── README.md                    # Dokumentasi proyek (file ini)
├── code.ipynb                   # Notebook utama: EDA & Preprocessing
├── water_potability.csv         # Dataset kualitas air
├── water_quality_analysis copy.ipynb  # Notebook analisis tambahan
└── bone-fracture-classification-pytorch-cnn.ipynb  # Proyek lain (CNN)
```

---

## 🛠 Teknologi & Library

Proyek ini dibangun menggunakan **Python** dengan library berikut:

| Library | Fungsi |
|---------|--------|
| `pandas` | Manipulasi dan analisis data |
| `numpy` | Operasi numerik |
| `matplotlib` | Visualisasi data |
| `seaborn` | Visualisasi statistik |
| `scikit-learn` | Preprocessing & machine learning |

### Library yang Diimpor

```python
import warnings
import os
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

from sklearn.model_selection import train_test_split
from sklearn.preprocessing import RobustScaler
from sklearn.impute import SimpleImputer
```

---

## 🔬 Metodologi

### Alur Kerja Preprocessing

```
Load Dataset → EDA → Split Data → Handle Missing Values → Feature Scaling → Data Ready
```

### Langkah-langkah

1. **Load Dataset** 
   - Membaca file CSV ke dalam DataFrame pandas
   
2. **Exploratory Data Analysis (EDA)**
   - Statistik deskriptif (mean, median, std, min, max)
   - Analisis missing values
   - Distribusi target variable
   - Korelasi antar fitur
   - Visualisasi distribusi data

3. **Data Splitting**
   - Memisahkan features (X) dan target (y)
   - Train-test split dengan stratified sampling

4. **Handling Missing Values**
   - Menggunakan `SimpleImputer` dengan strategi yang sesuai
   - Kolom dengan missing values: `ph` (15%), `Sulfate` (24%), `Trihalomethanes` (5%)

5. **Feature Scaling**
   - Menggunakan `RobustScaler` (robust terhadap outlier)
   - Scaling penting untuk algoritma sensitif skala

---

## 📈 Hasil Analisis

### 📊 Ringkasan Dataset

| Metrik | Nilai |
|--------|-------|
| Total Baris | 3.276 |
| Total Kolom | 10 |
| Baris Duplikat | 0 |
| Total Missing Values | 1.434 |

### ⚠️ Missing Values per Kolom

| Kolom | Missing | Persentase |
|-------|---------|------------|
| `Sulfate` | 781 | 23.84% |
| `ph` | 491 | 14.99% |
| `Trihalomethanes` | 162 | 4.95% |

### 📉 Distribusi Target Variable

| Kelas | Deskripsi | Jumlah | Persentase |
|-------|-----------|--------|------------|
| 0 | Tidak Layak | 1.998 | 61.0% |
| 1 | Layak Minum | 1.278 | 39.0% |

> ⚠️ **Dataset tidak seimbang (imbalanced)** - Kelas 0 mendominasi dengan 61%

### 📊 Statistik Deskriptif

| Fitur | Mean | Std | Min | Max |
|-------|------|-----|-----|-----|
| ph | 7.08 | 1.59 | 0.00 | 14.00 |
| Hardness | 196.37 | 32.88 | 47.43 | 323.12 |
| Solids | 22014.09 | 8768.57 | 320.94 | 61227.20 |
| Chloramines | 7.12 | 1.58 | 0.35 | 13.13 |
| Sulfate | 333.78 | 41.42 | 129.00 | 481.03 |
| Conductivity | 426.21 | 80.82 | 181.48 | 753.34 |
| Organic_carbon | 14.29 | 3.31 | 2.20 | 28.30 |
| Trihalomethanes | 66.40 | 16.18 | 0.74 | 124.00 |
| Turbidity | 3.97 | 0.78 | 1.45 | 6.74 |

---

## 🚀 Cara Menjalankan

### Prasyarat

- Python 3.7 atau lebih tinggi
- Jupyter Notebook / JupyterLab

### Instalasi

1. **Clone repository ini**
   ```bash
   git clone <repository-url>
   cd project
   ```

2. **Install dependencies**
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn
   ```

3. **Jalankan Notebook**
   ```bash
   jupyter notebook code.ipynb
   ```

4. **Jalankan semua cells** untuk melihat hasil analisis lengkap

---

## 📓 Struktur Notebook

| Section | Cell | Deskripsi |
|---------|------|-----------|
| **Introduction** | 1-2 | Import library & konfigurasi |
| **Dataset** | 3-6 | Load data, preview, summary, statistics |
| **EDA** | 7-11 | Target distribution, missing values, correlation |
| **Preprocessing** | 12+ | Split, impute, scale |

---

## 👤 Kontributor

| Nama | NIM | Kelas |
|------|-----|-------|
| [Nama Anda] | [NIM Anda] | A11.4405 |

**Mata Kuliah:** Pembelajaran Mesin  
**Dosen Pengampu:** [Nama Dosen]  
**Semester:** 2  
**Tahun Akademik:** 2025

---

## 📄 Lisensi

Proyek ini dibuat untuk tujuan pendidikan. Dataset berasal dari Kaggle dan tersedia untuk penggunaan publik.

---

## 📞 Kontak

Jika ada pertanyaan atau saran, silakan hubungi saya melalui:

- 📧 Email: [your-email@example.com]
- 💼 LinkedIn: [Your LinkedIn Profile]
- 🐙 GitHub: [Your GitHub Username]

---

<div align="center">

**Made with ❤️ for Machine Learning Class**

⭐ Don't forget to star this repository if you find it helpful!

</div>
