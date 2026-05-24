# Face Recognition Eigenface + SVD
## Google Colab Version

> 🔗 Link Google Colab:  
> https://colab.research.google.com/drive/1aKPtuqdLmjBoEcAdAajcHexF-EUdu3x_?usp=sharing

---

# Deskripsi Program

Program ini menggunakan metode:

- Eigenface
- Singular Value Decomposition (SVD)
- Euclidean Distance

untuk melakukan pengenalan wajah sederhana menggunakan Python di Google Colab.

---

# Install Library

```python
!pip install opencv-python matplotlib -q
```

---

# Import Library

```python
import os
import cv2
import numpy as np
import matplotlib.pyplot as plt

from google.colab import files
```

---

# Format Upload Foto

Upload semua gambar training langsung dari komputer.

Contoh nama file:

```text
amba_1.jpg
amba_2.jpg
amba_3.jpg

bahlil_1.jpg
bahlil_2.jpg
bahlil_3.jpg
```

Nama sebelum `_` akan menjadi label wajah.

Contoh:

```text
amba_1.jpg → label = amba
```

---

# Upload Foto Training

```python
print("Upload semua foto training")

uploaded = files.upload()
```

---

# Load Dataset

Program membaca semua gambar training.

Tahapan preprocessing:

1. Grayscale
2. Resize 100×100
3. Flatten menjadi vector
4. Simpan ke matrix data

---

```python
data_matrix = []
labels = []

img_size = (100, 100)

for file_name in uploaded.keys():

    label = file_name.split("_")[0]

    img = cv2.imread(file_name, cv2.IMREAD_GRAYSCALE)

    img = cv2.resize(img, img_size)

    img_vector = img.flatten()

    data_matrix.append(img_vector)

    labels.append(label)
```

---

# Convert ke Numpy Array

```python
data_matrix = np.array(data_matrix, dtype='float32')

print("Jumlah data training :", len(data_matrix))

print("Ukuran matrix data   :", data_matrix.shape)

print(labels)
```

---

# Visualisasi Sample Training

```python
plt.figure(figsize=(4,4))

plt.imshow(data_matrix[0].reshape(100,100), cmap='gray')

plt.title(f"Sample : {labels[0]}")

plt.axis('off')

plt.show()
```

---

# Mean Face

Mean face adalah rata-rata semua wajah training.

---

```python
mean_face = np.mean(data_matrix, axis=0)
```

---

# Visualisasi Mean Face

```python
plt.figure(figsize=(5,5))

plt.imshow(mean_face.reshape(100,100), cmap='gray')

plt.title("Mean Face")

plt.axis('off')

plt.show()
```

---

# Centering Data

Semua data dikurangi mean face.

---

```python
A = data_matrix - mean_face
```

---

# Singular Value Decomposition (SVD)

Persamaan dasar:

```text
A = U × Σ × VT
```

---

```python
U, S, VT = np.linalg.svd(A, full_matrices=False)
```

---

# Ukuran Matrix Hasil SVD

```python
print("Ukuran U  :", U.shape)

print("Ukuran S  :", S.shape)

print("Ukuran VT :", VT.shape)
```

---

# Singular Values

```python
print(S)
```

Semakin besar singular value:

- semakin penting komponen tersebut
- semakin besar variasi wajah yang disimpan

---

# Visualisasi Singular Values

```python
plt.plot(S)

plt.title("Singular Values")

plt.xlabel("Komponen")

plt.ylabel("Nilai Singular")

plt.grid()

plt.show()
```

---

# Eigenface

Eigenface berasal dari baris-baris matrix VT.

---

```python
num_eigenfaces = len(S)

plt.figure(figsize=(15,8))

for i in range(num_eigenfaces):

    plt.subplot(2, 3, i+1)

    eigenface = VT[i].reshape(100,100)

    plt.imshow(eigenface, cmap='gray')

    plt.title(f"Eigenface {i+1}")

    plt.axis('off')

plt.tight_layout()

plt.show()
```

---

# Project Training ke Eigenspace

```python
SIGMA = np.diag(S)

projected_training = U @ SIGMA
```

---

# Upload Gambar Test

```python
print("Upload gambar test")

uploaded_test = files.upload()
```

---

# Load Test Image

```python
test_file = list(uploaded_test.keys())[0]

test_img = cv2.imread(test_file, cv2.IMREAD_GRAYSCALE)

test_img = cv2.resize(test_img, (100,100))
```

---

# Visualisasi Test Image

```python
plt.imshow(test_img, cmap='gray')

plt.title("Test Image")

plt.axis('off')

plt.show()
```

---

# Flatten Test Image

```python
test_vector = test_img.flatten().astype('float32')
```

---

# Centering Test Image

```python
test_centered = test_vector - mean_face
```

---

# Project Test ke Eigenspace

```python
test_projected = test_centered @ VT.T
```

---

# Hitung Euclidean Distance

```python
distances = []

for i in range(len(projected_training)):

    dist = np.linalg.norm(
        test_projected - projected_training[i]
    )

    distances.append(dist)

    print(f"{labels[i]} = {dist:.2f}")
```

---

# Hasil Recognition

```python
min_index = np.argmin(distances)

hasil = labels[min_index]

print("Hasil Face Recognition :", hasil)
```

---

# Visualisasi Matching

```python
matched_img = data_matrix[min_index].reshape(100,100)

plt.figure(figsize=(8,4))

plt.subplot(1,2,1)
plt.imshow(test_img, cmap='gray')
plt.title("Test Image")
plt.axis('off')

plt.subplot(1,2,2)
plt.imshow(matched_img, cmap='gray')
plt.title(f"Matched : {hasil}")
plt.axis('off')

plt.tight_layout()

plt.show()
```

---

# Alur Program

```text
1. Upload semua foto training
2. Ambil label dari nama file
3. Grayscale dan resize gambar
4. Flatten gambar menjadi vector
5. Membentuk matrix data
6. Menghitung mean face
7. Melakukan centering data
8. Menjalankan SVD
9. Membentuk eigenface
10. Project training ke eigenspace
11. Upload gambar test
12. Project gambar test
13. Menghitung Euclidean distance
14. Mengambil jarak terkecil
15. Menampilkan hasil recognition
```

---

# Hubungan PCA dan SVD

| PCA | SVD |
|---|---|
| Principal Component | Eigenface |
| Eigenvalue | Singular Value² |
| Eigenvector | VT |
| PCA Projection | U × Σ |

---

# Kekurangan Metode Eigenface

- Sensitif pencahayaan
- Sensitif pose wajah
- Kurang akurat jika dataset kecil
- Tidak sekuat Deep Learning modern

---

# Kesimpulan

Program berhasil:

- Membaca dataset wajah
- Mengubah gambar menjadi data numerik
- Menghitung mean face
- Melakukan SVD
- Membentuk eigenface
- Melakukan face recognition menggunakan Euclidean Distance

Metode ini cocok untuk mempelajari:

- PCA
- SVD
- Eigenvector
- Face Recognition klasik