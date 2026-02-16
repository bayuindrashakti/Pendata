# Data Understanding
Data Understanding bertujuan untuk memahami kondisi, struktur, kualitas, dan potensi dataset sebelum dilakukan pemodelan.
Data merupakan representasi dari realitas bisnis. Oleh karena itu, pemahaman terhadap data berarti memahami perilaku sistem atau pelanggan yang direpresentasikan.

### 2.1 Identifikasi dan Integrasi Sumber Data
Data dapat berasal dari berbagai sistem:
Sistem transaksi
Data pelanggan
Log aktivitas pengguna
Sistem keuangan
Data eksternal seperti demografi atau pasar
Pada tahap ini dilakukan identifikasi:
Format data
Periode waktu
Volume data
Konsistensi antar sumber
Integrasi data sering menjadi tantangan karena perbedaan struktur dan format.

### 2.2 Eksplorasi Statistik dan Visualisasi
Eksplorasi data dilakukan untuk memahami karakteristik statistik dataset, seperti:
Rata-rata dan median
Distribusi nilai
Variansi
Korelasi antar variabel
Visualisasi membantu mengidentifikasi pola yang tidak terlihat secara numerik, seperti:
Distribusi tidak normal
Hubungan non-linear
Pola musiman
Misalnya, dalam analisis penjualan, dapat ditemukan bahwa transaksi meningkat tajam pada akhir bulan atau saat promosi tertentu.

### 2.3 Analisis Kualitas Data
Kualitas data sangat memengaruhi performa model. Beberapa aspek yang dianalisis:
Missing values dan pola kemunculannya
Duplikasi data
Nilai ekstrem
Ketidakseimbangan kelas
Jika data churn hanya 5% dari total dataset, maka model mungkin cenderung memprediksi semua pelanggan sebagai “tidak churn” untuk mencapai akurasi tinggi. Ini adalah contoh pentingnya memahami distribusi kelas.
Tahap Data Understanding memberikan gambaran realistis mengenai kekuatan dan keterbatasan dataset sebelum masuk ke tahap teknis berikutnya.