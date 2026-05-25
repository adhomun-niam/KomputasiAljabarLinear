# Determinan Matriks

## Pengertian Determinan

Determinan adalah suatu nilai skalar yang diperoleh dari matriks persegi.
Determinan digunakan untuk:
- Menentukan apakah matriks memiliki invers
- Menentukan solusi SPL
- Digunakan dalam transformasi matriks

## Matriks Koefisien

$$
A =
\begin{bmatrix}
1 & 1 & 1 & 1 & 1 \\
2 & 1 & 1 & 1 & 1 \\
2 & 2 & 1 & 1 & 1 \\
2 & 2 & 2 & 1 & 1 \\
2 & 2 & 2 & 2 & 1
\end{bmatrix}
$$

## Eliminasi Matriks

$$
\begin{bmatrix}
1 & 1 & 1 & 1 & 1 \\
0 & -1 & -1 & -1 & -1 \\
0 & 0 & -1 & -1 & -1 \\
0 & 0 & 0 & -1 & -1 \\
0 & 0 & 0 & 0 & -1
\end{bmatrix}
$$

## Menghitung Determinan

Karena matriks sudah berbentuk segitiga atas, maka determinan diperoleh dari hasil perkalian diagonal utama.

$$
\det(A) = 1 \times (-1) \times (-1) \times (-1) \times (-1)
$$

$$
\det(A) = 1
$$

## Kesimpulan

Karena determinan matriks tidak sama dengan nol,
maka matriks memiliki invers.