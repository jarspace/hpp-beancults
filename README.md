# HPP Beancults — v8.6.0

Aplikasi web HPP/COGS untuk operasional F&B. Build ini mempertahankan struktur data Firebase dan fitur utama versi sebelumnya.

## Perubahan v8.6.0
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
