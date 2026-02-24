# Data Preparation
Data Preparation adalah tahap transformasi data mentah menjadi dataset yang siap dianalisis. Tahap ini sering kali memakan waktu terbesar karena kompleksitas dan variasi permasalahan data.

## 3.1 Pembersihan Data (Data Cleaning)
Proses ini meliputi:
Menghapus record duplikat
Menangani missing values
Memperbaiki inkonsistensi format
Menghapus data yang tidak relevan
Penanganan missing value dapat dilakukan dengan:
Imputasi statistik
Penghapusan record
Prediksi nilai menggunakan model lain
Pemilihan metode harus mempertimbangkan dampaknya terhadap bias dan variansi.

## 3.2 Transformasi dan Normalisasi
Algoritma berbasis jarak seperti K-Means sensitif terhadap skala data. Oleh karena itu dilakukan:
Normalisasi (rentang 0–1)
Standarisasi (mean 0, standar deviasi 1)
Transformasi juga dapat mencakup:
Log transformation untuk distribusi miring
Discretization untuk mengelompokkan nilai kontinu

## 3.3 Feature Engineering
Feature engineering adalah proses kreatif yang menggabungkan pemahaman domain dengan teknik analitik.
Contoh:
Menghitung rata-rata pembelian bulanan
Menghitung durasi sejak transaksi terakhir
Menggabungkan beberapa variabel menjadi indikator komposit
Feature engineering sering kali meningkatkan kemampuan model menangkap pola kompleks.

## 3.4 Seleksi Fitur
Tidak semua variabel memberikan kontribusi signifikan. Terlalu banyak fitur dapat menyebabkan:
Overfitting
Kompleksitas model tinggi
Waktu komputasi meningkat
Seleksi fitur dilakukan untuk meningkatkan efisiensi dan interpretabilitas model.
Tahap ini menghasilkan dataset akhir yang optimal dan siap digunakan dalam modeling.