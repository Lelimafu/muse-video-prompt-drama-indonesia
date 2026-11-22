# Indeks Pustaka Kasus

Kasus awal berasal dari sesi eksperimen prompt video bawaan pada 2026-10-05 — satu kasus per baris, terus ditambah. File kasus awal (`cases-2026-10-05.md`) masih berbahasa Mandarin; kasus baru ditulis dalam Bahasa Indonesia.

| Tanggal | Kasus | Jenis | Pelajaran Utama |
|---|---|---|---|
| 2026-10-05 | [POV pacar di pintu masuk](cases-2026-10-05.md) | POV alur kehidupan | Nama file gambar berbahasa Mandarin ditolak upload (400); diganti nama Latin langsung lolos |
| 2026-10-05 | [Monolog kunci muka kuat](cases-2026-10-05.md) | Monolog + gambar referensi | Perintah kunci muka yang kuat pun hasilnya tetap tidak mirip → kunci muka bawaan itu lemah |
| 2026-10-05 | [Monolog teks murni](cases-2026-10-05.md) | Monolog teks murni | Setelah gambar referensi dihapus, tokohnya justru lebih natural |
| 2026-10-05 | [Metro Tokyo](cases-2026-10-05.md) | Realistis 9:16 | Minta 15 detik tapi dipadatkan jadi 10 detik; warna lantai melenceng |
| 2026-10-05 | [Menari pedang di hutan bambu](cases-2026-10-05.md) | Gaya sinematik | Gerakan padat tetap terjaga; kualitas gambar bagus |
| 2026-10-05 | [POV matahari terbenam di atap](cases-2026-10-05.md) | POV alur kehidupan | Aturan lemah membuat bahu pacar masuk frame → aturan harus ditulis keras |
| 2026-10-05 | [Pagi Jumat di gang Beijing v1/v2](cases-2026-10-05.md) | Realistis + gambar referensi | Gambar referensi hanya dinyatakan merujuk tokoh; v2 arah awalnya terbalik |
| 2026-10-05 | [Mahjong 30 detik](cases-2026-10-05.md) | Multi-segmen | Sambungan snapshot membuat tiga segmen tokohnya nyambung; gabung ffmpeg tanpa kehilangan kualitas |
| 2026-11-22 | [Prompt biasa vs template 6 bagian (Ratna ruang tamu)](cases-2026-11-22.md) | Drama 9:16 | Template 6 bagian saja (tanpa skill terinstall) sudah bikin wajah, baju, framing, dan ketukan jauh lebih nurut |
| 2026-11-22 | [Segmen 2: kamera ikut tracking saat tokoh berjalan](cases-2026-11-22.md) | Drama multi-segmen | Aturan "kamera diam total" saja tidak ditaati saat tokoh berjalan — harus eksplisit "kamera tidak pernah mengikuti tokoh" |
| 2026-11-22 | [Gabungan dengan skill: sambungan lebih mulus, dialog bisikan hilang](cases-2026-11-22.md) | Drama multi-segmen | Stitching snapshot memperbaiki sambungan; bisikan terlalu pelan membuat kata hilang di transkrip |
| 2026-11-22 | [Foto menghadap kamera, bukan ke tokoh](cases-2026-11-22.md) | Drama 9:16 | Foto yang ditatap tokoh harus menghadap ke tokoh — kalau tidak ditulis, model membaliknya ke kamera |
| 2026-11-22 | [Punggung bingkai malah berisi foto](cases-2026-11-22.md) | Drama 9:16 | Punggung benda harus ditulis kosong dan polos — kalau tidak, model mengisi sisi belakang dengan foto lain |
| 2026-11-22 | [Logika arah foto: pegang-menatap vs peluk](cases-2026-11-22.md) | Drama 9:16 | Arah foto mengikuti aksi: pegang-menatap = foto ke tokoh; peluk ke dada = foto ke kamera |
| 2026-11-22 | [Keyframe dulu sebelum generate video](cases-2026-11-22.md) | Drama 9:16 | Jangan langsung generate dari prompt — bikin dulu 3 keyframe, lock satu, langsung generate |

## Cara Menambah Kasus Baru
Salin satu baris tabel di atas, lalu tambahkan kartu kasusnya ke file `cases-<tanggal>.md` dengan format:

```
## [Judul kasus] — <tanggal>
- Prompt (poin penting):
- Hasil:
- Penyimpangan:
- Pelajaran:
```
