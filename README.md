# Capstone Project: E-commerce Customer Churn Classification

Repositori ini berisi implementasi end-to-end dari proyek klasifikasi untuk memprediksi *customer churn* pada sebuah perusahaan e-commerce. Proyek ini bertujuan untuk mengidentifikasi pelanggan yang berisiko berhenti bertransaksi guna memungkinkan intervensi bisnis yang proaktif.

# Latar Belakang Masalah & Objektif

**Problem Statement:** Tingginya tingkat *customer churn* merupakan tantangan operasional yang signifikan, berdampak langsung pada `revenue` dan meningkatkan biaya akuisisi pelanggan. Diperlukan sebuah mekanisme sistematis untuk mengidentifikasi pelanggan yang berisiko *churn*.
**Project Objective:** Mengembangkan dan mengevaluasi beberapa model klasifikasi *machine learning* untuk memprediksi *customer churn*. Objektif utama dari model adalah memaksimalkan **`Recall`** untuk kelas *churn*, dengan tujuan mengidentifikasi sebanyak mungkin pelanggan yang benar-benar akan berhenti bertransaksi.

# Metodologi

Alur kerja proyek ini mengikuti tahapan standar dalam *data science lifecycle*:
1.  **Data Understanding:** Analisis awal terhadap dataset untuk memahami struktur, tipe data, dan distribusi setiap fitur, termasuk `Tenure`, `DaySinceLastOrder`, dan variabel target `Churn`.
2.  **Data Preprocessing:** Tahap ini mencakup pembersihan dan transformasi data, termasuk imputasi nilai yang hilang (*missing values*) menggunakan `median`, *One-Hot Encoding* untuk fitur kategorikal, dan *Feature Scaling* menggunakan `StandardScaler`.
3.  **Modeling:** Eksperimen dilakukan dengan tiga algoritma klasifikasi: `Random Forest`, `XGBoost`, dan `Logistic Regression` untuk perbandingan performa awal.
4.  **Evaluation:** Model dievaluasi menggunakan metrik standar klasifikasi. Berdasarkan analisis biaya bisnis (`False Negative` vs. `False Positive`), `Recall` dipilih sebagai metrik evaluasi utama.
5.  **Optimization:** Model `Random Forest` dioptimalkan menggunakan `GridSearchCV` untuk menemukan kombinasi *hyperparameter* terbaik yang memaksimalkan `Recall`.

# Hasil & Analisis

Model `Random Forest` yang telah dioptimalkan menghasilkan performa sebagai berikut pada data uji:

-   **`Precision` (untuk kelas Churn): 0.89 (89%)**
    -   **Implikasi:** Ketika model memprediksi seorang pelanggan akan *churn*, prediksi tersebut 89% benar. Hal ini menunjukkan efisiensi model dalam menargetkan pelanggan.
-   **`Recall` (untuk kelas Churn): 0.68 (68%)**
    -   **Implikasi:** Model berhasil mengidentifikasi 68% dari total pelanggan yang sebenarnya *churn*. Hasil ini **belum mencapai target objektif awal (Recall 80%)** dan mengindikasikan bahwa model masih melewatkan 32% pelanggan berisiko.
Analisis ini menunjukkan bahwa meskipun model memiliki presisi yang tinggi, sensitivitasnya masih perlu ditingkatkan.

## Rekomendasi & Langkah Selanjutnya
Berdasarkan temuan di atas, rekomendasi strategis berikut diajukan:
**Prioritas utama adalah melakukan *hyperparameter tuning* pada model `XGBoost`.**
**Justifikasi:** Pada tahap eksperimen awal, `XGBoost` (tanpa optimasi) menunjukkan `Recall` sebesar 85%. Ini adalah indikator kuat bahwa `XGBoost` memiliki potensi untuk menjadi solusi final yang dapat mencapai target bisnis setelah melalui proses optimasi yang sama.

## Stack Teknologi
-   **Bahasa:** Python
-   **Library:**
    -   Pandas & NumPy (Manipulasi Data)
    -   Scikit-learn (Preprocessing & Modeling)
    -   XGBoost (Modeling)
    -   Matplotlib & Seaborn (Visualisasi)

## Panduan Penggunaan
1.  *Clone* repositori ini.
2.  Instal dependensi yang tercantum dalam *stack* teknologi.
3.  Tempatkan dataset `data_ecommerce_customer_churn.csv` pada direktori *root*.
