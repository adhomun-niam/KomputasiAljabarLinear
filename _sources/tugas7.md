# Face Recognition Eigenface + SVD
## Google Colab Version

> 🔗 Link Google Colab:  
> https://colab.research.google.com/drive/1aKPtuqdLmjBoEcAdAajcHexF-EUdu3x_?usp=sharing


## Deskripsi Program

Program ini digunakan untuk:

* Mengupload gambar
* Mengubah gambar menjadi grayscale
* Melakukan proses Singular Value Decomposition (SVD)
* Mereconstruct gambar menggunakan hasil SVD
* Membandingkan kualitas hasil rekonstruksi berdasarkan nilai `k`
* Menghitung nilai MSE dan PSNR

Program dibuat menggunakan Python pada Google Colab.

---

# Library yang Digunakan

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
from google.colab import files
```

## Penjelasan

### 1. OpenCV

```python
import cv2
```

Digunakan untuk:

* Membaca gambar
* Mengolah citra digital
* Menghitung perbedaan gambar

---

### 2. NumPy

```python
import numpy as np
```

Digunakan untuk:

* Operasi matriks
* Perhitungan matematika
* Singular Value Decomposition (SVD)

---

### 3. Matplotlib

```python
import matplotlib.pyplot as plt
```

Digunakan untuk:

* Menampilkan gambar
* Membuat visualisasi hasil

---

### 4. Files Google Colab

```python
from google.colab import files
```

Digunakan untuk mengupload file gambar ke Google Colab.

---

# Upload Gambar

```python
uploaded = files.upload()
```

Kode ini digunakan untuk mengupload gambar dari komputer pengguna.

---

# Perulangan File

```python
for file_name in uploaded.keys():
```

Digunakan untuk membaca semua file yang berhasil diupload.

---

# Membaca Gambar

```python
img = cv2.imread(file_name, cv2.IMREAD_GRAYSCALE)
```

## Penjelasan

Gambar dibaca dalam bentuk grayscale.

Artinya gambar hanya memiliki:

* warna hitam
* putih
* abu-abu

Setiap pixel memiliki nilai 0–255.

---

# Mengambil Ukuran Gambar

```python
rows, cols = img.shape
```

## Penjelasan

* `rows` = jumlah baris
* `cols` = jumlah kolom

Karena gambar dianggap sebagai matriks.

---

# Menampilkan Ukuran Matriks

```python
print("===== UKURAN GAMBAR =====")
print("Kolom :", cols)
print("Baris :", rows)
print("Matrix A :", rows, "x", cols)
```

Program menampilkan ukuran matriks gambar.

Contoh:

```python
Matrix A : 512 x 512
```

Artinya gambar memiliki:

* 512 baris
* 512 kolom

---

# Singular Value Decomposition (SVD)

```python
U, S, VT = np.linalg.svd(img, full_matrices=False)
```

## Penjelasan

Fungsi ini memecah matriks gambar menjadi:

[
A = U \Sigma V^T
]

A = U\Sigma V^T

Dimana:

* `U` = matriks orthogonal kiri
* `Σ` (Sigma) = nilai singular
* `VT` = transpose matriks orthogonal kanan

---

# Membentuk Matriks Sigma

```python
Sigma = np.diag(S)
```

## Penjelasan

Nilai singular pada `S` diubah menjadi matriks diagonal.

Contoh:

[
\Sigma =
\begin{bmatrix}
5 & 0 & 0 \
0 & 3 & 0 \
0 & 0 & 1
\end{bmatrix}
]

---

# Menampilkan Ukuran Hasil SVD

```python
print("\n===== HASIL SVD =====")
print("Ukuran U     :", U.shape)
print("Ukuran Sigma :", Sigma.shape)
print("Ukuran VT    :", VT.shape)
```

Program menampilkan ukuran masing-masing matriks hasil SVD.

---

# Proses Perkalian Matriks

## Perkalian Pertama

```python
US = U @ Sigma
```

Dilakukan perkalian:

[
U \times \Sigma
]

U\Sigma

---

## Perkalian Kedua

```python
A_hasil = US @ VT
```

Dilakukan perkalian:

[
(U\Sigma)V^T
]

(U\Sigma)V^T

Hasil akhirnya adalah rekonstruksi gambar asli.

---

# Cek Rekonstruksi

```python
print(np.allclose(img, A_hasil))
```

## Penjelasan

Digunakan untuk mengecek apakah hasil rekonstruksi sama dengan gambar asli.

Jika hasil:

```python
True
```

Maka rekonstruksi berhasil.

---

# Konversi ke Format Gambar

```python
img_reconstructed = np.clip(A_hasil, 0, 255).astype(np.uint8)
```

## Penjelasan

Digunakan untuk:

* Membatasi pixel antara 0–255
* Mengubah tipe data menjadi gambar (`uint8`)

---

# Menghitung Selisih Gambar

```python
diff_full = cv2.absdiff(img, img_reconstructed)
```

## Penjelasan

Menghitung perbedaan pixel antara:

* gambar asli
* gambar hasil rekonstruksi

---

# Menghitung Error

```python
print("Rata-rata selisih :", np.mean(diff_full))
print("Maks selisih      :", np.max(diff_full))
```

## Penjelasan

### Mean Difference

Rata-rata perbedaan pixel.

### Max Difference

Perbedaan pixel terbesar.

---

# Nilai k pada SVD

```python
k_values = [10, 50, 100, 200]
```

## Penjelasan

`k` digunakan untuk mengambil sebagian singular value saja.

Semakin kecil `k`:

* ukuran data lebih kecil
* kualitas gambar menurun

Semakin besar `k`:

* gambar lebih jelas
* ukuran data lebih besar

---

# Mencari Hasil Terbaik

```python
best_k = None
best_mse = float("inf")
```

Digunakan untuk menyimpan:

* nilai `k` terbaik
* nilai error terkecil

---

# Menampilkan Gambar Asli

```python
plt.subplot(2,3,1)
plt.imshow(img, cmap='gray')
plt.title("Asli")
plt.axis('off')
```

Digunakan untuk menampilkan gambar asli.

---

# Perulangan Nilai k

```python
for k in k_values:
```

Program akan mencoba beberapa nilai `k`.

---

# Mengambil Sebagian Matriks

```python
Uk = U[:, :k]
Sk = np.diag(S[:k])
VTk = VT[:k, :]
```

## Penjelasan

Hanya mengambil `k` komponen terpenting dari hasil SVD.

---

# Rekonstruksi Berdasarkan k

```python
hasil_k = Uk @ Sk @ VTk
```

Rumus rekonstruksi:

[
A_k = U_k \Sigma_k V_k^T
]

A_k = U_k\Sigma_kV_k^T

---

# Menghitung MSE

```python
mse = np.mean((img.astype(np.float64) - hasil_k) ** 2)
```

## Rumus MSE

[
MSE = \frac{1}{n}\sum (I - K)^2
]

MSE = \frac{1}{n}\sum (I-K)^2

## Penjelasan

MSE digunakan untuk mengukur error gambar.

Semakin kecil MSE:

* gambar semakin mirip asli

---

# Menghitung PSNR

```python
psnr = 10 * np.log10((255**2) / mse)
```

## Rumus PSNR

[
PSNR = 10\log_{10}\left(\frac{255^2}{MSE}\right)
]

PSNR = 10\log_{10}\left(\frac{255^2}{MSE}\right)

## Penjelasan

PSNR digunakan untuk mengukur kualitas gambar.

Semakin besar PSNR:

* kualitas gambar semakin baik

---

# Menentukan k Terbaik

```python
if mse < best_mse:
    best_mse = mse
    best_k = k
```

Program memilih nilai `k` dengan MSE terkecil.

---

# Menampilkan Hasil Gambar

```python
plt.imshow(hasil_k, cmap='gray')
```

Digunakan untuk menampilkan hasil rekonstruksi berdasarkan nilai `k`.

---

# Menampilkan Semua Gambar

```python
plt.tight_layout()
plt.show()
```

Digunakan untuk merapikan tampilan hasil visualisasi.

---

# Menampilkan Hasil Terbaik

```python
print("\n===== HASIL TERBAIK =====")
print("k terbaik :", best_k)
print("MSE       :", best_mse)
```

Program menampilkan:

* nilai `k` terbaik
* nilai MSE terkecil

---

# Kesimpulan

Program ini menunjukkan bagaimana metode Singular Value Decomposition (SVD) digunakan pada pengolahan citra digital.

SVD mampu:

* memecah gambar menjadi beberapa matriks
* melakukan kompresi gambar
* merekonstruksi gambar dengan kualitas tertentu

Nilai `k` sangat mempengaruhi kualitas hasil rekonstruksi.

* `k kecil` → kompresi tinggi tetapi kualitas menurun
* `k besar` → kualitas lebih baik tetapi ukuran data lebih besar

Metode ini sering digunakan dalam:

* kompresi gambar
* face recognition
* machine learning
* pengolahan citra digital
