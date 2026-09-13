# PACAR.BY/RIFQI

Website formulir kenalan dengan desain mobile-first dan neo-brutalism.

## Isi paket

- `index.html`: HTML, CSS, JavaScript, ikon SVG, dan foto wajah Rifqi dalam satu file.
- `PETUNJUK.md`: panduan penggunaan, aktivasi email, dan catatan implementasi.

Tidak ada npm, proses build, atau file foto tambahan yang perlu dipasang.
Font Google dimuat secara opsional. Saat tidak tersedia, halaman memakai font pengganti dari perangkat. Tidak ada file font yang disertakan.

## PENTING: aktifkan pengiriman email

Penerima sudah diatur ke: **naufalrifqi203@gmail.com**.

Pengiriman memakai FormSubmit, bukan `mailto:`. Pengunjung tidak perlu membuka aplikasi email.

1. Jalankan `index.html` melalui web server atau unggah ke hosting statis milikmu. Gunakan HTTPS untuk situs publik.
2. Isi formulir satu kali dari alamat situs tersebut, lalu klik **Kirim Lamaran**. Gunakan data uji milikmu sendiri.
3. Buka inbox atau folder Spam **naufalrifqi203@gmail.com**. Cari email aktivasi dari **FormSubmit**, lalu klik tautan aktivasi.
4. Kirim satu lamaran uji lagi dari situs tersebut dan pastikan email benar-benar diterima, lengkap dengan semua jawabannya, sebelum membagikan situs.

FormSubmit mensyaratkan konfirmasi penerima sebelum meneruskan email. File ini sudah terhubung ke endpoint yang benar, tetapi status aktivasi inbox kamu belum diverifikasi. Aktivasi mungkin perlu diulang setelah mengubah alamat penerima atau konfigurasi situs. Konfirmasi yang diberikan layanan di browser bukan bukti email sudah masuk ke inbox.

### Mencoba di komputer

Buka terminal di folder yang berisi `index.html`. Dengan Python terpasang:

```sh
python -m http.server 8000
```

Di Windows, bila perintah `python` tidak tersedia tetapi Python Launcher terpasang:

```sh
py -m http.server 8000
```

Di macOS/Linux, nama perintahnya bisa `python3`.

Buka browser di `http://localhost:8000`.

Klik dua kali file HTML hanya untuk pratinjau. Kode menolak pengiriman dari URL `file://` agar tidak menampilkan keberhasilan palsu. Internet tetap dibutuhkan untuk mengirim data ke FormSubmit. Untuk menerima pengunjung dari perangkat lain, unggah file ke hosting; localhost bukan alamat situs publik.

## Field dan perilakunya

**Nama** adalah input teks wajib, 2-80 karakter. **Umur** menerima angka bulat 18-120 tahun. Batas minimum 18 tahun adalah konfigurasi form ini, bukan pernyataan tentang persyaratan hukum. **Hobi** berupa textarea wajib dengan batas 500 karakter dan penghitung karakter.

**3 Makanan favorit** terdiri dari tiga input terpisah, masing-masing wajib dan maksimal 100 karakter. Pengisian tidak memaksa ketiga jawaban berbeda karena yang diminta adalah tiga field terpisah.

**Jam Available** memiliki dua pilihan:

- **Pilih jam**: dua input `type="time"`, Dari dan Sampai. Nilai dan ringkasan memakai format 24 jam. Tampilan pemilih native bisa mengikuti pengaturan bahasa/jam browser atau perangkat, termasuk AM/PM pada perangkat tertentu.
- **24 jam**: berarti tersedia seharian, bukan hanya format tampilan jam. Kedua input jam tidak wajib dan dinonaktifkan. Jawaban dikirim sebagai `24 jam (sepanjang hari)`.

Rentang 22:00-02:00 diperbolehkan dan ditandai sebagai selesai pada hari berikutnya. Jam mulai dan selesai yang sama ditolak; pengguna diarahkan memilih 24 jam. Rentang yang sebelumnya diisi tetap tersedia saat kembali dari mode 24 jam. Zona waktu perangkat ditampilkan dan dikirim bersama jawaban, sehingga jam tidak otomatis diasumsikan sebagai WIB.

**Keahlian khusus** adalah input teks wajib, maksimal 250 karakter. **Persetujuan** berisi teks pakta dari permintaan dan checkbox wajib yang tidak dicentang secara otomatis. Karakter `|` di akhir kalimat asli tidak ditampilkan karena merupakan karakter penutup yang tidak diperlukan.

## Yang dikirim ke email

Nama, umur, hobi, ketiga makanan favorit, mode ketersediaan, rentang waktu atau 24 jam, jam mulai/selesai, zona waktu, keahlian, persetujuan, versi dan isi pakta, ID lamaran, serta waktu pengiriman UTC.

Subjek email: `Lamaran Calon Pacar | [Nama]`.
Template email: tabel bawaan FormSubmit.

Tidak ada input kontak/email pendaftar karena tidak diminta. Karena itu, email notifikasi tidak menyediakan alamat Reply-To milik pendaftar.

## Validasi, kegagalan, dan privasi

Validasi menolak isian wajib yang kosong atau hanya spasi. Fokus dipindahkan ke field pertama yang tidak valid. Selama pengiriman, tombol dan isian dinonaktifkan untuk mencegah klik berulang atau perubahan jawaban. Tidak ada pengiriman ulang otomatis.

Jika layanan gagal, menolak permintaan, membatasi frekuensi, atau koneksi terputus, isian tetap berada di halaman. Timeout 25 detik diperlakukan sebagai status belum pasti karena server mungkin sudah menerima data. Retry dengan jawaban yang sama memakai ID lamaran yang sama; ini membantu mengenali duplikat di email, bukan jaminan idempotensi server.

Layar hasil baru muncul setelah respons FormSubmit menyatakan sukses (`true` atau string `"true"`). Respons `"false"` tidak dianggap sukses. Pesan aktivasi dikenali apabila layanan menyebutkannya. Tidak ada klaim bahwa frontend bisa memastikan email benar-benar masuk inbox.

Tidak ada penyimpanan jawaban di localStorage, sessionStorage, database, atau layanan analitik yang ditambahkan oleh file ini. Jawaban tetap di memori halaman sampai pengguna memulai formulir baru, memuat ulang, atau menutup halaman; browser dapat menerapkan perilaku pemulihan formnya sendiri. FormSubmit memproses kiriman sesuai kebijakan layanannya. Pengguna diberi penjelasan di dekat tombol kirim.

Alamat penerima dan endpoint dapat dilihat di source HTML, sebagaimana endpoint form publik. Tidak ada password Gmail, kredensial SMTP, atau API key rahasia di frontend. Jangan menambahkannya.

Implementasi memakai honeypot dasar dan `_captcha=false` untuk alur AJAX tanpa pindah halaman. Ini bukan perlindungan spam yang kuat. Untuk publikasi dengan risiko spam/traffic tinggi, pindahkan pengiriman ke backend dengan validasi server, pembatasan request, dan CAPTCHA yang diverifikasi server. Validasi di browser tidak mencegah orang mengirim request langsung ke endpoint.

Halaman memakai `noindex, nofollow` agar tidak sengaja dioptimalkan untuk pencarian. Ini bukan kontrol akses; siapa pun yang mengetahui URL publik dapat membukanya.

## Pengujian yang sudah dilakukan

20 pemeriksaan lolos pada Chromium 144 dengan viewport 320, 360, 390, 430, 768, 920, 1024, dan 1440 piksel. Pemeriksaan meliputi susunan field, overflow horizontal, validasi, persetujuan wajib, mode 24 jam, lintas tengah malam, kelengkapan payload, reset, pencegahan klik ganda, pemeliharaan jawaban setelah gagal, offline, timeout, rate limit, dan respons aktivasi. Teks jawaban ditampilkan memakai `textContent`, bukan HTML mentah.

**Batas pengujian:** HTML dirender di dokumen browser dalam memori karena navigasi jaringan browser lingkungan pengembangan dibatasi. Font eksternal memakai fallback lokal. Request pengiriman diuji dengan respons jaringan simulasi; **tidak ada email uji yang dikirim ke inbox kamu**. Pengiriman nyata dari situs publik, aktivasi akun, dan penerimaan di Gmail tetap perlu diuji mengikuti langkah aktivasi di atas. Belum diuji pada perangkat iOS/Android fisik atau Safari.

## Mengubah konfigurasi

- Email penerima: ubah `RECIPIENT_EMAIL` di bagian `<script>` dan alamat pada atribut `action` form.
- Warna utama: ubah variabel `--paper`, `--ink`, `--pink`, dan `--lime` di CSS.
- Batas umur: ubah `min`/`max` pada input `umur` dan validasi di `errorMessage()`.
- Batas karakter: ubah `maxlength` input terkait dan teks penghitung bila relevan.
- Foto sudah dipotong ke wajah dari foto asli yang diberikan; tubuh dan metadata foto asli tidak disertakan. Untuk menggantinya, ubah `src` pada gambar di `.portrait-frame`.

## Dokumentasi acuan

- FormSubmit setup dan opsi: https://formsubmit.co/
- AJAX/fetch: https://formsubmit.co/ajax-documentation
- Aktivasi, troubleshooting, dan web server: https://formsubmit.co/help
- Input waktu native: https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/time
