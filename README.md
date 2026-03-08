# Water Quality Analysis - Exploratory Data Analysis & Preprocessing

Analisis kualitas air dan preprocessing data untuk memprediksi apakah air **layak minum (potable)** atau **tidak layak minum (not potable)** berdasarkan parameter fisikokimia air.

---

## - Daftar Isi

- [Tentang Proyek](#-tentang-proyek)
- [Dataset](#-dataset)
- [Tujuan](#-tujuan)
- [Struktur Proyek](#-struktur-proyek)
- [Teknologi & Library](#-teknologi--library)
- [Cara Menjalankan](#-cara-menjalankan)
- [Struktur Notebook](#-struktur-notebook)
- [Mata Kuliah](#-mata-kuliah)
- [Lisensi](#-lisensi)

---

## - Tentang Proyek

Proyek ini merupakan bagian dari tugas mata kuliah **Pembelajaran Mesin** yang berfokus pada tahap **Exploratory Data Analysis (EDA)** dan **Preprocessing** data kualitas air.

Analisis ini penting untuk memahami karakteristik data sebelum membangun model machine learning untuk klasifikasi kelayakan air minum.

---

## - Dataset

Dataset yang digunakan adalah **Water Potability Dataset** dari Kaggle.

| Informasi           | Detail                                                                                      |
| ------------------- | ------------------------------------------------------------------------------------------- |
| **Sumber**          | [Kaggle - Water Potability](https://www.kaggle.com/datasets/adityakadiwal/water-potability) |
| **Jumlah Sampel**   | 3.276 baris                                                                                 |
| **Jumlah Fitur**    | 9 parameter + 1 target                                                                      |
| **Target Variable** | `Potability` (0 = Tidak Layak, 1 = Layak Minum)                                             |

### Parameter Kualitas Air

| Kolom             | Deskripsi                                     | Satuan   |
| ----------------- | --------------------------------------------- | -------- |
| `ph`              | Tingkat keasaman air                          | pH scale |
| `Hardness`        | Kekerasan air (kandungan kalsium & magnesium) | mg/L     |
| `Solids`          | Total padatan terlarut                        | mg/L     |
| `Chloramines`     | Senyawa klorin untuk desinfeksi               | mg/L     |
| `Sulfate`         | Kandungan sulfat                              | mg/L     |
| `Conductivity`    | Konduktivitas listrik air                     | μS/cm    |
| `Organic_carbon`  | Karbon organik total                          | mg/L     |
| `Trihalomethanes` | Senyawa kimia hasil klorinasi                 | μg/L     |
| `Turbidity`       | Kekeruhan air                                 | NTU      |
| `Potability`      | **Target**: Kelayakan air minum               | 0/1      |

---

## - Tujuan

1. **Memahami karakteristik data** kualitas air melalui analisis statistik deskriptif
2. **Mengidentifikasi missing values** dan menentukan strategi penanganan yang tepat
3. **Menganalisis distribusi kelas target** untuk mendeteksi class imbalance
4. **Melakukan preprocessing data** untuk menyiapkan data sebelum modeling
5. **Visualisasi data** untuk insight yang lebih mudah dipahami

---

## - Struktur Proyek

```
project/
├── README.md                    # Dokumentasi proyek (file ini)
├── code.ipynb                   # Notebook utama: EDA & Preprocessing
├── water_potability.csv         # Dataset kualitas air
```

---

## - Teknologi & Library

Proyek ini dibangun menggunakan **Python** dengan library berikut:

| Library        | Fungsi                           |
| -------------- | -------------------------------- |
| `pandas`       | Manipulasi dan analisis data     |
| `numpy`        | Operasi numerik                  |
| `matplotlib`   | Visualisasi data                 |
| `seaborn`      | Visualisasi statistik            |
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

## - Cara Menjalankan

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

## - Struktur Notebook

| Section           | Cell | Deskripsi                                        |
| ----------------- | ---- | ------------------------------------------------ |
| **Introduction**  | 1-2  | Import library & konfigurasi                     |
| **Dataset**       | 3-6  | Load data, preview, summary, statistics          |
| **EDA**           | 7-11 | Target distribution, missing values, correlation |
| **Preprocessing** | 12+  | Split, impute, scale                             |

---

## - Mata Kuliah

**Mata Kuliah:** Pembelajaran Mesin
**Dosen Pengampu:** ABU SALAM M.Kom

**Nama:** Alfaturachman Maulana Pahlevi
**NIM:** A11.2025.16609
**Kelas:** A11.4405

---

## - Lisensi

Proyek ini dibuat untuk tujuan pendidikan. Dataset berasal dari Kaggle dan tersedia untuk penggunaan publik.

---
