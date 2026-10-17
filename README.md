# Crab Body Completeness Detection Dataset

## Deskripsi

Dataset ini dikembangkan untuk mendukung penelitian identifikasi kelengkapan tubuh kepiting menggunakan teknologi *Computer Vision*, khususnya algoritma YOLO (*You Only Look Once*). Dataset berfokus pada deteksi bagian tubuh kepiting yang meliputi capit, kaki, dan kaki renang melalui pendekatan *object detection*.

Dataset ini merupakan hasil penggabungan data primer dan data sekunder untuk memperkaya variasi visual serta mendukung pengembangan model deteksi bagian tubuh kepiting secara otomatis. Dataset digunakan dalam penelitian akademis untuk mendukung sistem *Crab Sorting Profiling*, khususnya pada aspek identifikasi kelengkapan tubuh kepiting.

## Sumber Data

Dataset ini berasal dari tiga sumber berikut:

1. **Data Primer**  
   Citra kepiting yang dikumpulkan dan dianotasi secara mandiri untuk keperluan penelitian akademis/skripsi.

2. **Data Sekunder — Emora**  
   Dataset [KEBAK](https://universe.roboflow.com/emora/kebak-xlevz) yang diperoleh melalui Roboflow Universe.

3. **Data Sekunder — KEBAK**  
   Dataset [Kepiting](https://universe.roboflow.com/kebak-f0d2w/kepiting-0tjel) yang diperoleh melalui Roboflow Universe.

Data dari berbagai sumber disiapkan melalui proses penggabungan, pemeriksaan anotasi, dan penyesuaian format agar dapat digunakan dalam pelatihan model deteksi objek.

## Kelas Deteksi

Dataset ini memiliki tiga kelas objek (*object classes*):

| ID | Nama Kelas | Deskripsi |
|---|---|---|
| 0 | `Capit` | Bagian capit kepiting yang terlihat pada citra. |
| 1 | `Kaki` | Bagian kaki jalan kepiting yang terlihat pada citra. |
| 2 | `Kaki Renang` | Bagian kaki renang kepiting yang terlihat pada citra. |

**Catatan:** Ketiga kelas tersebut menunjukkan bagian tubuh yang dideteksi, bukan label kondisi tubuh seperti utuh atau tidak utuh. Penentuan kelengkapan tubuh dilakukan dengan menganalisis hasil deteksi bagian tubuh berdasarkan aturan yang ditetapkan dalam penelitian.

## Struktur Dataset

Dataset menggunakan format YOLO dengan pembagian data menjadi *training*, *validation*, dan *testing*.

```text
crab_ready_dataset/
├── data.yaml
├── train/
│   ├── images/
│   └── labels/
├── valid/
│   ├── images/
│   └── labels/
└── test/
    ├── images/
    └── labels/
```

Keterangan:

- `train/`: data untuk melatih model.
- `valid/`: data untuk memvalidasi model selama pelatihan.
- `test/`: data untuk mengevaluasi performa model setelah pelatihan.
- `images/`: berisi citra kepiting.
- `labels/`: berisi anotasi objek dalam format YOLO.
- `data.yaml`: konfigurasi dataset yang berisi lokasi data dan daftar kelas.

## Konfigurasi Dataset

File `data.yaml` yang digunakan dalam pelatihan model adalah sebagai berikut:

```yaml
path: /content/crab_ready_dataset
train: train/images
val: valid/images
test: test/images

nc: 3
names:
  0: Capit
  1: Kaki
  2: Kaki Renang
```

**Catatan:** Path `/content/crab_ready_dataset` merupakan lokasi dataset pada lingkungan Google Colab. Sesuaikan nilai `path` dengan lokasi dataset apabila digunakan pada komputer lokal atau server lain.

## Teknologi

- **Python** — bahasa pemrograman untuk pengolahan data dan pelatihan model.
- **Ultralytics YOLO** — framework deteksi objek.
- **Google Colab** — lingkungan komputasi untuk persiapan dataset dan pelatihan model.
- **Roboflow Universe** — sumber dataset sekunder.

## Tujuan Penggunaan

Dataset ini digunakan untuk:

1. Melatih model YOLO dalam mendeteksi bagian tubuh kepiting.
2. Mengidentifikasi keberadaan capit, kaki, dan kaki renang pada citra.
3. Mendukung pengembangan sistem otomatis untuk analisis kelengkapan tubuh kepiting.
4. Menjadi salah satu komponen dalam penelitian *Crab Sorting Profiling*.

## Lisensi dan Atribusi

Dataset ini menggabungkan data primer dan data sekunder dari sumber yang memiliki ketentuan penggunaan masing-masing. Penggunaan, modifikasi, dan distribusi ulang dataset gabungan harus memperhatikan lisensi dari setiap sumber data serta hak penggunaan data primer.

- Emora — [KEBAK Dataset](https://universe.roboflow.com/emora/kebak-xlevz). Lisensi yang tercantum: CC BY 4.0.
- KEBAK — [Kepiting Dataset](https://universe.roboflow.com/kebak-f0d2w/kepiting-0tjel). Lisensi perlu diverifikasi pada halaman sumber.
- Data primer — mengikuti hak kepemilikan dan izin penggunaan yang berlaku.

Atribusi sumber perlu dipertahankan sesuai ketentuan lisensi masing-masing. Publikasi kode pelatihan di repositori GitHub tidak secara otomatis memberikan izin untuk mendistribusikan ulang seluruh citra dataset.

## Penggunaan dalam Penelitian

Dataset ini merupakan bagian dari penelitian pengembangan sistem *Crab Sorting Profiling* berbasis *Computer Vision*. Model deteksi bagian tubuh yang dikembangkan diharapkan dapat mendukung proses identifikasi kelengkapan fisik kepiting sebagai salah satu parameter dalam proses profiling.

Hasil deteksi model perlu diolah lebih lanjut menggunakan aturan keputusan yang ditetapkan dalam penelitian untuk menentukan status kelengkapan tubuh. Deteksi bagian tubuh saja tidak secara langsung membuktikan bahwa seluruh bagian tubuh kepiting lengkap atau bahwa kepiting berada dalam kondisi sehat.

## Pengembangan Selanjutnya

Pengembangan dataset dan model dapat mencakup:

- Penambahan variasi citra kepiting dari berbagai sudut pengambilan gambar.
- Peningkatan jumlah data untuk setiap kelas.
- Evaluasi menggunakan metrik *Precision*, *Recall*, dan *mAP*.
- Integrasi hasil deteksi dengan logika penentuan kelengkapan tubuh.
- Integrasi model dengan modul profiling kepiting lainnya.

---

**Project:** Crab Sorting Profiling  
**Task:** Object Detection  
**Framework:** Ultralytics YOLO  
**Dataset Classes:** Capit, Kaki, Kaki Renang
