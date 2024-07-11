# Pengolahan_Citra_UAS

Nama  : M. Iqbal Fadillah
Nim   : 312210586
Kelas : TI.22.B2

A. K-means Clustering
K-means Clustering adalah metode segmentasi gambar yang digunakan untuk mengelompokkan data (piksel-piksel) ke dalam sejumlah bagian (cluster) berdasarkan kesamaan warna, tekstur atau intensitasnya. Tujuannya adalah untuk menyederhanakan representasi gambar dan mempermudah analisis dengan mengelompokkan piksel yang memiliki karakteristik serupa ke dalam kluster yang sama.

![image](https://github.com/IQBAL06102002/Pengolahan_Citra_UAS/assets/115945207/6e3ced59-b72b-478f-b7df-c48d5c098a13)

# Penjelasan Program

Berikut adalah program Python yang telah dirapikan dan dijelaskan setiap langkahnya. Program ini menggunakan OpenCV untuk memproses gambar melakukan clustering dengan algoritma k-means, dan menampilkan hasilnya menggunakan matplotlib.

import numpy as np
import matplotlib.pyplot as plt
import cv2
image = cv2.imread('S.jpg')
image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
plt.figure(figsize=(12, 6))
plt.subplot(1, 2, 1)
plt.imshow(image)
plt.title('Gambar Asli')
plt.axis('off')
pixel_vals = image.reshape((-1, 3))
pixel_vals = np.float32(pixel_vals)
criteria = (cv2.TERM_CRITERIA_EPS + cv2.TERM_CRITERIA_MAX_ITER, 100, 0.85)
k = 3
retval, labels, centers = cv2.kmeans(pixel_vals, k, None, criteria, 10, cv2.KMEANS_RANDOM_CENTERS)
centers = np.uint8(centers)
segmented_data = centers[labels.flatten()]
segmented_image = segmented_data.reshape((image.shape))
plt.subplot(1, 2, 2)
plt.imshow(segmented_image)
plt.title('Gambar Tersegmentasi (K=3)')
plt.axis('off')
plt.tight_layout()
plt.show()

HASIL OUTPUT GAMBAR TERSEGMENTASI K=3

<img width="178" alt="image" src="https://github.com/IQBAL06102002/Pengolahan_Citra_UAS/assets/115945207/5bc1f3fd-e0b2-410e-b378-2548e9d7d7c4">
