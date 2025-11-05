# Analisis Klastering Destinasi Wisata di Bali

Sebuah proyek analisis data sederhana untuk mengelompokkan (clustering) destinasi wisata di Bali berdasarkan popularitas (jumlah review) dan kepuasan pengunjung (rating) menggunakan algoritma K-Means.

## 📌 Latar Belakang

Bali memiliki ratusan destinasi wisata. Proyek ini bertujuan untuk mengidentifikasi segmen-segmen berbeda dari tempat wisata tersebut. Dengan memahami pengelompokan ini, kita dapat memperoleh wawasan seperti:
* Destinasi mana yang merupakan "Hidden Gem" (rating tinggi, tapi belum terlalu populer)?
* Destinasi mana yang paling populer dan menjadi ikon?
* Destinasi mana yang mungkin memerlukan peningkatan layanan (rating/popularitas rendah)?

## 🗂️ Dataset

* **Sumber Data:** `Bali2022.csv`
* **Jumlah Entri:** 34 Destinasi Wisata
* **Fitur Utama yang Digunakan:**
    * `Google Maps Rating`: Rating rata-rata destinasi (numerik).
    * `Google Reviews (Count)`: Jumlah ulasan yang diterima (numerik).

## ⚙️ Metodologi Analisis

Alur kerja analisis data dalam proyek ini adalah sebagai berikut:

1.  **Pemuatan Data:** Memuat dataset `Bali2022.csv` menggunakan `pandas`.
2.  **Pembersihan Data:** Memeriksa nilai *null* dan data duplikat untuk memastikan kualitas data. (Pada analisis ini, data sudah bersih).
3.  **Pemilihan & Penskalaan Fitur:**
    * Memilih fitur `Google Maps Rating` dan `Google Reviews (Count)`.
    * Melakukan penskalaan (scaling) data menggunakan `StandardScaler` dari Scikit-learn agar kedua fitur memiliki bobot yang setara.
4.  **Modeling (K-Means Clustering):**
    * Menerapkan algoritma K-Means dengan jumlah klaster yang ditentukan, yaitu **k=3**.
    * Menyimpan hasil label klaster (0, 1, atau 2) kembali ke DataFrame utama.
5.  **Evaluasi Model:**
    * Menghitung **Silhouette Score** untuk menilai seberapa baik dan padat pengelompokan yang terbentuk.
6.  **Visualisasi & Interpretasi:**
    * Membuat *scatter plot* menggunakan `matplotlib` dan `seaborn` untuk memvisualisasikan klaster.
    * Menganalisis karakteristik rata-rata dari setiap klaster.

## 📊 Hasil dan Temuan

Model K-Means menghasilkan **Silhouette Score sebesar 0.4045**, yang menunjukkan struktur pengelompokan yang cukup baik.

Ke-34 destinasi wisata berhasil dikelompokkan ke dalam 3 segmen utama:

| Klaster | Interpretasi | Jml. Tempat | Rata-rata Rating | Rata-rata Review | Contoh Destinasi |
| :--- | :--- | :---: | :---: | :---: | :--- |
| **Cluster 1** | **Perlu Perhatian / Potensial** | 17 | 4.39 | 9,302 | Mount Batur, Goa Gajah, Tegenungan Waterfall, Bali Zoo |
| **Cluster 2** | **Rating Tinggi (Disukai)** | 15 | 4.63 | 15,630 | Uluwatu Temple, Ubud Monkey Forest, Kuta Beach, Waterboom Bali |
| **Cluster 3** | **Sangat Populer (Ikonik)** | 2 | 4.55 | 63,301 | Tanah Lot, Garuda Wisnu Kencana Cultural Park |

### 📈 Visualisasi Hasil Klaster

Grafik di bawah ini memetakan setiap destinasi berdasarkan Rating (sumbu x) dan Jumlah Review (sumbu y).

*(Anda dapat mengambil screenshot dari output notebook dan menambahkannya di sini)*
`![Visualisasi Klaster](gambar/hasil-klastering.png)`

## 🛠️ Teknologi & Library

Proyek ini dibuat menggunakan Python 3 dan library berikut:

* `pandas`: Untuk manipulasi dan analisis data.
* `numpy`: Untuk operasi numerik.
* `scikit-learn`: Untuk K-Means, StandardScaler, dan Silhouette Score.
* `matplotlib`: Untuk visualisasi data.
* `seaborn`: Untuk visualisasi data yang lebih menarik.

## 🚀 Cara Menjalankan Proyek

1.  **Clone repositori ini:**
    ```bash
    git clone [https://github.com/username-anda/nama-repositori-ini.git](https://github.com/username-anda/nama-repositori-ini.git)
    cd nama-repositori-ini
    ```

2.  **Install dependensi:**
    (Sangat disarankan untuk menggunakan *virtual environment*)
    ```bash
    pip install pandas numpy scikit-learn matplotlib seaborn jupyter
    ```

3.  **Pastikan data tersedia:**
    Letakkan file `Bali2022.csv` di direktori yang sama dengan notebook.

4.  **Jalankan Jupyter Notebook:**
    ```bash
    jupyter notebook "Analisis Klastering Destinasi Wisata di Bali.ipynb"
    ```
    Atau buka menggunakan [Google Colab](https://colab.research.google.com/) dan unggah file notebook serta CSV.
