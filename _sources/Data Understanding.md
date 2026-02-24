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

## Eksplorasi/Tugas
### korelasi antara sepal_width dan sepal_length

![Gambar1](gambartugas1/tugas1.png)

Dari gambar di atas menunjukkan korelasi antara sepal_widh dan sepal_length sangat lemah atau tidak ada korelasi, dikarenakan Titik-titik data tersebar tanpa membentuk pola yang jelas, menunjukkan bahwa tidak ada hubungan yang kuat antara sepal length dan sepal width. artinya Kedua variabel ini dapat dianggap sebagai fitur yang berdiri sendiri dan tidak saling mempengaruhi secara linear.

### korelasi antara petal_width dan petal_length

![Gambar2](gambartugas1/tugas2.png)

dari gambar di atas menunjukkan korelasi antara petal_width dan petal_length sangat kuat, dikarenakan Titik-titik data membentuk pola yang jelas dari kiri bawah ke kanan atas, menunjukkan bahwa semakin besar nilai petal_length, semakin besar pula nilai petal_width. artinya kedua variabel sangat rapat membentuk pola linear yang jelas. namun terdapat Dua cluster yang terpisah kemungkinan besar merepresentasikan iris yang berbeda, tetapi tidak menyebabkan ambigu.

### korelasi antara sepal_length dan petal_length

![Gambar3](gambartugas1/tugas3.png)

Dari gambar di atas menunjukkan korelasi antara sepal_length dan petal_length sangat kuat, dikarenakan titik-titik data membentuk pola yang jelas dari kiri bawah ke kanan atas, menunjukkan bahwa semakin besar nilai sepal_length, semakin besar pula nilai petal_length. Artinya kedua variabel sangat rapat membentuk pola linear yang jelas. Namun terdapat dua cluster yang terpisah kemungkinan besar merepresentasikan iris yang berbeda, tetapi tidak menyebabkan ambigu.

### korelasi antara sepal_length dan petal_width

![Gambar3](gambartugas1/tugas3.png)

Dari gambar di atas menunjukkan korelasi antara sepal_length dan petal_width sangat kuat, dikarenakan titik-titik data membentuk pola yang jelas dari kiri bawah ke kanan atas, menunjukkan bahwa semakin besar nilai sepal_length, semakin besar pula nilai petal_width. Artinya kedua variabel sangat rapat membentuk pola linear yang jelas. Namun terdapat dua cluster yang terpisah kemungkinan besar merepresentasikan iris yang berbeda, tetapi tidak menyebabkan ambigu.

### korelasi antara sepal_width dan petal_length

![Gambar4](gambartugas1/tugas4.png)

Dari gambar di atas menunjukkan korelasi antara sepal_width dan petal_length cenderung lemah, dikarenakan titik-titik data tidak membentuk pola linear yang konsisten dari kiri bawah ke kanan atas. Terlihat adanya dua cluster yang sangat terpisah secara vertikal, di mana cluster bawah memiliki petal_length rendah dan cluster atas memiliki petal_length tinggi, namun dalam masing-masing cluster tidak ada hubungan yang jelas dengan sepal_width. Artinya kedua variabel tidak menunjukkan pola yang rapat dan penyebaran data relatif acak. Dua cluster yang terpisah ini kemungkinan besar merepresentasikan spesies iris yang berbeda dengan karakteristik yang sangat berbeda, dan pemisahan yang sangat jelas ini tidak menyebabkan ambigu.

### korelasi antara sepal_width dan petal_length

![Gambar5](gambartugas1/tugas5.png)

Dari gambar di atas menunjukkan korelasi antara sepal_width dan petal_length cenderung lemah, dikarenakan titik-titik data tidak membentuk pola linear yang konsisten dari kiri bawah ke kanan atas. Terlihat adanya dua cluster yang sangat terpisah secara vertikal, di mana cluster bawah memiliki petal_length rendah dan cluster atas memiliki petal_length tinggi, namun dalam masing-masing cluster tidak ada hubungan yang jelas dengan sepal_width. Artinya kedua variabel tidak menunjukkan pola yang rapat dan penyebaran data relatif acak. Dua cluster yang terpisah ini kemungkinan besar merepresentasikan spesies iris yang berbeda dengan karakteristik yang sangat berbeda, dan pemisahan yang sangat jelas ini tidak menyebabkan ambigu.

### korelasi antara sepal_width dan petal_width

![Gambar6](gambartugas1/tugas6.png)

Dari gambar di atas menunjukkan korelasi antara sepal_width dan petal_width lemah atau tidak konsisten, dikarenakan titik-titik data tidak membentuk pola linear yang jelas dari kiri bawah ke kanan atas. Terlihat adanya dua cluster yang sangat terpisah secara vertikal, di mana cluster bawah memiliki petal_width sangat rendah dan cluster atas memiliki petal_width lebih tinggi, namun dalam masing-masing cluster penyebaran data relatif acak tanpa menunjukkan hubungan yang kuat dengan sepal_width. Artinya kedua variabel tidak membentuk pola linear yang rapat dan peningkatan sepal_width tidak diikuti oleh peningkatan petal_width secara konsisten. Dua cluster yang terpisah ini kemungkinan besar merepresentasikan spesies iris yang berbeda, dan pemisahan yang sangat jelas ini tidak menyebabkan ambigu.

### statistik deskriptif

![statistik](gambartugas1/statistik.jpg)

Berdasarkan tabel statistik deskriptif di atas, dataset Iris menunjukkan karakteristik yang menarik untuk setiap variabel pengukuran. Pada sepal_length, nilai rata-rata sebesar 5.84 cm sangat dekat dengan median 5.8 cm, mengindikasikan distribusi data yang relatif simetris dan terkonsentrasi di kisaran 5-6 cm dengan variasi yang kecil. Sementara itu, sepal_width memiliki mean 3.05 cm dengan median dan mode sama-sama bernilai 3 cm, menunjukkan bahwa lebar sepal cenderung homogen antar spesies dengan penyebaran data yang rapat. Berbeda dengan pengukuran sepal, variabel petal_length dan petal_width menunjukkan pola yang lebih kompleks. Nilai mode pada petal_length (1.5 cm) dan petal_width (0.2 cm) sangat berbeda dengan median masing-masing (4.35 cm dan 1.3 cm), yang mengindikasikan adanya distribusi bimodal atau dua kelompok data yang terpisah jelas. Hal ini diperkuat oleh nilai dispersi yang lebih tinggi pada petal_width (0.63) dibandingkan variabel lainnya, menunjukkan bahwa pengukuran petal memiliki variabilitas yang lebih besar dan lebih efektif untuk membedakan antar spesies.



