# Laporan Proyek Machine Learning - Putu Gio Satria Adinata
![download](https://github.com/user-attachments/assets/16f091af-2693-447c-9ebb-158b2b7ca551)

## Project Overview
Layanan streaming musik seperti Spotify kini menjadi bagian tak terpisahkan dari kehidupan jutaan orang di seluruh dunia. Platform ini memberikan akses luas ke jutaan lagu dari berbagai genre dan artis, menghadirkan pengalaman mendengarkan musik yang bisa disesuaikan dengan preferensi tiap pengguna. Namun, dengan begitu banyaknya konten yang tersedia, tantangan terbesar Spotify adalah bagaimana menampilkan lagu-lagu yang benar-benar relevan dan menarik bagi setiap pengguna. Salah satu solusi yang digunakan adalah teknik segmentasi pengguna. Teknik ini memungkinkan Spotify mengenali selera musik individu, sehingga dapat menyajikan rekomendasi yang lebih tepat sasaran (Dharmasena & Pramarthaa, 2024).
Didukung oleh perkembangan smartphone dan perangkat musik digital, aktivitas mendengarkan musik semakin populer dari waktu ke waktu (Mastrika Giri & Harjoko, 2016; Putra & Irwansyah, 2019). Saat ini, musik digital tersedia dalam jumlah yang sangat besar secara daring. Dalam periode tiga bulan, tercatat sebanyak 17,6 miliar lagu dan lebih dari 662.000 jam waktu dengar digunakan oleh 5.808 pengguna Spotify. Aktivitas ini mencerminkan beragam preferensi individual—tidak hanya dalam hal jenis musik, tetapi juga waktu, lokasi, dan cara menikmati musik (Gatzioura et al., 2021). Per Februari 2025, Spotify mencatatkan 675 juta pengguna aktif bulanan di akhir tahun 2024, meningkat sebesar 12% dari tahun sebelumnya.
Banyak pengguna kini lebih memilih playlist otomatis dibandingkan membuat daftar putar sendiri. Meskipun Spotify telah menyediakan beragam playlist berdasarkan aktivitas atau suasana hati, sebagian besar masih bersifat umum dan belum sepenuhnya dipersonalisasi. Akibatnya, terdapat kemungkinan pengguna menemukan lagu yang kurang sesuai dengan selera mereka (Indraswara et al., 2020).

## Business Understanding
### Problem Statements
Rumusan masalah untuk proyek ini, yang didasarkan pada latar belakang yang telah dijelaskan adalah sebagai berikut:
1. Bagaimana cara membangun sistem rekomendasi musik yang mampu menyarankan lagu berdasarkan preferensi genre pengguna dengan memanfaatkan algoritma machine learning?
2. Bagaimana proses pengembangan model machine learning yang efektif untuk menghasilkan rekomendasi musik yang sesuai dengan genre pilihan pengguna?
3. Bagaimana kinerja dan hasil evaluasi dari model machine learning yang telah dibuat dalam memberikan rekomendasi musik tersebut?

### Goals
Merujuk pada rumusan masalah yang telah diidentifikasi, proyek machine learning ini memiliki tujuan-tujuan berikut:
1. Memahami dan mendemonstrasikan bagaimana algoritma machine learning dapat diterapkan secara efektif untuk menghasilkan rekomendasi musik yang spesifik berdasarkan genre.
2. Mendalami dan memaparkan keseluruhan tahapan yang terlibat dalam proses pengembangan model machine learning untuk sistem rekomendasi musik berbasis genre, mulai dari persiapan data hingga implementasi model.
3. Menganalisis dan menyajikan hasil evaluasi kinerja model machine learning yang telah berhasil dikembangkan dalam memberikan rekomendasi musik berdasarkan preferensi genre pengguna.

### Solution Statements
Merujuk pada rumusan masalah dan tujuan yang telah dijabarkan sebelumnya, solusi yang ditawarkan dalam proyek machine learning ini meliputi:
1. Mengembangkan model machine learning secara menyeluruh, dimulai dari tahap awal seperti pembersihan dan pengolahan data (data wrangling), analisis eksploratif (Exploratory Data Analysis atau EDA), pembangunan model (modelling), hingga tahap evaluasi.
2. Proses pembangunan model dilakukan dengan menerapkan dua pendekatan utama, yaitu content-based filtering (CBF) dan collaborative filtering (CF), yang dipilih sesuai dengan karakteristik permasalahan dan dataset yang tersedia.
3. Melakukan evaluasi terhadap kedua model menggunakan metrik evaluasi yang telah ditentukan, guna menilai performa masing-masing pendekatan dalam memberikan rekomendasi musik berdasarkan genre dan preferensi pengguna. Evaluasi ini bertujuan untuk menentukan metode rekomendasi yang paling efektif dalam meningkatkan relevansi dan personalisasi bagi pengguna.

## Data Understanding
Pada proyek ini dataset yang digunakan adalah Spotify dataset: A Comprehensive Collection of Spotify Tracks Across Various Genres yang diupload oleh Gati Ambaliya. Dataset ini memiliki 6187 rows dan 8 features. Datasetnya dapat dilihat pada tautan ini https://www.kaggle.com/datasets/ambaliyagati/spotify-dataset-for-playing-around-with-sql

### Variabel Dataset
Berikut adalah detail dari *features* dataset yang digunakan dalam pengembangan model *machine learning* proyek ini :
Tabel 1. Spotify dataset: A Comprehensive Collection of Spotify Tracks Across Various Genres
| Attribute | Description |
|---|---|
| id | Unique identifier for the track on Spotify. |
| name | Name of the track. |
| genre | genre of the song. |
| artists | Names of the artists who performed the track, separated by commas if there are multiple artists. |
| album | Name of the album the track belongs to. |
| popularity | Popularity score of the track (0-100, where higher is more popular). |
| duration_ms | Duration of the track in milliseconds. |
| explicit | Boolean indicating whether the track contains explicit content. |

## Data Preparation
Persiapan data merupakan tahapan penting dalam mengubah data mentah menjadi format yang siap untuk dianalisis atau digunakan dalam pemrosesan selanjutnya. Beberapa teknik yang diterapkan dalam proses ini antara lain:

### 1. **Penanganan Nilai Hilang (Handling Missing Value)**
Nilai yang hilang atau *missing value* adalah salah satu permasalahan umum dalam proyek analisis data, terutama di dunia industri. Nilai yang hilang ini biasanya ditandai dengan *NaN* saat menggunakan pustaka seperti pandas. Penyebabnya bisa bermacam-macam, mulai dari kesalahan manusia, kendala privasi, hingga proses penggabungan data (*merging/join*). Langkah ini dilakukan agar data yang digunakan lebih akurat dan dapat diandalkan. Jika dibiarkan, nilai hilang dapat menimbulkan bias atau kesalahan pada hasil analisis. Oleh karena itu, proses identifikasi dan penanganan nilai yang hilang menjadi krusial untuk meningkatkan kualitas analisis dan model yang dibangun.

### 2. **Penanganan Data Duplikat (Handling Duplicated Data)**
Data duplikat merupakan masalah lain yang sering ditemui, yaitu ketika satu baris data memiliki isi yang identik di seluruh kolom.
Langkah ini bertujuan menjaga keutuhan data dan mencegah distorsi dalam proses analisis. Data yang terduplikasi bisa menurunkan akurasi hasil analisis. Untuk mengatasi masalah ini, salah satu metode yang umum digunakan adalah menghapus baris-baris yang teridentifikasi sebagai duplikat (*dropping duplicates*).

### 3. **Content Based Filltering Preparation**
Tahap persiapan data untuk model Content-Based Filtering (CBF) difokuskan pada pengolahan fitur. Langkah fundamental dalam proses ini adalah transformasi fitur tekstual, seperti genre lagu menjadi representasi numerik yang dapat dianalisis oleh algoritma untuk menentukan kemiripan.
#### Inisialisasi Vectorizer
Pertama, sebuah instance dari TfidfVectorizer dibuat. Vectorizer ini nantinya akan mempelajari kosakata dari data genre dan menghitung bobot TF-IDF untuk setiap term (kata).
#### Pembelajaran (Fit) dan Transformasi
TfidfVectorizer kemudian "dilatih" (fit) pada seluruh data genre yang ada di kolom `df['genre']`. Selama proses fit, vectorizer mengidentifikasi semua term unik yang ada dan menghitung skor IDF (Inverse Document Frequency) untuk masing-masing term. Setelah itu, proses transform mengubah setiap teks genre menjadi sebuah vektor numerik, di mana setiap elemen vektor adalah skor TF-IDF dari term yang sesuai. Kedua langkah ini digabungkan dengan metode `fit_transform()`. Hasil dari langkah ini adalah tfidf_matrix, sebuah matriks sparse yang merepresentasikan semua lagu sebagai vektor TF-IDF dari genre mereka.
#### Verifikasi Dimensi Matriks
Untuk memahami struktur matriks yang dihasilkan, dimensinya diperiksa.
#### Konversi ke Matriks Padat (Dense Matrix) dan Pembuatan DataFrame (untuk Inspeksi)
Matriks ini diubah menjadi format dense (padat) di mana semua nilai (termasuk nol) disimpan secara eksplisit. Hasilnya kemudian dapat ditampilkan sebagai DataFrame pandas untuk kemudahan pembacaan, dengan nama lagu sebagai indeks dan term unik dari genre sebagai nama kolom.

### 4. **Collaborative Filltering Preparation**
Persiapan data untuk model Collaborative Filtering (CF), khususnya untuk pendekatan berbasis model neural network, melibatkan serangkaian transformasi agar data sesuai dengan format input yang dibutuhkan model dan untuk memastikan proses pelatihan yang efektif. Langkah-langkah utama yang dilakukan adalah sebagai berikut:
#### Pembuatan dan Pemetaan ID Numerik (ID Encoding)
Model machine learning, terutama embedding layers dalam jaringan saraf, memerlukan input berupa ID numerik untuk pengguna dan item. Oleh karena itu, nama artis (yang dalam proyek ini bertindak sebagai proxy untuk pengguna) dan nama lagu dikonversi menjadi ID integer unik. Pemetaan ini kemudian diterapkan pada DataFrame utama untuk membuat kolom baru (`user_encoded` dan `song_encoded`) yang berisi ID numerik untuk setiap artis dan lagu pada setiap baris. Jumlah total pengguna unik (`num_users`) dan lagu unik (`num_songs`) juga dihitung untuk digunakan dalam definisi model.
#### Penskalaan Fitur Target (Popularity Scaling)
Fitur `popularity`, yang akan digunakan sebagai target prediksi oleh model CF, memiliki rentang nilai asli (misalnya 0-100). Untuk membantu stabilitas dan konvergensi pelatihan model, terutama jika menggunakan fungsi aktivasi seperti sigmoid di layer output, fitur ini dinormalisasi ke rentang 0 hingga 1 menggunakan teknik Min-Max scaling.
#### Pengacakan Data (Shuffle)
Sebelum membagi data menjadi set pelatihan dan validasi, keseluruhan dataset diacak urutannya. Pengacakan ini penting untuk menghilangkan potensi bias akibat urutan asli data dan memastikan bahwa data latih dan validasi merupakan representasi yang baik dari distribusi data secara keseluruhan. Parameter `random_state` digunakan untuk menjamin reprodusibilitas hasil acakan.
#### Pembagian Dataset (Train-Validation Split)
Dataset yang telah diacak kemudian dibagi menjadi dua bagian: data pelatihan (train_data) dan data validasi (val_data). Data pelatihan digunakan untuk "mengajari" model, sementara data validasi digunakan untuk mengevaluasi performa model pada data yang belum pernah dilihat sebelumnya dan untuk memantau overfitting. Pembagian ini dilakukan dengan proporsi tertentu (misalnya, 80% untuk pelatihan dan 20% untuk validasi), dan random_state juga digunakan di sini untuk konsistensi.

## Modeling
Pada proyek ini, algoritma machine learning yang diimplementasikan untuk sistem rekomendasi mencakup Content-Based Filtering dan Collaborative Filtering.
**A. Content-Based Filtering**
Content-Based Filtering adalah metode sistem rekomendasi yang menganalisis dan merekomendasikan item berdasarkan karakteristik atau konten intrinsik dari item tersebut. Pendekatan ini memanfaatkan atribut atau fitur-fitur spesifik dari setiap item untuk mengidentifikasi kesamaan antar item dan mencocokkannya dengan preferensi pengguna yang diketahui berdasarkan interaksi masa lalu dengan item serupa.


![download (1)](https://github.com/user-attachments/assets/9a65df00-d3cd-4fba-b73d-c21c54a0ae0a)


Kelebihan pendekatan ini, adalah sebagai berikut.
1. Mampu menghasilkan rekomendasi yang sangat personal karena secara langsung mempertimbangkan fitur item yang disukai pengguna.
2. Tidak bergantung pada data interaksi dari pengguna lain, sehingga efektif diimplementasikan meskipun data pengguna secara keseluruhan terbatas atau untuk merekomendasikan item baru yang belum banyak interaksi.

Kekurangan pendekatan ini, adalah sebagai berikut
1. Cenderung kurang mampu menyarankan item yang sangat berbeda (kurang serendipity) dari apa yang pernah disukai pengguna sebelumnya, karena terbatas pada kemiripan fitur.
2. Berpotensi mengalami overfitting jika model terlalu terpaku pada atribut atau fitur yang sangat spesifik dan tidak umum.

Implementasi pada Proyek Ini, diantaranya:
1. Vektorisasi Fitur dengan TF-IDF yang di mana data fitur item (misalnya, genre musik) yang telah dibersihkan dikonversi menjadi representasi vektor numerik menggunakan TfidfVectorizer dari pustaka scikit-learn. Langkah ini menghasilkan matriks TF-IDF yang merepresentasikan pentingnya setiap term (kata dalam genre) untuk setiap lagu.
2. Perhitungan Kemiripan Konten (Cosine Similarity) pada derajat kesamaan antar lagu dihitung berdasarkan vektor TF-IDF mereka menggunakan fungsi `cosine_similarity`. Hasilnya adalah matriks kemiripan yang menunjukkan seberapa mirip konten setiap pasang lagu.
3. Pembuatan fungsi rekomendasi yang dikembangkan untuk menghasilkan rekomendasi. Fungsi ini, memanfaatkan argpartition, mengambil lagu input, mencari skor kemiripan tertinggi dari matriks kemiripan (cosine_sim_df), dan mengembalikan k lagu teratas yang paling mirip, setelah menghilangkan lagu input dari daftar hasil.

**Hasil**
Tahapan pengembangan model machine learning rekomendasi musik atau lagu telah berhasil dibuat. Tahap selanjutnya yaitu melihat bagaimana hasil dari rekomendasi musik atau lagu yang dibuat. Dalam kasus ini, akan dicari lagu yang mirip dengan lagu dari John Denver dengan judul Rocky Mountain High yang bergenre Rock.

Tabel 2. Hasil Pengujian Melalui Pendekatan CBF
|    | song              | genre |
|----|-------------------|-------|
| 0  | hikikomori rock | j-rock |
| 1  | Jibun ROCK | j-rock |
| 2  | Fallin' In Love | j-rock |
| 3  | Ceria | j-rock |
| 4  | Prove - Japanese Version | j-rock |

**B. Collaborative Filtering (CF)**
Collaborative Filtering adalah metode sistem rekomendasi yang memberikan saran berdasarkan pola perilaku dan preferensi kolektif dari sekelompok besar pengguna. Ide dasarnya adalah jika pengguna A memiliki selera yang mirip dengan pengguna B, maka item yang disukai pengguna B (dan belum diketahui pengguna A) kemungkinan besar juga akan disukai oleh pengguna A. Pendekatan ini tidak memerlukan pemahaman tentang konten item itu sendiri, melainkan fokus pada riwayat interaksi pengguna-item (misalnya, rating, riwayat dengar, pembelian).

![download](https://github.com/user-attachments/assets/ff66965b-8a7a-4d82-ac5f-a29b98c0593e)

Kelebihan:
1. Mampu menghasilkan rekomendasi yang mengejutkan (serendipitous) dan menemukan item lintas genre atau kategori yang mungkin tidak teridentifikasi oleh CBF.
2. Tidak memerlukan analisis fitur item secara manual (domain knowledge tidak selalu esensial untuk item), karena bergantung pada data interaksi.
3. Dapat menangkap preferensi pengguna yang kompleks dan implisit yang sulit diwakili oleh atribut konten.

Kekurangan:
1. Mengalami masalah cold start, yaitu kesulitan memberikan rekomendasi untuk pengguna baru (yang belum memiliki riwayat interaksi) atau untuk item baru (yang belum mendapatkan interaksi).
2. Rentan terhadap data sparsity, di mana matriks interaksi pengguna-item sangat kosong karena pengguna hanya berinteraksi dengan sebagian kecil dari total item yang tersedia.
3. Bisa memiliki popularity bias, yaitu cenderung merekomendasikan item-item yang sudah populer.
Skalabilitas bisa menjadi tantangan pada dataset dengan jumlah pengguna dan item yang sangat besar, terutama untuk pendekatan berbasis memori.

**Implementasi pada Proyek Ini (RecommenderNet):**
Tahapan pemodelan menggunakan Collaborative Filtering (berbasis model) dalam proyek ini adalah sebagai berikut:
1. Persiapan Data Interaksi
   - Membuat pemetaan ID numerik untuk pengguna (atau proxy pengguna seperti artis) dan item (lagu).
   - Menyusun dataset yang berisi pasangan ID pengguna dan ID lagu, beserta target interaksi (misalnya, skor popularitas yang dinormalisasi sebagai representasi implisit preferensi).
   - Membagi dataset menjadi data pelatihan dan data validasi.
2. Definisi dan Pelatihan Model
   - Membangun model machine learning (misalnya, jaringan saraf seperti RecommenderNet yang telah dibahas) yang menggunakan embedding layers untuk mempelajari representasi vektor laten (fitur tersembunyi) bagi setiap pengguna dan item.
   - Model ini dilatih untuk memprediksi skor interaksi (misalnya, popularitas yang diskalakan) berdasarkan vektor laten pengguna dan item, seringkali menggunakan operasi dot product dan bias.
   - Model dikompilasi dengan loss function (BinaryCrossentropy) dan optimizer (Adam), kemudian dilatih menggunakan data interaksi.
3. Pembuatan Fungsi Rekomendasi
   - Untuk seorang pengguna (artis input), model digunakan untuk memprediksi skor preferensi terhadap semua lagu yang belum pernah berinteraksi dengannya. Lagu-lagu tersebut kemudian diurutkan berdasarkan skor prediksi tertinggi, dan k lagu teratas dikembalikan sebagai rekomendasi.

**Hasil**


![topn-1](https://github.com/user-attachments/assets/ee0eff4d-9ef1-4a63-9f40-6e22a5e06ae0)

![topnew2](https://github.com/user-attachments/assets/a885bcf2-ff3f-4caa-b19f-6c85e74a59fb)

## Evaluation
Proyek machine learning ini dikembangkan dengan menggunakan algoritma Content-Based Filtering dan Collaborative Filtering (berbasis model prediktif). Oleh karena itu, metrik evaluasi yang digunakan akan mencerminkan performa dari kedua jenis pendekatan tersebut.
1. Evaluasi untuk Content-Based Filtering (CBF)
Untuk CBF, di mana rekomendasi didasarkan pada kemiripan konten item, salah satu metrik yang relevan adalah Precision. Precision mengukur seberapa banyak item yang direkomendasikan benar-benar relevan bagi pengguna atau item input, berdasarkan suatu ground truth (kebenaran dasar) yang telah ditentukan.

![cbfevaluation](https://github.com/user-attachments/assets/524554ca-c955-4b10-a705-aa7f69cd37ca)

Hasil ini menunjukkan bahwa untuk kasus uji tersebut, semua rekomendasi dari CBF dianggap sangat relevan. Selain Precision, analisis kualitatif terhadap keragaman (diversity) dan kebaruan (novelty) rekomendasi CBF juga bisa memberikan wawasan tambahan.

2. Evaluasi untuk Collaborative Filtering (CF) dengan Model Prediktif (RecommenderNet)
Untuk pendekatan CF yang menggunakan model prediktif seperti RecommenderNet (yang dilatih untuk memprediksi skor popularity_scaled), metrik evaluasi utama berfokus pada seberapa akurat prediksi skor tersebut. Metrik yang umum digunakan adalah RMSE.

![evaluationcf](https://github.com/user-attachments/assets/14ca56e4-0433-4223-8381-fb448adc7b07)

Kesimpulan:
1. Model Belajar dengan Baik pada Data Pelatihan, dimana penurunan nilai loss dan RMSE pada set pelatihan menunjukkan bahwa model berhasil mempelajari pola-pola yang ada dalam data pelatihan.
2. Overfitting Terjadi, dimana perbedaan yang signifikan dan meningkat antara kinerja pada data pelatihan dan data validasi (di mana kinerja pada data pelatihan terus membaik sementara pada data validasi stagnan atau memburuk) adalah gejala klasik dari overfitting. Ini berarti model Anda mulai "menghafal" data pelatihan, termasuk noise di dalamnya, daripada mempelajari pola umum yang bisa digeneralisasi ke data baru. Akibatnya, performa model pada data yang belum pernah dilihat (data validasi) tidak sebaik performanya pada data pelatihan.
3. Epoch Optimal, dimana titik di mana kurva validasi mulai stagnan atau naik (sekitar epoch 5-15 dalam kasus ini) bisa dianggap sebagai perkiraan jumlah epoch optimal untuk pelatihan sebelum overfitting menjadi terlalu parah. Melatih lebih lama dari titik ini mungkin tidak meningkatkan kemampuan generalisasi model.

## References

Dharmasena, K. B., & Pramartha, C. (2018). Integration K-Means Clustering Method and Elbow Method For Identification of The Best Customer Profile Cluster. IOP Conference Series: Materials Science and Engineering, 336, 012017. https://doi.org/10.1088/1757-899X/336/1/012017
Gatzioura, A., Vinagre, J., Jorge, A. M., & Sanchez-Marre, M. (2021). A Hybrid Recommender System for Improving Automatic Playlist Continuation. IEEE Transactions on Knowledge and Data Engineering, 33(5). https://doi.org/10.1109/TKDE.2019.2952099
Indraswara, R., Brata, K. C., & Herlambang, A. D. (2020). Analisis Pembelian Fitur Premium Pada Pengguna Aplikasi Spotify Menggunakan Variabel Hedonic Motivation System. Program Studi Sistem Informasi, Fakultas Ilmu Komputer, Universitas Brawijaya, 4(1).
Mastrika Giri, G. A. V., & Harjoko, A. (2016). Music recommendation system based on context using case-based reasoning and self organizing map. Indonesian Journal of Electrical Engineering and Computer Science, 4(2). https://doi.org/10.11591/ijeecs.v4.i2.pp459-464
Putra, R. M., & Irwansyah, I. (2019). Musik Rilisan Fisik Di Era Digital: Musik Indie Dan Konsumsi Rilisan Musik Fisik. Jurnal Komunikasi, 11(2). https://doi.org/10.24912/jk.v11i2.4062
