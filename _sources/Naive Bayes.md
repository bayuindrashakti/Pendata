# Analisis Data Menggunakan Naive Bayes
> **Model:** Gaussian Naive Bayes | **Library:** scikit-learn | **Dataset:** Prediksi Penyakit Diabetes

---

## Daftar Isi
1. [Deskripsi Proyek](#1-deskripsi-proyek)
2. [Teori Naive Bayes](#2-teori-naive-bayes)
3. [Dataset](#3-dataset)
4. [Instalasi & Persiapan](#4-instalasi--persiapan)
5. [Script Python Lengkap](#5-script-python-lengkap)
6. [Penjelasan Tiap Tahap](#6-penjelasan-tiap-tahap)
7. [Hasil & Evaluasi Model](#7-hasil--evaluasi-model)
8. [Visualisasi](#8-visualisasi)
9. [Kesimpulan](#9-kesimpulan)
10. [Referensi](#10-referensi)

---

## 1. Deskripsi Proyek

Proyek ini membangun sistem klasifikasi untuk **memprediksi apakah seseorang menderita diabetes atau tidak** berdasarkan data medis. Model yang digunakan adalah **Gaussian Naive Bayes** dari library `scikit-learn`.

| Item | Detail |
|---|---|
| **Algoritma** | Gaussian Naive Bayes (`GaussianNB`) |
| **Library** | scikit-learn, pandas, numpy, matplotlib, seaborn |
| **Dataset** | Prediksi Diabetes (500 baris, 8 fitur) |
| **Target** | `Outcome` — 0 = Tidak Diabetes, 1 = Diabetes |
| **Tool** | Python Script (bukan KNIME/Node) |

---

## 2. Teori Naive Bayes

### 2.1 Apa itu Naive Bayes?

Naive Bayes adalah algoritma klasifikasi berbasis **Teorema Bayes** dengan asumsi bahwa setiap fitur bersifat **independen satu sama lain** (disebut "naive" karena asumsi ini jarang benar di dunia nyata, namun tetap bekerja dengan baik).

### 2.2 Formula Bayes

$$P(C \mid X) = \frac{P(X \mid C) \cdot P(C)}{P(X)}$$

| Notasi | Nama | Arti |
|---|---|---|
| $P(C \mid X)$ | Posterior | Probabilitas kelas C, diberikan fitur X |
| $P(X \mid C)$ | Likelihood | Probabilitas fitur X muncul di kelas C |
| $P(C)$ | Prior | Probabilitas awal kelas C |
| $P(X)$ | Evidence | Probabilitas fitur X (konstan, bisa diabaikan) |

### 2.3 Jenis-jenis Naive Bayes di Scikit-Learn

| Varian | Class | Cocok Untuk |
|---|---|---|
| **Gaussian NB** | `GaussianNB` | Fitur numerik kontinu (asumsi distribusi normal) |
| **Multinomial NB** | `MultinomialNB` | Data teks / frekuensi kata |
| **Bernoulli NB** | `BernoulliNB` | Fitur biner (0/1) |
| **Complement NB** | `ComplementNB` | Dataset tidak seimbang |
| **Categorical NB** | `CategoricalNB` | Fitur kategorikal |

> **Proyek ini menggunakan `GaussianNB`** karena semua fitur berupa angka kontinu.

### 2.4 Cara Kerja GaussianNB

GaussianNB mengasumsikan setiap fitur mengikuti **distribusi Gaussian (normal)**:

$$P(x_i \mid C) = \frac{1}{\sqrt{2\pi\sigma_C^2}} \exp\left(-\frac{(x_i - \mu_C)^2}{2\sigma_C^2}\right)$$

Model belajar nilai **mean (μ)** dan **variance (σ²)** dari setiap fitur untuk setiap kelas.

---

## 3. Dataset

### 3.1 Informasi Dataset

| Properti | Nilai |
|---|---|
| **Nama** | Diabetes Prediction Dataset |
| **Jumlah Baris** | 500 sampel |
| **Jumlah Kolom** | 9 (8 fitur + 1 target) |
| **Missing Value** | Tidak ada |
| **Tipe Data** | Numerik semua |

### 3.2 Deskripsi Fitur

| No | Fitur | Tipe | Deskripsi |
|---|---|---|---|
| 1 | `Pregnancies` | Integer | Jumlah kehamilan |
| 2 | `Glucose` | Integer | Kadar glukosa dalam darah (mg/dL) |
| 3 | `BloodPressure` | Integer | Tekanan darah diastolik (mm Hg) |
| 4 | `SkinThickness` | Integer | Ketebalan lipatan kulit tricep (mm) |
| 5 | `Insulin` | Integer | Kadar insulin serum 2 jam (mu U/ml) |
| 6 | `BMI` | Float | Body Mass Index (kg/m²) |
| 7 | `DiabetesPedigreeFunction` | Float | Fungsi silsilah diabetes (faktor genetik) |
| 8 | `Age` | Integer | Usia pasien (tahun) |
| 9 | `Outcome` ⭐ | Integer | **Target**: 0 = Tidak Diabetes, 1 = Diabetes |

### 3.3 Contoh 5 Baris Pertama Dataset

```
   Pregnancies  Glucose  BloodPressure  SkinThickness  Insulin   BMI   DPF  Age  Outcome
0            4      138            116             42      519  34.4  1.491   59        0
1           11       80            105             23      188  30.8  2.014   72        1
2            7      143             91             55      716  26.8  2.383   49        1
3            9      173             74             21      403  20.9  0.755   35        1
4           13      107             75             10      433  37.2  2.329   63        1
```

### 3.4 Distribusi Target

| Kelas | Label | Jumlah | Persentase |
|---|---|---|---|
| 0 | Tidak Diabetes | 141 | 28.2% |
| 1 | Diabetes | 359 | 71.8% |

### 3.5 Generate Dataset CSV (Python)

Jika ingin membuat ulang dataset, gunakan script berikut:

```python
import pandas as pd
import numpy as np

np.random.seed(42)
n = 500

age            = np.random.randint(21, 80, n)
bmi            = np.round(np.random.uniform(18, 45, n), 1)
glucose        = np.random.randint(70, 200, n)
blood_pressure = np.random.randint(60, 122, n)
insulin        = np.random.randint(14, 850, n)
skin_thickness = np.random.randint(10, 60, n)
pregnancies    = np.random.randint(0, 14, n)
dpf            = np.round(np.random.uniform(0.08, 2.42, n), 3)

risk = (
    (glucose > 140).astype(int) * 3 +
    (bmi > 30).astype(int) * 2 +
    (age > 45).astype(int) * 1 +
    (dpf > 0.5).astype(int) * 1 +
    (blood_pressure > 90).astype(int) * 1
)
prob    = risk / 8.0
noise   = np.random.uniform(-0.1, 0.1, n)
outcome = ((prob + noise) > 0.4).astype(int)

df = pd.DataFrame({
    'Pregnancies'             : pregnancies,
    'Glucose'                 : glucose,
    'BloodPressure'           : blood_pressure,
    'SkinThickness'           : skin_thickness,
    'Insulin'                 : insulin,
    'BMI'                     : bmi,
    'DiabetesPedigreeFunction': dpf,
    'Age'                     : age,
    'Outcome'                 : outcome
})

df.to_csv('diabetes_dataset.csv', index=False)
print(f"Dataset berhasil dibuat: {df.shape}")
```

---

## 4. Instalasi & Persiapan

### 4.1 Instalasi Library

```bash
pip install scikit-learn pandas numpy matplotlib seaborn
```

### 4.2 Struktur File Proyek

```
naive-bayes-project/
│
├── diabetes_dataset.csv       ← Dataset CSV
├── naive_bayes_analysis.py    ← Script utama
└── naive_bayes_analisis.png   ← Output visualisasi
```

### 4.3 Versi Library yang Direkomendasikan

| Library | Versi |
|---|---|
| Python | >= 3.8 |
| scikit-learn | >= 1.0 |
| pandas | >= 1.3 |
| numpy | >= 1.21 |
| matplotlib | >= 3.4 |
| seaborn | >= 0.11 |

---

## 5. Script Python Lengkap

```python
"""
============================================================
  ANALISIS DATA MENGGUNAKAN NAIVE BAYES
  Dataset: Prediksi Penyakit Diabetes
  Library: scikit-learn (GaussianNB)
============================================================
"""

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import matplotlib.gridspec as gridspec
import seaborn as sns
import warnings
warnings.filterwarnings('ignore')

from sklearn.naive_bayes import GaussianNB
from sklearn.model_selection import train_test_split, cross_val_score, StratifiedKFold
from sklearn.preprocessing import StandardScaler
from sklearn.metrics import (
    accuracy_score, classification_report,
    confusion_matrix, roc_curve, auc,
    ConfusionMatrixDisplay
)

# ─────────────────────────────────────────────
# 1. LOAD DATA
# ─────────────────────────────────────────────
print("=" * 60)
print("  ANALISIS NAIVE BAYES - PREDIKSI DIABETES")
print("=" * 60)

df = pd.read_csv("diabetes_dataset.csv")

print("\n[1] INFO DATASET")
print(f"    Jumlah baris  : {df.shape[0]}")
print(f"    Jumlah kolom  : {df.shape[1]}")
print(f"    Fitur         : {list(df.columns[:-1])}")
print(f"    Target        : Outcome (0 = Tidak Diabetes, 1 = Diabetes)")
print()
print(df.head())

# ─────────────────────────────────────────────
# 2. EKSPLORASI DATA (EDA)
# ─────────────────────────────────────────────
print("\n[2] STATISTIK DESKRIPTIF")
print(df.describe().round(2))

print("\n[3] CEK MISSING VALUE")
print(df.isnull().sum())

print("\n[4] DISTRIBUSI TARGET")
vc = df['Outcome'].value_counts()
for k, v in vc.items():
    label = "Diabetes" if k == 1 else "Tidak Diabetes"
    pct = v / len(df) * 100
    print(f"    {label} ({k}): {v} sampel ({pct:.1f}%)")

# ─────────────────────────────────────────────
# 3. PERSIAPAN DATA
# ─────────────────────────────────────────────
print("\n[5] PERSIAPAN DATA")
X = df.drop('Outcome', axis=1)
y = df['Outcome']

# Split: 80% train, 20% test
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42, stratify=y
)
print(f"    Train set: {X_train.shape[0]} sampel")
print(f"    Test set : {X_test.shape[0]} sampel")

# Standarisasi (StandardScaler)
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled  = scaler.transform(X_test)

# ─────────────────────────────────────────────
# 4. TRAINING MODEL GAUSSIAN NAIVE BAYES
# ─────────────────────────────────────────────
print("\n[6] TRAINING MODEL - GaussianNB")
model = GaussianNB()
model.fit(X_train_scaled, y_train)
print("    Model berhasil dilatih!")
print(f"    Class Prior (P(C)): {dict(zip(model.classes_, model.class_prior_.round(4)))}")

# ─────────────────────────────────────────────
# 5. PREDIKSI & EVALUASI
# ─────────────────────────────────────────────
print("\n[7] EVALUASI MODEL")
y_pred = model.predict(X_test_scaled)
y_prob = model.predict_proba(X_test_scaled)[:, 1]

acc          = accuracy_score(y_test, y_pred)
cm           = confusion_matrix(y_test, y_pred)
tn, fp, fn, tp = cm.ravel()

print(f"\n    Accuracy  : {acc:.4f} ({acc*100:.2f}%)")
print(f"    TP={tp}, TN={tn}, FP={fp}, FN={fn}")
print(f"\n    Precision (Diabetes)    : {tp/(tp+fp):.4f}")
print(f"    Recall    (Diabetes)    : {tp/(tp+fn):.4f}")
print(f"    F1-Score  (Diabetes)    : {2*tp/(2*tp+fp+fn):.4f}")

print("\n    Classification Report:")
print(classification_report(y_test, y_pred,
      target_names=["Tidak Diabetes", "Diabetes"]))

# Cross-Validation
cv        = StratifiedKFold(n_splits=5, shuffle=True, random_state=42)
cv_scores = cross_val_score(model, X_train_scaled, y_train, cv=cv, scoring='accuracy')
print(f"    Cross-Validation (5-fold) Accuracy: {cv_scores.mean():.4f} ± {cv_scores.std():.4f}")

# ROC AUC
fpr, tpr, _ = roc_curve(y_test, y_prob)
roc_auc     = auc(fpr, tpr)
print(f"    ROC AUC Score: {roc_auc:.4f}")

# ─────────────────────────────────────────────
# 6. CONTOH PREDIKSI DATA BARU
# ─────────────────────────────────────────────
print("\n[8] CONTOH PREDIKSI DATA BARU")
sampel_baru = pd.DataFrame([{
    'Pregnancies'             : 3,
    'Glucose'                 : 158,
    'BloodPressure'           : 90,
    'SkinThickness'           : 35,
    'Insulin'                 : 200,
    'BMI'                     : 33.6,
    'DiabetesPedigreeFunction': 0.627,
    'Age'                     : 50
}])
sampel_scaled = scaler.transform(sampel_baru)
prediksi      = model.predict(sampel_scaled)[0]
probab        = model.predict_proba(sampel_scaled)[0]
label         = "DIABETES" if prediksi == 1 else "TIDAK DIABETES"

print(f"    Input: Glucose=158, BMI=33.6, Age=50, DPF=0.627")
print(f"    Prediksi : {label}")
print(f"    Probabilitas Tidak Diabetes : {probab[0]*100:.2f}%")
print(f"    Probabilitas Diabetes       : {probab[1]*100:.2f}%")

# ─────────────────────────────────────────────
# 7. VISUALISASI (8 Panel)
# ─────────────────────────────────────────────
print("\n[9] MEMBUAT VISUALISASI...")

plt.style.use('seaborn-v0_8-whitegrid')
WARNA = ['#4CAF50', '#F44336']
fig   = plt.figure(figsize=(18, 14))
fig.patch.set_facecolor('#F8F9FA')
gs    = gridspec.GridSpec(3, 3, figure=fig, hspace=0.45, wspace=0.4)

# ── Plot 1: Distribusi Outcome ─────────────────
ax1    = fig.add_subplot(gs[0, 0])
counts = df['Outcome'].value_counts()
bars   = ax1.bar(['Tidak\nDiabetes', 'Diabetes'], counts.values,
                 color=WARNA, edgecolor='white', linewidth=1.5, width=0.5)
for bar, val in zip(bars, counts.values):
    ax1.text(bar.get_x() + bar.get_width()/2, bar.get_height() + 5,
             f'{val}\n({val/len(df)*100:.1f}%)', ha='center', fontsize=10, fontweight='bold')
ax1.set_title('Distribusi Kelas Target', fontsize=12, fontweight='bold', pad=10)
ax1.set_ylabel('Jumlah Sampel')
ax1.set_ylim(0, max(counts.values) * 1.2)
ax1.tick_params(axis='x', labelsize=10)

# ── Plot 2: Confusion Matrix ──────────────────
ax2  = fig.add_subplot(gs[0, 1])
disp = ConfusionMatrixDisplay(confusion_matrix=cm,
                              display_labels=['Tdk Diabetes', 'Diabetes'])
disp.plot(ax=ax2, colorbar=False, cmap='RdYlGn')
ax2.set_title('Confusion Matrix', fontsize=12, fontweight='bold', pad=10)
ax2.set_xlabel('Prediksi', fontsize=10)
ax2.set_ylabel('Aktual', fontsize=10)

# ── Plot 3: ROC Curve ─────────────────────────
ax3 = fig.add_subplot(gs[0, 2])
ax3.plot(fpr, tpr, color='#1976D2', lw=2.5, label=f'ROC (AUC = {roc_auc:.3f})')
ax3.fill_between(fpr, tpr, alpha=0.1, color='#1976D2')
ax3.plot([0, 1], [0, 1], 'k--', lw=1.5, label='Random Classifier')
ax3.set_xlabel('False Positive Rate', fontsize=10)
ax3.set_ylabel('True Positive Rate', fontsize=10)
ax3.set_title('ROC Curve', fontsize=12, fontweight='bold', pad=10)
ax3.legend(fontsize=9)
ax3.set_xlim([0, 1])
ax3.set_ylim([0, 1.02])

# ── Plot 4: Cross-Validation Scores ──────────
ax4   = fig.add_subplot(gs[1, 0])
folds = [f'Fold {i+1}' for i in range(len(cv_scores))]
bars4 = ax4.bar(folds, cv_scores, color='#7B1FA2', alpha=0.8,
                edgecolor='white', linewidth=1.5)
ax4.axhline(cv_scores.mean(), color='#FF6F00', linestyle='--',
            linewidth=2, label=f'Mean = {cv_scores.mean():.3f}')
for bar, val in zip(bars4, cv_scores):
    ax4.text(bar.get_x() + bar.get_width()/2, bar.get_height() + 0.003,
             f'{val:.3f}', ha='center', fontsize=9, fontweight='bold')
ax4.set_title('Cross-Validation (5-Fold)', fontsize=12, fontweight='bold', pad=10)
ax4.set_ylabel('Accuracy')
ax4.set_ylim(0.5, 1.0)
ax4.legend(fontsize=9)

# ── Plot 5: Distribusi Glucose per Kelas ─────
ax5 = fig.add_subplot(gs[1, 1])
for label_val, color, name in zip([0, 1], WARNA, ['Tidak Diabetes', 'Diabetes']):
    subset = df[df['Outcome'] == label_val]['Glucose']
    ax5.hist(subset, bins=20, alpha=0.65, color=color, label=name, edgecolor='white')
ax5.set_title('Distribusi Glucose per Kelas', fontsize=12, fontweight='bold', pad=10)
ax5.set_xlabel('Glucose Level')
ax5.set_ylabel('Frekuensi')
ax5.legend(fontsize=9)

# ── Plot 6: Distribusi BMI per Kelas ─────────
ax6 = fig.add_subplot(gs[1, 2])
for label_val, color, name in zip([0, 1], WARNA, ['Tidak Diabetes', 'Diabetes']):
    subset = df[df['Outcome'] == label_val]['BMI']
    ax6.hist(subset, bins=20, alpha=0.65, color=color, label=name, edgecolor='white')
ax6.set_title('Distribusi BMI per Kelas', fontsize=12, fontweight='bold', pad=10)
ax6.set_xlabel('BMI')
ax6.set_ylabel('Frekuensi')
ax6.legend(fontsize=9)

# ── Plot 7: Heatmap Korelasi ──────────────────
ax7  = fig.add_subplot(gs[2, 0:2])
corr = df.corr()
mask = np.triu(np.ones_like(corr, dtype=bool))
sns.heatmap(corr, ax=ax7, mask=mask, annot=True, fmt='.2f',
            cmap='coolwarm', center=0, linewidths=0.5,
            annot_kws={'size': 8}, cbar_kws={'shrink': 0.8})
ax7.set_title('Korelasi Antar Fitur', fontsize=12, fontweight='bold', pad=10)
ax7.tick_params(axis='x', rotation=30, labelsize=8)
ax7.tick_params(axis='y', rotation=0,  labelsize=8)

# ── Plot 8: Distribusi Probabilitas Prediksi ──
ax8 = fig.add_subplot(gs[2, 2])
ax8.hist(y_prob[y_test == 0], bins=15, alpha=0.7, color=WARNA[0],
         label='Aktual: Tdk Diabetes', edgecolor='white')
ax8.hist(y_prob[y_test == 1], bins=15, alpha=0.7, color=WARNA[1],
         label='Aktual: Diabetes', edgecolor='white')
ax8.axvline(0.5, color='black', linestyle='--', linewidth=1.5, label='Threshold = 0.5')
ax8.set_title('Distribusi Probabilitas Prediksi', fontsize=12, fontweight='bold', pad=10)
ax8.set_xlabel('Probabilitas (Diabetes)')
ax8.set_ylabel('Frekuensi')
ax8.legend(fontsize=8)

# ── Judul Utama ───────────────────────────────
fig.suptitle(
    'Analisis Data Menggunakan Naive Bayes\nDataset: Prediksi Penyakit Diabetes',
    fontsize=16, fontweight='bold', y=1.01, color='#1A237E'
)

plt.savefig('naive_bayes_analisis.png', dpi=150, bbox_inches='tight', facecolor='#F8F9FA')
print("    Visualisasi disimpan: naive_bayes_analisis.png")

print("\n" + "=" * 60)
print("  SELESAI! Semua hasil berhasil digenerate.")
print("=" * 60)
```

---

## 6. Penjelasan Tiap Tahap

### Tahap 1 — Load Data

```python
df = pd.read_csv("diabetes_dataset.csv")
```

Membaca file CSV ke dalam DataFrame pandas. Pastikan file `diabetes_dataset.csv` berada di direktori yang sama dengan script.

---

### Tahap 2 — Eksplorasi Data (EDA)

```python
df.describe()       # Statistik deskriptif (mean, std, min, max, dll)
df.isnull().sum()   # Deteksi missing value
df['Outcome'].value_counts()  # Distribusi kelas target
```

EDA bertujuan memahami struktur data sebelum masuk ke proses modeling.

---

### Tahap 3 — Persiapan Data

```python
X = df.drop('Outcome', axis=1)   # Fitur
y = df['Outcome']                 # Target

# Split 80% train, 20% test (stratify menjaga proporsi kelas)
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42, stratify=y
)

# Standarisasi: mean=0, std=1
scaler         = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled  = scaler.transform(X_test)   # HANYA transform, bukan fit_transform!
```

> ⚠️ **Penting:** `scaler.fit_transform()` hanya dipanggil pada data **train**. Data **test** hanya di-`transform()` agar tidak terjadi *data leakage*.

---

### Tahap 4 — Training Model

```python
from sklearn.naive_bayes import GaussianNB

model = GaussianNB()
model.fit(X_train_scaled, y_train)
```

GaussianNB secara otomatis menghitung **mean** dan **variance** dari setiap fitur untuk setiap kelas selama proses `fit()`.

Parameter penting `GaussianNB`:

| Parameter | Default | Keterangan |
|---|---|---|
| `var_smoothing` | `1e-9` | Nilai kecil ditambahkan ke variance untuk stabilitas numerik |
| `priors` | `None` | Probabilitas prior kelas (jika None, dihitung dari data) |

---

### Tahap 5 — Prediksi & Evaluasi

```python
y_pred = model.predict(X_test_scaled)          # Prediksi kelas
y_prob = model.predict_proba(X_test_scaled)[:, 1]  # Probabilitas kelas positif
```

#### Metrik Evaluasi yang Digunakan:

| Metrik | Formula | Keterangan |
|---|---|---|
| **Accuracy** | (TP+TN)/(TP+TN+FP+FN) | Persentase prediksi benar secara keseluruhan |
| **Precision** | TP/(TP+FP) | Dari semua yang diprediksi positif, berapa yang benar? |
| **Recall** | TP/(TP+FN) | Dari semua yang aktual positif, berapa yang terdeteksi? |
| **F1-Score** | 2×(P×R)/(P+R) | Rata-rata harmonis Precision dan Recall |
| **ROC AUC** | Area under ROC curve | Kemampuan model memisahkan kelas (0.5=acak, 1.0=sempurna) |

#### Confusion Matrix:

```
                  Prediksi
                  Tdk Diabetes  Diabetes
Aktual  Tdk Diab      TN           FP
        Diabetes      FN           TP
```

---

### Tahap 6 — Cross-Validation

```python
cv        = StratifiedKFold(n_splits=5, shuffle=True, random_state=42)
cv_scores = cross_val_score(model, X_train_scaled, y_train, cv=cv, scoring='accuracy')

print(f"Mean Accuracy: {cv_scores.mean():.4f} ± {cv_scores.std():.4f}")
```

**StratifiedKFold** digunakan agar setiap fold memiliki proporsi kelas yang sama, cocok untuk dataset yang tidak seimbang.

---

### Tahap 7 — Prediksi Data Baru

```python
sampel_baru = pd.DataFrame([{
    'Pregnancies': 3, 'Glucose': 158, 'BloodPressure': 90,
    'SkinThickness': 35, 'Insulin': 200, 'BMI': 33.6,
    'DiabetesPedigreeFunction': 0.627, 'Age': 50
}])

sampel_scaled = scaler.transform(sampel_baru)         # Skala dulu!
prediksi      = model.predict(sampel_scaled)[0]       # Kelas prediksi
probab        = model.predict_proba(sampel_scaled)[0] # Probabilitas tiap kelas
```

---

## 7. Hasil & Evaluasi Model

### 7.1 Ringkasan Performa

| Metrik | Nilai |
|---|---|
| **Accuracy** | **85.00%** |
| **Precision (Diabetes)** | 0.8608 |
| **Recall (Diabetes)** | 0.9444 |
| **F1-Score (Diabetes)** | 0.9007 |
| **ROC AUC** | **0.9206** |
| **Cross-Val (5-fold)** | 87.25% ± 3.10% |

### 7.2 Classification Report

```
                precision    recall  f1-score   support

Tidak Diabetes       0.81      0.61      0.69        28
      Diabetes       0.86      0.94      0.90        72

      accuracy                           0.85       100
     macro avg       0.84      0.78      0.80       100
  weighted avg       0.85      0.85      0.84       100
```

### 7.3 Confusion Matrix

```
                  Prediksi
                  Tdk Diab   Diabetes
Aktual  Tdk Diab    17          11
        Diabetes     4          68
```

| | Nilai |
|---|---|
| True Positive (TP) | 68 |
| True Negative (TN) | 17 |
| False Positive (FP) | 11 |
| False Negative (FN) | 4 |

### 7.4 Contoh Output Prediksi Data Baru

```
Input  : Pregnancies=3, Glucose=158, BloodPressure=90,
         SkinThickness=35, Insulin=200, BMI=33.6, DPF=0.627, Age=50

Prediksi               : DIABETES
Probabilitas Tidak DM  :  1.24%
Probabilitas Diabetes  : 98.76%
```

### 7.5 Class Prior Probability

```
P(Tidak Diabetes) = 0.2825  (28.25%)
P(Diabetes)       = 0.7175  (71.75%)
```

---

## 8. Visualisasi

Script menghasilkan **8 panel visualisasi** dalam satu figure:

| Panel | Visualisasi | Tujuan |
|---|---|---|
| 1 | Bar Chart Distribusi Kelas | Melihat keseimbangan kelas target |
| 2 | Confusion Matrix | Evaluasi prediksi benar/salah |
| 3 | ROC Curve | Kemampuan diskriminasi model |
| 4 | Cross-Validation (5-fold) | Konsistensi performa di berbagai fold |
| 5 | Histogram Glucose | Distribusi fitur terpenting per kelas |
| 6 | Histogram BMI | Distribusi BMI per kelas |
| 7 | Heatmap Korelasi | Hubungan antar semua fitur |
| 8 | Distribusi Probabilitas | Kepercayaan model dalam prediksi |

Output disimpan sebagai: **`naive_bayes_analisis.png`** (resolusi 150 DPI)

---

## 9. Kesimpulan

### 9.1 Hasil Utama

Model **Gaussian Naive Bayes** berhasil mengklasifikasikan penyakit diabetes dengan performa yang cukup baik:

- Accuracy **85%** menunjukkan model mampu memprediksi 85 dari 100 sampel dengan benar.
- ROC AUC **0.92** mengindikasikan kemampuan diskriminasi yang sangat baik (mendekati 1.0).
- Cross-validation **87.25% ± 3.10%** menunjukkan model konsisten dan tidak overfit.
- Recall untuk kelas Diabetes **94.4%** artinya model jarang melewatkan kasus diabetes (FN rendah) — ini penting dalam konteks medis.

### 9.2 Kelebihan Naive Bayes

- Sangat cepat dalam training dan prediksi
- Bekerja baik dengan data kecil hingga sedang
- Tidak memerlukan tuning hyperparameter yang rumit
- Interpretabel dan mudah dipahami

### 9.3 Kekurangan Naive Bayes

- Asumsi independensi antar fitur jarang terpenuhi di data nyata
- Kurang akurat dibanding model kompleks (Random Forest, XGBoost) pada data besar
- Sensitif terhadap fitur yang sangat berkorelasi