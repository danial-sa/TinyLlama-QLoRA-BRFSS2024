# Panduan mengunggah repositori ke GitHub

Langkah berikut dapat dijalankan di **Git Bash** atau terminal yang sudah memiliki Git.

1. Ekstrak berkas ZIP, lalu buka terminal di dalam folder `TinyLlama-QLoRA-BRFSS2024`.
2. Buat **repositori kosong** melalui GitHub, misalnya bernama `TinyLlama-QLoRA-BRFSS2024`. Pilih **Private** terlebih dahulu. Saat membuat repositori, jangan centang opsi untuk menambahkan README, `.gitignore`, atau lisensi karena berkasnya sudah tersedia secara lokal.
3. Jalankan perintah berikut, lalu ganti `USERNAME` dengan nama akun GitHub Anda.

```bash
git init
git add .
git status
git commit -m "Initial research notebook and documentation"
git branch -M main
git remote add origin https://github.com/USERNAME/TinyLlama-QLoRA-BRFSS2024.git
git push -u origin main
```

Pastikan `git status` tidak memuat data mentah, file prediksi responden, token akses, atau checkpoint sebelum melakukan `commit`. Jika Git meminta nama dan surel untuk commit, jalankan `git config --global user.name "Nama Anda"` serta `git config --global user.email "email-yang-terdaftar"`, lalu ulangi commit.

**Autentikasi:** GitHub menggunakan kredensial yang aman, seperti Git Credential Manager atau GitHub CLI. Jangan mengirimkan kata sandi atau *personal access token* melalui percakapan atau menyimpannya dalam berkas notebook.

Setelah unggahan berhasil, gunakan tautan repositori sebagai referensi pada Lampiran 2. Saat versi final dinyatakan siap, buat tag/release agar rujukannya stabil.
