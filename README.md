# MII227425 — Kecerdasan Buatan Lanjut Kelas B

Repositori tugas mata kuliah Kecerdasan Buatan Lanjut, Kelas B.

## Daftar tugas

| Folder | Deskripsi |
| --- | --- |
| [single layer perceptron](single%20layer%20perceptron/) | Klasifikasi biner Iris menggunakan satu neuron sigmoid yang diimplementasikan dari awal dengan Python. |

## Single Layer Perceptron

Folder tugas berisi:

- [Notebook Python](single%20layer%20perceptron/SLP_from_scratch.ipynb): implementasi manual, hasil eksekusi, serta grafik akurasi dan loss.
- [Workbook Excel](single%20layer%20perceptron/Single%20Layer%20Perceptron.xlsx): perhitungan training dan validation.
- [Deskripsi dan petunjuk lengkap](single%20layer%20perceptron/README.md).
- Data CSV, metrik acuan spreadsheet, dan dependensi notebook.

Model tidak menggunakan Keras, TensorFlow, PyTorch, scikit-learn, atau NumPy. Matplotlib hanya digunakan untuk visualisasi.

## Cara menjalankan

```sh
git clone https://github.com/SalametHimawan/DeepLearning.git
cd "DeepLearning/single layer perceptron"
python -m pip install -r requirements.txt
python -m jupyterlab
```

Buka `SLP_from_scratch.ipynb`, lalu jalankan **Run All Cells**. Pertahankan folder `data/` dan `output/` di dalam folder tugas agar notebook dapat membaca data dan metrik acuan.
