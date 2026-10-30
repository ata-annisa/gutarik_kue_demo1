# Gutarik Kue (proyek demo kuliah, gratis total)

Website toko kue dengan tiga antarmuka (Pembeli, Penjual, Admin). Satu file `index.html`, tanpa server, tanpa database, tanpa akun layanan apa pun. Di-hosting di GitHub Pages.

## Pasang
1. Buat repo publik di GitHub, upload `index.html` dan `README.md`.
2. Settings > Pages > Deploy from a branch > `main` > `/ (root)`.
3. Buka `https://USERNAME.github.io/NAMA-REPO/`.

## Isi gambar
Buka `index.html`, cari blok `ISI LINK GAMBAR DI SINI` di awal `<script>`, lalu isi:
- `IMG_HERO`: foto besar di beranda (rasio 4:3).
- `IMG_CAT`: foto bulat tiap kategori (rasio 1:1). Kosong = pakai foto produk pertama kategori itu.
- `IMG_PROD`: foto tiap produk (rasio 4:3), kunci = id produk.
Penjual juga bisa menempel link gambar lewat form Tambah/Edit produk.

## Akun contoh
| Role | Email | Password |
|---|---|---|
| Admin | admin@gk.demo | admin123 |
| Penjual | penjual@gk.demo | penjual123 |
| Pembeli | pembeli@gk.demo | pembeli123 |

Pendaftaran umum hanya membuat akun pembeli. Admin yang bisa mengubah role.

## Fitur
- Pembeli: katalog, cari/filter/urut, detail, keranjang, checkout (validasi, stok dicek ulang), riwayat pesanan.
- Penjual: statistik, tambah/edit/hapus produk milik sendiri, pesanan masuk, ubah status (Menunggu konfirmasi > Diproses > Siap > Selesai, atau Batal).
- Admin: statistik, ubah role dan aktif/nonaktif akun, moderasi (hapus) produk, semua pesanan, audit log.
- Role dicek di setiap aksi dan di setiap halaman dasbor (403 bila tidak berhak).

## Batasan (penting untuk dijelaskan saat presentasi)
- Ini SIMULASI. "Database" adalah localStorage di browser masing-masing, jadi data tidak dibagi antar perangkat dan hilang jika data browser dihapus. Penjual dan pembeli di perangkat berbeda tidak saling melihat pesanan.
- Pengecekan role berjalan di browser, sehingga bisa dilewati lewat DevTools. Keamanan sungguhan butuh backend server. Password di-hash SHA-256, tetapi tetap tersimpan di sisi klien.
- Tidak ada pembayaran, upload gambar, pagination, grafik, atau laporan per periode.
- Gambar memakai link eksternal (lihat "Isi gambar"). Kalau link kosong atau gagal dimuat, otomatis tampil ilustrasi SVG bawaan. Tidak ada upload file.
- Pengujian: sintaks JS lolos, dan tes otomatis di jsdom (bukan browser asli) lulus untuk guard 403, login, tambah produk, validasi, checkout mengurangi stok, dan penjual mengubah status. Belum dicoba di browser dan perangkat nyata, dan tampilan responsif belum dicek.
