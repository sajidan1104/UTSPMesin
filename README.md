# Klasifikasi Buah Citrus (Orange vs Grapefruit)

Proyek ini bertujuan untuk membangun dan membandingkan model *Machine Learning* yang dapat mengklasifikasikan jenis buah citrus (Jeruk vs Grapefruit) berdasarkan fitur fisik seperti diameter, berat, dan tingkat warna RGB.

## Tahapan Pembuatan Model

### 1. Pengumpulan dan Pemahaman Data (Data Understanding)
Dataset yang digunakan adalah `citrus.csv`. Dataset ini terdiri dari 6 kolom:
* `name`: Kelas target yang berisi label teks ('orange' atau 'grapefruit').
* `diameter` & `weight`: Fitur fisik ukuran dan berat buah.
* `red`, `green`, `blue`: Fitur nilai spektrum warna RGB pada buah.

### 2. Pra-pemrosesan Data (Data Preprocessing)
Sebelum dimasukkan ke dalam model, data harus disiapkan melalui tahapan berikut:
* **Label Encoding:** Mengubah variabel target (`name`) dari bentuk teks ('orange', 'grapefruit') menjadi bentuk numerik biner (0 dan 1) agar dapat dipahami oleh algoritma.
* **Pemisahan Fitur dan Target:** Memisahkan kolom target (y) dari kolom fitur/prediktor (X).
* **Feature Scaling (Standarisasi):** Menyamakan rentang nilai (skala) pada seluruh fitur. Hal ini sangat krusial, terutama untuk model **Support Vector Machine (SVM)** yang sangat sensitif terhadap perbedaan skala data (misalnya rentang nilai warna 0-255 disamakan skalanya dengan nilai diameter).

### 3. Pembagian Data (Data Splitting)
Dataset dibagi menjadi dua bagian:
* **Training Data (80%):** Digunakan untuk melatih model agar mengenali pola.
* **Testing Data (20%):** Digunakan untuk menguji kinerja model pada data yang belum pernah dilihat sebelumnya.

### 4. Pelatihan Model (Model Training)
Proyek ini membandingkan 3 algoritma klasifikasi:
1. **Decision Tree:** Membangun model berupa struktur pohon keputusan berdasarkan aturan "If-Else" dari nilai fitur (misal: jika berat > X dan nilai merah > Y, maka Jeruk).
2. **Naive Bayes (Gaussian):** Menggunakan probabilitas bersyarat berdasarkan Teorema Bayes dengan asumsi bahwa setiap fitur independen satu sama lain.
3. **Support Vector Machine (SVM):** Mencari garis pemisah (*hyperplane*) terbaik yang memiliki margin terjauh antara kelompok jeruk dan grapefruit di ruang dimensi berdasar fitur-fiturnya.

### 5. Evaluasi Model (Model Evaluation)
Ketiga model dievaluasi menggunakan metrik performa standar klasifikasi:
* **Accuracy:** Persentase tebakan model yang benar secara keseluruhan.
* **Precision:** Ketepatan model dalam menebak kelas positif.
* **Recall:** Kemampuan model menemukan seluruh data yang benar di kelas tersebut.
* **F1-Score:** Rata-rata harmonis antara Precision dan Recall.

Kesimpulan model terbaik akan ditentukan dari hasil *Classification Report* pada tahap pengujian.
