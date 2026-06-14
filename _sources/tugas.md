# Sistem Persamaan Linear (SPL)

## 1. Pengertian Sistem Persamaan Linear

Sistem Persamaan Linear (SPL) adalah kumpulan dua atau lebih persamaan linear yang memiliki variabel yang sama dan harus dipenuhi secara bersamaan. Persamaan disebut **linear** karena setiap variabel berpangkat satu dan tidak terdapat perkalian antar variabel.

Contoh persamaan linear:

$$
2x + 3y = 12
$$

Persamaan tersebut disebut linear karena variabel $x$ dan $y$ hanya berpangkat satu.

Contoh yang **bukan** persamaan linear:

$$
x^2 + y = 10
$$

atau

$$
xy + 2x = 5
$$

karena terdapat pangkat lebih dari satu dan perkalian antar variabel.

---

## 2. Bentuk Umum Sistem Persamaan Linear

Bentuk umum SPL dengan $n$ variabel adalah:

$$
\begin{aligned}
a_{11}x_1 + a_{12}x_2 + \cdots + a_{1n}x_n &= b_1 \\
a_{21}x_1 + a_{22}x_2 + \cdots + a_{2n}x_n &= b_2 \\
\vdots \\
a_{m1}x_1 + a_{m2}x_2 + \cdots + a_{mn}x_n &= b_m
\end{aligned}
$$

Keterangan:

- $a_{ij}$ = koefisien
- $x_1,x_2,\ldots,x_n$ = variabel
- $b_i$ = konstanta

---

## 3. Tujuan Penyelesaian SPL

Tujuan utama SPL adalah mencari nilai variabel yang memenuhi seluruh persamaan secara bersamaan.

Misalnya:

$$
\begin{aligned}
x+y &= 8 \\
x-y &= 2
\end{aligned}
$$

Nilai yang memenuhi kedua persamaan adalah:

$$
x=5,\quad y=3
$$

Karena:

$$
5+3=8
$$

dan

$$
5-3=2
$$

---

## 4. Jenis-Jenis Sistem Persamaan Linear

### A. SPL Dua Variabel (SPLDV)

Memiliki dua variabel.

Contoh:

$$
\begin{aligned}
2x+y &= 7\\
x-y &= 2
\end{aligned}
$$

Variabelnya adalah $x$ dan $y$.

---

### B. SPL Tiga Variabel (SPLTV)

Memiliki tiga variabel.

Contoh:

$$
\begin{aligned}
x+y+z &= 6\\
2x-y+z &= 3\\
x+2y-z &= 4
\end{aligned}
$$

Variabelnya adalah $x$, $y$, dan $z$.

---

### C. SPL n Variabel

Memiliki lebih dari tiga variabel.

Contoh:

$$
\begin{aligned}
x_1+x_2+x_3+x_4 &= 10\\
2x_1+x_2-x_3+x_4 &= 8\\
x_1+3x_2+x_3-x_4 &= 7\\
2x_1+x_2+x_3+2x_4 &= 12
\end{aligned}
$$

---

## 5. Bentuk Matriks SPL

SPL dapat ditulis dalam bentuk matriks:

$$
AX=B
$$

dengan:

$$
A=
\begin{bmatrix}
2 & 1\\
1 & -1
\end{bmatrix}
$$

$$
X=
\begin{bmatrix}
x\\
y
\end{bmatrix}
$$

$$
B=
\begin{bmatrix}
7\\
2
\end{bmatrix}
$$

Sehingga:

$$
\begin{bmatrix}
2 & 1\\
1 & -1
\end{bmatrix}
\begin{bmatrix}
x\\
y
\end{bmatrix}
=
\begin{bmatrix}
7\\
2
\end{bmatrix}
$$

Bentuk matriks sangat penting dalam komputasi dan pemrograman.

---

## 6. Metode Penyelesaian SPL

### A. Metode Substitusi

Salah satu variabel dinyatakan dalam variabel lain, kemudian disubstitusikan ke persamaan lainnya.

Contoh:

$$
\begin{aligned}
x+y &= 8\\
x-y &= 2
\end{aligned}
$$

Dari persamaan kedua:

$$
x=y+2
$$

Substitusi ke persamaan pertama:

$$
(y+2)+y=8
$$

$$
2y+2=8
$$

$$
2y=6
$$

$$
y=3
$$

Substitusi kembali:

$$
x=3+2=5
$$

Jadi:

$$
(x,y)=(5,3)
$$

---

### B. Metode Eliminasi

Menghilangkan salah satu variabel dengan menjumlahkan atau mengurangkan persamaan.

Contoh:

$$
\begin{aligned}
x+y &= 8\\
x-y &= 2
\end{aligned}
$$

Jumlahkan kedua persamaan:

$$
(x+y)+(x-y)=8+2
$$

$$
2x=10
$$

$$
x=5
$$

Substitusi ke persamaan pertama:

$$
5+y=8
$$

$$
y=3
$$

---

### C. Metode Grafik

Setiap persamaan digambarkan sebagai garis.

Titik perpotongan kedua garis merupakan solusi SPL.

Contoh:

$$
\begin{aligned}
x+y &= 8\\
x-y &= 2
\end{aligned}
$$

Diubah menjadi:

$$
y = 8 - x
$$

dan

$$
y = x - 2
$$

Kedua garis berpotongan pada titik:

$$
(5,3)
$$

---

### D. Metode Matriks

Jika:

$$
AX=B
$$

maka:

$$
X=A^{-1}B
$$

dengan syarat matriks $A$ memiliki invers.

Metode ini banyak digunakan dalam komputasi numerik.

---

### E. Metode Eliminasi Gauss

Metode yang paling banyak digunakan dalam ilmu komputer dan matematika numerik.

Langkah-langkah:

1. Membentuk matriks augmented.
2. Mengubah matriks menjadi bentuk segitiga atas.
3. Melakukan substitusi balik.

Contoh:

$$
\left[
\begin{array}{cc|c}
1&1&8\\
1&-1&2
\end{array}
\right]
$$

Operasi baris:

$$
R_2 \leftarrow R_2-R_1
$$

menghasilkan:

$$
\left[
\begin{array}{cc|c}
1&1&8\\
0&-2&-6
\end{array}
\right]
$$

Diperoleh:

$$
y=3
$$

dan

$$
x=5
$$

---

## 7. Kemungkinan Solusi SPL

### A. Solusi Tunggal

Memiliki tepat satu solusi.

Contoh:

$$
\begin{aligned}
x+y &= 8\\
x-y &= 2
\end{aligned}
$$

Hasil:

$$
(5,3)
$$

---

### B. Tak Hingga Solusi

Persamaan saling bergantung.

Contoh:

$$
\begin{aligned}
x+y &= 4\\
2x+2y &= 8
\end{aligned}
$$

Persamaan kedua merupakan kelipatan persamaan pertama.

---

### C. Tidak Memiliki Solusi

Garis sejajar sehingga tidak berpotongan.

Contoh:

$$
\begin{aligned}
x+y &= 4\\
x+y &= 8
\end{aligned}
$$

Mustahil memenuhi kedua persamaan sekaligus.

---

## 8. Penerapan SPL dalam Kehidupan Nyata

### 1. Ekonomi

Menentukan harga barang.

Misal:

- 2 buku + 1 pensil = Rp7.000
- 1 buku + 2 pensil = Rp5.000

SPL digunakan untuk menentukan harga masing-masing barang.

### 2. Teknik Informatika

Digunakan pada:

- Machine Learning
- Artificial Intelligence
- Computer Vision
- Grafik Komputer
- Analisis Data

Banyak algoritma bekerja dengan matriks dan SPL.

### 3. Teknik Sipil

Menghitung gaya pada struktur bangunan dan jembatan.

### 4. Teknik Elektro

Menyelesaikan rangkaian listrik menggunakan Hukum Kirchhoff.

### 5. Statistik dan Data Science

Digunakan dalam regresi linear dan pemodelan data.

---

## 9. Keunggulan SPL

- Dapat menyelesaikan banyak masalah nyata.
- Menjadi dasar aljabar linear.
- Digunakan dalam pemrograman dan komputasi ilmiah.
- Mendukung pengembangan AI dan Machine Learning.
- Dapat diselesaikan secara manual maupun menggunakan komputer.

---

## 10. Kesimpulan

Sistem Persamaan Linear (SPL) adalah sekumpulan dua atau lebih persamaan linear yang harus dipenuhi secara bersamaan. Solusi SPL merupakan nilai variabel yang memenuhi seluruh persamaan dalam sistem. Penyelesaiannya dapat dilakukan dengan metode substitusi, eliminasi, grafik, matriks, Eliminasi Gauss, maupun metode numerik lainnya. Karena kemampuannya memodelkan berbagai permasalahan nyata, SPL menjadi salah satu materi paling penting dalam matematika, teknik, statistika, dan ilmu komputer.

---

## Contoh
- eq1 : x + y = 4
- eq2 : x - y = 2

![original image](https://cdn.mathpix.com/snip/images/Je1xlDOue0ix7lOp3b7k-zMVnFOVoOWMH1zTmIzbUq8.original.fullsize.png)