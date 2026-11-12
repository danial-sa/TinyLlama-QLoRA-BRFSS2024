# Ringkasan keluaran eksperimen terdokumentasi

Angka berikut dibaca dari **hasil eksekusi yang tertanam pada notebook sebelum output dibersihkan**. Angka-angka ini bukan hasil pengujian ulang.

## Alur data

| Indikator | Jumlah |
|---|---:|
| Data mentah | 457.670 rekaman, 301 variabel |
| Data setelah pembersihan | 371.043 |
| Sampel eksperimen | 87.500 |
| Latih sebelum RUS | 61.251 |
| Latih setelah RUS | 11.610 |
| Validasi | 13.120 |
| Pengujian | 13.129 |
| Panjang token maksimum teramati | 88 token |

## Evaluasi pada data uji

| Pendekatan | Aturan keputusan | Akurasi | Macro F1 | Presisi CVD | Recall CVD | F1 CVD |
|---|---|---:|---:|---:|---:|---:|
| Frozen backbone | Argmax | 0,8376 | 0,6467 | 0,3014 | 0,5406 | 0,3870 |
| QLoRA | Argmax | 0,7920 | 0,6279 | 0,2653 | 0,6747 | 0,3809 |
| Frozen backbone | Threshold 0,61 | 0,8673 | 0,6464 | 0,3351 | 0,4056 | 0,3670 |
| QLoRA | Threshold 0,67 | 0,8559 | 0,6551 | 0,3267 | 0,4900 | 0,3920 |

Hasil evaluasi standar tidak menunjukkan keunggulan QLoRA pada seluruh metrik. QLoRA mempunyai *recall* kelas CVD lebih tinggi saat memakai argmax, sedangkan sesudah *threshold tuning* memperoleh *macro F1-score* tertinggi di antara empat kondisi yang tercatat. Interpretasi tetap terbatas pada dataset serta rancangan eksperimen yang digunakan.
