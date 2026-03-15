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

### python (google colab)

bukti screenshot

![screenshot](gambartugas1/buktiss.png)

### link program

https://colab.research.google.com/drive/1xl65AHBp9bWO_wA2mRbTdoj_e6VPWey1?usp=sharing

### kode lengkap

```python
import pandas as pd
from scipy import stats

df = pd.read_csv("IRIS.csv")

print("Daftar Kolom:", df.columns.tolist())
print("-" * 60)

kolom_numerik = ['sepal_length', 'sepal_width', 'petal_length', 'petal_width']

for kolom in kolom_numerik:
    print(f"\n Statistik untuk kolom: {kolom.upper()}")
    print("-" * 40)
    print("Jumlah data     :", df[kolom].count())
    print("Rata-rata       :", "{0:.2f}".format(df[kolom].mean()))
    print("Nilai minimal   :", df[kolom].min())
    print("Q1              :", "{0:.2f}".format(df[kolom].quantile(0.25)))
    print("Q2 (Median)     :", "{0:.2f}".format(df[kolom].quantile(0.5)))
    print("Q3              :", "{0:.2f}".format(df[kolom].quantile(0.75)))
    print("Nilai Max       :", df[kolom].max())
    print("Kemencengan 1   :", "{0:.2f}".format(round(df[kolom].skew(), 2)))
    print("Kemencengan 2   :", "{0:.6f}".format(round(df[kolom].skew(), 6)))
    print("Standar Deviasi :", "{0:.2f}".format(round(df[kolom].std(), 2)))
    print("Variansi        :", "{0:.2f}".format(round(df[kolom].var(), 2)))
    
    mode_result = stats.mode(df[kolom].dropna(), keepdims=True)
    if len(mode_result.mode) > 0 and not pd.isna(mode_result.mode[0]):
        print("Nilai modus     : {} dengan frekuensi {}".format(
            mode_result.mode[0], mode_result.count[0]))
    else:
        print("Nilai modus     : Tidak ada modus tunggal")

print(f"\n🌸 Statistik untuk kolom: SPECIES")
print("-" * 40)
print("Jumlah data     :", df['species'].count())
print("Jumlah unik     :", df['species'].nunique())
print("Nilai unik      :", df['species'].unique().tolist())
print("\nDistribusi frekuensi:")
print(df['species'].value_counts())
print("\nModus (kategori paling sering):", df['species'].mode().values[0])
```

### output

''' text
Daftar Kolom: ['sepal_length', 'sepal_width', 'petal_length', 'petal_width', 'species']
------------------------------------------------------------

 Statistik untuk kolom: SEPAL_LENGTH
----------------------------------------
Jumlah data     : 150
Rata-rata       : 5.84
Nilai minimal   : 4.3
Q1              : 5.10
Q2 (Median)     : 5.80
Q3              : 6.40
Nilai Max       : 7.9
Kemencengan 1   : 0.31
Kemencengan 2   : 0.314911
Standar Deviasi : 0.83
Variansi        : 0.69
Nilai modus     : 5.0 dengan frekuensi 10

 Statistik untuk kolom: SEPAL_WIDTH
----------------------------------------
Jumlah data     : 150
Rata-rata       : 3.05
Nilai minimal   : 2.0
Q1              : 2.80
Q2 (Median)     : 3.00
Q3              : 3.30
Nilai Max       : 4.4
Kemencengan 1   : 0.33
Kemencengan 2   : 0.334053
Standar Deviasi : 0.43
Variansi        : 0.19
Nilai modus     : 3.0 dengan frekuensi 26

 Statistik untuk kolom: PETAL_LENGTH
----------------------------------------
Jumlah data     : 150
Rata-rata       : 3.76
Nilai minimal   : 1.0
Q1              : 1.60
Q2 (Median)     : 4.35
Q3              : 5.10
Nilai Max       : 6.9
Kemencengan 1   : -0.27
Kemencengan 2   : -0.274464
Standar Deviasi : 1.76
Variansi        : 3.11
Nilai modus     : 1.5 dengan frekuensi 14

 Statistik untuk kolom: PETAL_WIDTH
----------------------------------------
Jumlah data     : 150
Rata-rata       : 1.20
Nilai minimal   : 0.1
Q1              : 0.30
Q2 (Median)     : 1.30
Q3              : 1.80
Nilai Max       : 2.5
Kemencengan 1   : -0.10
Kemencengan 2   : -0.104997
Standar Deviasi : 0.76
Variansi        : 0.58
Nilai modus     : 0.2 dengan frekuensi 28

🌸 Statistik untuk kolom: SPECIES
----------------------------------------
Jumlah data     : 150
Jumlah unik     : 3
Nilai unik      : ['Iris-setosa', 'Iris-versicolor', 'Iris-virginica']

Distribusi frekuensi:
species
Iris-setosa        50
Iris-versicolor    50
Iris-virginica     50
Name: count, dtype: int64

Modus (kategori paling sering): Iris-setosa
'''

### penjelasan mengukur Jarak dengan tipe data campuran
#### Latar Belakang

Dalam praktik nyata, database yang digunakan untuk analisis data sering kali tidak hanya mengandung satu jenis tipe data saja, melainkan berbagai tipe data yang tercampur menjadi satu kesatuan. Sebagai contoh, sebuah dataset dapat memuat atribut nominal seperti warna atau jenis produk, atribut binary simetris seperti jenis kelamin, atribut binary asimetris seperti hasil tes medis yang bernilai Y/N, atribut numerik berupa data interval atau rasio seperti suhu atau pendapatan, serta atribut ordinal yang memiliki tingkatan atau peringkat seperti level kepuasan atau tingkat pendidikan. Karena setiap tipe data tersebut memiliki karakteristik dan cara pengukuran yang berbeda-beda, kita tidak dapat menerapkan satu rumus jarak secara langsung untuk menghitung kemiripan atau perbedaan antar objek. Sebagai solusi, pendekatan yang dapat digunakan adalah metode pembobotan, yaitu dengan menghitung jarak untuk setiap atribut secara terpisah sesuai dengan tipe datanya, kemudian menggabungkan seluruh hasil perhitungan tersebut menggunakan rumus jarak campuran yang memperhitungkan indikator validitas setiap atribut. Dengan pendekatan ini, seluruh jenis atribut dapat berkontribusi secara proporsional dalam perhitungan jarak akhir, sehingga hasil analisis menjadi lebih akurat dan mencerminkan karakteristik data yang sebenarnya.


### Rumus mengukur jarak data campuran

![rumusjarak](gambartugas1/rumusjarakcampur.png)

Keterangan:

simbol	penjelasan
d(i,j)	Jarak antara objek i dan j
p	umlah total atribut
δ ij (f)​	Indikator: 1 jika atribut ke-f valid untuk dibandingkan, 0 jika tidak (misal: data missing)
d ij (f)​	Jarak untuk atribut ke-f saja
Cara Menghitung d(f)ij per Tipe Atribut
#### 1. Atribut Nominal atau Binary

ij(f) = 0, jika xif = xjf (nilai sama)


dij(f) = 1, jika xif ≠ xjf (nilai berbeda)


cara penghitungannya Menggunakan metode simple matching.


#### 2. Atribut Numerik

Lakukan normalisasi terlebih dahulu agar skala seragam, misalnya dengan:

![numerik](gambartugas1/atributnumerik.png)

Mean Absolute Deviation: lebih robust terhadap outlier


Setelah dinormalisasi, hitung jarak dengan metode numerik (Euclidean, Manhattan, dll).


#### Atribut Ordinal

Langkah-langkah:


Ganti nilai dengan ranking r i f​ (misal: rendah=1, sedang=2, tinggi=3)

![ordinal](gambartugas1/atributnominal.png)

Hitung jarak menggunakan metode numerik pada nilai z i f​


### analisis mengunakan orange data mining untuk data yang campuran

contoh data saya untuk menganalisis penghitungan jarak di orange
![analisis](gambartugas1/analisisdataorange.png)

Widget Distances digunakan untuk menghitung matriks dissimilarity (jarak) antar objek dalam dataset. arameter Compare diset ke Rows yang berarti perhitungan jarak dilakukan antar objek/data point (baris dalam dataset), bukan antar atribut. Hal ini sesuai dengan konsep matriks dissimilarity, dimana matriks segitiga dihasilkan dari perhitungan jarak antar n titik data. Metric jarak yang dipilih adalah Manhattan (normalized) karena data yang saya pakai memiliki data campuran

![gambar2](gambartugas1/analisisdataorange2.png)

Gambar tersebut menampilkan Matriks Dissimilarity (Distance Matrix) yang dihasilkan melalui widget Distance Matrix pada Orange Data Mining. matriks ini berbentuk segitiga (single mode) yang memuat data jarak antar n titik data. Struktur matriks ini bersifat simetris, dimana jarak antara objek i ke objek j sama dengan jarak objek j ke objek i atau d(i,j) = d(j,i), dan memiliki nilai diagonal nol yang menunjukkan jarak objek terhadap dirinya sendiri. nilai dissimilarity dalam matriks ini merupakan ukuran numerik dari perbedaan dua objek data. Interpretasi nilai jarak mengikuti prinsip dimana nilai yang sangat rendah menunjukkan benda yang lebih mirip, sedangkan nilai yang tinggi menunjukkan perbedaan yang besar. Hal ini terlihat jelas pada data pelanggan dalam matriks. Sebagai contoh, jarak antara customer 7590-VHVEG dan 5575-GNVDE adalah 2,074, yang menunjukkan tingkat perbedaan sedang. Namun, customer 7590-VHVEG memiliki nilai jarak yang lebih kecil yaitu 0,554 terhadap customer 3668-QPYBK, yang mengindikasikan bahwa kedua customer tersebut memiliki karakteristik yang sangat mirip. Sebaliknya, perbedaan yang signifikan terlihat pada pasangan customer 8091-TTVAX dan 3668-QPYBK yang memiliki nilai jarak sebesar 4,519. Nilai yang besar ini menandakan bahwa kedua objek tersebut sangat berbeda secara karakteristik. Secara keseluruhan, matriks ini memenuhi sifat-sifat jarak yaitu positive definiteness (nilai > 0 untuk objek berbeda), symmetry, dan triangle inequality. Hasil matriks dissimilarity ini menjadi dasar utama untuk tahapan selanjutnya yaitu Hierarchical Clustering dalam mengelompokkan pelanggan berdasarkan kemiripan karakteristiknya.

![gambar3](gambartugas1/analisisdataorange3.png)

![gambar4](gambartugas1/analisisdataorange4.png)

Berdasarkan dendrogram, hierarchical clustering dilakukan dengan metode linkage Ward dan menghasilkan 4 cluster optimal. Pemotongan dendrogram dilakukan pada ketinggian tertentu sehingga diperoleh:

Cluster 1: sejumlah X customer, Cluster 2: sejumlah X customer, Cluster 3: sejumlah X customer, Cluster 4: sejumlah X customer,

Metode Ward linkage dipilih karena mampu menghasilkan cluster yang lebih kompak dengan meminimalkan varians dalam setiap cluster.

### implementasikan data iris untuk mengukur jara di orange

![implementasi1](gaambartugas1/implementasidataorange.png)

gambar diatas merupakan sebagian data mentah dari iris untuk diimplementasikan dalam menghitung jarak

![implementasi2](gambartugas1/implementasidataorange2.png)

gambar di atas merupakan hasil dari menghitung jarak pada data iris dimana prosesnya sama dengan yang tadi
![implementasi3](gambartugas1/implementasidataorange3.png)

gambar di atas merupakan visualiasi pengukuran jarak pada orange, tetapi sementara saya menggunakan widget csv file impor untuk mengimpor data iris bukan menggunakan sql table karena widget tersebut masih ada erornya atau tidak bisa di pakai dan belum menemukan solusinya


## Mengukur Jarak/Similaritas Data

---

### Normalisasi data

Normalisasi data adalah teknik pra-pemrosesan yang sangat penting dalam *data mining* dan *machine learning*. Tujuannya adalah menyamakan skala seluruh variabel/fitur agar tidak ada satu atribut pun yang mendominasi atribut lain hanya karena memiliki rentang angka yang lebih besar (misalnya, membandingkan atribut **Penghasilan Orang Tua** dalam ribuan dengan **IPK** dalam satuan kecil 2–4).

**Misal kita punya data mahasiswa: X = [IPK, Penghasilan_OT, Nilai_UAS, Jarak_Kampus]**

Berikut adalah tiga teknik normalisasi data yang paling sering digunakan:

---

#### Dataset Sebelum Normalisasi

| No | Nama  | IPK  | Penghasilan_OT (rb) | Nilai_UAS | Jarak_Kampus (km) |
|----|-------|------|----------------------|-----------|-------------------|
| 1  | Andi  | 3.50 | 5000                 | 85        | 10                |
| 2  | Budi  | 2.75 | 2000                 | 65        | 25                |
| 3  | Citra | 3.85 | 8000                 | 92        | 5                 |
| 4  | Deni  | 2.40 | 1500                 | 55        | 40                |
| 5  | Eva   | 3.10 | 3500                 | 78        | 15                |
| 6  | Fajar | 3.60 | 6000                 | 88        | 8                 |
| 7  | Gina  | 2.90 | 2500                 | 70        | 30                |
| 8  | Hadi  | 3.20 | 4000                 | 80        | 12                |
| 9  | Indah | 3.75 | 7500                 | 90        | 6                 |
| 10 | Joko  | 2.55 | 1800                 | 60        | 35                |

---

#### 1. Min-Max Normalization

Metode ini digunakan untuk menyesuaikan nilai data agar berada dalam rentang tertentu, biasanya **0 sampai 1**. Teknik ini sering dipakai pada algoritma yang menghitung jarak antar data, misalnya pada *K-Means Clustering* dan *K-Nearest Neighbor*.

- **Kelebihan:** Hubungan antar nilai data tetap terjaga. Output selalu dalam rentang [0, 1].
- **Kelemahan:** Mudah terpengaruh oleh *outlier* — jika ada satu data yang nilainya jauh melebihi lainnya, semua data lain akan terkompresi mendekati 0.
- **Rumus:**

$$x' = \frac{x - x_{min}}{x_{max} - x_{min}}$$

##### Contoh

Mengubah nilai data agar berada pada rentang **0 sampai 1**. Kolom **IPK**, mahasiswa **Andi (IPK = 3.50)**:

- Nilai minimum IPK: $x_{min}$ = **2.40** (Deni)
- Nilai maksimum IPK: $x_{max}$ = **3.85** (Citra)
- Contoh hitung (IPK Andi = 3.50):

$$IPK'_{Andi} = \frac{3.50 - 2.40}{3.85 - 2.40} = \frac{1.10}{1.45} \approx \mathbf{0.7586}$$

Artinya, IPK Andi berada di posisi **75.86%** dari rentang nilai terendah ke tertinggi. Nilai **0** dimiliki Deni (terendah) dan nilai **1** dimiliki Citra (tertinggi).

**Tabel Sebelum (kiri) dan Sesudah Min-Max Normalization (kanan):**

| Nama  | IPK  | Penghasilan_OT | Nilai_UAS | Jarak_Km |   | IPK'   | Penghasilan' | UAS'   | Jarak' |
|-------|------|----------------|-----------|----------|---|--------|--------------|--------|--------|
| **Andi**  | **3.50** | **5000**   | **85**    | **10**   |   | **0.7586** | **0.5385** | **0.8108** | **0.1429** |
| Budi  | 2.75 | 2000           | 65        | 25       |   | 0.2414 | 0.0769       | 0.2703 | 0.5714 |
| Citra | 3.85 | 8000           | 92        | 5        |   | 1.0000 | 1.0000       | 1.0000 | 0.0000 |
| Deni  | 2.40 | 1500           | 55        | 40       |   | 0.0000 | 0.0000       | 0.0000 | 1.0000 |
| Eva   | 3.10 | 3500           | 78        | 15       |   | 0.4828 | 0.3077       | 0.6216 | 0.2857 |
| Fajar | 3.60 | 6000           | 88        | 8        |   | 0.8276 | 0.6923       | 0.8919 | 0.0857 |
| Gina  | 2.90 | 2500           | 70        | 30       |   | 0.3448 | 0.1538       | 0.4054 | 0.7143 |
| Hadi  | 3.20 | 4000           | 80        | 12       |   | 0.5517 | 0.3846       | 0.6757 | 0.2000 |
| Indah | 3.75 | 7500           | 90        | 6        |   | 0.9310 | 0.9231       | 0.9459 | 0.0286 |
| Joko  | 2.55 | 1800           | 60        | 35       |   | 0.1034 | 0.0462       | 0.1351 | 0.8571 |

> Baris **Andi** (tebal) = contoh yang dihitung manual di atas. Citra mendapat **1.0000** karena nilai tertinggi, Deni mendapat **0.0000** karena nilai terendah.

##### Min-Max New (Custom Range)

Min-Max juga bisa digunakan untuk mengubah data ke **rentang baru yang kita tentukan sendiri**, misalnya 0–10, −1 sampai 1, atau rentang lainnya.

- **Rumus:**

$$x' = \frac{x - x_{min}}{x_{max} - x_{min}} \times (New_{max} - New_{min}) + New_{min}$$

###### Contoh

Misalnya IPK Andi ingin diubah ke rentang **0 sampai 10**:

$$IPK'_{Andi} = \frac{3.50 - 2.40}{3.85 - 2.40} \times (10 - 0) + 0 = \frac{1.10}{1.45} \times 10 \approx \mathbf{7.586}$$

---

#### 2. Z-Score Normalization

Teknik ini mengubah data sehingga nilai rata-rata (*mean*) menjadi **0** dan standar deviasi menjadi **1**. Metode ini sering digunakan ketika data memiliki skala yang berbeda atau terdapat *outlier*.

- **Kelebihan:** Lebih tahan terhadap *outlier* dibanding Min-Max karena mempertimbangkan penyebaran data.
- **Kelemahan:** Hasil normalisasi tidak memiliki batas rentang tetap seperti 0 sampai 1.
- **Rumus:**

$$x' = \frac{x - \mu}{\sigma}$$

*(Keterangan: $\mu$ adalah rata-rata dan $\sigma$ adalah standar deviasi)*

##### Contoh

Tujuan: mengubah data sehingga **mean = 0** dan **standar deviasi = 1**. Kolom **IPK**, mahasiswa **Andi (IPK = 3.50)**:

**Langkah 1 — Hitung rata-rata (μ):**

$$\mu = \frac{3.50+2.75+3.85+2.40+3.10+3.60+2.90+3.20+3.75+2.55}{10} = \mathbf{3.16}$$

**Langkah 2 — Hitung standar deviasi (σ):**

$$\sigma = \sqrt{\frac{\sum (x - \mu)^2}{n-1}} = \mathbf{0.5082}$$

**Langkah 3 — Masukkan ke rumus Z-Score:**

$$IPK'_{Andi} = \frac{3.50 - 3.16}{0.5082} = \frac{0.34}{0.5082} \approx \mathbf{0.6691}$$

Nilai positif berarti IPK Andi berada **0.6691 standar deviasi di atas rata-rata**. Jika hasilnya negatif seperti Budi (−0.8068), berarti IPK Budi berada di bawah rata-rata kelompok.

**Tabel Sebelum (kiri) dan Sesudah Z-Score Normalization (kanan):**

| Nama  | IPK  | Penghasilan_OT | Nilai_UAS | Jarak_Km |   | IPK'    | Penghasilan' | UAS'    | Jarak'  |
|-------|------|----------------|-----------|----------|---|---------|--------------|---------|---------|
| **Andi**  | **3.50** | **5000**   | **85**    | **10**   |   | **0.6691**  | **0.3461**   | **0.6629**  | **−0.6696** |
| Budi  | 2.75 | 2000           | 65        | 25       |   | −0.8068 | −0.9202      | −0.8610 | 0.4983  |
| Citra | 3.85 | 8000           | 92        | 5        |   | 1.3579  | 1.6124       | 1.1963  | −1.0590 |
| Deni  | 2.40 | 1500           | 55        | 40       |   | −1.4956 | −1.1312      | −1.6230 | 1.6663  |
| Eva   | 3.10 | 3500           | 78        | 15       |   | −0.1181 | −0.2870      | 0.1295  | −0.2803 |
| Fajar | 3.60 | 6000           | 88        | 8        |   | 0.8659  | 0.7682       | 0.8915  | −0.8254 |
| Gina  | 2.90 | 2500           | 70        | 30       |   | −0.5117 | −0.7091      | −0.4800 | 0.8877  |
| Hadi  | 3.20 | 4000           | 80        | 12       |   | 0.0787  | −0.0760      | 0.2819  | −0.5139 |
| Indah | 3.75 | 7500           | 90        | 6        |   | 1.1611  | 1.4013       | 1.0439  | −0.9811 |
| Joko  | 2.55 | 1800           | 60        | 35       |   | −1.2004 | −1.0046      | −1.2420 | 1.2770  |

> Nilai **positif** = di atas rata-rata. Nilai **negatif** = di bawah rata-rata. Baris **Andi** (tebal) = contoh perhitungan manual di atas.

---

#### 3. Decimal Scaling

Teknik ini bekerja dengan menggeser titik desimal dari nilai data. Jumlah pergeseran desimal bergantung pada nilai absolut maksimum di dalam atribut tersebut. Ini adalah metode normalisasi yang **paling mudah dihitung secara manual**.

- **Kelebihan:** Sederhana dan mudah dihitung, tidak perlu menghitung mean atau std.
- **Kelemahan:** Tidak mempertimbangkan distribusi data secara keseluruhan.
- **Rumus:**

$$x' = \frac{x}{10^j}$$

*(Keterangan: $j$ adalah bilangan bulat terkecil sehingga nilai mutlak maksimum dari $x'$ kurang dari 1)*

##### Contoh

Menggeser koma desimal. Pembaginya ditentukan oleh jumlah digit nilai terbesar di setiap kolom supaya nilai akhirnya kurang dari 1:

**Kolom IPK** — nilai terbesar = 3.85, bagian bulat = 3 → **1 digit** → $j = 1$ → dibagi $10^1 = 10$:

$$IPK'_{Andi} = \frac{3.50}{10} = \mathbf{0.350}$$

**Kolom Penghasilan_OT** — nilai terbesar = 8000 → **4 digit** → $j = 4$ → dibagi $10^4 = 10.000$:

$$Penghasilan'_{Andi} = \frac{5000}{10000} = \mathbf{0.5000}$$

Nilai $j$ yang digunakan per kolom:
- **IPK**: maks = 3.85 → j = 1 → dibagi **10**
- **Penghasilan_OT**: maks = 8000 → j = 4 → dibagi **10.000**
- **Nilai_UAS**: maks = 92 → j = 2 → dibagi **100**
- **Jarak_Kampus**: maks = 40 → j = 2 → dibagi **100**

**Tabel Sebelum (kiri) dan Sesudah Decimal Scaling (kanan):**

| Nama  | IPK  | Penghasilan_OT | Nilai_UAS | Jarak_Km |   | IPK'   | Penghasilan' | UAS' | Jarak' |
|-------|------|----------------|-----------|----------|---|--------|--------------|------|--------|
| **Andi**  | **3.50** | **5000**   | **85**    | **10**   |   | **0.3500** | **0.5000** | **0.85** | **0.10** |
| Budi  | 2.75 | 2000           | 65        | 25       |   | 0.2750 | 0.2000       | 0.65 | 0.25   |
| Citra | 3.85 | 8000           | 92        | 5        |   | 0.3850 | 0.8000       | 0.92 | 0.05   |
| Deni  | 2.40 | 1500           | 55        | 40       |   | 0.2400 | 0.1500       | 0.55 | 0.40   |
| Eva   | 3.10 | 3500           | 78        | 15       |   | 0.3100 | 0.3500       | 0.78 | 0.15   |
| Fajar | 3.60 | 6000           | 88        | 8        |   | 0.3600 | 0.6000       | 0.88 | 0.08   |
| Gina  | 2.90 | 2500           | 70        | 30       |   | 0.2900 | 0.2500       | 0.70 | 0.30   |
| Hadi  | 3.20 | 4000           | 80        | 12       |   | 0.3200 | 0.4000       | 0.80 | 0.12   |
| Indah | 3.75 | 7500           | 90        | 6        |   | 0.3750 | 0.7500       | 0.90 | 0.06   |
| Joko  | 2.55 | 1800           | 60        | 35       |   | 0.2550 | 0.1800       | 0.60 | 0.35   |

> Baris **Andi** (tebal) = contoh yang dihitung manual di atas.

---

#### Implementasi dengan Sklearn dan Fungsi Kustom

Berikut adalah script Python menggunakan `scikit-learn` untuk Min-Max dan Z-Score, serta fungsi manual untuk Decimal Scaling.

```python
import pandas as pd
import numpy as np
from sklearn.preprocessing import MinMaxScaler, StandardScaler

# Data asli mahasiswa
data = {
    'Nama':           ['Andi','Budi','Citra','Deni','Eva','Fajar','Gina','Hadi','Indah','Joko'],
    'IPK':            [3.50, 2.75, 3.85, 2.40, 3.10, 3.60, 2.90, 3.20, 3.75, 2.55],
    'Penghasilan_OT': [5000, 2000, 8000, 1500, 3500, 6000, 2500, 4000, 7500, 1800],
    'Nilai_UAS':      [85, 65, 92, 55, 78, 88, 70, 80, 90, 60],
    'Jarak_Kampus':   [10, 25, 5, 40, 15, 8, 30, 12, 6, 35]
}
df    = pd.DataFrame(data)
fitur = ['IPK', 'Penghasilan_OT', 'Nilai_UAS', 'Jarak_Kampus']

print("Data Asli:")
print(df.to_string(index=False))

# 1. Min-Max Scaling (Sklearn)
minmax_scaler = MinMaxScaler()
X_minmax = minmax_scaler.fit_transform(df[fitur])
print("\n1. Hasil Min-Max Scaling:")
print(X_minmax.round(4))

# 2. Z-Score / Standardization (Sklearn)
standard_scaler = StandardScaler()
X_standard = standard_scaler.fit_transform(df[fitur])
print("\n2. Hasil Z-Score (Standardization):")
print(X_standard.round(4))

# 3. Decimal Scaling (Custom Function)
def decimal_scaling(df_input, cols):
    """
    Melakukan decimal scaling pada setiap kolom numerik.
    Nilai dibagi dengan 10^j, di mana j adalah jumlah digit
    dari nilai absolut terbesar pada kolom tersebut.
    """
    result = df_input.copy()
    for col in cols:
        max_abs = result[col].abs().max()
        j = len(str(int(max_abs)))          # Jumlah digit nilai maks
        result[col] = (result[col] / (10 ** j)).round(4)
        print(f"  Kolom '{col}': nilai maks = {max_abs}, j = {j}, dibagi {10**j}")
    return result

print("\n3. Decimal Scaling (Fungsi Manual):")
df_decimal = decimal_scaling(df, fitur)
print(df_decimal.to_string(index=False))
```

---

### Tugas - Missing Values

#### 1. Transkripsi Data

Dataset mahasiswa ditambah kolom **Nilai_Tugas**. Baris ke-7 (**Gina**) memiliki nilai **?** yang akan dicari menggunakan WKNN. Fitur yang digunakan untuk menghitung jarak adalah **IPK** dan **Penghasilan_OT** yang sudah dinormalisasi Min-Max.

**Tabel Data Asli (Kiri) & Data Normalisasi (Kanan)**

| No | Nama  | IPK  | Penghasilan_OT | Nilai_Tugas |   | No | Nama  | IPK'   | Penghasilan' | Nilai_Tugas |
|----|-------|------|----------------|-------------|---|----|-------|--------|--------------|-------------|
| 1  | Andi  | 3.50 | 5000           | 80          |   | 1  | Andi  | 0.7586 | 0.5385       | 80          |
| 2  | Budi  | 2.75 | 2000           | 65          |   | 2  | Budi  | 0.2414 | 0.0769       | 65          |
| 3  | Citra | 3.85 | 8000           | 92          |   | 3  | Citra | 1.0000 | 1.0000       | 92          |
| 4  | Deni  | 2.40 | 1500           | 55          |   | 4  | Deni  | 0.0000 | 0.0000       | 55          |
| 5  | Eva   | 3.10 | 3500           | 75          |   | 5  | Eva   | 0.4828 | 0.3077       | 75          |
| 6  | Fajar | 3.60 | 6000           | 85          |   | 6  | Fajar | 0.8276 | 0.6923       | 85          |
| **7**  | **Gina**  | **2.90** | **2500** | **?**   |   | **7**  | **Gina**  | **0.3448** | **0.1538** | **?** |
| 8  | Hadi  | 3.20 | 4000           | 78          |   | 8  | Hadi  | 0.5517 | 0.3846       | 78          |
| 9  | Indah | 3.75 | 7500           | 88          |   | 9  | Indah | 0.9310 | 0.9231       | 88          |
| 10 | Joko  | 2.55 | 1800           | 60          |   | 10 | Joko  | 0.1034 | 0.0462       | 60          |

---

#### 2. Mencari Nilai Tanda Tanya (?) dengan WKNN

Untuk memprediksi **Nilai_Tugas Gina (?)** dengan data ternormalisasi `(IPK' = 0.3448, Penghasilan' = 0.1538)`, kita hitung jarak **Euclidean** dari Gina ke semua baris lain yang nilainya sudah diketahui (baris 1–6 dan 8–10). Algoritma WKNN memberikan bobot (*weight*) berdasarkan kebalikan dari jarak ($w = 1/d$) — semakin dekat jaraknya, semakin besar bobotnya.

**Rumus jarak Euclidean:**

$$d = \sqrt{(IPK'_{target} - IPK'_i)^2 + (Penghasilan'_{target} - Penghasilan'_i)^2}$$

**Rumus bobot WKNN:**

$$w_i = \frac{1}{d_i}$$

**Rumus nilai imputasi:**

$$\hat{Nilai\_Tugas}_{Gina} = \frac{\sum_{i=1}^{K} w_i \cdot Nilai\_Tugas_i}{\sum_{i=1}^{K} w_i}$$

**Perhitungan Jarak Target (Gina) ke Setiap Baris:**

- **Ke Andi** (0.7586, 0.5385): $d = \sqrt{(0.3448-0.7586)^2 + (0.1538-0.5385)^2} = \sqrt{0.1712+0.1480} \approx 0.5650$ | Nilai_Tugas = 80
- **Ke Budi** (0.2414, 0.0769): $d = \sqrt{(0.3448-0.2414)^2 + (0.1538-0.0769)^2} = \sqrt{0.0107+0.0059} \approx 0.1288$ | Nilai_Tugas = 65
- **Ke Citra** (1.0000, 1.0000): $d = \sqrt{(0.3448-1.0)^2 + (0.1538-1.0)^2} \approx 1.0703$ | Nilai_Tugas = 92
- **Ke Deni** (0.0000, 0.0000): $d = \sqrt{(0.3448)^2 + (0.1538)^2} \approx 0.3777$ | Nilai_Tugas = 55
- **Ke Eva** (0.4828, 0.3077): $d = \sqrt{(0.3448-0.4828)^2 + (0.1538-0.3077)^2} \approx 0.2067$ | Nilai_Tugas = 75
- **Ke Fajar** (0.8276, 0.6923): $d \approx 0.7480$ | Nilai_Tugas = 85
- **Ke Hadi** (0.5517, 0.3846): $d \approx 0.2802$ | Nilai_Tugas = 78
- **Ke Indah** (0.9310, 0.9231): $d \approx 0.9382$ | Nilai_Tugas = 88
- **Ke Joko** (0.1034, 0.0462): $d \approx 0.2601$ | Nilai_Tugas = 60

**Urutkan — Ambil K=5 Tetangga Terdekat + Hitung Bobot:**

| Rank | Nama  | Jarak (d) | Nilai_Tugas | Bobot w = 1/d | w × Nilai_Tugas |
|------|-------|-----------|-------------|---------------|-----------------|
| 1    | Budi  | 0.1288    | 65          | 7.7639        | 504.65          |
| 2    | Eva   | 0.2067    | 75          | 4.8380        | 362.85          |
| 3    | Joko  | 0.2601    | 60          | 3.8447        | 230.68          |
| 4    | Hadi  | 0.2802    | 78          | 3.5688        | 278.37          |
| 5    | Deni  | 0.3777    | 55          | 2.6476        | 145.62          |
| **Σ Total** | | | | **22.6630** | **1522.17** |

**Hasil akhir:**

$$\hat{Nilai\_Tugas}_{Gina} = \frac{1522.17}{22.6630} \approx \mathbf{67.16}$$

**Kesimpulan:** Nilai Tugas Gina yang sebelumnya **?** diisi dengan **67.16** (dibulatkan menjadi 67). Budi yang paling dekat (d = 0.1288) mendapat bobot terbesar (w = 7.76) dan paling mempengaruhi hasil, sedangkan Deni yang paling jauh (d = 0.3777) hanya mendapat bobot 2.65.

---

#### Kode untuk Menghitung Missing Values

```python
import math

# 1. Data latih (ternormalisasi Min-Max) — Baris 1-6 dan 8-10
train_data = [
    {"nama": "Andi",  "ipk": 0.7586, "po": 0.5385, "nilai": 80},
    {"nama": "Budi",  "ipk": 0.2414, "po": 0.0769, "nilai": 65},
    {"nama": "Citra", "ipk": 1.0000, "po": 1.0000, "nilai": 92},
    {"nama": "Deni",  "ipk": 0.0000, "po": 0.0000, "nilai": 55},
    {"nama": "Eva",   "ipk": 0.4828, "po": 0.3077, "nilai": 75},
    {"nama": "Fajar", "ipk": 0.8276, "po": 0.6923, "nilai": 85},
    {"nama": "Hadi",  "ipk": 0.5517, "po": 0.3846, "nilai": 78},
    {"nama": "Indah", "ipk": 0.9310, "po": 0.9231, "nilai": 88},
    {"nama": "Joko",  "ipk": 0.1034, "po": 0.0462, "nilai": 60},
]

# 2. Data target: Gina (yang dicari)
target_ipk = 0.3448
target_po  = 0.1538

print("=== PERHITUNGAN JARAK (EUCLIDEAN DISTANCE) ===")
hasil_jarak = []
for d in train_data:
    jarak = math.sqrt((d["ipk"] - target_ipk)**2 + (d["po"] - target_po)**2)
    hasil_jarak.append({"nama": d["nama"], "jarak": jarak, "nilai": d["nilai"]})

hasil_jarak.sort(key=lambda x: x["jarak"])
for h in hasil_jarak:
    print(f"Ke {h['nama']:6} -> Jarak = {h['jarak']:.4f} | Nilai_Tugas = {h['nilai']}")

print("\n=== PERHITUNGAN BOBOT WKNN (K=5) ===")
K      = 5
top5   = hasil_jarak[:K]
sum_w  = 0.0
sum_wv = 0.0
for t in top5:
    w = 1 / t["jarak"]
    sum_w  += w
    sum_wv += w * t["nilai"]
    print(f"{t['nama']:6} (nilai={t['nilai']}) | d={t['jarak']:.4f} | w={w:.4f} | w×v={w*t['nilai']:.2f}")

print(f"\n=== HASIL AKHIR ===")
print(f"Nilai_Tugas Gina = {sum_wv:.2f} / {sum_w:.4f} = {sum_wv/sum_w:.2f}")
```

**Output:**

```
=== PERHITUNGAN JARAK (EUCLIDEAN DISTANCE) ===
Ke Budi   -> Jarak = 0.1288 | Nilai_Tugas = 65
Ke Eva    -> Jarak = 0.2067 | Nilai_Tugas = 75
Ke Joko   -> Jarak = 0.2601 | Nilai_Tugas = 60
Ke Hadi   -> Jarak = 0.2802 | Nilai_Tugas = 78
Ke Deni   -> Jarak = 0.3777 | Nilai_Tugas = 55
Ke Andi   -> Jarak = 0.5650 | Nilai_Tugas = 80
Ke Fajar  -> Jarak = 0.7480 | Nilai_Tugas = 85
Ke Indah  -> Jarak = 0.9382 | Nilai_Tugas = 88
Ke Citra  -> Jarak = 1.0703 | Nilai_Tugas = 92

=== PERHITUNGAN BOBOT WKNN (K=5) ===
Budi   (nilai=65) | d=0.1288 | w=7.7639 | w×v=504.65
Eva    (nilai=75) | d=0.2067 | w=4.8380 | w×v=362.85
Joko   (nilai=60) | d=0.2601 | w=3.8447 | w×v=230.68
Hadi   (nilai=78) | d=0.2802 | w=3.5688 | w×v=278.37
Deni   (nilai=55) | d=0.3777 | w=2.6476 | w×v=145.62

=== HASIL AKHIR ===
Nilai_Tugas Gina = 1522.17 / 22.6630 = 67.16
```