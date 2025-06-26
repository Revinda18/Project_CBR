# SISTEM CASE-BASED REASONING (CBR) UNTUK PREDIKSI PUTUSAN PERCERAIAN

Repositori ini berisi implementasi sistem *Case-Based Reasoning* (CBR) untuk mendukung pencarian dan prediksi amar putusan perceraian berdasarkan kasus-kasus terdahulu dari Direktori Putusan Mahkamah Agung Republik Indonesia.

Sistem ini terdiri dari lima tahap utama: pembangunan basis kasus, representasi kasus, pencarian kasus serupa, pemanfaatan solusi, dan evaluasi sistem.

## Struktur Direktori
PROJECT-CBR/
├── data/
│ ├── raw/ # File .txt hasil cleaning putusan
│ ├── processed/ # Representasi kasus akhir (.csv, .json)
│ ├── eval/ # Query uji, ground truth, dan evaluasi
│ └── results/ # Output hasil prediksi solusi CBR
├── logs/ # Log proses cleaning teks
├── Scraping_PA_Balikpapan.ipynb
├── Case_Retrieval.ipynb
├── Reuse_Evaluation.ipynb
├── README.md

## Instalasi

1. **Aktifkan virtual environment** (opsional namun disarankan):
   ```bash
   python -m venv venv
   source venv/bin/activate  # atau venv\Scripts\activate (Windows)
2. **Install Dependensi** 
   ```bash
   pip install -r requirements.txt

Isi requirements.txt:
pandas
numpy
scikit-learn
matplotlib
seaborn
transformers
torch

## Menjalankan Pipeline CBR
Pipeline terdiri dari 5 tahap dan dapat dijalankan melalui notebook berikut:

1. Scraping & Cleaning Teks
   📄 Scraping_PA_Balikpapan.ipynb
   - Mengambil data putusan dari MA
   - Membersihkan teks PDF → simpan ke .txt (data/raw/)
    Log disimpan di logs/cleaning.log
2. Representasi Kasus
   - Menambahkan fitur: ringkasan fakta, argumen hukum, BoW, QA-pair
   - Simpan ke cases.csv dan cases.json (data/processed/)
3. Case Retrieval
   📄 Case_Retrieval.ipynb
   Menggunakan:
   - TF-IDF Cosine Similarity
   - SVM-TF-IDF (LinearSVC)
   - IndoBERT Semantic Embedding
   Output: daftar case_id yang paling relevan
4. Case Reuse
   📄 Reuse_Evaluation.ipynb
   - Prediksi amar putusan dari 5 kasus terdekat
   - Metode: Majority Voting & Weighted Similarity
   - Output: predictions.csv di data/results/
5. Evaluasi Sistem
   - Evaluasi retrieval: precision@5, recall@5, f1@5, accuracy@5
   - Evaluasi reuse: akurasi terhadap ground truth
   - Visualisasi hasil → retrieval_barplot.png

## Penggunaan BERT
> Model IndoBERT digunakan untuk menghasilkan representasi semantik dari ringkasan fakta kasus. Implementasi lengkapnya terdapat pada file `Case_Retrieval.ipynb`.

## Ringkasan Evaluasi
### Hasil Evaluasi Retrieval

| Model        | Precision@5 | Recall@5 | F1@5  | Accuracy@5 |
|--------------|-------------|----------|-------|------------|
| TF-IDF       | 0.00        | 0.00     | 0.000 | 0.00       |
| SVM-TF-IDF   | 0.00        | 0.00     | 0.000 | 0.00       |
| IndoBERT     | 0.04        | 0.20     | 0.067 | 0.20       |

### Hasil Prediksi Solusi:

| Metode               | Akurasi     |  
|----------------------|-------------|
| Majority Voting      | 0.00        | 
| Weighted Similarity  | 0.00        | 



