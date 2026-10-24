# Kejutan Ultah (situs mandiri)

Situs ulang tahun yang berdiri sendiri, **tanpa halaman Amplop Kasih**. Memakai sheet master, akun, folder Drive, Apps Script, dan Worker yang sama dengan proyek Amplop Kasih. Akun yang sudah terdaftar tetap bisa masuk, tetapi arsip di situs ini hanya menampilkan kejutan ulang tahun.

```
kejutan-ultah/
├── index.html    Halaman utama (generator + penonton kejutan)
├── musics.mp3    Lagu latar Happy Birthday (opsional; tanpa file ini dipakai nada sintetis)
├── Code.gs       Backend bersama (tempel ke Apps Script yang sudah ada)
└── README.md
```

## Pasang

1. **Apps Script (sekali saja).** Tempel isi `Code.gs` ke project yang sudah ada, lalu **Deploy → Manage deployments → Edit → New version**.
2. **Daftarkan alamat situs baru.** Script properties → `APP_ORIGINS` berisi alamat situs ini (tanpa slash akhir). Jika sudah ada isinya, tambahkan dengan koma:
   `https://ppbltahun2025.github.io/Amplop-Kasih,https://alamat-situs-baru`
   Contoh alamat situs baru di GitHub Pages: `https://ppbltahun2025.github.io/Kejutan-Ultah`.
3. **Unggah situs.** Buat repo baru (misalnya `Kejutan-Ultah`) berisi `index.html` dan `musics.mp3`, lalu aktifkan GitHub Pages. Cloudflare Pages atau hosting statis lain juga bisa. `Code.gs` tidak perlu diunggah.
4. **Worker.** Tidak perlu diubah. Jika kamu pernah mengisi secret `ALLOWED_ORIGINS`, tambahkan domain situs baru (hanya domainnya, tanpa path).
5. **Uji.** Buka situsnya, masuk (login terpisah per domain, akunnya tetap sama), buat kejutan, simpan, lalu buka link `?v=ID` di perangkat lain.

`API_URL` di bagian atas script `index.html` sudah berisi alamat Worker `https://amplop-kasih.ppbltahun2025.workers.dev/api`. Ubah hanya jika Workernya berganti.

## Catatan

- Link kejutan berbentuk `https://alamat-situs-baru/?v=ID`. Email verifikasi dan email "buka kejutan" otomatis memakai alamat situs tempat pengguna mendaftar atau menyimpan, asalkan sudah terdaftar di `APP_ORIGINS`.
- Kartu tetap disimpan di folder Drive akun dan tab `Cards` pada sheet master (kolom `kind` = `birthday`).
- Video latar maksimal 6 MB (MP4 atau WebM). Detail alur animasi, kursor kue, dan musik ada di README proyek Amplop Kasih.
