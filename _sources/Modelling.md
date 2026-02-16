# Modeling
Modeling adalah tahap pembangunan model analitik untuk menemukan pola atau melakukan prediksi.

## 4.1 Pemilihan Teknik
Pemilihan teknik bergantung pada tujuan:
Klasifikasi → memprediksi kategori
Regresi → memprediksi nilai kontinu
Clustering → segmentasi tanpa label
Setiap teknik memiliki asumsi dan karakteristik berbeda.
## 4.2 Proses Pelatihan Model
Data dibagi menjadi training dan testing untuk menghindari overfitting. Model dilatih menggunakan data training dan diuji pada data yang belum pernah dilihat sebelumnya.
Cross-validation sering digunakan untuk memastikan stabilitas performa model.
## 4.3 Evaluasi dan Interpretasi
Evaluasi dilakukan menggunakan metrik yang sesuai konteks. Namun, interpretasi hasil sama pentingnya dengan nilai metrik.
Misalnya:
Model dengan recall tinggi mungkin lebih penting dalam deteksi fraud.
Model dengan precision tinggi mungkin lebih penting dalam kampanye pemasaran agar tidak salah sasaran.
Interpretabilitas juga menjadi perhatian, terutama pada sektor keuangan dan kesehatan yang memerlukan transparansi keputusan.
Modeling bukan hanya soal memilih algoritma terbaik, tetapi menemukan keseimbangan antara akurasi, kompleksitas, dan interpretasi.