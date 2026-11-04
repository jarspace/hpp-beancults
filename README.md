# HPP Beancults v8.9.7

## Perubahan v8.9.6 – Ultra compact recipe form
- Kartu bahan dipadatkan lagi dengan pengurangan padding, jarak, dan tinggi kontrol secara terukur.
- Ringkasan jumlah bahan dan total sementara dibuat lebih tipis; daftar ringkasan saat dibuka juga lebih rapat.
- Panel Biaya Ops/Overhead diubah menjadi kontrol satu baris yang lebih pendek; keterangan sekunder disembunyikan pada layar HP.
- Bar ringkas HPP dan harga jual di footer dipendekkan.
- Target sentuh pemilihan bahan tetap 38 px dan input takaran 40 px agar masih layak digunakan.
- Rumus HPP, margin, struktur Firestore, dan penyimpanan tidak diubah.

## Catatan pengujian
- ZIP dan sintaks JavaScript diperiksa secara lokal. Perlu pengujian visual pada HP untuk memastikan ukuran baru nyaman dan tidak terlalu kecil.

# HPP Beancults v8.9.5

## Perubahan v8.9.5 – Compact ingredient cards
- Kartu komposisi bahan dibuat lebih pendek dengan mengurangi padding dan jarak vertikal.
- Tombol pemilihan bahan tetap memiliki tinggi sentuh yang nyaman.
- Input takaran dipadatkan menjadi 88 × 46 px; satuan dan HPP item tetap terlihat.
- Rumus HPP, struktur Firestore, dan alur penyimpanan tidak diubah.



## Perubahan v8.9.4 – Composition-first mobile layout
- Pada layar HP, panel perhitungan harga jual dimulai dalam kondisi ringkas.
- Bar ringkas tetap menampilkan Modal/HPP dan Harga Jual Dasar (menu), atau HPP batch dan HPP per unit (prep).
- Ketuk bar ringkas untuk membuka/menutup pengaturan margin/harga atau rincian HPP prep.
- Tombol Batal dan Simpan tetap selalu terlihat.
- Area komposisi mendapat ruang vertikal lebih besar; tombol pemilihan bahan dan input takaran dipertahankan dengan area sentuh yang nyaman.
- Desktop tetap membuka panel perhitungan secara penuh saat modal dibuka.
- Tidak mengubah rumus HPP, margin, struktur Firestore, autentikasi, maupun format backup.

## Catatan pengujian
- Perlu diuji di perangkat HP: membuka/menutup panel harga, input margin dan harga manual, pemilihan bahan, input kuantitas, serta simpan menu dan prep.
- Pemeriksaan lokal meliputi integritas ZIP dan sintaks JavaScript. Belum merupakan pengujian langsung terhadap Firebase atau seluruh perilaku browser/perangkat.


## Perubahan v8.9.7 – Koreksi form mobile
- Tombol hapus diberi ruang tersendiri agar tidak menimpa pemilih bahan.
- Teks pemilih bahan dipersingkat menjadi “Pilih bahan…”.
- Kolom takaran diperkecil.
- Keterangan Biaya Ops / Overhead ditampilkan kembali.
- Rumus HPP dan struktur data Firebase tidak diubah.
