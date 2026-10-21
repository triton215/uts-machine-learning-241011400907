# UTS Machine Learning – Linear Regression & Logistic Regression

- **Nama  :** Adi Ryan Gunawan Situmorang
- **NIM   :** 241011400907
- **Kelas :** (Reg B / ~~Reg C~~)
- **random_state :** 7 (2 digit terakhir NIM = 07)

## Isi Repositori
| File | Keterangan |
|---|---|
| `tugas_UTS.ipynb` | Notebook jawaban (sudah dijalankan, lengkap dengan output) |
| `Ads_Data.csv` | Dataset biaya iklan vs penjualan (40 data) |
| `Email_Data.csv` | Dataset email spam (60 data) |

Semua model dan metrik diimplementasikan sendiri dengan NumPy (scikit-learn hanya dipakai pada soal bonus).

## Ringkasan Hasil

### Bagian A – Linear Regression (`Ads_Data.csv`, test_size = 0.2)
- Persamaan (normal equation): **ŷ = 28,2320 + 9,2168 · X**
- Data testing: MAE = 4,3539 · RMSE = 6,0321 · **R² = 0,9550** (training: R² = 0,9383)
- Gradient descent (5000 iterasi): lr 0,001 terlalu lambat, **lr 0,02 sama dengan normal equation**, lr 0,1 divergen (overflow → NaN)
- Prediksi: 4,5 juta → 69,71 · 7 juta → 92,75 · 12 juta → 138,83 (ekstrapolasi, kurang dapat dipercaya)

### Bagian B – Logistic Regression (`Email_Data.csv`, test_size = 0.25)
- Model: P(Spam) = σ(−12,3111 + 1,0950 · JumlahLink + 0,9655 · KataPromo)
- Data testing (threshold 0,5): **Accuracy = 0,8667** · Precision = 1,0 · Recall = 0,7143 · F1 = 0,8333
- Confusion matrix: TN = 8, FP = 0, FN = 2, TP = 5
- Threshold dipilih: **0,5** (0,3 sama hasilnya; 0,7 menurunkan recall menjadi 0,5714)

### Bonus – scikit-learn
- Linear Regression: hasil identik dengan implementasi sendiri.
- Logistic Regression: koefisien berbeda karena sklearn memakai regularisasi L2 (C = 1) secara default dan solver yang konvergen penuh; accuracy testing tetap 0,8667.
