# credit-risk-prediction
Machine learning model to predict the risk of late credit card payments.

# Prediksi Risiko Keterlambatan Pembayaran Kartu Kredit

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge&logo=python)
![Scikit-Learn](https://img.shields.io/badge/SciKit--Learn-1.2.2-orange?style=for-the-badge&logo=scikit-learn)
![Status](https://img.shields.io/badge/Status-Completed-green?style=for-the-badge)

Proyek ini bertujuan untuk membangun model klasifikasi guna memprediksi nasabah yang berpotensi mengalami keterlambatan pembayaran kartu kredit di FinanKu.

---

### ► Daftar Isi
1. [Gambaran Umum Proyek](#-gambaran-umum-proyek)
2. [Sumber Data](#-sumber-data)
3. [Metodologi](#-metodologi)
4. [Hasil](#-hasil)
5. [Kesimpulan](#-kesimpulan)
6. [Teknologi yang Digunakan](#-teknologi-yang-digunakan)
7. [Informasi Kontak](#-informasi-kontak)

---

### ► Gambaran Umum Proyek
Keterlambatan pembayaran kartu kredit merupakan masalah bisnis yang dapat merugikan perusahaan finansial seperti FinanKu. Proyek ini bertujuan untuk mengembangkan sebuah model machine learning yang dapat memprediksi secara proaktif nasabah mana yang memiliki risiko tinggi untuk telat bayar. Dengan identifikasi dini, perusahaan dapat menerapkan strategi penagihan yang lebih efektif dan personal. Tujuan utama dari model ini adalah mencapai nilai **Akurasi dan Recall di atas 60%**.

---

### ► Sumber Data
Dataset yang digunakan dalam proyek ini adalah data transaksional internal nasabah FinanKu selama periode satu tahun.
*(Jika datasetnya publik, Anda bisa menambahkan link di sini, misalnya: [Credit Card Default Dataset](https-www-kaggle-com/datasets/uciml/default-of-credit-card-clients-dataset))*

---

### ► Metodologi
Proses analisis dan pemodelan dilakukan dalam beberapa tahap:
1. **Data Understanding**: Menganalisis distribusi nasabah berdasarkan demografi dan perilaku finansial awal untuk mendapatkan wawasan pertama.
2. **Feature Engineering**: Membuat fitur-fitur baru yang lebih prediktif, seperti `Mean Balance`, `Delta Balance`, dan `Active Month` untuk menangkap tren perilaku nasabah.
3. **Data Preparation**: Melakukan standarisasi pada data numerik dan *one-hot encoding* pada data kategorikal.
4. **Modeling**: Menguji tiga algoritma klasifikasi (Logistic Regression, XGBoost, Random Forest) dan melakukan tuning *hyperparameter* menggunakan `GridSearchCV` untuk menemukan model dengan performa terbaik, dengan fokus pada metrik **Recall**.
5. **Evaluation**: Mengevaluasi model terbaik pada data uji untuk memastikan performanya.

---

### ► Hasil
Model **Gradient Boosting (XGBoost)** terpilih sebagai model terbaik dengan performa sebagai berikut pada data uji:
* **Akurasi**: 71.9%
* **Recall**: 60.5%
* **Fitur Paling Berpengaruh**: `Active Month`, `Delta Balance`, dan `Age`.

Model ini berhasil memenuhi target bisnis dengan mampu mengidentifikasi lebih dari 60% nasabah yang benar-benar akan mengalami keterlambatan bayar.

_*(Di sini Anda bisa menambahkan visualisasi kunci, seperti Feature Importance Plot)*_
![Feature Importance Plot](images/feature-importance.png)

---

### ► Kesimpulan
Proyek ini berhasil mengembangkan model prediksi yang fungsional untuk mengidentifikasi nasabah berisiko. Untuk pengembangan lebih lanjut, disarankan untuk menerapkan teknik *oversampling* (seperti SMOTE) guna menangani data yang tidak seimbang dan berpotensi meningkatkan performa model lebih jauh lagi.

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
- **Nama**: [Gloryanis Veronica Lase]
- **LinkedIn**: [linkedin.com/in/gloryanisveronicalase]
- **Email**: [gloryanislase@gmail.com]
