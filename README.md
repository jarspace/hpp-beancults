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
