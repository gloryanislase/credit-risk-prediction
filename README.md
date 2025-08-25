# Model Prediksi Risiko Gagal Bayar Kartu Kredit - FinanKu

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge&logo=python)
![Scikit-Learn](https://img.shields.io/badge/SciKit--Learn-1.2.2-orange?style=for-the-badge&logo=scikit-learn)
![Status](https://img.shields.io/badge/Status-Completed-green?style=for-the-badge)

Proyek ini bertujuan untuk membangun model klasifikasi untuk memprediksi kemungkinan seorang nasabah akan mengalami gagal bayar (default) pada pembayaran kartu kreditnya untuk perusahaan fintech imajiner, FinanKu.

---

### ► Daftar Isi
1. [Latar Belakang Proyek](#-latar-belakang-proyek)
2. [Sumber Data](#-sumber-data)
3. [Metodologi](#-metodologi)
4. [Analisis Eksplorasi Data (EDA)](#-analisis-eksplorasi-data-eda)
5. [Pemodelan dan Evaluasi](#-pemodelan-dan-evaluasi)
6. [Kesimpulan dan Rekomendasi](#-kesimpulan-dan-rekomendasi)
7. [Teknologi yang Digunakan](#-teknologi-yang-digunakan)
8. [Informasi Kontak](#-informasi-kontak)

---

### ► Latar Belakang Proyek
FinanKu adalah sebuah startup fintech yang sedang berkembang pesat. Salah satu produk unggulannya adalah Kartu Kredit dengan fitur *instant approval*. Namun, dalam setahun terakhir, **lebih dari 20% nasabah kartu kredit mengalami gagal bayar**, yang berpotensi mengganggu stabilitas finansial perusahaan.

Proyek ini bertujuan untuk membangun sebuah model machine learning yang dapat secara proaktif memprediksi nasabah mana yang berisiko tinggi untuk gagal bayar. Dengan identifikasi dini, perusahaan dapat menerapkan strategi penagihan yang lebih efektif dan personal untuk memitigasi risiko kerugian. Tujuan utama bisnis adalah untuk mencapai **Akurasi dan Recall di atas 60%**.

---

### ► Sumber Data
Dataset yang digunakan dalam proyek ini adalah data transaksional dan demografis internal dari nasabah FinanKu selama satu tahun terakhir. Dataset utama mencakup informasi seperti demografi nasabah, saldo, jumlah produk, dan aktivitas transaksi per kuartal.

---

### ► Metodologi
Proyek ini menggunakan pendekatan eksperimental untuk menemukan model terbaik dengan membandingkan dua skenario data.
1.  **Eksperimen 1**: Menggunakan data perilaku nasabah selama **12 bulan terakhir**.
2.  **Eksperimen 2**: Menggunakan data perilaku nasabah selama **6 bulan terakhir**.

Proses ini mencakup *feature engineering* untuk membuat variabel prediktif baru (seperti `Delta Balance`, `Active Month`, dan `Mean Balance` untuk melihat tren perilaku), *one-hot encoding* untuk variabel kategorikal, dan standardisasi data numerik sebelum dimasukkan ke dalam model.

---

### ► Analisis Eksplorasi Data (EDA)
Analisis awal data menunjukkan bahwa distribusi nasabah yang berpotensi gagal bayar berdasarkan kota sebanding dengan distribusi pelanggan secara keseluruhan, dengan **Surabaya** memiliki jumlah tertinggi. Dari segi usia, nasabah yang berpotensi gagal bayar tersebar cukup merata di berbagai rentang usia, dengan puncak di usia produktif (30-40 tahun).

![Distribusi Usia Pelanggan](images/Customer%20Distribution%20by%20Age.png)

---

### ► Pemodelan dan Evaluasi
Tiga algoritma klasifikasi diuji untuk setiap eksperimen: **Logistic Regression, Gradient Boosting (XGBoost), dan Random Forest**. Berdasarkan hasil `GridSearchCV` dengan fokus optimasi pada metrik **Recall**, model dengan performa terbaik adalah:

**Model Terbaik: Gradient Boosting (dari Eksperimen 1 - data 12 bulan)**

Performa model ini pada **data uji (test set)** dan **data validasi (unseen data)** adalah sebagai berikut:

| Metrik | Performa pada Test Set | Performa pada Validation Set | Target Bisnis | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Akurasi** | **68.6%** | 59.3% | > 60% | ⚠️ Tercapai (Test), Tidak (Validasi) |
| **Recall** | **60.5%** | 44.8% | > 60% | ❌ **Tidak Tercapai** |

Meskipun model berhasil mencapai target Recall di atas 60% pada *test set*, performanya turun drastis menjadi **44.8%** pada data validasi. Hal ini menunjukkan bahwa model **belum cukup andal untuk digeneralisasi pada data baru** dan dengan demikian, **tujuan bisnis belum tercapai**. Analisis *feature importance* menunjukkan bahwa `Vintage_CR`, `Delta Balance`, dan `Mean Balance` adalah prediktor paling berpengaruh.

![Pentingnya Fitur dari Model XGBoost](images/Mean%20Score%20Decrease%20Model%20Gradient%20Boosting%20Eksperimen%201.png)

---

### ► Kesimpulan dan Rekomendasi
Proyek ini berhasil mengembangkan model prediksi (Gradient Boosting) sebagai *baseline* yang baik. Namun, model ini **belum memenuhi objektif bisnis** karena gagal mencapai target recall 60% pada data validasi, yang berarti masih banyak nasabah gagal bayar yang terlewatkan.

**Rekomendasi untuk Pengembangan Selanjutnya:**
1.  **Menangani Data Tidak Seimbang**: Proporsi kelas minoritas (gagal bayar) jauh lebih kecil. Perlu diimplementasikan teknik *oversampling* seperti **SMOTE** untuk menyeimbangkan data training.
2.  **Memperluas Horizon Waktu & Fitur**: Menggunakan data dengan rentang waktu lebih panjang dan menambah variabel baru untuk menangkap pola yang lebih kompleks.
3.  **Memperbanyak Sampel Data**: Jika memungkinkan, menambah jumlah sampel nasabah untuk melatih model yang lebih robust.
4.  **Eksplorasi Algoritma Lain**: Mencoba algoritma *supervised machine learning* lain yang mungkin lebih cocok untuk dataset ini.

---

### ► Teknologi yang Digunakan
- Python
- Pandas
- Scikit-Learn
- XGBoost
- Matplotlib & Seaborn
- Jupyter Notebook

---

### ► Informasi Kontak
- **Nama**: Gloryanis Veronica Lase
- **Hubungi Saya**:

  [![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/gloryanisveronicalase)
  [![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:gloryanislase@gmail.com)
