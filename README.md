# Klasifikasi Status Riwayat Penyakit Kardiovaskular dengan TinyLlama dan QLoRA

Repositori ini memuat **kode eksperimen** tesis mengenai adaptasi **TinyLlama-1.1B-Chat-v1.0** menggunakan *Quantized Low-Rank Adaptation* (QLoRA) untuk klasifikasi biner berbasis survei **BRFSS 2024**. Pendekatan **frozen backbone** digunakan sebagai pembanding.

Target `_MICHD` mengacu pada riwayat penyakit jantung koroner atau infark miokard menurut jawaban survei, **bukan diagnosis klinis dan bukan prediksi kejadian di masa depan**.

## Isi repositori

| Berkas | Keterangan |
|---|---|
| `notebooks/TinyLlama_QLoRA_BRFSS2024.ipynb` | Notebook eksperimen asli, seluruh 53 sel kode dipertahankan, output eksekusi dibersihkan |
| `docs/DATASET.md` | Data sumber, sebelas prediktor dan target |
| `docs/ALUR_EKSPERIMEN.md` | Urutan pemrosesan hingga evaluasi |
| `docs/LINGKUNGAN.md` | Versi lingkungan pada eksekusi yang tercatat |
| `docs/HASIL_TERCATAT.md` | Ringkasan angka dari output notebook sebelum dibersihkan |
| `docs/PANDUAN_GITHUB.md` | Cara mengunggah folder menggunakan Git |
| `requirements.txt` | Dependensi pustaka utama untuk lingkungan Colab |

## Menjalankan eksperimen

1. Gunakan **Google Colab** dengan GPU NVIDIA yang mendukung *bitsandbytes* 4-bit. Eksekusi terdokumentasi menggunakan **Tesla T4**.
2. Unduh dataset BRFSS 2024 dari **[CDC BRFSS Annual Data](https://www.cdc.gov/brfss/annual_data/annual_data.htm)**. Notebook mengharapkan berkas **SAS XPORT**.
3. Unggah berkas data ke Google Drive Anda. **Pada sel ke-2** di notebook, sesuaikan `ROOT`, `FILE` dan `OUT` dengan lokasi berkas yang sebenarnya. Nilai awal mengikuti penamaan dalam eksperimen asli (`LLCP2024.XPT_`).
4. Jalankan sel secara **berurutan** dari awal. Sel pertama memasang pustaka, sel berikutnya menghubungkan Google Drive dan mengatur eksperimen.
5. Periksa kapasitas Drive dan GPU sebelum menjalankan *training*. Notebook menyimpan CSV, PNG, metadata, serta *checkpoint* ke lokasi `OUT`.

**Penting:** Repositori ini menyajikan kode penelitian, bukan paket siap pakai untuk prediksi klinis. Kode memerlukan dataset, koneksi Drive, GPU, dan unduhan bobot dasar TinyLlama. Notebook tidak dijalankan ulang selama penyiapan repositori ini. Perbedaan versi lingkungan dapat memengaruhi reproduksi hasil.

## Ringkasan metode

- Sumber: BRFSS 2024; 11 atribut kesehatan; target `_MICHD`.
- Persiapan: validasi kode kategori, pengambilan 87.500 sampel terstratifikasi, dan pembagian berdasarkan profil atribut menggunakan `GroupShuffleSplit`.
- Penyeimbangan: *Random Under Sampling* (RUS) **hanya pada data latih**.
- Masukan model: atribut tabular diubah menjadi teks berbahasa Inggris, kemudian ditokenisasi dengan *tokenizer* TinyLlama.
- Model: *frozen backbone* dibandingkan dengan QLoRA NF4 4-bit, lima *epoch*.
- Evaluasi: *confusion matrix*, akurasi, presisi, *recall*, F1-score, *macro F1-score*, serta penyesuaian *threshold* berdasarkan validasi.

Seluruh detail implementasi tetap berada dalam notebook. Hasil yang tercatat sebelum output dibersihkan dirangkum pada [`docs/HASIL_TERCATAT.md`](docs/HASIL_TERCATAT.md).

## Data, bobot, dan privasi

**Dataset sumber, salinan data responden, hasil prediksi per rekaman, dan berkas checkpoint tidak disertakan.** File-file tersebut harus dikelola terpisah dan tidak diunggah secara tidak sengaja. `.gitignore` mencegah banyak jenis berkas besar atau sensitif masuk ke staging Git.

Tidak ada lisensi kode yang ditetapkan pada paket ini. Tentukan izin penggunaan kode sebelum mendistribusikannya secara luas.

## Menautkan ke tesis

Apabila repositori telah dipublikasikan, tautkan ke Lampiran 2 sebagai dokumentasi kode. Untuk versi final yang tetap dapat dirujuk, buat **GitHub Release** dengan nomor versi, misalnya `v1.0.0`, setelah pemeriksaan akhir.
