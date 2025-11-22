# 🩺 Projek Klasifikasi Diabetes

Aplikasi web interaktif untuk prediksi diabetes menggunakan Machine Learning dengan algoritma Random Forest.

## 📋 Daftar Isi

- [Tentang Proyek](#tentang-proyek)
- [Dataset](#dataset)
- [Model Machine Learning](#model-machine-learning)
- [Fitur](#fitur)
- [Instalasi](#instalasi)
- [Cara Penggunaan](#cara-penggunaan)
- [Struktur Proyek](#struktur-proyek)
- [Teknologi yang Digunakan](#teknologi-yang-digunakan)
- [Hasil Evaluasi Model](#hasil-evaluasi-model)
- [Kontribusi](#kontribusi)

## 🎯 Tentang Proyek

Proyek ini adalah aplikasi klasifikasi diabetes yang menggunakan teknik Machine Learning untuk memprediksi apakah seseorang terdiagnosis diabetes atau tidak berdasarkan beberapa parameter medis. Aplikasi ini dibangun dengan menggunakan Streamlit untuk antarmuka web yang interaktif dan mudah digunakan.

### Tujuan

- Membantu dalam deteksi dini diabetes
- Menyediakan tool prediksi yang mudah digunakan
- Menerapkan machine learning dalam bidang kesehatan

## 📊 Dataset

Dataset yang digunakan adalah **Pima Indians Diabetes Database** yang berisi data medis dari 768 pasien wanita.

### Fitur Dataset

Dataset terdiri dari 8 fitur input dan 1 target variable:

| Fitur | Deskripsi | Tipe Data |
|-------|-----------|-----------|
| **Pregnancies** | Jumlah kehamilan | Integer |
| **Glucose** | Konsentrasi glukosa plasma (mg/dL) | Integer |
| **BloodPressure** | Tekanan darah diastolik (mm Hg) | Integer |
| **SkinThickness** | Ketebalan lipatan kulit trisep (mm) | Integer |
| **Insulin** | Insulin serum 2 jam (mu U/ml) | Integer |
| **BMI** | Body Mass Index (kg/m²) | Float |
| **DiabetesPedigreeFunction** | Fungsi silsilah diabetes | Float |
| **Age** | Usia (tahun) | Integer |
| **Outcome** | Target (0 = Tidak Diabetes, 1 = Diabetes) | Integer |

### Statistik Dataset

- **Total Data:** 768 sampel
- **Fitur:** 9 kolom (8 fitur + 1 target)
- **Tidak ada missing values**
- **Distribusi Target:**
  - Tidak Diabetes (0): ~65%
  - Diabetes (1): ~35%

## 🤖 Model Machine Learning

### Algoritma yang Digunakan

Proyek ini mengimplementasikan beberapa algoritma machine learning:

1. **Decision Tree Classifier**
   - Criterion: Entropy
   - Max Depth: 5
   - Max Features: sqrt
   
2. **Random Forest Classifier** (Model Utama)
   - N Estimators: 200
   - Max Depth: 10
   - Bootstrap: True
   - Random State: 42

### Proses Training

1. **Preprocessing:**
   - Handling missing values (nilai 0 pada fitur tertentu)
   - Feature scaling menggunakan StandardScaler
   - Feature selection menggunakan SelectKBest

2. **Split Data:**
   - Training Set: 568 sampel
   - Testing Set: 200 sampel

3. **Hyperparameter Tuning:**
   - Grid Search untuk menemukan parameter terbaik
   - Cross-validation dengan 5 folds

### Feature Importance

Berdasarkan analisis Random Forest, urutan pentingnya fitur:

1. Insulin (33.95%)
2. Glucose (16.35%)
3. SkinThickness (14.61%)
4. BMI (8.43%)
5. Pregnancies (7.96%)
6. Age (7.31%)
7. DiabetesPedigreeFunction (6.38%)
8. BloodPressure (5.00%)

## ✨ Fitur

### Fitur Aplikasi Web

- ✅ **Interface User-Friendly:** Antarmuka yang intuitif dan mudah digunakan
- ✅ **Input Interaktif:** Form input untuk memasukkan data medis
- ✅ **Real-time Prediction:** Prediksi instan setelah input data
- ✅ **Session State Management:** Menyimpan input pengguna
- ✅ **Reset Function:** Tombol reset untuk menghapus semua input
- ✅ **Error Handling:** Validasi input dan penanganan error
- ✅ **Support Format Input:** Mendukung format angka dengan koma atau titik

### Fitur Teknis

- Model persistence menggunakan pickle
- Responsive design dengan Streamlit columns
- Validasi input numerik
- Feedback visual (success/error messages)

## 🚀 Instalasi

### Prasyarat

- Python 3.7 atau lebih tinggi
- pip (Python package manager)

### Langkah Instalasi

1. **Clone repository:**
```bash
git clone https://github.com/zickrian/Projek-Klasifikasi-Diabetes.git
cd Projek-Klasifikasi-Diabetes
```

2. **Buat virtual environment (opsional tapi disarankan):**
```bash
python -m venv venv
source venv/bin/activate  # Untuk Linux/Mac
# atau
venv\Scripts\activate  # Untuk Windows
```

3. **Install dependencies:**
```bash
pip install -r requirements.txt
```

### Dependencies

Package yang dibutuhkan:
- pandas==2.2.3
- streamlit
- scikit-learn
- setuptools

## 💻 Cara Penggunaan

### Menjalankan Aplikasi Web

1. **Pastikan model sudah ada:**
   - File `random_forest_model.pkl` harus ada di direktori utama
   - Jika belum ada, jalankan notebook `Diabetes(PembelajaranMesin).ipynb` terlebih dahulu

2. **Jalankan aplikasi Streamlit:**
```bash
streamlit run Stream_diabetes.py
```

3. **Akses aplikasi:**
   - Aplikasi akan terbuka secara otomatis di browser
   - Atau akses manual di: `http://localhost:8501`

### Menggunakan Aplikasi

1. **Input Data:**
   - Masukkan nilai untuk semua 8 parameter medis
   - Gunakan format angka yang valid (titik atau koma sebagai desimal)

2. **Test Diabetes:**
   - Klik tombol "🧪Test Diabetes"
   - Hasil prediksi akan ditampilkan:
     - ✅ Hijau: Tidak terdiagnosis diabetes
     - ⚠️ Merah: Terdiagnosis diabetes

3. **Reset:**
   - Klik tombol "🔄Reset" untuk menghapus semua input dan mulai dari awal

### Contoh Input

```
Pregnancies: 6
Glucose: 148
Blood Pressure: 72
Skin Thickness: 35
Insulin: 0
BMI: 33.6
Diabetes Pedigree Function: 0.627
Age: 50
```

### Training Model Baru

Jika ingin melatih ulang model:

1. **Buka Jupyter Notebook:**
```bash
jupyter notebook Diabetes(PembelajaranMesin).ipynb
```

2. **Jalankan semua cell** untuk:
   - Load dan eksplorasi data
   - Preprocessing dan feature engineering
   - Training model
   - Evaluasi model
   - Save model ke file `.pkl`

## 📁 Struktur Proyek

```
Projek-Klasifikasi-Diabetes/
│
├── Stream_diabetes.py              # Aplikasi web Streamlit
├── Diabetes(PembelajaranMesin).ipynb  # Notebook training model
├── random_forest_model.pkl         # Model terlatih (pickle)
├── diabetes.csv                    # Dataset asli
├── diabetes_updated.csv            # Dataset yang sudah diproses
├── requirements.txt                # Dependencies Python
└── README.md                       # Dokumentasi (file ini)
```

### Deskripsi File

- **Stream_diabetes.py:** Aplikasi web utama menggunakan Streamlit untuk prediksi diabetes
- **Diabetes(PembelajaranMesin).ipynb:** Notebook Jupyter berisi proses lengkap machine learning
- **random_forest_model.pkl:** Model Random Forest yang sudah dilatih dan disimpan
- **diabetes.csv:** Dataset Pima Indians Diabetes Database
- **diabetes_updated.csv:** Dataset setelah preprocessing
- **requirements.txt:** Daftar package Python yang dibutuhkan

## 🛠️ Teknologi yang Digunakan

### Libraries & Frameworks

- **Streamlit:** Framework untuk membuat web app interaktif
- **Scikit-learn:** Library machine learning untuk training dan prediksi
- **Pandas:** Manipulasi dan analisis data
- **NumPy:** Komputasi numerik
- **Seaborn & Matplotlib:** Visualisasi data
- **Pickle:** Serialisasi model

### Machine Learning Tools

- **StandardScaler:** Normalisasi fitur
- **SelectKBest:** Feature selection
- **GridSearchCV:** Hyperparameter tuning
- **RandomForestClassifier:** Model klasifikasi utama
- **DecisionTreeClassifier:** Model alternatif

## 📈 Hasil Evaluasi Model

### Performa Random Forest Classifier

#### Akurasi
- **Training Accuracy:** 100% (1.0)
- **Testing Accuracy:** 90.5% (0.905)
- **Best CV Score:** 91.0% (Grid Search)

#### Classification Report (Test Set)

```
              precision    recall  f1-score   support

           0       0.92      0.89      0.90       100
           1       0.89      0.92      0.91       100

    accuracy                           0.91       200
   macro avg       0.91      0.91      0.90       200
weighted avg       0.91      0.91      0.90       200
```

#### Confusion Matrix

- **True Negative:** 89 (prediksi benar tidak diabetes)
- **False Positive:** 11 (prediksi salah diabetes)
- **False Negative:** 8 (prediksi salah tidak diabetes)
- **True Positive:** 92 (prediksi benar diabetes)

### Metrik Evaluasi

- **Precision (Class 1):** 89% - Dari semua prediksi diabetes, 89% benar
- **Recall (Class 1):** 92% - Dari semua kasus diabetes, 92% terdeteksi
- **F1-Score:** 0.91 - Keseimbangan antara precision dan recall
- **ROC-AUC:** Model menunjukkan performa yang sangat baik

### Best Hyperparameters (Grid Search)

```python
{
    'bootstrap': True,
    'max_depth': None,
    'max_features': 'sqrt',
    'min_samples_leaf': 1,
    'min_samples_split': 2,
    'n_estimators': 100  # Hasil Grid Search
}
```

**Catatan:** Dalam implementasi final aplikasi web (Stream_diabetes.py), model menggunakan `n_estimators=200` dan `max_depth=10` untuk meningkatkan performa.

## 🤝 Kontribusi

Kontribusi sangat diterima! Jika Anda ingin berkontribusi:

1. Fork repository ini
2. Buat branch fitur baru (`git checkout -b feature/AmazingFeature`)
3. Commit perubahan (`git commit -m 'Add some AmazingFeature'`)
4. Push ke branch (`git push origin feature/AmazingFeature`)
5. Buat Pull Request

### Area Pengembangan

- [ ] Implementasi model deep learning
- [ ] Tambahkan visualisasi hasil prediksi
- [ ] Deploy ke cloud platform (Heroku, Streamlit Cloud)
- [ ] Tambahkan fitur interpretability (SHAP, LIME)
- [ ] Implementasi API REST
- [ ] Tambahkan multiple model comparison
- [ ] Improve UI/UX design

## 📝 Lisensi

Proyek ini dibuat untuk tujuan pembelajaran dan penelitian.

## 👤 Author

**Zickrian**

- GitHub: [@zickrian](https://github.com/zickrian)

## 🙏 Acknowledgments

- Dataset: Pima Indians Diabetes Database
- Framework: Streamlit Team
- Machine Learning: Scikit-learn Contributors

---

## 📞 Kontak & Support

Jika Anda memiliki pertanyaan atau membutuhkan bantuan:

- Buat issue di GitHub repository
- Hubungi melalui GitHub profile

---

**⚠️ Disclaimer:**
Aplikasi ini dibuat untuk tujuan pembelajaran dan demonstrasi. Hasil prediksi tidak dapat menggantikan diagnosis medis profesional. Selalu konsultasikan dengan tenaga medis yang berkualifikasi untuk diagnosis dan perawatan yang tepat.

---

*Terakhir diperbarui: 2025*
