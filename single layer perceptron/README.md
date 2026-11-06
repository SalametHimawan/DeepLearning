# Single Layer Perceptron — Klasifikasi Biner Iris

Implementasi Single Layer Perceptron (SLP) dari awal menggunakan Python untuk mengklasifikasikan **Iris Setosa (0)** dan **Iris Versicolor (1)**. Proyek ini dibuat untuk Assignment 1 mata kuliah Deep Learning.

Model menggunakan satu neuron dengan aktivasi sigmoid sesuai template spreadsheet tugas. Perhitungan forward pass, gradien, dan pembaruan bobot ditulis secara manual menggunakan `math`, list, dan perulangan Python. Tidak menggunakan Keras, TensorFlow, PyTorch, scikit-learn, atau NumPy. Matplotlib hanya digunakan untuk membuat grafik.

## Isi repositori

| File/folder | Deskripsi |
| --- | --- |
| `SLP_from_scratch.ipynb` | Notebook berisi penjelasan, implementasi model, hasil eksekusi, grafik akurasi dan loss, serta verifikasi terhadap spreadsheet. |
| `Single Layer Perceptron.xlsx` | Workbook dengan rumus training, validation, ringkasan metrik, dan grafik yang dapat diedit. |
| `data/train.csv` | 80 sampel training dari template tugas. |
| `data/validation.csv` | 20 sampel validation dari template tugas. |
| `output/spreadsheet_metrics.csv` | Metrik workbook sebagai acuan verifikasi notebook. |
| `requirements.txt` | Dependensi untuk membuka dan menjalankan notebook. |

## Dataset dan konfigurasi

- Empat fitur: panjang sepal, lebar sepal, panjang petal, dan lebar petal.
- Training: 40 sampel Setosa dan 40 sampel Versicolor.
- Validation: 10 sampel Setosa dan 10 sampel Versicolor.
- Urutan data mengikuti template; tidak menggunakan pengacakan atau normalisasi.
- Bobot awal dan bias awal: **0,5**.
- Learning rate: **0,1**; jumlah epoch: **5**.
- Prediksi kelas 1 jika probabilitas **lebih besar dari 0,5**; selain itu kelas 0.
- Fungsi loss: **Mean Squared Error (MSE)**.

## Perhitungan model

Untuk setiap sampel, neuron menghitung:

```text
z = bias + sum(weight[j] * x[j])
p = 1 / (1 + exp(-z))
loss = (p - target)^2
delta = 2 * (p - target) * p * (1 - p)
bias = bias - learning_rate * delta
weight[j] = weight[j] - learning_rate * delta * x[j]
```

Semua gradien menggunakan probabilitas yang dihitung sebelum pembaruan parameter. Pembaruan dilakukan setiap sampel (online gradient descent).

Akurasi dan MSE training dihitung dari prediksi sebelum pembaruan pada setiap baris, mengikuti struktur spreadsheet. Validation menggunakan bobot akhir setiap epoch dan tidak memperbarui parameter. Karena itu, metrik training bukan evaluasi ulang seluruh data dengan bobot akhir epoch.

## Cara menjalankan

Gunakan Python 3.9 atau lebih baru. Buka terminal pada folder repositori, lalu masuk ke folder tugas:

```sh
cd "single layer perceptron"
python -m pip install -r requirements.txt
python -m jupyterlab
```

Buka `SLP_from_scratch.ipynb`, pilih kernel Python yang sesuai, lalu jalankan **Run All Cells**. Pertahankan struktur folder `data/` dan `output/` agar seluruh sel berjalan. Dataset sudah disertakan sehingga tidak perlu diunduh kembali.

Notebook akan menghasilkan `output/notebook_metrics.csv`, `output/notebook_accuracy.png`, dan `output/notebook_loss.png`. Semua grafik juga ditampilkan langsung di notebook.

## Hasil

| Epoch | Akurasi training | Akurasi validation | MSE training | MSE validation |
| --- | ---: | ---: | ---: | ---: |
| 1 | 52,50% | 50,00% | 0,44988866 | 0,32895116 |
| 2 | 95,00% | 50,00% | 0,03745191 | 0,24728932 |
| 3 | 97,50% | 50,00% | 0,02437219 | 0,17589164 |
| 4 | 97,50% | 85,00% | 0,01735720 | 0,11938137 |
| 5 | 98,75% | 100,00% | 0,01274016 | 0,08158137 |

Notebook telah dijalankan dan seluruh metrik lima epoch cocok dengan hasil workbook lokal pada toleransi absolut **1e-12**. Verifikasi ini belum mencakup perhitungan ulang oleh Google Sheets setelah impor.

Workbook melengkapi blok epoch yang belum selesai dan menggunakan referensi bobot tetap pada validation, sesuai instruksi template. Checkpoint bobot mencakup pembaruan sampel training terakhir setiap epoch.

## Referensi

1. [Template spreadsheet tugas](https://docs.google.com/spreadsheets/d/1yhi8ASebpmljJ3NpYQ7NmxlWLmhGOI6W/edit?gid=1211907647), sumber data dan konfigurasi yang digunakan dalam perhitungan.
2. Fisher, R. (1936). [Iris — UCI Machine Learning Repository](https://doi.org/10.24432/C56C76). Dataset berlisensi CC BY 4.0.
