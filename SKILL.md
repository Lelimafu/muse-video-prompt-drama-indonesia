---
name: "muse-video-prompt-drama-indonesia"
description: "Workflow prompt untuk video bawaan Muse (Muse Video), diadaptasi untuk drama Indonesia: template prompt 6 bagian → 3 keyframe → generate → sambung multi-segmen → verifikasi frame. Dialog Bahasa Indonesia, vertikal 9:16, adegan 8 detik, kamera diam. Diadaptasi dari masonmosen/muse-video-prompt-skill (MIT)."
---

# Muse Video Studio — Workflow Video untuk Drama Indonesia

## Tujuan
Video bawaan Muse (Muse Video) dari prompt sampai jadi film: tulis prompt, generate, sambung film panjang per segmen, verifikasi frame. Khusus untuk drama Indonesia vertikal 9:16.

## Workflow
1. **Desain adegan** (opsional, untuk adegan kompleks): tentukan dulu gaya sutradara dan keputusan kamera; hasilnya langsung jadi bahan prompt.
2. **Tulis prompt**: pakai template 6 bagian di `references/prompt-template.md`. Prompt final dari user dipakai apa adanya di `media.generate_video`, jangan diubah atau ditambah-tambah. Default dialog: Bahasa Indonesia sehari-hari (lihat `references/dialogue.md`), ditulis terpisah dan jelas.
3. **Buat keyframe dulu (otomatis, wajib)**: sebelum generate video apa pun, OTOMATIS buat 3 opsi keyframe (tiga variasi framing/komposisi dari prompt yang sama) dan tunjukkan ke user; user memilih satu dan mengunci (lock). Video HANYA digenerate dari keyframe yang sudah dikunci — jangan pernah langsung generate video dari prompt tanpa keyframe. Begitu user memilih satu keyframe, LANGSUNG generate videonya — jangan tunda, jangan minta konfirmasi tambahan.
4. **Generate**: teks dulu; kalau pakai gambar referensi, pastikan file-nya ada dan nama file ASCII (nama file non-ASCII ditolak upload, error 400). Batas kemampuan lihat `references/model-notes.md`.
5. **Film panjang (>10 detik)**: pecah per ketukan, tiap segmen satu prompt sendiri; segmen berikutnya disambung dari `snapshot_id` segmen sebelumnya supaya tokoh dan lokasi tetap nyambung; terakhir gabung pakai ffmpeg. Lihat `references/stitch-workflow.md`.
6. **Verifikasi**: tiap segmen di-extract frame-nya pakai `bin/extract_frames.py` dan dicek sendiri; untuk review resmi pakai skill review video (tiga mode: satu klip / beberapa versi / adegan berurutan, lengkap dengan bukti frame + kesimpulan rilis + perbaikan minimal). Audio, gerakan bibir, dan kelancaran gerakan saya tidak bisa lihat/dengar — harus dinyatakan jelas dan diserahkan ke user untuk verifikasi akhir.
7. **Simpan pelajaran**: tiap eksperimen ditulis jadi kartu kasus di `references/cases/` (poin prompt, hasil, penyimpangan, pelajaran).

## Skill Terkait (tidak termasuk dalam paket ini)
- Sebelum generate: `cinematic-shot-design` — desain kamera dan pencocokan gaya sutradara, output berupa prompt yang bisa langsung dipakai.
- Sesudah generate: `ai-director-video-review` — review video: kelengkapan teknis, kontinuitas, jejak hasil generate; output kesimpulan rilis dan rencana perbaikan.
- Alur lengkap lihat `references/integration.md`.

## Kontrak Output
- File video jadi (`workspace/prompt-experiments/<tanggal>/`); film panjang juga disertakan versi gabungannya, file per segmen tetap disimpan.
- Kesimpulan cek frame: mana yang masuk sesuai prompt, mana yang melenceng, dan perkiraan penyebab melencengnya.
- Daftar jelas apa yang harus diverifikasi user (audio, gerakan bibir, detail gerakan) — tanpa ditutup-tutupi.

## Aturan Operasional
1. Semua balasan pakai Bahasa Indonesia.
2. Prompt yang dikirim ke model adalah versi final user; versi yang saya tulis ditunjukkan dulu ke user, baru dijalankan setelah dikonfirmasi.
3. Jangan janjiin kunci muka (face lock) dan jangan jamin gambar referensi pasti mirip — itu batas kemampuan model (lihat `references/consistency.md`); sampaikan dulu sebelum mulai.
4. Satu klip maksimal 10 detik (keras); adegan drama standar 8 detik. Kalau user mau lebih panjang, tawarkan skema pecah segmen + sambung, jangan cuma kasih satu klip 10 detik.
5. Gambar referensi hanya pakai nama file ASCII; `/tmp` itu sementara, pastikan file ada sebelum dikirim.
6. Tiap hasil generate harus sudah dicek frame-nya sebelum diserahkan; video yang belum dicek jangan dibilang "tidak ada masalah".
7. Dalam kondisi apa pun jangan mengarang detail gambar/suara — yang belum diverifikasi, katakan belum diverifikasi.
8. Aturan kamera drama: kamera DIAM TOTAL, framing tidak berubah, semua tokoh tetap terlihat, tanpa zoom/push-in/dolly/pan/tilt — kecuali user minta lain. Kamera TIDAK PERNAH mengikuti tokoh yang berjalan: kalau tokoh berjalan, ia berjalan di dalam frame yang diam (mendekati kamera atau melintasi frame), bukan kamera yang bergerak mengikutinya. (Pelajaran tes 22 Nov 2026: aturan "diam total" saja tidak ditaati model saat tokoh berjalan menyeberang ruangan — kamera ikut tracking sampai ke jendela.)
9. Saat dialog, wajah tokoh yang bicara harus terlihat kamera (menghadap depan atau profil), jangan membelakangi kamera — kalau tidak, gerakan bibir tidak bisa diverifikasi. (Tes 22 Nov 2026: segmen 2 berakhir membelakangi kamera tepat saat dialog diucapkan.)
10. Dialog berbisik harus tetap jelas terdengar: tiap kata terucap jelas dan utuh, jangan terlalu pelan sampai hilang. (Tes 22 Nov 2026: bisikan "Maafkan Ibu, Nak..." tidak tertangkap transkrip — kata "Nak"-nya hilang; dialog kedua "Ibu pulang, Nak." tidak tertangkap sama sekali.)
11. Arah foto mengikuti aksi tokoh (logika, bukan aturan kaku): saat tokoh MEMEGANG sambil MENATAP bingkai, foto menghadap ke tokoh — kamera hanya melihat punggung bingkai yang polos (tidak ada foto di sisi belakang; bahan punggung tidak perlu disebut, model mengisinya sendiri). Saat tokoh MEMELUK bingkai ke dada, foto menghadap ke KAMERA — penonton melihat fotonya. Singkatnya: cukup tulis aksinya — 'menatap' = punggung polos otomatis; 'memeluk' = foto ke kamera otomatis. (Tes 22 Nov 2026: foto lama menghadap kamera padahal Ratna yang menatapnya — logikanya terbalik; take berikutnya sisi belakang bingkai malah berisi foto punggung anak berbaju merah.)
12. Setiap mau generate video, OTOMATIS bikin dulu 3 keyframe (tiga opsi framing/komposisi) dan tunjukkan ke user; video baru digenerate setelah user memilih dan mengunci satu keyframe. Jangan pernah langsung generate video dari prompt tanpa keyframe. Begitu keyframe dipilih, LANGSUNG generate — tanpa penundaan. (Dodot 22 Nov 2026: keyframe-first = cara paling benar; video langsung dari prompt gagal — foto menghadap kamera sejak frame 0, padahal keyframe gambarnya benar.)
