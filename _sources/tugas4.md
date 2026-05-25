# Adjoin dan Invers Matriks

## Pengertian Adjoin

Adjoin matriks adalah transpose dari matriks kofaktor.

## Hasil Adjoin Matriks

$$
\text{adj}(A) =
\begin{bmatrix}
-1 & 1 & 0 & 0 & 0 \\
2 & -1 & 1 & 0 & 0 \\
0 & 2 & -1 & 1 & 0 \\
0 & 0 & 2 & -1 & 1 \\
0 & 0 & 0 & 2 & -1
\end{bmatrix}
$$

## Rumus Invers

$$
A^{-1} = \frac{1}{\det(A)} \cdot \text{adj}(A)
$$

Karena:

$$
\det(A) = 1
$$

maka:

$$
A^{-1} = \text{adj}(A)
$$

## Hasil Invers

$$
A^{-1} =
\begin{bmatrix}
-1 & 1 & 0 & 0 & 0 \\
2 & -1 & 1 & 0 & 0 \\
0 & 2 & -1 & 1 & 0 \\
0 & 0 & 2 & -1 & 1 \\
0 & 0 & 0 & 2 & -1
\end{bmatrix}
$$

## Kesimpulan

Karena determinan matriks sama dengan 1,
maka matriks memiliki invers dan inversnya sama dengan adjoin matriks.