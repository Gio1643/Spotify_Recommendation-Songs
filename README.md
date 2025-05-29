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

**Rubrik/Kriteria Tambahan**:
### Solution Statements
Merujuk pada rumusan masalah dan tujuan yang telah dijabarkan sebelumnya, solusi yang ditawarkan dalam proyek machine learning ini meliputi:
1. Mengembangkan model machine learning secara menyeluruh, dimulai dari tahap awal seperti pembersihan dan pengolahan data (data wrangling), analisis eksploratif (Exploratory Data Analysis atau EDA), pembangunan model (modelling), hingga tahap evaluasi.
2. Proses pembangunan model dilakukan dengan menerapkan dua pendekatan utama, yaitu content-based filtering (CBF) dan collaborative filtering (CF), yang dipilih sesuai dengan karakteristik permasalahan dan dataset yang tersedia.
3. Melakukan evaluasi terhadap kedua model menggunakan metrik evaluasi yang telah ditentukan, guna menilai performa masing-masing pendekatan dalam memberikan rekomendasi musik berdasarkan genre dan preferensi pengguna. Evaluasi ini bertujuan untuk menentukan metode rekomendasi yang paling efektif dalam meningkatkan relevansi dan personalisasi bagi pengguna.
