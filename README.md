# Classification of Customer Satisfaction Ratings Based on Shopping Patterns

Mengklasifikasikan tingkat kepuasan pelanggan (Buruk/Netral/Baik) berdasarkan pola belanja (kategori barang, jumlah pembelian, lokasi, metode pembayaran, dan atribut lainnya), menggunakan model Random Forest.

> *Project ini dikerjakan sebagai tugas mata kuliah, dikerjakan secara individu.*

## Latar Belakang

Perusahaan ritel sering ingin memahami pola belanja seperti apa yang berkaitan dengan kepuasan pelanggan, agar dapat mengambil langkah yang tepat untuk meningkatkan pengalaman berbelanja. Model klasifikasi dapat membantu mengeksplorasi hubungan ini berdasarkan data transaksi yang sudah ada.

## Rumusan Masalah

- Faktor pola belanja apa saja (kategori barang, jumlah pembelian, lokasi, metode pembayaran, dll.) yang berkaitan dengan tingkat kepuasan pelanggan (Review Rating)?
- Seberapa baik model klasifikasi dapat memprediksi tingkat kepuasan pelanggan berdasarkan pola belanja tersebut?

## Tujuan Project

1. Membangun label tingkat kepuasan (Buruk/Netral/Baik) berdasarkan distribusi nilai Review Rating yang sebenarnya.
2. Membangun model klasifikasi Random Forest untuk memprediksi tingkat kepuasan pelanggan.
3. Mengevaluasi performa model menggunakan baseline dan cross-validation.

## Keterbatasan dan Temuan Penting

Setelah label diperbaiki agar sesuai dengan rentang data asli dan dievaluasi secara robust (baseline & cross-validation), performa model berada di sekitar atau bahkan sedikit di bawah baseline tebak kelas mayoritas (36.6%). Pengecekan korelasi menunjukkan fitur numerik seperti usia, jumlah pembelian, dan riwayat pembelian sebelumnya memiliki korelasi yang nyaris nol terhadap Review Rating.

Temuan ini mengindikasikan bahwa pada dataset ini, kolom `Review Rating` kemungkinan besar tidak memiliki hubungan yang benar-benar bisa dipelajari dengan pola belanja lainnya (umum terjadi pada dataset sintetis yang dibuat untuk latihan). Notebook ini karena itu lebih tepat dipahami sebagai demonstrasi metodologi klasifikasi yang lengkap dan benar (pembersihan data, encoding, labeling berbasis data, modeling, dan evaluasi), bukan sebagai model prediksi kepuasan pelanggan yang siap dipakai.

## Metodologi

1. Menentukan Objek Data - memuat dan pemeriksaan awal dataset
2. Membersihkan Data - pengecekan missing value/duplikat, menghapus kolom identitas (Customer ID)
3. Mengkonstruksi Data - encoding fitur kategorikal menjadi numerik
4. Exploratory Data Analysis - memeriksa rentang dan distribusi Review Rating
5. Menentukan Label Data - membangun label Buruk/Netral/Baik berdasarkan quantile dari rentang data asli
6. Membangun Model Data - membangun pipeline preprocessing + Random Forest
7. Mengevaluasi Hasil Pemodelan Data - baseline, cross-validation, evaluasi data test, confusion matrix, visualisasi decision tree, dan feature importance

## Hasil Utama

| Metode Evaluasi | Akurasi |
|---|---|
| Baseline (kelas mayoritas) | 36.7% |
| Random Forest (cross-validation) | 35.0% |
| Random Forest (data test) | 36.3% |

## Tech Stack

- Python
- Pandas, NumPy - manipulasi data
- Matplotlib, Seaborn - visualisasi data
- Scikit-learn - preprocessing pipeline, Random Forest, cross-validation, dan metrik evaluasi

## Struktur Project

```
Customer_Satisfaction_Classification.ipynb   - Notebook analisis lengkap
shopping_behavior_updated.csv                - Dataset
```

## Cara Menjalankan

### Prerequisites
- Python 3.x

### Instalasi

```bash
# 1. Clone repository
git clone https://github.com/DanuSetiawan05/Classification-of-Customer-Satisfaction-Ratings-Based-on-Shopping-Patterns.git
cd Classification-of-Customer-Satisfaction-Ratings-Based-on-Shopping-Patterns

# 2. Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn

# 3. Jalankan notebook
jupyter notebook Customer_Satisfaction_Classification.ipynb
```

## Pengembangan Selanjutnya

- Menggunakan dataset lain yang memiliki hubungan lebih jelas antara pola belanja dan kepuasan pelanggan untuk membangun model prediksi yang benar-benar dapat diandalkan.
- Menambahkan fitur tambahan (misalnya waktu respons layanan pelanggan atau riwayat komplain) yang berpotensi memiliki sinyal prediktif lebih kuat terhadap kepuasan pelanggan.
- Membandingkan hasil dengan algoritma lain (Logistic Regression, Gradient Boosting, SVM, KNN) sebagai bagian dari proses eksplorasi model.

## Author

Muhammad Danu Setiawan

## Lisensi

Project ini bersifat open source dan tersedia untuk keperluan pembelajaran.
