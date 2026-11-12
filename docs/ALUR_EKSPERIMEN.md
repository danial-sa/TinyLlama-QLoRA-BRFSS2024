# Struktur kode dan alur eksperimen

Notebook terdiri atas **53 sel kode** dan dijalankan secara berurutan. Urutan fungsionalnya sebagai berikut.

| Tahap | Sel notebook | Fungsi |
|---|---|---|
| Instalasi dan inisialisasi | 1–4 | Pustaka, Google Drive, konfigurasi dan visualisasi |
| Pemilihan atribut dan pembersihan | 5–10 | Membaca XPT, memvalidasi kode dan memeriksa distribusi |
| Sampling dan audit profil | 11–15 | Sampel 87.500, profil berulang dan audit label |
| Pemisahan serta RUS | 16–20 | Pembagian berdasarkan kelompok dan penyeimbangan data latih |
| Representasi teks dan tokenisasi | 21–23 | Konversi atribut ke teks, tokenisasi dan audit panjang |
| Model dan utilitas pelatihan | 24–26 | Konfigurasi *frozen backbone*, QLoRA, evaluasi dan checkpoint |
| Pelatihan dan evaluasi standar | 27–39 | Dua pendekatan, grafik, prediksi dan perbandingan metrik |
| Evaluasi *threshold tuning* | 40–51 | Pemilihan threshold validasi, pengujian dan visualisasi |
| Metadata dan daftar artefak | 52–53 | Menyimpan konfigurasi dan hasil eksperimen |

**Catatan reproduksi:** sel 42 kosong. Beberapa sel visualisasi memuat alternatif grafik untuk analisis tesis. Sel-sel tersebut dipertahankan agar kode sumber penelitian tidak berubah.

## Parameter inti yang terbaca pada sumber

- `SEED = 42`, `N_SAMPEL = 87500`, `JUMLAH_KANDIDAT = 120`.
- `EPOCHS = 5`, `BATCH = 8`, `BATCH_EVAL = 24`.
- `MAX_TOKEN = 128` adalah batas rancangan. Audit dari output asli mencatat panjang maksimum aktual 88 token.
- TinyLlama dasar: `TinyLlama/TinyLlama-1.1B-Chat-v1.0`.
- QLoRA menggunakan NF4 4-bit, `r=64`, `lora_alpha=32`, `lora_dropout=0.05`, dengan target `q_proj`, `k_proj`, `v_proj`, dan `o_proj`.
- Bobot dipilih dari *macro F1-score* pada validasi. *Threshold* ditentukan dari data validasi dan selanjutnya diuji pada data pengujian.

Dataset yang sudah diklasifikasikan, daftar hasil per rekaman, dan checkpoint **tidak disertakan**. Hasil ringkas dari eksekusi yang ada sebelum notebook dibersihkan tersedia pada `HASIL_TERCATAT.md`.
