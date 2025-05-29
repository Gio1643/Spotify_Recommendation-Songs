# Laporan Proyek Machine Learning - Putu Gio Satria Adinata
![download](https://github.com/user-attachments/assets/16f091af-2693-447c-9ebb-158b2b7ca551)

## Project Overview
Layanan streaming musik seperti Spotify kini menjadi bagian tak terpisahkan dari kehidupan jutaan orang di seluruh dunia. Platform ini memberikan akses luas ke jutaan lagu dari berbagai genre dan artis, menghadirkan pengalaman mendengarkan musik yang bisa disesuaikan dengan preferensi tiap pengguna. Namun, dengan begitu banyaknya konten yang tersedia, tantangan terbesar Spotify adalah bagaimana menampilkan lagu-lagu yang benar-benar relevan dan menarik bagi setiap pengguna. Salah satu solusi yang digunakan adalah teknik segmentasi pengguna. Teknik ini memungkinkan Spotify mengenali selera musik individu, sehingga dapat menyajikan rekomendasi yang lebih tepat sasaran (Dharmasenaa & Pramarthaa, 2024).
Didukung oleh perkembangan smartphone dan perangkat musik digital, aktivitas mendengarkan musik semakin populer dari waktu ke waktu (Mastrika Giri & Harjoko, 2016; Putra & Irwansyah, 2019). Saat ini, musik digital tersedia dalam jumlah yang sangat besar secara daring. Dalam periode tiga bulan, tercatat sebanyak 17,6 miliar lagu dan lebih dari 662.000 jam waktu dengar digunakan oleh 5.808 pengguna Spotify. Aktivitas ini mencerminkan beragam preferensi individual—tidak hanya dalam hal jenis musik, tetapi juga waktu, lokasi, dan cara menikmati musik (Gatzioura et al., 2021; Giri et al., 2022; Volokhin & Agichtein, 2018). Per Februari 2025, Spotify mencatatkan 675 juta pengguna aktif bulanan di akhir tahun 2024, meningkat sebesar 12% dari tahun sebelumnya.
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
Pada proyek ini dataset yang digunakan adalah Spotify dataset: A Comprehensive Collection of Spotify Tracks Across Various Genres yang diupload oleh Gati Ambaliya. Datasetnya dapat dilihat pada tautan ini https://www.kaggle.com/datasets/ambaliyagati/spotify-dataset-for-playing-around-with-sql

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
1. **Penanganan Nilai Hilang (Handling Missing Value)**
- Nilai yang hilang atau *missing value* adalah salah satu permasalahan umum dalam proyek analisis data, terutama di dunia industri. Nilai yang hilang ini biasanya ditandai dengan *NaN* saat menggunakan pustaka seperti pandas. Penyebabnya bisa bermacam-macam, mulai dari kesalahan manusia, kendala privasi, hingga proses penggabungan data (*merging/join*).
- Langkah ini dilakukan agar data yang digunakan lebih akurat dan dapat diandalkan. Jika dibiarkan, nilai hilang dapat menimbulkan bias atau kesalahan pada hasil analisis. Oleh karena itu, proses identifikasi dan penanganan nilai yang hilang menjadi krusial untuk meningkatkan kualitas analisis dan model yang dibangun.
2. **Penanganan Data Duplikat (Handling Duplicated Data)**
- Data duplikat merupakan masalah lain yang sering ditemui, yaitu ketika satu baris data memiliki isi yang identik di seluruh kolom.
Langkah ini bertujuan menjaga keutuhan data dan mencegah distorsi dalam proses analisis. Data yang terduplikasi bisa menurunkan akurasi hasil analisis. Untuk mengatasi masalah ini, salah satu metode yang umum digunakan adalah menghapus baris-baris yang teridentifikasi sebagai duplikat (*dropping duplicates*).
3. **Rekayasa Fitur (Feature Engineering)**
- Rekayasa fitur adalah proses mengembangkan dan memilih atribut yang relevan agar dapat digunakan dalam analisis data atau dalam membangun model machine learning. Dalam proyek ini, rekayasa fitur dilakukan pada atribut genre. Beberapa entri memiliki lebih dari satu genre dalam satu data, sehingga perlu ditangani dengan memilih genre yang muncul pertama. Langkah ini bertujuan menyederhanakan proses pembangunan model serta meningkatkan performanya.

## Modeling
Pada proyek ini, algoritma machine learning yang diimplementasikan untuk sistem rekomendasi mencakup Content-Based Filtering dan Collaborative Filtering.
A. Content-Based Filtering adalah metode sistem rekomendasi yang menganalisis dan merekomendasikan item berdasarkan karakteristik atau konten intrinsik dari item tersebut. Pendekatan ini memanfaatkan atribut atau fitur-fitur spesifik dari setiap item untuk mengidentifikasi kesamaan antar item dan mencocokkannya dengan preferensi pengguna yang diketahui berdasarkan interaksi masa lalu dengan item serupa.

![download (1)](https://github.com/user-attachments/assets/9a65df00-d3cd-4fba-b73d-c21c54a0ae0a)


Kelebihan pendekatan ini, adalah sebagai berikut.
1. Mampu menghasilkan rekomendasi yang sangat personal karena secara langsung mempertimbangkan fitur item yang disukai pengguna.
2. Tidak bergantung pada data interaksi dari pengguna lain, sehingga efektif diimplementasikan meskipun data pengguna secara keseluruhan terbatas atau untuk merekomendasikan item baru yang belum banyak interaksi.

Kekurangan pendekatan ini, adalah sebagai berikut
1. Cenderung kurang mampu menyarankan item yang sangat berbeda (kurang serendipity) dari apa yang pernah disukai pengguna sebelumnya, karena terbatas pada kemiripan fitur.
2. Berpotensi mengalami overfitting jika model terlalu terpaku pada atribut atau fitur yang sangat spesifik dan tidak umum.

Implementasi pada Proyek Ini, diantaranya:
1. Vektorisasi Fitur dengan TF-IDF yang di mana data fitur item (misalnya, genre musik) yang telah dibersihkan dikonversi menjadi representasi vektor numerik menggunakan TfidfVectorizer dari pustaka scikit-learn. Langkah ini menghasilkan matriks TF-IDF yang merepresentasikan pentingnya setiap term (kata dalam genre) untuk setiap lagu.
2. Perhitungan Kemiripan Konten (Cosine Similarity) pada derajat kesamaan antar lagu dihitung berdasarkan vektor TF-IDF mereka menggunakan fungsi cosine_similarity. Hasilnya adalah matriks kemiripan yang menunjukkan seberapa mirip konten setiap pasang lagu.
3. Pembuatan fungsi rekomendasi yang dikembangkan untuk menghasilkan rekomendasi. Fungsi ini, memanfaatkan argpartition, mengambil lagu input, mencari skor kemiripan tertinggi dari matriks kemiripan (cosine_sim_df), dan mengembalikan k lagu teratas yang paling mirip, setelah menghilangkan lagu input dari daftar hasil.
