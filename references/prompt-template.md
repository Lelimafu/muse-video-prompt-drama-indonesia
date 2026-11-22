# Template Prompt 6 Bagian (Drama Indonesia)

> Gagasan dari six-part prompt LuoJiangYong/muse-video-skill, field ditulis ulang untuk workflow ini.
> Setelah ditulis, tunjukkan ke user untuk disahkan; versi sah dipakai apa adanya di `media.generate_video`.

## Template Umum

```
[Durasi / format] [Satu kalimat adegan]
Tokoh: usia / jenis kelamin / ciri wajah / pakaian / gaya rambut (tepat sampai warna dan model)
Lokasi: tempat / waktu / cahaya / suasana
Alur / ketukan (pakai garis waktu):
  0-2 detik: ...
  2-5 detik: ...
  5-8 detik: ...
Bahasa kamera: posisi kamera / gerakan kamera / ukuran shot / statis (kamera DIAM TOTAL, tanpa zoom/push-in/dolly/pan/tilt) / gerakan yang dilarang — kamera TIDAK PERNAH mengikuti tokoh yang berjalan; kalau tokoh berjalan, ia berjalan di dalam frame yang diam (mendekati kamera atau melintasi frame), bukan kamera yang bergerak mengikutinya
Suara: suara lingkungan / efek suara / dialog (tulis jelas)
Bahasa dialog: Bahasa Indonesia sehari-hari yang natural (lihat dialogue.md; kalau tanpa dialog, hapus bagian ini)
Keterangan gambar referensi: (hanya bagian mana yang dirujuk — wajah / pakaian / lokasi; nama file harus ASCII)
Larangan: jangan…… (tulis satu per satu: wajah berubah, tubuh berubah proporsi, pakaian berubah, jari cacat, dan lain-lain)
```

## Contoh — Adegan Drama Indonesia (ruang tamu, 8 detik, 9:16)

```
[8 detik / vertikal 9:16] Seorang ibu menatap foto lama di ruang tamu saat senja.
Tokoh: Ratna, 42 tahun, perempuan, wajah oval lembut, rambut cokelat gelap bergelombang sebahu, blouse krem lengan panjang, celana panjang cokelat muda
Lokasi: ruang tamu rumah sederhana, sore hari, cahaya jingga masuk dari jendela, suasana hening dan sendu
Alur / ketukan:
  0-2 detik: Ratna duduk di sofa, memegang bingkai foto lama dengan kedua tangan, bingkai foto menghadap ke arah Ratna (dialah yang melihat isi foto), punggung bingkai menghadap kamera — punggung bingkai KOSONG dan polos, tidak ada foto di sisi belakang bingkai; isi foto: anak kecil berbaju merah
  2-5 detik: ia menatap foto itu, mata berkaca-kaca, napas tertahan
  5-8 detik: ia menunduk perlahan, memeluk bingkai foto erat di dada — saat dipeluk, foto menghadap ke kamera
Bahasa kamera: kamera DIAM TOTAL di depan sofa, medium shot, seluruh tubuh terlihat dari kepala sampai lutut, tanpa zoom, tanpa gerakan kamera
Suara: suara jam dinding berdetak pelan, napas Ratna yang tertahan
Dialog: Ratna berbisik pelan tapi jelas terdengar: "Maafkan Ibu, Nak..." (suara dan gerakan bibir sinkron, tanpa teks di layar)
Keterangan gambar referensi: hanya wajah Ratna dari foto referensi, jangan tiru pakaian atau latarnya
Larangan: jangan ubah wajah, jangan ubah pakaian, jangan ubah warna dinding, jangan ada teks di layar, jangan ada orang lain di frame, jangan kamera mengikuti tokoh yang berjalan, jangan tokoh membelakangi kamera saat berdialog, jangan putar foto menghadap kamera saat Ratna menatapnya — foto menghadap ke tokoh, kamera hanya melihat punggung bingkai, jangan ubah isi foto dalam bingkai, jangan ada foto di sisi belakang bingkai — punggung bingkai harus kosong dan polos; saat dipeluk ke dada, foto menghadap ke kamera
```

## Template Varian

### POV Alur Kehidupan
- Buka dengan pernyataan: `Seluruh adegan dari sudut pandang orang pertama: kamera adalah mata (pacar/teman) tokoh, tokoh itu sendiri TIDAK PERNAH masuk frame, hanya tangan atau lengan bawah sesekali di tepi frame.`
- Kalau "tokoh dilarang masuk frame", tulis sebagai aturan keras dan jadikan paragraf sendiri — aturan lemah akan diabaikan model (eksperimen 5 Okt 2026: dengan aturan lemah, bahu pacar masuk frame cukup besar).

### Monolog ke Kamera (talking-head)
- Tokoh menghadap kamera, pandangan ke lensa; tulis "bukan selfie, tidak ada kamera/ponsel di dalam frame".
- Dialog ditulis dengan tanda kutip, sertakan nada bicara, akhiran kalimat, dan syarat sinkronisasi gerakan bibir.

### Film Panjang Multi-Segmen (>10 detik)
- Tiap segmen satu prompt sendiri, buka segmen dengan: `Segmen ke-N dari film 30 detik (detik X-Y), lanjutkan tokoh / lokasi / cahaya / nuansa yang sama dengan segmen sebelumnya, wajah, pakaian, dan gaya rambut tokoh harus sama persis.`
- Tiap segmen hanya berisi 2–3 shot dari segmen itu saja, jangan tulis seluruh film.
- Saat generate, segmen berikutnya disambung pakai `resume_from_snapshot_id` dari segmen sebelumnya.
- **Adegan berjalan:** tokoh yang berjalan harus berjalan di dalam frame yang diam — mendekati kamera atau melintasi frame — jangan pernah menulis tokoh "berjalan ke jendela/ruangan lain" tanpa menegaskan kamera diam; model cenderung mengikuti tokoh dengan tracking kalau ia menyeberang ruangan (tes 22 Nov 2026).
- **Dialog antar segmen:** dialog hanya ditulis di ketukan saat wajah tokoh terlihat kamera (depan/profil); jangan letakkan dialog di ketukan tokoh membelakangi kamera atau berjalan menjauh.

### Contoh — Lanjutan segmen (tokoh berjalan, 8 detik, 9:16)

```
[8 detik / vertikal 9:16] Lanjutan adegan sebelumnya, orang dan tempat yang sama persis.
Tokoh: Ratna, 42 tahun, perempuan, wajah oval lembut, rambut cokelat gelap bergelombang sebahu, blouse krem lengan panjang, celana panjang cokelat muda
Lokasi: ruang tamu rumah sederhana yang sama, sore hari, cahaya jingga masuk dari jendela
Alur / ketukan:
  0-2 detik: Ratna meletakkan bingkai foto dengan hati-hati di atas meja di samping sofa, foto tetap menghadap ke arahnya; isi foto: anak kecil berbaju merah
  2-5 detik: ia berdiri perlahan dari sofa, mengusap air matanya dengan punggung tangan
  5-8 detik: ia berjalan pelan mendekati kamera, menatap ke arah kamera, wajah terlihat jelas
Bahasa kamera: kamera DIAM TOTAL di depan sofa, medium shot, seluruh tubuh terlihat, tanpa zoom, tanpa gerakan kamera, kamera tidak mengikuti tokoh yang berjalan
Suara: langkah kaki pelan di lantai, napas Ratna yang mulai tenang
Dialog: Ratna berbisik pelan tapi jelas terdengar: "Ibu pulang, Nak..." (suara dan gerakan bibir sinkron, tanpa teks di layar)
Keterangan gambar referensi: hanya wajah Ratna dari foto referensi, jangan tiru pakaian atau latarnya
Larangan: jangan ubah wajah, jangan ubah pakaian, jangan ubah warna dinding, jangan ada teks di layar, jangan ada orang lain di frame, jangan kamera mengikuti tokoh yang berjalan, jangan tokoh membelakangi kamera saat berdialog, jangan putar foto menghadap kamera saat Ratna menatapnya — foto menghadap ke tokoh, kamera hanya melihat punggung bingkai, jangan ubah isi foto dalam bingkai, jangan ada foto di sisi belakang bingkai — punggung bingkai harus kosong dan polos; saat dipeluk ke dada, foto menghadap ke kamera
```

## Disiplin Menulis
- Deskripsi tokoh di semua segmen **disalin kata-per-kata** — menulis ulang adalah penyebab nomor satu muka berubah.
- Arah hadap benda yang ditatap/dipegang tokoh ditulis eksplisit: benda menghadap ke tokoh, kamera hanya melihat punggungnya. (Tes 22 Nov 2026: foto lama menghadap kamera padahal Ratna yang menatapnya — logikanya terbalik, ia tidak bisa melihat foto yang sedang ia tatapi.)
- Isi benda yang ditatap/dipegang tokoh ditulis juga di ketukan (misal isi foto: anak kecil berbaju merah) supaya tidak berubah-ubah tiap segmen; tulis juga di Larangan. Punggung benda juga ditulis: punggung bingkai harus KOSONG dan polos — bahan punggungnya (kayu/karton) tidak perlu disebut, cukup tulis kosong dan tidak ada foto di sisi belakang; kalau tidak ditulis, model mengisi sisi belakang dengan foto lain. (Tes 22 Nov 2026: sisi belakang bingkai malah berisi foto punggung anak berbaju merah; foto referensi punggung bingkai: bingkai-foto-belakang-reference.jpg.) Arah foto mengikuti aksi: pegang-menatap = foto ke tokoh (punggung polos ke kamera); peluk ke dada = foto ke kamera.
- Garis waktu ditulis per segmen 8–10 detik; jangan tulis garis waktu panjang 15/30 detik (model akan memampatkannya).
- Daftar larangan lebih baik kebanyakan daripada kekurangan; hal yang pernah gagal (wajah berubah, tokoh lain masuk frame, kulit terlalu halus) tulis eksplisit di larangan.
