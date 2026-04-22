# UTS
# Analisis Data Kesuburan Tanah

## Dataset Klasifikasi Kesuburan Tanah

### Deskripsi Umum

Dataset berisi **2.000 sampel** data tanah dengan **10 fitur agronomis** dan 1 kolom label yang membagi kondisi tanah menjadi dua kelas: **Subur** dan **Tidak Subur**. Data mengandung *missing values* (data hilang).

### Informasi Dataset

| Atribut | Keterangan |
|---|---|
| Jumlah Sampel | 2.000 baris |
| Jumlah Fitur | 10 fitur (9 numerik, 1 kategorikal) |
| Jumlah Kelas | 2 kelas |
| Target / Label | Subur / Tidak Subur |

---

## Penjelasan Fitur

### 1. pH Tanah
- **Satuan:** Skala pH (0–14)
- **Deskripsi:** Tingkat keasaman atau kebasaan tanah. pH optimal untuk pertanian berkisar 6,0–7,5.
- **Nilai Subur:** 6,0 – 7,5
- **Nilai Tidak Subur:** 3,5 – 5,4 (asam kuat) atau 7,6 – 9,0 (basa kuat)

### 2. N Total (%)
- **Satuan:** Persen (%)
- **Deskripsi:** Kandungan nitrogen total dalam tanah. Nitrogen sangat penting untuk pertumbuhan vegetatif tanaman.
- **Nilai Subur:** 0,21 – 0,50%
- **Nilai Tidak Subur:** 0,01 – 0,20%

### 3. P Tersedia (ppm)
- **Satuan:** Parts per million (ppm)
- **Deskripsi:** Fosfor tersedia yang dapat diserap tanaman. Fosfor berperan dalam pembentukan akar dan buah.
- **Nilai Subur:** 15 – 60 ppm
- **Nilai Tidak Subur:** 1 – 14 ppm

### 4. K Tersedia (meq/100g)
- **Satuan:** Milliequivalent per 100 gram tanah
- **Deskripsi:** Kalium tersedia dalam tanah. Penting untuk ketahanan tanaman dan proses fotosintesis.
- **Nilai Subur:** 0,30 – 0,80 meq/100g
- **Nilai Tidak Subur:** 0,05 – 0,29 meq/100g

### 5. C Organik (%)
- **Satuan:** Persen (%)
- **Deskripsi:** Kandungan karbon organik tanah, indikator utama kesuburan dan kesehatan biologi tanah.
- **Nilai Subur:** 2,0 – 5,0%
- **Nilai Tidak Subur:** 0,2 – 1,9%

### 6. KTK (meq/100g)
- **Satuan:** Milliequivalent per 100 gram tanah
- **Deskripsi:** Kapasitas Tukar Kation — kemampuan tanah mengikat dan menyediakan unsur hara bagi tanaman. Semakin tinggi semakin subur.
- **Nilai Subur:** 20 – 45 meq/100g
- **Nilai Tidak Subur:** 5 – 19 meq/100g

### 7. Kejenuhan Basa (%)
- **Satuan:** Persen (%)
- **Deskripsi:** Persentase kation basa (Ca, Mg, K, Na) dari total KTK. Menggambarkan kualitas kesuburan kimia tanah.
- **Nilai Subur:** 60 – 100%
- **Nilai Tidak Subur:** 10 – 59%

### 8. Tekstur Tanah
- **Tipe:** Kategorikal
- **Deskripsi:** Komposisi partikel tanah yang memengaruhi drainase, aerasi, dan kemampuan menahan air.

| Kelas | Tekstur yang Umum |
|---|---|
| Subur | Lempung, Lempung Berpasir, Lempung Berliat |
| Tidak Subur | Pasir, Liat, Debu |

### 9. Kadar Air (%)
- **Satuan:** Persen (%)
- **Deskripsi:** Persentase kadar air dalam tanah. Terlalu kering atau terlalu basah sama-sama merugikan pertumbuhan tanaman.
- **Nilai Subur:** 25 – 45%
- **Nilai Tidak Subur:** 5 – 20% (terlalu kering) atau 55 – 75% (terlalu basah)

### 10. Bulk Density (g/cm³)
- **Satuan:** Gram per sentimeter kubik
- **Deskripsi:** Kerapatan tanah. Nilai tinggi menandakan tanah padat, aerasi buruk, dan sulit ditembus akar.
- **Nilai Subur:** 0,9 – 1,2 g/cm³
- **Nilai Tidak Subur:** 1,4 – 1,9 g/cm³

---

## Definisi Kelas

| Label | Deskripsi |
|---|---|
| **Subur** | Tanah dengan kondisi fisik, kimia, dan biologi yang optimal untuk pertumbuhan tanaman. Ditandai dengan pH seimbang, unsur hara cukup, tekstur ideal, dan struktur tanah yang baik. |
| **Tidak Subur** | Tanah yang memiliki satu atau lebih kondisi pembatas seperti pH ekstrem, kekurangan unsur hara, tekstur buruk, kadar air tidak ideal, atau kerapatan tanah tinggi. |

### Distribusi Kelas

| Kelas | Jumlah | Persentase |
|---|---|---|
| Subur | 1.000 sampel | 50% |
| Tidak Subur | 1.000 sampel | 50% |
| **Total** | **2.000 sampel** | **100%** |

---

## Pemrosesan Data

### Missing Values

| Kolom | Jumlah Missing | Metode Imputasi |
|---|---|---|
| N Total (%) | 160 | Median = 0,1995 |
| P Tersedia (ppm) | 240 | Median = 15,065 |
| K Tersedia (meq/100g) | 140 | Median = 0,3005 |
| C Organik (%) | 200 | Median = 2,000 |
| Kadar Air (%) | 180 | Median = 34,365 |
| Bulk Density (g/cm³) | 120 | Median = 1,405 |
| Tekstur Tanah | 100 | Modus = "Lempung" |
| **Total** | **1.140** | — |

### Encoding Fitur Kategorikal

Kolom **Tekstur Tanah** diubah menjadi angka menggunakan *Label Encoding*:

| Tekstur | Nilai Numerik |
|---|---|
| Debu | 0 |
| Lempung | 1 |
| Lempung Berliat | 2 |
| Lempung Berpasir | 3 |
| Liat | 4 |
| Pasir | 5 |

### Encoding Label

| Label | Nilai Numerik |
|---|---|
| Subur | 0 |
| Tidak Subur | 1 |

### Normalisasi

Seluruh fitur numerik dinormalisasi menggunakan **Z-Score (StandardScaler)** agar KNN tidak bias terhadap perbedaan skala antar fitur.

$$z = \frac{x - \mu}{\sigma}$$

### Pembagian Data (Train/Test Split)

| Set | Jumlah | Persentase |
|---|---|---|
| Training | 1.600 data | 80% |
| Testing | 400 data | 20% |

- **Metode:** Stratified Sampling
- **Random Seed:** 42

---

## Analisis K-Nearest Neighbors (KNN)

### Konfigurasi Model

| Parameter | Nilai |
|---|---|
| Algoritma | K-Nearest Neighbors (KNN) |
| Nilai k | 5 |
| Metrik Jarak | Euclidean Distance |
| Kolom Target | Label |

### Rumus Euclidean Distance

$$d(x, y) = \sqrt{\sum_{i=1}^{n}(x_i - y_i)^2}$$

---

## Metrik Evaluasi

### Hasil

| Metrik | Nilai |
|---|---|
| **Accuracy** | **100,00%** |
| **Precision** | **1,0000** |
| **Recall** | **1,0000** |
| **F1-Score** | **1,0000** |

### Penjelasan Metrik

| Metrik | Keterangan | Rumus |
|---|---|---|
| **Accuracy** | Persentase prediksi benar dari total data | $\frac{TP + TN}{TP + TN + FP + FN}$ |
| **Precision** | Ketepatan prediksi kelas positif | $\frac{TP}{TP + FP}$ |
| **Recall** | Kemampuan mendeteksi seluruh kelas positif | $\frac{TP}{TP + FN}$ |
| **F1-Score** | Harmonic mean antara Precision dan Recall | $\frac{2 \times Precision \times Recall}{Precision + Recall}$ |

### Classification Report

| Kelas | Precision | Recall | F1-Score | Support |
|---|---|---|---|---|
| Subur | 1,00 | 1,00 | 1,00 | 200 |
| Tidak Subur | 1,00 | 1,00 | 1,00 | 200 |
| **Rata-rata** | **1,00** | **1,00** | **1,00** | **400** |

### Confusion Matrix

|  | Prediksi: Subur | Prediksi: Tidak Subur |
|---|---|---|
| **Aktual: Subur** | 200 (TP) | 0 (FP) |
| **Aktual: Tidak Subur** | 0 (FN) | 200 (TN) |

---

## Kesimpulan

Model **K-Nearest Neighbors (KNN)** dengan nilai `k=5` dan metrik jarak Euclidean berhasil mengklasifikasikan kesuburan tanah dengan hasil **sempurna (100%)** pada seluruh metrik evaluasi.

Hal ini terjadi karena dataset bersifat **sintetis** dengan aturan pembagian kelas yang sangat deterministik — setiap fitur memiliki rentang nilai yang benar-benar terpisah antara kelas Subur dan Tidak Subur, sehingga model KNN mampu memisahkan kedua kelas tanpa kesalahan sama sekali.

### Urutan Langkah Analisis (Pipeline)

```
CSV Reader
    ↓
Column Filter  (hapus kolom ID)
    ↓
Missing Value  (imputasi: Median & Most Frequent)
    ↓
Category To Number  (encoding Tekstur Tanah)
    ↓
Normalizer  (Z-Score)
    ↓
Partitioning  (80% train / 20% test, stratified)
    ↓
K Nearest Neighbor  (k=5, Euclidean)
    ↓
Scorer  (Accuracy, Precision, Recall, F1-Score)
```