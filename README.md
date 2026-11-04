# HPP Beancults — v8.7.7

Aplikasi web HPP/COGS untuk operasional F&B. Build ini mempertahankan struktur data Firebase dan fitur utama versi sebelumnya.

## Perubahan v8.7.0
- Perhitungan yield bahan tidak lagi menganggap nilai 0 sebagai 100% secara diam-diam.
- Validasi bahan: nama, harga beli, kuantitas beli, dan yield.
- Konversi satuan dibatasi pada pasangan yang didukung: kg↔gram dan liter↔ml. Satuan yang tidak kompatibel ditolak saat menyimpan resep.
- Validasi komposisi resep, jumlah bahan, hasil sub-resep, dan referensi sub-resep yang membentuk siklus.
- Penghitungan harga jual dan biaya platform diberi batas aman untuk mencegah pembagian dengan nol atau fee 100% ke atas.
- Operasi simpan/hapus Firebase kini ditunggu (`await`) dan kegagalannya ditampilkan kepada pengguna.
- Listener sinkronisasi Firebase menampilkan kesalahan jika akses/koneksi bermasalah.
- Cache Service Worker dinaikkan versinya agar browser mengambil aset build terbaru.
- Keterangan BEP diperjelas: ini estimasi rata-rata dengan asumsi semua menu memiliki proporsi penjualan sama, belum menggunakan volume penjualan aktual atau komisi platform.

## Menjalankan
1. Upload seluruh isi folder ke hosting statis yang mendukung HTTPS.
2. Pastikan `firebase-config.js` berada satu folder dengan `index.html`.
3. Login menggunakan akun Firebase Authentication yang sudah terdaftar.

## Catatan keamanan penting
- `firebase-config.js` berisi konfigurasi web Firebase. API key web Firebase bukan password; keamanan data harus ditegakkan melalui Firebase Authentication dan Firestore Security Rules.
- Build ini tidak menyertakan perubahan Firestore Security Rules karena aturan proyek aktif tidak tersedia di dalam arsip. Jangan menganggap data aman hanya karena aplikasi mewajibkan login.
- PIN Mode Dapur adalah pembatas tampilan di sisi browser, bukan mekanisme keamanan untuk menyembunyikan data dari pengguna yang memiliki akses developer tools atau Firestore.
- Sebelum mengganti build di hosting, simpan salinan versi lama dan lakukan pengujian login, baca/tulis data, serta mode offline pada akun uji.

## Batasan kalkulasi yang perlu diketahui
- Satuan yang didukung langsung: gram, kg, ml, liter, pcs, dan porsi. Konversi hanya dilakukan dalam kelompok massa atau volume yang kompatibel.
- Yield bahan diterapkan sebagai hasil bersih dari kuantitas pembelian.
- BEP saat ini masih berupa estimasi rata-rata per menu, bukan BEP berbobot berdasarkan bauran penjualan aktual.


## Perubahan v8.7.2
- Mencegah penghapusan bahan baku yang masih digunakan dalam resep.
- Mencegah penghapusan sub-resep yang masih digunakan resep lain.
- Menampilkan peringatan pada kartu resep jika ditemukan bahan/sub-resep hilang, satuan tidak cocok, atau takaran tidak valid.
- Menambahkan pilihan pengurutan resep dan tombol Reset Sort By pada daftar resep dan bahan baku.
- Reset Filter & Sort mengembalikan urutan ke A-Z sekaligus menghapus pencarian dan filter kategori; pada bahan baku, filter supplier juga direset.


## Perubahan v8.7.3
- Pagination pada Manajemen Resep: default 10 item pada layar HP dan 20 item pada layar lebih lebar.
- Pilihan jumlah item per halaman: 10, 20, atau 50.
- Informasi rentang item dan total resep, serta navigasi halaman.
- Sortir resep berdasarkan nama, HPP terendah/tertinggi, harga jual terendah/tertinggi, margin, dan tanggal perubahan.
- Pencarian, kategori, tab Menu/Prep, dan sortir diterapkan sebelum pagination.


## Perubahan v8.7.4
- Notifikasi mengambang untuk tambah, edit, dan hapus supplier, bahan baku, serta resep.
- Notifikasi otomatis hilang setelah sekitar 2,8 detik dan dapat ditutup manual.
- Peringatan ketika bahan/sub-resep masih digunakan juga tampil sebagai notifikasi mengambang.
- Notifikasi sukses muncul setelah operasi Firestore berhasil diselesaikan.


## Perubahan v8.7.5
- Posisi notifikasi mengambang dinaikkan agar berada di atas navigasi bawah, termasuk memperhitungkan safe area perangkat.


## Perubahan v8.7.7
- Modal tambah/edit bahan baku menggunakan layar penuh pada HP, dengan header tetap terlihat dan area form yang dapat digulir.
- Tombol Batal/Simpan pada form bahan tetap berada di bagian bawah area form dan memperhitungkan safe area perangkat.
- Modal resep memakai satu area scroll utama; bagian identitas resep tidak lagi memiliki scroll bersarang.
- Tinggi kontrol input/select pada form mobile ditingkatkan untuk memudahkan sentuhan dan mencegah zoom otomatis pada sebagian browser iOS.
- Tidak mengubah rumus HPP, struktur data Firestore, atau alur penyimpanan.
- Pemeriksaan yang dilakukan: integritas ZIP dan sintaks JavaScript. Belum merupakan pengujian langsung di browser/perangkat atau Firebase.


## Perubahan v8.7.7
- Toast reset filter resep dan bahan menggunakan notifikasi mengambang yang hilang otomatis.
- Resep baru menyimpan `createdAt` dan `updatedAt` (timestamp milidetik).
- Saat resep diedit, `createdAt` dipertahankan dan `updatedAt` diperbarui.
- Kartu resep menampilkan tanggal dibuat dan terakhir diubah. Resep lama tanpa `createdAt` ditandai belum tersedia, tanpa mengarang tanggal.


## v8.7.8
- Menambahkan cap waktu Dibuat dan Terakhir diubah pada kartu bahan baku.
- Bahan baru menyimpan createdAt dan updatedAt; saat edit, createdAt dipertahankan.
- Bahan lama tanpa createdAt ditandai belum tersedia, tanpa tanggal perkiraan.


## v8.7.9
- Menambahkan timestamp dibuat dan terakhir diubah pada kartu supplier.
- Supplier baru menyimpan `createdAt` dan `updatedAt`; saat diedit, `createdAt` dipertahankan.
- Validasi nama supplier wajib diisi dan mencegah duplikat tanpa membedakan huruf besar/kecil serta spasi di awal/akhir.
- Validasi duplikat dan kegagalan simpan menggunakan floating toast yang konsisten.
- Tidak mengubah rumus HPP atau struktur koleksi Firestore.


## v8.8.0 — Backup & Restore
- Ekspor bahan, resep, supplier, dan pengaturan ke JSON.
- Pemulihan memvalidasi versi backup dan UID akun yang sama.
- Pemulihan menggabungkan data berdasarkan ID dokumen; tidak menghapus dokumen lain.
- Proses restore dilakukan per dokumen; jika koneksi terputus di tengah proses, sebagian data mungkin sudah masuk. Jalankan ulang file backup yang sama setelah koneksi pulih.


## v8.8.1 – Restore Security Fix
- Restore hanya menerima koleksi `ingredients`, `recipes`, dan `suppliers`; koleksi tambahan/asing ditolak.
- Validasi ID dokumen: wajib berupa string, tidak kosong, tidak mengandung `/`, panjang maksimal 1.500 karakter, dan tidak duplikat per koleksi.
- Memastikan UID akun tetap sama selama proses restore.
- Validasi seluruh struktur dilakukan sebelum konfirmasi dan penulisan.
- Pengaturan tetap dipulihkan ke dokumen `settings/preferences`; merge tetap dipertahankan dan dokumen lain tidak dihapus.
- Tidak mengubah rumus HPP atau Firestore Security Rules.


## v8.9.0 – Recipe Integrity & Composition UX
- Added a sticky recipe-composition summary showing selected ingredients, quantities, and provisional ingredient total while scrolling.
- Added live integrity hints for missing ingredients/sub-recipes, invalid quantities, incompatible units, invalid ingredient purchase data, and sub-recipe cycles.
- Existing HPP calculation formulas and Firestore paths were not changed.


## v8.9.1 – Compact Recipe Composition Summary
- Ringkasan komposisi resep dibuat ringkas dan sticky.
- Daftar bahan terpilih dapat dibuka/tutup saat diperlukan.
- Jumlah bahan dan total sementara tetap terlihat saat daftar ditutup.
- Tidak mengubah perhitungan HPP, struktur Firestore, atau alur penyimpanan.


## v8.9.2 – Compact Mobile Price Panel
- Reduced mobile recipe-footer padding and vertical spacing.
- Made modal cost and margin cards more compact while preserving all inputs and values.
- Reduced the selling-price summary block height.
- Kept Cancel and Save buttons at a practical touch height.
- No changes to pricing formulas, HPP calculations, Firestore paths, or save behavior.
