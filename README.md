Nama: Marsha Oktapia
Kelas: Sistem Informasi (3A)
Mata Kuliah: Machine Learning
Dosen Pengampu: Dr. DWI WAHYU PRABOWO, S.Si., M.Eng.

Prediksi Status Kelulusan Mahasiswa Menggunakan SVM

Project ini bertujuan untuk membangun model Machine Learning berbasis Support Vector Machine (SVM) untuk memprediksi Status Kelulusan Mahasiswa berdasarkan data akademik dan demografis. Dataset berisi variabel seperti IPK, IPS setiap semester, umur, jenis kelamin, status mahasiswa, dan status pernikahan.
Project ini mengikuti seluruh instruksi dari modul/praktikum SVM, mencakup EDA, preprocessing, training model, evaluasi, hyperparameter tuning, serta fungsi prediksi untuk deployment.
 1. Tujuan Proyek
Melakukan analisis data mahasiswa (EDA) untuk menemukan pola kelulusan.
Melakukan preprocessing data: imputasi, encoding, dan scaling.
Membangun model SVM dengan kernel Linear dan RBF.
Melakukan GridSearchCV untuk menemukan parameter terbaik.
Mengevaluasi performa model dengan berbagai train-test split.
Membuat fungsi prediksi berbasis dictionary untuk penggunaan lanjutan.

2. Dataset
Dataset merupakan data kelulusan mahasiswa dengan beberapa kategori variabel:
Variabel Numerik:
Umur
IPK
IPS 1 – IPS 8
Variabel Kategorikal:
Jenis Kelamin
Status Mahasiswa
Status Nikah
Variabel Target:
Status Kelulusan (Lulus / Tidak Lulus)

 3. Exploratory Data Analysis (EDA)
EDA dilakukan untuk memahami karakteristik data:
Visualisasi:
Histogram IPK
Distribusi Jenis Kelamin
Distribusi Status Pernikahan
Distribusi Status Mahasiswa
Distribusi Status Kelulusan
Heatmap Korelasi antar fitur
Rata-rata IPS per semester

Temuan EDA:
IPK menjadi faktor paling berpengaruh terhadap kelulusan.
Umur tidak menunjukkan perbedaan signifikan antara mahasiswa lulus dan tidak.
Mahasiswa belum menikah memiliki tingkat kelulusan sedikit lebih tinggi.
Korelasi kuat terlihat antara IPK dan nilai IPS pada semester akhir.

 4. Preprocessing Data
Langkah-langkah yang digunakan:
Menghapus spasi di nama kolom.
Mengisi missing value:
Numerik → median
Kategorikal → mode
Encoding variabel kategorikal menggunakan LabelEncoder.
Scaling fitur numerik menggunakan StandardScaler.
Memisahkan dataset menjadi fitur (X) dan target (y).

 5. Train-Test Split
Sesuai instruksi modul, dilakukan 4 variasi pembagian data:
Train : Test	Akurasi
60 : 40	0.894
75 : 25	0.863
80 : 20	0.868
90 : 10	0.894
Model terbukti stabil pada berbagai variasi split.

 6. Model SVM
Dua model diuji:

 SVM Linear
Digunakan untuk menguji apakah data dapat dipisahkan secara linear.

 SVM RBF
Cocok untuk pola non-linear. Pada dataset ini, SVM RBF menghasilkan akurasi lebih baik.

 7. Hyperparameter Tuning
Dilakukan menggunakan GridSearchCV dengan parameter:
C: [0.1, 1, 10]
gamma: ["scale", 0.1, 1]
kernel: ["linear", "rbf"]
Hasil terbaik:
Model terbaik adalah SVM RBF dengan kombinasi parameter optimal berdasarkan GridSearch.

 8. Evaluasi Model
Evaluasi dilakukan menggunakan:
Accuracy Score
Classification Report
Confusion Matrix (heatmap)
Model SVM RBF memberikan performa lebih tinggi dibanding Linear, mengindikasikan bahwa pola kelulusan tidak linear dan membutuhkan kernel kompleks.

 9. Feature Importance
Menggunakan Permutation Importance, didapatkan fitur paling berpengaruh:
IPK
IPS Semester Akhir
IPS Semester Pertengahan (IPS 4–6)
Status Mahasiswa & Status Pernikahan (lebih kecil pengaruhnya)

10. Fungsi Prediksi (Deployment)
Tersedia fungsi prediksi berbasis dictionary:
predict_status(model, scaler, raw_dict)
Fungsi ini menerima input dalam bentuk dict dan menghasilkan output:
"LULUS" atau "TIDAK LULUS"
Cocok untuk integrasi ke aplikasi web atau dashboard.

11. Kesimpulan
SVM RBF adalah model terbaik untuk dataset kelulusan mahasiswa.
IPK dan IPS merupakan fitur yang paling menentukan.
Preprocessing dan scaling sangat penting untuk meningkatkan performa model.
Model stabil pada berbagai train-test split dan dapat digunakan untuk prediksi di dunia nyata.

12. Teknologi yang Digunakan
Python
Pandas
NumPy
Scikit-Learn
Seaborn
Matplotlib
Google Colab
