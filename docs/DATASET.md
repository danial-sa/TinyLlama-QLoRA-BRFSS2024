# Dataset dan definisi target

Dataset bersumber dari **BRFSS 2024** yang disediakan CDC dalam format SAS XPORT. **Data mentah tidak disertakan** pada repositori ini. Baca juga dokumentasi resmi CDC: [BRFSS Annual Data](https://www.cdc.gov/brfss/annual_data/annual_data.htm).

## Atribut input

| Variabel | Informasi |
|---|---|
| `_AGEG5YR` | Kelompok usia |
| `_SEX` | Jenis kelamin |
| `_BMI5CAT` | Kategori indeks massa tubuh |
| `GENHLTH` | Penilaian kondisi kesehatan umum |
| `DIABETE4` | Riwayat diabetes |
| `CHCKDNY2` | Riwayat penyakit ginjal |
| `CVDSTRK3` | Riwayat stroke |
| `CHCCOPD3` | Riwayat COPD |
| `_RFSMOK3` | Indikator merokok |
| `_TOTINDA` | Indikator aktivitas fisik |
| `_RFBING6` | Indikator konsumsi alkohol berlebihan dalam satu kesempatan (*binge drinking*) |

## Target

`_MICHD` adalah variabel perhitungan BRFSS mengenai status riwayat penyakit jantung koroner atau infark miokard berdasarkan jawaban survei. Implementasi notebook memetakan nilai **1 menjadi kelas positif (1)** dan nilai **2 menjadi kelas negatif (0)**. Nama kelas yang dipakai pada pelaporan adalah `CVD History` dan `No CVD History`.

Kode kategori dan nilai tidak valid ditangani oleh definisi `VALID` pada **sel 6**. Kriteria yang diterapkan dalam notebook adalah bagian dari implementasi penelitian dan bukan klaim bahwa seluruh kategori survei telah dicakup. Interpretasi label dibatasi pada data survei, bukan diagnosis klinis.
