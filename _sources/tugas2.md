# Tugas Transformasi Matriks

## Link Colab:
https://colab.research.google.com/drive/1iL5nqRIsoeJeI79x1v6-39YUz9FXvmGU?usp=sharinggit push

## 1. Titik Awal

Objek awal berupa **segitiga** dengan titik:

A(1,1), B(3,1), C(2,3)

Dalam bentuk matriks (koordinat homogen):

$$
P = \begin{bmatrix} x \\ y \\ 1 \end{bmatrix}
$$

Setiap titik direpresentasikan dalam bentuk ini agar mudah dikenai transformasi matriks.

## 2. Translasi (Langkah Pertama)

Pada program, setiap titik digeser ke kanan sejauh **1 satuan**.

Rumus:

$$T(x,y) = (x + 1, y)$$

Dalam bentuk matriks translasi:

$$
T = \begin{bmatrix}
1 & 0 & 1 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}
$$

Sehingga:

$$P' = T \cdot P$$
$$\downarrow$$

Artinya:
* nilai x bertambah 1
* nilai y tetap

## 3. Refleksi terhadap Sumbu-Y (Langkah Kedua)

Setelah translasi, objek juga dicerminkan terhadap sumbu-Y.

Rumus:

$$R(x,y) = (-x,y)$$

Dalam bentuk matriks:

$$
R = \begin{bmatrix}
-1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}
$$

Sehingga:

$$P'' = R \cdot P'$$
$$\downarrow$$

Artinya:
* nilai x berubah tanda (positif menjadi negatif)

## 4. Proses Iterasi (Animasi)

Program menjalankan proses sebanyak beberapa langkah:

* Setiap langkah:
    1. Menyimpan posisi segitiga
    2. Menghitung hasil refleksi
    3. Menggeser segitiga ke kanan

Sehingga terbentuk pola:

* segitiga bergerak ke kanan
* bayangannya selalu muncul di sisi kiri (cermin)

## 5. Visualisasi

Pada grafik:
* **Garis biru** -> objek asli (segitiga)
* **Garis merah putus-putus** -> hasil refleksi
* Titik diberi label:
    * A, B, C (asli)
    * A', B', C' (bayangan)

Setiap frame menunjukkan perubahan posisi akibat translasi.

## 6. Kesimpulan

Program ini menggabungkan dua transformasi:
1. **Translasi** → menggeser objek
2. **Refleksi** → mencerminkan objek

Dengan animasi, kita bisa melihat bahwa:
* objek bergerak secara bertahap
* bayangan selalu simetris terhadap sumbu-Y