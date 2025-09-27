# Laporan Praktikum Kecerdasan Buatan  
## Local Search  

**11S23024**  
**Glen Rejeki Sitorus**  

S1 Informatika  
Fakultas Informatika dan Teknik Elektro  
TA 2025/2026  

---

## 1. Pendahuluan  
Praktikum ini bertujuan untuk memahami konsep algoritma Local Search dalam penyelesaian masalah optimasi. Dua algoritma utama yang dipelajari adalah **Hill-Climbing Search** dan **Simulated Annealing**. Selain itu, dilakukan pula percobaan dengan algoritma tambahan **Random-Restart Hill-Climbing** untuk meningkatkan peluang menemukan solusi optimal.  

Studi kasus yang digunakan adalah **8-Queens Problem**, yaitu menempatkan 8 ratu pada papan catur sehingga tidak ada dua ratu yang saling menyerang.  

---

## 2. Dasar Teori  
- **Local Search** adalah algoritma pencarian yang hanya menyimpan satu state (keadaan) dan memperbaikinya secara iteratif.  
- **Hill-Climbing** adalah metode *greedy* yang selalu memilih tetangga terbaik, sehingga cepat tetapi rentan terjebak di *local optimum*.  
- **Simulated Annealing** terinspirasi dari pendinginan logam, memperbolehkan langkah ke solusi lebih buruk dengan probabilitas tertentu untuk menghindari jebakan *local optimum*.  
- **Random-Restart Hill-Climbing** menjalankan Hill-Climbing berkali-kali dari state acak yang berbeda untuk meningkatkan peluang menemukan solusi global.  

---

## 3. Implementasi  
Implementasi menggunakan bahasa **Python** dengan library standar `random` dan `math`. Program terdiri dari tiga algoritma utama:  
1. Hill-Climbing  
2. Simulated Annealing  
3. Random-Restart Hill-Climbing  

Kode lengkap terdapat pada file `local_search.py`.  

---

## 4. Percobaan  

### 4.1 Hill-Climbing  
| No | Initial Board | H awal | Final Board | H akhir | Status |
|----|---------------|--------|-------------|---------|--------|
| 1 | [6, 2, 6, 1, 3, 2, 0, 7] | 4 | [5, 2, 6, 1, 3, 4, 0, 7] | 1 | Terjebak di local minimum |
| 2 | [2, 7, 1, 2, 6, 0, 4, 6] | 8 | [2, 7, 1, 3, 5, 0, 4, 6] | 1 | Terjebak di local minimum |
| 3 | [3, 0, 3, 5, 7, 0, 5, 4] | 9 | [3, 0, 7, 5, 2, 0, 6, 4] | 1 | Terjebak di local minimum |
| 4 | [3, 0, 3, 5, 7, 0, 5, 4] | 9 | [3, 0, 7, 5, 2, 0, 6, 4] | 1 | Terjebak di local minimum |
| 5 | [3, 0, 3, 5, 7, 0, 5, 4] | 9 | [3, 0, 7, 5, 2, 0, 6, 4] | 1 | Terjebak di local minimum |
| 6 | [4, 5, 2, 1, 3, 0, 4, 1] | 7 | [1, 5, 2, 6, 3, 0, 4, 1] | 1 | Terjebak di local minimum |

### 4.2 Simulated Annealing  
| No | Initial Board | H awal | Iterasi | Final Board | H akhir | Status |
|----|---------------|--------|---------|-------------|---------|--------|
| 1 | [1, 7, 7, 7, 7, 5, 6, 3] | 10 | 1800 | [1, 7, 4, 1, 7, 0, 3, 6] | 2 | Tidak solusi |
| 2 | [5, 2, 3, 6, 2, 3, 5, 7] | 6 | 1641 | [2, 6, 1, 7, 4, 0, 3, 5] | 0 | Solusi |
| 3 | [0, 4, 0, 7, 5, 2, 1, 7] | 4 | 1739 | [6, 0, 2, 7, 5, 3, 1, 4] | 0 | Solusi |
| 4 | [0, 4, 0, 7, 5, 2, 1, 7] | 4 | 1739 | [6, 0, 2, 7, 5, 3, 1, 4] | 0 | Solusi |
| 5 | [0, 4, 0, 7, 5, 2, 1, 7] | 4 | 1739 | [6, 0, 2, 7, 5, 3, 1, 4] | 0 | Solusi |
| 6 | [2, 6, 4, 1, 4, 6, 1, 4] | 8 | 1800 | [3, 0, 2, 5, 1, 6, 4, 7] | 1 | Tidak solusi |

### 4.3 Random-Restart Hill-Climbing  
| No | Algoritma | Initial Board | H awal | Final Board | H akhir | Status |
|----|-----------|---------------|--------|-------------|---------|--------|
| 1 | Hill-Climbing | [1, 0, 7, 2, 4, 7, 0, 1] | 7 | [1, 5, 7, 2, 4, 7, 0, 3] | 2 | Local minimum (tidak solusi) |
|   | Simulated Annealing | [3, 5, 6, 5, 7, 2, 5, 1] | 9 | [3, 7, 0, 2, 5, 1, 6, 4] | 0 | Solusi ditemukan |
| 2 | Hill-Climbing | [5, 3, 3, 6, 2, 1, 0, 2] | 7 | [7, 3, 0, 6, 4, 1, 5, 2] | 1 | Local minimum |
|   | Simulated Annealing | [0, 5, 6, 0, 0, 1, 7, 3] | 8 | [0, 4, 7, 5, 2, 6, 1, 3] | 0 | Solusi ditemukan |
| 3 | Hill-Climbing | [6, 6, 5, 2, 6, 7, 5, 1] | 7 | [6, 1, 5, 2, 0, 7, 3, 1] | 1 | Local minimum |
|   | Simulated Annealing | [1, 4, 1, 0, 0, 1, 0, 2] | 9 | [2, 4, 1, 7, 5, 3, 6, 0] | 0 | Solusi ditemukan |
| 4 | Hill-Climbing | [0, 5, 6, 6, 3, 3, 7, 1] | 6 | [2, 5, 2, 6, 3, 0, 7, 1] | 1 | Local minimum |
|   | Simulated Annealing | [0, 7, 7, 5, 7, 2, 2, 0] | 9 | [4, 6, 1, 5, 2, 0, 7, 3] | 0 | Solusi ditemukan |
| 5 | Hill-Climbing | [5, 3, 1, 2, 6, 4, 4, 0] | 7 | [5, 7, 1, 3, 6, 2, 4, 0] | 2 | Local minimum |
|   | Simulated Annealing | [3, 7, 6, 3, 7, 1, 5, 7] | 9 | [7, 3, 0, 2, 5, 1, 6, 4] | 0 | Solusi ditemukan |
| 6 | Hill-Climbing | [2, 5, 6, 1, 2, 4, 5, 5] | 10 | [2, 4, 6, 1, 7, 5, 3, 0] | 1 | Local minimum |
|   | Simulated Annealing | [2, 7, 7, 2, 4, 6, 2, 2] | 11 | [5, 3, 1, 7, 4, 6, 0, 2] | 0 | Solusi ditemukan |

---

## 5. Analisis  
Berdasarkan hasil percobaan pada Tabel 4.1 hingga 4.3, dapat dilihat bahwa algoritma Hill-Climbing memiliki keterbatasan dalam menyelesaikan permasalahan 8-Queens. Hampir di semua percobaan, Hill-Climbing hanya mampu menurunkan konflik hingga titik tertentu, tetapi akhirnya terjebak pada *local minimum* dengan nilai konflik (h) tersisa antara 1–2. Hal ini terjadi karena Hill-Climbing hanya bergerak menuju tetangga yang lebih baik tanpa mekanisme untuk keluar dari kondisi buntu. Dengan demikian, meskipun sederhana dan cepat, Hill-Climbing tidak dapat diandalkan untuk menemukan solusi optimal pada permasalahan kompleks yang memiliki banyak jebakan *local optimum*.  

Sebaliknya, pada Tabel 4.2 dan 4.3, algoritma Simulated Annealing menunjukkan performa yang jauh lebih baik. Dengan mekanisme probabilistiknya, algoritma ini dapat menerima solusi yang lebih buruk pada tahap awal untuk kemudian memperbaikinya saat suhu menurun, sehingga mampu keluar dari jebakan *local minimum*. Hasil percobaan menunjukkan bahwa Simulated Annealing berhasil menemukan solusi global (h=0) pada sebagian besar percobaan, bahkan pada kasus yang cukup sulit. Perbandingan ini menegaskan bahwa Simulated Annealing lebih efektif dan andal dibandingkan Hill-Climbing dalam menyelesaikan permasalahan 8-Queens, karena mampu menjelajahi ruang solusi lebih luas dan tidak mudah terjebak dalam solusi parsial.  

---

## 6. Kesimpulan  
Berdasarkan hasil percobaan yang dituangkan dalam tabel 4.1 hingga 4.3, terlihat bahwa algoritma Hill-Climbing memang mampu melakukan pencarian solusi dengan cepat, namun sering kali terjebak pada *local minimum*. Hal ini ditunjukkan dari hasil akhir yang umumnya berhenti pada nilai konflik (h = 1) atau (h = 2) tanpa mampu mencapai solusi optimal. Mekanisme pencarian tetangga terbaik yang deterministik membuat Hill-Climbing tidak memiliki fleksibilitas untuk keluar dari kondisi macet tersebut. Dengan kata lain, meskipun lebih efisien dari segi waktu eksekusi, Hill-Climbing memiliki keterbatasan serius dalam menemukan solusi global pada permasalahan kompleks seperti 8-Queens.  

Sebaliknya, algoritma Simulated Annealing menunjukkan performa yang lebih stabil dan konsisten dalam menemukan solusi optimal. Melalui mekanisme probabilistiknya, algoritma ini memungkinkan penerimaan langkah yang lebih buruk pada tahap awal sehingga ruang solusi dapat dijelajahi lebih luas. Hasil percobaan membuktikan bahwa Simulated Annealing berhasil mencapai solusi dengan (h = 0) pada hampir semua percobaan, meskipun membutuhkan lebih banyak iterasi dan waktu. Dengan demikian, dapat disimpulkan bahwa Simulated Annealing lebih andal dibandingkan Hill-Climbing karena mampu mengatasi jebakan *local minimum* dan memberikan peluang lebih besar untuk menemukan solusi global.  
