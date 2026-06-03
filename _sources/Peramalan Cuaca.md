# Peramalan Konsentrasi Nitrogen Dioksida (NO₂) di Sekitar Stadion Santiago Bernabéu(Madrid,Spanyol) Menggunakan K-Nearest Neighbors Regression
## Pendahuluan
Nitrogen Dioksida (NO₂) merupakan salah satu polutan udara yang berasal dari aktivitas transportasi, industri, dan pembakaran bahan bakar fosil. Konsentrasi NO₂ yang tinggi dapat berdampak negatif terhadap kesehatan manusia dan kualitas lingkungan.
Pada penelitian ini dilakukan analisis dan peramalan konsentrasi NO₂ menggunakan data satelit Sentinel-5P yang diperoleh melalui platform OpenEO. Wilayah yang menjadi fokus penelitian adalah area di sekitar Stadion Santiago Bernabéu, Madrid, Spanyol.

Stadion Santiago Bernabéu merupakan salah satu kawasan dengan aktivitas lalu lintas yang tinggi di pusat Kota Madrid sehingga menarik untuk dianalisis terkait tingkat polusi udara.

## 1. Pengumpulan Data

Pertama kita akan mengumpulkan data Time Series Harian kadar NO2 di daerah Bangkalan. Pengumpulan data dari sumber website https://dataspace.copernicus.eu/ , buat akun terlebih dahulu di website copernicus tersebut.

Dokumentasi cara pengambilan data di https://documentation.dataspace.copernicus.eu/notebook-samples/openeo/NO2Covid.html .

Untuk menuliskan code Python untuk mengambil data, silahkan buka Google Colaboratory

Disini kita akan mengambil data kadar NO2 di daerah Bangkalan dari tanggal … sampai … .

Kita install terlebih dahulu openoneo:

```python
pip install openeo
```

Lalu tuliskan code dibawah:

```python
import openeo
```

```python
connection = openeo.connect("openeo.dataspace.copernicus.eu").authenticate_oidc()
```
pada saat menjalankan baris code diatas (connection), nanti akan diminta authentikasi seperti output berikut:

Terminal/Output
Visit (link authentikasi) 📋 to authenticate.
✅ Authorized successfully
Authenticated using device code flow.

Kalian tinggal klik link authentikasi lalu login menggunakan akun “copernicus” kalian.

```python
aoi = {
    "type": "Polygon",
    "coordinates": [[
        [-3.6931554036528667, 40.4558109199653],
        [-3.6827714192710914, 40.4558109199653],
        [-3.6827714192710914, 40.44977565083849],
        [-3.6931554036528667, 40.44977565083849],
        [-3.6931554036528667, 40.4558109199653]
    ]]
}

s5post = connection.load_collection(
    "SENTINEL_5P_L2",
    temporal_extent=["2026-06-01", "2026-06-03"],
    spatial_extent={
        "west": -3.6931554036528667,
        "south": 40.44977565083849,
        "east": -3.6827714192710914,
        "north": 40.4558109199653
    },
    bands=["NO2"],
)

# Agregasi harian
s5p_no2_daily = s5post.aggregate_temporal_period(
    reducer="mean",
    period="day"
)

# Mean NO2 pada AOI
s5p_no2_aoi = s5p_no2_daily.aggregate_spatial(
    reducer="mean",
    geometries=aoi
)
```
Code diatas memerlukan titik koordinasi area yang akan diambil data 
-nya, untuk mengambil titik koordinasi kaian kunjungi webiste https://geojson.io/#map=14.8/-7.04732/112.69463 . Didalam website tersebut kalian akan memilih daerah dengan cara memberi shape kotak didaerah yang ingin kalian ambil datanya.

![screenshot](gambartugasramal/wilayah.png)

Di panel sebelah kanan terdapat data JSON yang berupa koordinat daerah yang kalian pilih, kalian salin terus sesuaikan dengan code diatas di bagian variabel “aoi” dan spatial_extent.

Lalu kalian tambahkan baris code dibawah untuk memulai pengambilan data:

```python
job = s5post.execute_batch(title="NO2 in Stadion Santiago Bernabeu", outputfile="NO2SantiagoBernabeu.nc")
```
Tunggu proses pengambilan data, output proses seperti berikut:

```python
0:00:00 Job 'j-2606030407474727839de38a7aa7342c': send 'start'
0:00:10 Job 'j-2606030407474727839de38a7aa7342c': queued (progress 0%)
0:00:16 Job 'j-2606030407474727839de38a7aa7342c': queued (progress 0%)
0:00:22 Job 'j-2606030407474727839de38a7aa7342c': queued (progress 0%)
0:00:30 Job 'j-2606030407474727839de38a7aa7342c': queued (progress 0%)
0:00:41 Job 'j-2606030407474727839de38a7aa7342c': queued (progress 0%)
0:00:53 Job 'j-2606030407474727839de38a7aa7342c': queued (progress 0%)
0:01:09 Job 'j-2606030407474727839de38a7aa7342c': queued (progress 0%)
0:01:28 Job 'j-2606030407474727839de38a7aa7342c': queued (progress 0%)
0:01:52 Job 'j-2606030407474727839de38a7aa7342c': finished (progress 100%)
```
Ketika proses pengambilan data, aktivitas kalian akan terekam di halaman https://editor.openeo.org/?server=https%3A%2F%2Fopeneo.dataspace.copernicus.eu%2Fopeneo%2F1.2 . Disitu terdapat nama dataset dan status pengambilan data.

## 2. Preproccessing Data

Setelah kita mengambil data, data bisa diunduh di halaman https://editor.openeo.org/?server=https%3A%2F%2Fopeneo.dataspace.copernicus.eu%2Fopeneo%2F1.2 . File akan berbentuk .nc. Kita hanya perlu kolom date dan NO2 menggunakan code dibawah:

```python
!pip install netCDF4
import netCDF4
import netCDF4

file_path = "openEO.nc"
ds = netCDF4.Dataset(file_path)

# Lihat variabel
print("📦 Variabel dalam file:")
print(ds.variables.keys())

# Ambil data
no2 = ds.variables["NO2"][:]
time = ds.variables["t"][:]

# Konversi waktu
try:
    dates = netCDF4.num2date(
        time,
        ds.variables["t"].units
    )
except:
    dates = time

# Cek dimensi data
print("Shape NO2:", no2.shape)

# Contoh nilai pertama
print("Nilai pertama:", no2[0, 0, 0])

# Tampilkan beberapa tanggal pertama
for i in range(min(5, len(dates))):
    print(dates[i])
    
```

output:
```python
📦 Variabel dalam file:
dict_keys(['t', 'x', 'y', 'crs', 'NO2'])
Shape NO2: (727, 1, 1)
Nilai pertama: 0.00014712424
2023-10-01 00:00:00
2023-10-02 00:00:00
2023-10-03 00:00:00
2023-10-04 00:00:00
2023-10-05 00:00:00
```

Untuk melihat 10 data pertama adalah:

```python
print("Contoh data pertama:")
for i in range(0, 10):
    print(no2[i])

```
Dalam sehari, terdapat banyak data NO2, jadi kita rata-ratakan agar satu cell data hanya terdapat satu value. Namun terdapat masalah pada data NO2 seperti missing value. Contoh pada output dibawah:
output:
```python
Contoh data pertama:
[[0.0001471242430852726]]
[[0.000155751607962884]]
[[0.00017890642629936337]]
[[0.00012874705134890974]]
[[0.0001914915192173794]]
[[7.86088130553253e-05]]
[[5.038464951212518e-05]]
[[0.00019671146583277732]]
[[0.0003217300109099597]]
[[0.00022306358732748777]]
```
### a. Mengatasi Missing Value menggunakan metode Interpolasi Linear

Sekarang kita akan mengatasi permasalahan missing value pada data NO2.
```python
import numpy as np
import pandas as pd

# Interpolasi Linear
no2_filled = np.zeros_like(no2)
# Untuk jaga-jaga jika terdapat '--' tidak berubah menjadi 0
no2_filled = no2_filled.filled(0)

# loop tiap grid (y,x)
for i in range(no2.shape[1]):     # 9 baris
    for j in range(no2.shape[2]): # 8 kolom
        series = pd.Series(no2[:, i, j])
        no2_filled[:, i, j] = series.interpolate(method='linear', limit_direction='both').to_numpy()
```
Dengan code diatas, missing value yang terdapat pada data NO2 akan diisi secara otomatis menggunakan metode Interpolasi Linear.

b. Rata-rata kan Data dan ubah Datetime

Setelah mengatasi missing value, kita akan me-rata-rata-kan data NO2 agar satu record hanya berupa single value. Sekalian kita mengambil date nya dan menaruh di array. Kita akan mengubah datetime dari awalnya (2023-10-04 00:00:00) menjadi (2023-10-04) karena kita mengambil data time series harian jadi kita tidak memerlukan data jam, menit dan detik.

```python
new_dates = []
new_no2 = []
for i in range(len(dates)):
    # ubah format datetime
    new_date = dates[i].strftime('%Y-%m-%d')
    new_dates.append(new_date)
    new_no2.append(np.mean(no2_filled[i]))
```
### c. Simpan data dalam bentuk CSV

Setelah itu kita akan membentuk data menjadi DataFrame Pandas untuk disimpan menjadi CSV.

```python
df = pd.DataFrame({
    "date": dates,
    "NO2": new_no2
})

# Simpan ke CSV
df.to_csv("NO2_Bernabeu.csv", index=False)
```

Untuk mengatasi missing value dan menyimpan data ke CSV sudah berhasil.

### d. Pengecekan Missing Value data harian pada CSV
Sekarang setelah data berbentuk CSV, kita cek apakah data Time Series harian lengkap. Cara men-cek apakah data Time Series Harian lengkap gunakan code dibawah:
```python
import pandas as pd
import numpy as np

df = pd.read_csv("NO2_Bernabeu.csv")

# Pastikan kolom 'date' bertipe datetime
df['date'] = pd.to_datetime(df['date'])

# Buat rentang tanggal lengkap
start_date = "2023-10-01"
end_date = "2025-09-30"
full_range = pd.date_range(start=start_date, end=end_date, freq='D')

# Cek tanggal yang hilang
missing_dates = full_range.difference(df['date'])

print(f"Jumlah hari missing: {len(missing_dates)}")
print("Daftar tanggal missing:")
print(missing_dates)
```
output:
```python
Jumlah hari missing: 4
Daftar tanggal missing:
DatetimeIndex(['2023-10-06', '2023-10-22', '2024-07-30', '2025-03-26'], dtype='datetime64[ns]', freq=None)
```
Dalam kasus saya ini, terdapat 4 hari missing value. Kita akan mengatasi lagi missing value menggunakan metode Interpolasi Linear. Cara memperbaikinya gunakan code dibawah:
```python
import pandas as pd

# Pastikan datetime dan sorting
df['date'] = pd.to_datetime(df['date'])
df = df.sort_values('date')

# Buat rentang tanggal lengkap
full_range = pd.date_range(start="2023-10-01", end="2025-09-30", freq='D')

# Reindex agar tanggal yang hilang muncul sebagai NaN
df = df.set_index('date').reindex(full_range)
df.index.name = 'date'

# Interpolasi linear berdasarkan indeks waktu
df['NO2'] = df['NO2'].interpolate(method='time')

# (Opsional) jika masih ada NaN di bagian awal/akhir bisa gunakan forward/backward fill
df['NO2'] = df['NO2'].fillna(method='bfill').fillna(method='ffill')

# Simpan kembali ke CSV
df.to_csv("no2_timeseries_interpolated.csv")
```
Setelah saya cek missing value harian, sudah tidak ada lagi missing value.
### e. Deteksi Outlier IQR

Setelah kita mengisi missing value menggunakan metode Interpolasi Linear, selanjutnya kita akan mendeteksi Outlier menggunakan metode IQR.

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

df = pd.read_csv("no2_timeseries_interpolated.csv")

df['date'] = pd.to_datetime(df['date'])

# Hitung IQR
Q1 = df['NO2'].quantile(0.25)
Q3 = df['NO2'].quantile(0.75)
IQR = Q3 - Q1

lower_bound = Q1 - 1.5 * IQR
upper_bound = Q3 + 1.5 * IQR

# Filter outlier
outliers_iqr = df[(df['NO2'] < lower_bound) | (df['NO2'] > upper_bound)]

print("Jumlah Outlier (IQR):", len(outliers_iqr))
print(outliers_iqr[['date', 'NO2']].head())
```
output:
```python
Jumlah Outlier (IQR): 56
         date       NO2
9  2023-10-10  0.000322
46 2023-11-16  0.000309
47 2023-11-17  0.000451
50 2023-11-20  0.000477
54 2023-11-24  0.000287
```

Untuk men-visualisasi outlier:

```python
# === Visualisasi ===
plt.figure(figsize=(15,5))
plt.plot(df['date'], df['NO2'], label="NO2", linewidth=1)

# Titik Outlier
plt.scatter(outliers_iqr['date'], outliers_iqr['NO2'], 
            color='red', marker='o', label="Outliers")

# Garis batas atas & bawah
plt.axhline(upper_bound, color='orange', linestyle='dashed', label="Upper Bound (IQR)")
plt.axhline(lower_bound, color='blue', linestyle='dashed', label="Lower Bound (IQR)")

plt.title("Deteksi Outlier Data NO2 (Metode IQR)")
plt.xlabel("Tanggal")
plt.ylabel("Kadar NO2")
plt.legend()
plt.tight_layout()
plt.xticks(
    ticks=[df['date'].iloc[0], df['date'].iloc[-1]],
    labels=[df['date'].iloc[0].strftime('%Y-%m-%d'),
            df['date'].iloc[-1].strftime('%Y-%m-%d')]
)
plt.show()
```
![screenshot](gambartugasramal/deteksioutlier.png)

Setelah itu, kita akan menghapus data outlier. Karena data ini merupakan data Time Series, maka data outlier yang dihapus akan diisi kembali menggunakan Interpolasi Linear.
```python
# Tandai outlier menjadi NaN
df['NO2_cleaned'] = df['NO2'].mask((df['NO2'] < lower_bound) | (df['NO2'] > upper_bound))

print("Jumlah nilai yang dinyatakan sebagai outlier:", df['NO2_cleaned'].isna().sum())

# Interpolasi linear untuk mengisi kembali nilai outlier
df['NO2_filled'] = df['NO2_cleaned'].interpolate(method='linear')

# Jika masih tersisa NaN di ujung data, isi dengan forward/backward fill
df['NO2_filled'] = df['NO2_filled'].bfill().ffill()
# df['NO2_filled'] = df['NO2_filled'].fillna(method='bfill').fillna(method='ffill')

print("Jumlah missing setelah interpolasi:", df['NO2_filled'].isna().sum())
```
output:
```python
Jumlah nilai yang dinyatakan sebagai outlier: 56
Jumlah missing setelah interpolasi: 0
```
Visualisasi data setelah menghapus Outlier dan mengisi kembali menggunakan Interpolasi Linear:

```python
plt.figure(figsize=(15,5))
# Plot data hasil interpolasi
plt.plot(df['date'], df['NO2_filled'], label="NO2 (Interpolated)", linewidth=1)
# Tampilkan hanya tanggal awal dan akhir di sumbu X
plt.xticks(
    ticks=[df['date'].iloc[0], df['date'].iloc[-1]],
    labels=[df['date'].iloc[0].strftime('%Y-%m-%d'),
            df['date'].iloc[-1].strftime('%Y-%m-%d')]
)
plt.title("Plot Data NO2 Setelah Outlier Removal & Interpolasi")
plt.xlabel("Tanggal")
plt.ylabel("Kadar NO2")
plt.legend()
plt.tight_layout()
plt.show()
```
![screenshot](gambartugasramal/plotdata.png)


## 3. Modeling menggunakan KNN Regression
Dengan data Time Series kadar NO2 harian di daerah Bangkalan, kita akan memprediksi kadar NO2 satu hari yang akan datang. Sekarang kita akan ubah data, mencoba mencari korelasi antara 1 hari dengan 4 hari sebelumnya. Kita juga akan membandingkan apakah semakin banyak hari sebelumnya, model akan lebih bagus?

### a. Uji Korelasi Data
Sebelum masuk ke modeling, data kita merupakan data unsupervised yang berarti tidak ada label. Kita ubah data menjadi supervised lalu uji korelasi terhadap label (t). Fitur-fitur nya merupakan 30 hari sebelum (t-30, t-29, … t-1) dan label (t).
```python
import pandas as pd

def create_supervised(data, n_lag=4):
    df_supervised = pd.DataFrame()
    
    # Membuat fitur t-4 sampai t-1
    for i in range(n_lag, 0, -1):
        df_supervised[f'NO2(t-{i})'] = data.shift(i)
    
    # Label hari H
    df_supervised['NO2(t)'] = data
    
    # Hapus baris yang masih mengandung NaN akibat shift
    df_supervised.dropna(inplace=True)
    
    return df_supervised

# contoh penggunaan
supervised_df30 = create_supervised(df['NO2_cleaned'], n_lag=30)

# Ambil semua lag dan kolom target
lag_cols = supervised_df30.drop(columns="NO2(t)").columns
correlations = supervised_df30[lag_cols].corrwith(supervised_df30['NO2(t)'])

# Tampilkan nilai korelasi
print(correlations)
```
output:
```python
NO2(t-30)   -0.112106
NO2(t-29)   -0.057493
NO2(t-28)    0.039267
NO2(t-27)    0.046718
NO2(t-26)   -0.034517
NO2(t-25)   -0.088170
NO2(t-24)   -0.159662
NO2(t-23)   -0.223371
NO2(t-22)   -0.113505
NO2(t-21)   -0.022261
NO2(t-20)   -0.038643
NO2(t-19)   -0.046750
NO2(t-18)    0.005223
NO2(t-17)    0.040197
NO2(t-16)    0.020270
NO2(t-15)    0.039495
NO2(t-14)    0.048992
NO2(t-13)   -0.019489
NO2(t-12)   -0.026928
NO2(t-11)   -0.002181
NO2(t-10)    0.026279
NO2(t-9)     0.030179
NO2(t-8)     0.030325
NO2(t-7)     0.068956
NO2(t-6)     0.089898
NO2(t-5)     0.090975
NO2(t-4)     0.058603
NO2(t-3)     0.058407
NO2(t-2)     0.140286
NO2(t-1)     0.465785
dtype: float64
```
Skala nilai uji korelasi itu dari -1 sampai 1, namun kita ambil nilai uji korelasi yang terbaik yaitu lebih dari 0.5 yaitu fitur t-1 sampai t-4.

### b. Normalisasi Data
karena kita menggunakan model KNN Regression, maka perlu normalisasi data menggunakan min-max Scaler.
```python
from sklearn.preprocessing import MinMaxScaler
import pandas as pd

scaler = MinMaxScaler()

df['NO2_scaled'] = scaler.fit_transform(df[['NO2']])
print(df[['NO2', 'NO2_scaled']].head())
print("\nInformasi Dataframe :")
df[['date','NO2','NO2_scaled']].info()
```
Maka data akan di-normalisasi 0-1.

output:
        NO2  NO2_scaled
0  0.000147    0.265960
1  0.000156    0.283231
2  0.000179    0.329585
3  0.000129    0.229171
4  0.000191    0.354779

Informasi Dataframe :
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 731 entries, 0 to 730
Data columns (total 3 columns):
 #   Column      Non-Null Count  Dtype         
---  ------      --------------  -----         
 0   date        731 non-null    datetime64[ns]
 1   NO2         731 non-null    float64       
 2   NO2_scaled  731 non-null    float64       
dtypes: datetime64[ns](1), float64(2)
memory usage: 17.3 KB
```

### c. Mengubah Data
Sekarang saya ingin mengubah data dari sebelumnya hanya 2 fitru menjadi 4 hari sebelum yang terdapat 5 fitur (t-4, t-3, t-2, t-1, dan t sebagai label) karena dari uji korelasi, keempat fitur tersebut (t-1 sampai t-4) merupakan nilai uji korelasi terbaik (lebih dari 0.5). Saya juga membuat data 10 hari sebelum untuk membandingkan apakah semakin banyak hari sebelum, semakin baik pula modelnya?
```python
supervised_df = create_supervised(df['NO2_scaled'], n_lag=4)

print(supervised_df)
print(supervised_df.shape)
```
output:
```python
     NO2(t-4)  NO2(t-3)  NO2(t-2)  NO2(t-1)    NO2(t)
4    0.265960  0.283231  0.329585  0.229171  0.354779
5    0.283231  0.329585  0.229171  0.354779  0.241789
6    0.329585  0.229171  0.354779  0.241789  0.128799
7    0.229171  0.354779  0.241789  0.128799  0.072297
8    0.354779  0.241789  0.128799  0.072297  0.365228
..        ...       ...       ...       ...       ...
726  0.171809  0.123577  0.221208  0.255438  0.216082
727  0.123577  0.221208  0.255438  0.216082  0.169305
728  0.221208  0.255438  0.216082  0.169305  0.122527
729  0.255438  0.216082  0.169305  0.122527  0.075750
730  0.216082  0.169305  0.122527  0.075750  0.075750

[727 rows x 5 columns]
(727, 5)
```
Untuk membuat data 10 hari sebelum tinggal tambah code dibawah (ubah parameter n_lag).

```python
supervised_df10 = create_supervised(df['NO2_scaled'], n_lag=10)

print(supervised_df10)
print(supervised_df10.shape)
```
output:
```python
     NO2(t-10)  NO2(t-9)  NO2(t-8)  NO2(t-7)  NO2(t-6)  NO2(t-5)  NO2(t-4)  \
10    0.265960  0.283231  0.329585  0.229171  0.354779  0.241789  0.128799   
11    0.283231  0.329585  0.229171  0.354779  0.241789  0.128799  0.072297   
12    0.329585  0.229171  0.354779  0.241789  0.128799  0.072297  0.365228   
13    0.229171  0.354779  0.241789  0.128799  0.072297  0.365228  0.615503   
14    0.354779  0.241789  0.128799  0.072297  0.365228  0.615503  0.417983   
..         ...       ...       ...       ...       ...       ...       ...   
726   0.110410  0.185586  0.247104  0.163373  0.079641  0.030363  0.171809   
727   0.185586  0.247104  0.163373  0.079641  0.030363  0.171809  0.123577   
728   0.247104  0.163373  0.079641  0.030363  0.171809  0.123577  0.221208   
729   0.163373  0.079641  0.030363  0.171809  0.123577  0.221208  0.255438   
730   0.079641  0.030363  0.171809  0.123577  0.221208  0.255438  0.216082   

     NO2(t-3)  NO2(t-2)  NO2(t-1)    NO2(t)  
10   0.072297  0.365228  0.615503  0.417983  
11   0.365228  0.615503  0.417983  0.197059  
12   0.615503  0.417983  0.197059  0.163395  
13   0.417983  0.197059  0.163395  0.129731  
14   0.197059  0.163395  0.129731  0.121645  
..        ...       ...       ...       ...  
726  0.123577  0.221208  0.255438  0.216082  
727  0.221208  0.255438  0.216082  0.169305  
728  0.255438  0.216082  0.169305  0.122527  
729  0.216082  0.169305  0.122527  0.075750  
730  0.169305  0.122527  0.075750  0.075750  

[721 rows x 11 columns]
(721, 11)
```
### d. Modeling dan Evaluation

Sekarang dari 2 data yang sudah kita rubah, kita train menggunakan model KNN Regression.

```python
from sklearn.neighbors import KNeighborsRegressor
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error, r2_score
import numpy as np

def MAPE(y_true, y_pred):
    y_true, y_pred = np.array(y_true), np.array(y_pred)
    # Hindari pembagian dengan nol
    nonzero = y_true != 0
    return np.mean(np.abs((y_true[nonzero] - y_pred[nonzero]) / y_true[nonzero])) * 100

def train_knn(df_supervised, model_name=""):
    # Pisahkan fitur & label
    X = df_supervised.drop(columns=['NO2(t)']).values
    y = df_supervised['NO2(t)'].values

    # Split data 80/20
    X_train, X_test, y_train, y_test = train_test_split(
        X, y, test_size=0.2, shuffle=False
    )

    # Model KNN
    knn = KNeighborsRegressor(n_neighbors=5)
    knn.fit(X_train, y_train)

    # Prediksi
    y_pred = knn.predict(X_test)

    # Evaluasi
    mse = mean_squared_error(y_test, y_pred)
    rmse = np.sqrt(mse)
    r2 = r2_score(y_test, y_pred)
    mape = MAPE(y_test, y_pred)

    print(f"\n=== {model_name} ===")
    print(f"Train Size: {len(X_train)} — Test Size: {len(X_test)}")
    print(f"RMSE: {rmse:.6f}")
    print(f"R² Score: {r2:.4f}")
    print(f"MAPE: {mape:.4f}%")

    return knn, y_test, y_pred


# Train model untuk 4 hari sebelumnya
knn_4, y_test_4, y_pred_4 = train_knn(supervised_df, "KNN - 4 Hari Sebelumnya")

# Train model untuk 10 hari sebelumnya
knn_10, y_test_10, y_pred_10 = train_knn(supervised_df10, "KNN - 10 Hari Sebelumnya")
```
output:
```python

=== KNN - 4 Hari Sebelumnya ===
Train Size: 581 — Test Size: 146
RMSE: 0.073933
R² Score: -0.7839
MAPE: 95.5552%

=== KNN - 10 Hari Sebelumnya ===
Train Size: 576 — Test Size: 145
RMSE: 0.065092
R² Score: -0.3784
MAPE: 81.2036%
```
Berdasarkan hasil arkurasi diatas menjunjukkan bahwa lebih banyak hari sebelumnya maka model semakin bagus. Kita coba gunakan data 30 hari sebelumnya juga untuk melihat apakah semakin banyak hari sebelumnya, model semakin baik?

```python
knn_30, y_test_30, y_pred_30 = train_knn(supervised_df30, "KNN - 30 Hari Sebelumnya")
```
output:

```python
=== KNN - 30 Hari Sebelumnya ===
Train Size: 238 — Test Size: 60
RMSE: 0.000030
R² Score: -0.1158
MAPE: 43.9335%
``` 

### e. Plotting
Plotting untuk visualisasi grafik antara label dan prediksi dari kedua data diatas.
4 hari sebelum:

```python
import matplotlib.pyplot as plt
import numpy as np

plt.figure()
plt.plot(np.arange(len(y_test_4)), y_test_4, label="Actual")
plt.plot(np.arange(len(y_pred_4)), y_pred_4, label="Predicted")
plt.title("KNN Regression - 4 Hari Sebelumnya")
plt.xlabel("Sample Index")
plt.ylabel("NO2 Value")
plt.legend()
plt.show()
```
![screenshot](gambartugasramal/knn4hari.png)

10 hari sebelum:

```python
plt.figure()
plt.plot(np.arange(len(y_test_10)), y_test_10, label="Actual")
plt.plot(np.arange(len(y_pred_10)), y_pred_10, label="Predicted")
plt.title("KNN Regression - 10 Hari Sebelumnya")
plt.xlabel("Sample Index")
plt.ylabel("NO2 Value")
plt.legend()
plt.show()
```

![screenshot](gambartugasramal/knn10hari.png)

30 hari sebelum`:

```python
plt.figure()
plt.plot(np.arange(len(y_test_30)), y_test_30, label="Actual")
plt.plot(np.arange(len(y_pred_30)), y_pred_30, label="Predicted")
plt.title("KNN Regression - 30 Hari Sebelumnya")
plt.xlabel("Sample Index")
plt.ylabel("NO2 Value")
plt.legend()
plt.show()
```

![screenshot](gambartugasramal/knn30hari.png)

Kesimpulan
Berdasarkan hasil penelitian dapat disimpulkan bahwa:
Data NO₂ berhasil diperoleh dari Sentinel-5P melalui OpenEO.
Wilayah penelitian mencakup area sekitar Stadion Santiago Bernabéu di Madrid.
Missing value dan missing date berhasil ditangani menggunakan interpolasi.
Outlier berhasil dideteksi menggunakan metode IQR.
Data berhasil ditransformasikan menjadi supervised learning menggunakan teknik lag.
Algoritma KNN Regression mampu digunakan untuk memprediksi konsentrasi NO₂ berdasarkan data historis.
Performa model dipengaruhi oleh jumlah lag yang digunakan.
Model terbaik dipilih berdasarkan nilai RMSE dan MAPE terkecil serta nilai R² terbesar.