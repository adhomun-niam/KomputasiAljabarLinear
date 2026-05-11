# Tugas Dekomposisi dan Nilai Eigen

## Link Colab:
https://colab.research.google.com/drive/12lJ6uo8rNRAcJvV1fADIOibkbBTVQAqD?usp=sharing

## 1. Membuat Matriks 2×2

Langkah pertama program adalah mendefinisikan matriks:

$$
A = \begin{bmatrix}
2 & 1 \\
1 & 2
\end{bmatrix}
$$

Matriks ini merupakan matriks simetris karena elemen di atas diagonal utama sama dengan elemen di bawah diagonal utama.

**Diagonal utama:**
* 2
* 2

**Elemen lainnya:**
* 1
* 1

Matriks simetris biasanya lebih mudah dianalisis pada proses pencarian eigenvalue.

## 2. Konsep Eigenvalue dan Eigenvector

Eigenvalue adalah nilai khusus yang dimiliki suatu matriks.

Sedangkan eigenvector adalah vektor yang arahya tetap setelah dikalikan matriks.

Hubungan keduanya ditulis sebagai:

$$ Av = \lambda v $$

$$ Av = \lambda v $$

Keterangan:

* $A$ = matriks
* $v$ = eigenvector
* $\lambda$ = eigenvalue

Artinya:
Ketika eigenvector dikalikan dengan matriks, hasilnya hanya berubah skala sebesar eigenvalue.

## 3. Proses Mencari Eigenvalue

Program mencari eigenvalue dari matriks menggunakan fungsi bawaan Python pada library NumPy.

Untuk matriks:

$$
\begin{bmatrix}
2 & 1 \\
1 & 2
\end{bmatrix}
$$

diperoleh eigenvalue:

$$ \lambda_1 = 3 $$

$$ \lambda_2 = 1 $$

Eigenvalue menunjukkan karakteristik utama dari matriks tersebut.

## 4. Proses Mencari Eigenvector

Setelah eigenvalue diperoleh, program menghitung eigenvector yang sesuai.

Hasil eigenvector biasanya berupa:

Untuk eigenvalue 3:

$$
\begin{bmatrix}
1 \\
1
\end{bmatrix}
$$

Untuk eigenvalue 1:

$$
\begin{bmatrix}
1 \\
-1
\end{bmatrix}
$$

Eigenvector pertama menunjukkan arah pertumbuhan utama matriks.

Eigenvector kedua menunjukkan arah lain yang tetap setelah transformasi matriks dilakukan

## 5. Konsep QR Decomposition

Program kemudian melakukan QR Decomposition.

QR Decomposition memecah matriks menjadi:

$$ A = QR $$

$$ A = QR $$

Keterangan:

* $Q$ = matriks ortogonal
* $R$ = matriks segitiga atas

Tujuan metode ini adalah mencari eigenvalue secara iteratif.

## 6. Proses Iterasi QR

Setelah mendapatkan $Q$ dan $R$, program membentuk matriks baru:

$$ A_{baru} = RQ $$

$$ A_{baru} = RQ $$

Langkah ini dilakukan berulang sebanyak 10 iterasi.

Pada setiap iterasi:

1. Matriks dipecah menjadi $Q$ dan $R$
2. Dibentuk matriks baru $RQ$
3. Nilai diagonal matriks mulai mendekati eigenvalue

Semakin banyak iterasi:

* nilai diagonal semakin stabil
* hasil semakin mendekati eigenvalue asli

## 7. Hasil Setelah 10 Iterasi

Setelah iterasi dilakukan sebanyak 10 kali, diagonal matriks akan mendekati:

$$
\begin{bmatrix}
3 & 0 \\
0 & 1
\end{bmatrix}
$$

**Nilai diagonal:**

* 3
* 1

merupakan eigenvalue dari matriks awal.