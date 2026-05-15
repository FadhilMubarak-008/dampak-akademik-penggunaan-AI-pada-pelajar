# Memprediksi Dampak Akademik Penggunaan Alat AI di Kalangan Mahasiswa

## 📌 Deskripsi Proyek

Proyek ini bertujuan untuk menganalisis dan memprediksi dampak penggunaan tools AI terhadap performa akademik mahasiswa.

Di era berkembangnya teknologi AI seperti ChatGPT, Grammarly, Gemini, dan tools AI lainnya, mahasiswa mulai menggunakan AI dalam berbagai aktivitas akademik seperti:

* Belajar
* Research
* Coding
* Homework
* Writing

Namun, muncul pertanyaan penting:

> Apakah penggunaan AI benar-benar meningkatkan performa akademik mahasiswa?

Melalui proyek ini, dilakukan analisis perilaku penggunaan AI mahasiswa menggunakan pendekatan Data Science dan Machine Learning.

---

# 🎯 Tujuan Proyek

Tujuan utama proyek ini adalah:

* Menganalisis hubungan antara penggunaan AI dan dampaknya terhadap nilai akademik mahasiswa
* Mengidentifikasi faktor yang paling berpengaruh terhadap peningkatan akademik
* Membuat model Machine Learning untuk memprediksi dampak akademik berdasarkan perilaku penggunaan AI

---

# 📂 Dataset

Dataset yang digunakan:

**AI_Student_Life_Pakistan_2026**

Jumlah data:

* 100 baris
* Tidak memiliki missing value
* Tidak memiliki duplicate data

## 📌 Kolom Dataset

| Kolom              | Deskripsi                        |
| ------------------ | -------------------------------- |
| Student_ID         | ID unik mahasiswa                |
| Age                | Umur mahasiswa                   |
| Gender             | Jenis kelamin                    |
| Education_Level    | Tingkat pendidikan               |
| City               | Kota asal                        |
| AI_Tool_Used       | Tools AI yang digunakan          |
| Daily_Usage_Hours  | Rata-rata penggunaan AI per hari |
| Purpose            | Tujuan penggunaan AI             |
| Impact_on_Grades   | Dampak terhadap nilai akademik   |
| Satisfaction_Level | Tingkat kepuasan penggunaan AI   |

---

# 🧠 Problem Statement

Bagaimana perilaku penggunaan AI mahasiswa mempengaruhi performa akademik mereka?

Apakah:

* durasi penggunaan AI,
* tujuan penggunaan,
* jenis tools AI,
* serta faktor lainnya

memiliki hubungan terhadap peningkatan atau penurunan nilai akademik?

---

# 🎯 Target Machine Learning

Kolom target yang digunakan:

```python
Impact_on_Grades
```

Target memiliki 3 kelas:

| Label | Arti           |
| ----- | -------------- |
| 0     | Slight Decline |
| 1     | No Change      |
| 2     | Improved       |

Karena memiliki lebih dari dua kelas, maka proyek ini termasuk:

# ✅ Multiclass Classification

---

# 🛠️ Tahapan Analisis

# 1. Pemahaman Data

Dilakukan pengecekan:

* Struktur dataset
* Tipe data
* Missing value
* Duplicate data
* Statistik deskriptif

## 📌 Hasil

* Tidak ditemukan missing value
* Tidak ditemukan data duplikat
* Rata-rata usia mahasiswa sekitar 19 tahun
* Rata-rata penggunaan AI sekitar 3 jam per hari

---

# 2. Exploratory Data Analysis (EDA)

Dilakukan visualisasi data untuk memahami pola penggunaan AI mahasiswa.

## 📊 Analisis yang dilakukan

### Distribusi Impact_on_Grades

Menunjukkan bahwa:

* Sebagian besar mahasiswa mengalami peningkatan akademik
* Distribusi kelas cukup seimbang untuk proses Machine Learning

---

### Daily Usage Hours vs Impact on Grades

Analisis menunjukkan:

* Mahasiswa dengan penggunaan AI lebih tinggi cenderung memiliki dampak akademik yang lebih positif
* Namun durasi penggunaan saja tidak cukup menjelaskan peningkatan akademik

---

### Purpose vs Impact on Grades

Dilakukan analisis hubungan antara tujuan penggunaan AI dan dampak akademik.

## 📌 Insight penting:

### Coding

Mahasiswa yang menggunakan AI untuk coding memiliki jumlah kategori "Improved" paling tinggi.

Kemungkinan karena AI membantu:

* debugging
* memahami syntax
* menyelesaikan project
* mempercepat proses belajar teknis

---

### Research

Penggunaan AI untuk research menunjukkan distribusi yang hampir seimbang pada seluruh kategori.

Hal ini mengindikasikan bahwa:

> penggunaan AI untuk research tidak memiliki hubungan yang terlalu jelas terhadap peningkatan nilai akademik.

---

### Learning

Kategori learning menunjukkan hasil yang cukup beragam.

Hal ini menunjukkan bahwa:

* AI dapat membantu proses belajar
* tetapi juga dapat menyebabkan ketergantungan jika digunakan secara tidak efektif

---

# ⚙️ Data Preprocessing

## 📌 Drop Kolom Tidak Penting

Kolom `Student_ID` dihapus karena hanya berfungsi sebagai identifier.

---

## 📌 Encoding Data Ordinal

Dilakukan mapping ordinal untuk:

* Satisfaction_Level
* Education_Level
* Impact_on_Grades

Contoh:

```python
impact_map = {
    'Slight Decline': 0,
    'No Change': 1,
    'Improved': 2
}
```

---

## 📌 One Hot Encoding

Dilakukan untuk data kategorikal nominal:

* Gender
* City
* AI_Tool_Used
* Purpose

---

# 🤖 Modeling

Model yang digunakan:

```python
Logistic Regression
```

Alasan penggunaan:

* Cocok untuk dataset kecil
* Mudah diinterpretasikan
* Baik sebagai baseline model classification

---

# 📈 Evaluasi Model

Evaluasi dilakukan menggunakan:

* Accuracy
* Precision
* Recall
* F1-Score
* Confusion Matrix

## 📌 Hasil Evaluasi

| Metric   | Nilai |
| -------- | ----- |
| Accuracy | 55%   |

### Insight Evaluasi

* Model cukup baik dalam mengenali mahasiswa dengan kategori "Improved"
* Model masih kesulitan membedakan kategori "No Change"
* Dataset yang terlalu kecil dan perilaku manusia yang kompleks mempengaruhi performa model

---

# 🔥 Feature Importance

Dilakukan analisis feature importance menggunakan koefisien Logistic Regression.

## 📌 Hasil Utama

Feature yang paling berpengaruh:

* Purpose_Learning
* Purpose_Research
* AI_Tool_Used_Grammarly
* Daily_Usage_Hours

---

# 🧠 Insight Utama Proyek

## 📌 Insight 1

> Tujuan penggunaan AI memiliki pengaruh yang lebih besar terhadap dampak akademik dibanding durasi penggunaan AI.

---

## 📌 Insight 2

Penggunaan AI untuk coding menunjukkan hubungan paling kuat terhadap peningkatan akademik.

---

## 📌 Insight 3

Durasi penggunaan AI saja tidak cukup untuk menjelaskan peningkatan performa akademik.

Cara penggunaan AI jauh lebih penting dibanding lamanya penggunaan.

---

## 📌 Insight 4

Tingkat kepuasan penggunaan AI ternyata tidak terlalu berpengaruh terhadap performa akademik dibanding tujuan penggunaan AI.

---

# 📚 Library yang Digunakan

```python
pandas
numpy
matplotlib
seaborn
scikit-learn
```

---

# 🚀 Pengembangan Selanjutnya

Beberapa pengembangan yang dapat dilakukan:

* Menambahkan jumlah data yang lebih besar
* Menggunakan model lain seperti Random Forest atau XGBoost
* Menambahkan analisis korelasi feature
* Melakukan hyperparameter tuning
* Deployment model menggunakan Streamlit atau Flask

---

# 👨‍💻 Author

Dibuat sebagai proyek portofolio Machine Learning dan Data Science.

## 📌 Apa yang Saya Pelajari dari Proyek Ini

Melalui proyek ini, saya mempelajari:

* Cara melakukan Exploratory Data Analysis (EDA) untuk mencari pola dan insight dari data
* Perbedaan data kategorikal nominal dan ordinal
* Teknik encoding seperti ordinal mapping dan one-hot encoding
* Cara membangun model multiclass classification menggunakan Logistic Regression
* Cara membaca confusion matrix, precision, recall, dan f1-score
* Pentingnya interpretasi model dibanding hanya berfokus pada accuracy
* Cara mencari feature importance untuk memahami faktor yang paling berpengaruh terhadap prediksi
* Bahwa dalam analisis perilaku manusia, durasi penggunaan tidak selalu menjadi faktor utama, tetapi tujuan penggunaan dapat memberikan pengaruh yang lebih besar

Selain itu, proyek ini juga membantu saya memahami bahwa proses Data Science bukan hanya tentang modeling, tetapi juga tentang memahami data, membangun hipotesis, dan menghasilkan insight yang relevan dari sebuah permasalahan.
