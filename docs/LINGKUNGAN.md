# Lingkungan eksperimen yang tercatat

Informasi berikut disalin dari **output sel 3** pada notebook yang diunggah, bukan merupakan hasil eksekusi ulang pada saat pembuatan repositori.

| Komponen | Versi atau spesifikasi tercatat |
|---|---|
| Python | 3.13.16 |
| GPU | NVIDIA Tesla T4, VRAM 14,56 GiB |
| PyTorch | 2.14.1+cu130 |
| pandas | 2.2.3 |
| NumPy | 2.4.6 |
| Transformers | 4.57.6 |
| PEFT | 0.19.1 |
| bitsandbytes | 0.50.2 |
| Accelerate | 1.15.0 |
| scikit-learn | 1.6.1 |
| imbalanced-learn | 0.14.2 |
| Matplotlib | 3.10.0 |
| tqdm | 4.67.3 |

File `requirements.txt` mencerminkan batas versi instalasi pada **sel 1**, bukan *lockfile* semua dependensi transitif. PyTorch dengan sufiks CUDA `+cu130` merupakan catatan lingkungan saat itu dan **tidak dijamin tersedia melalui instalasi pip umum**. Gunakan runtime GPU Google Colab yang kompatibel, periksa hasil sel 3, dan catat perbedaan lingkungan jika menjalankan ulang eksperimen.
