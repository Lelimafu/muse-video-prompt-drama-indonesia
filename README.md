# Muse Video Prompt Skill — Versi Drama Indonesia

**Workflow prompt untuk video bawaan Muse (Muse Video), diadaptasi untuk drama Indonesia.**

Diedit oleh **Le Li Mafu**.

Diadaptasi dari [masonmosen/muse-video-prompt-skill](https://github.com/masonmosen/muse-video-prompt-skill) (MIT). Isi asli berbahasa Mandarin dengan default dialog Mandarin Taiwan — versi ini sudah diterjemahkan dan disesuaikan: balasan Bahasa Indonesia, default dialog Bahasa Indonesia sehari-hari, format vertikal 9:16, adegan 8 detik, kamera diam total.

## Sumber Asli
Skill ini adalah adaptasi dari **[masonmosen/muse-video-prompt-skill](https://github.com/masonmosen/muse-video-prompt-skill)** oleh Mason Mosen, lisensi MIT. Semua gagasan workflow, template prompt 6 bagian, teknik sambung segmen, dan kartu kasus awal berasal dari repo tersebut. Yang diubah di sini hanya bahasa dan penyesuaian untuk drama Indonesia (lihat "Yang diubah dari versi asli" di bawah). Lisensi MIT asli tetap disertakan di file `LICENSE`. Adaptasi dan edit ke versi drama Indonesia oleh **Le Li Mafu**.

## Yang diubah dari versi asli
- Semua instruksi dan template diterjemahkan ke Bahasa Indonesia.
- Default dialog: **Bahasa Indonesia sehari-hari yang natural** (bukan Mandarin Taiwan).
- Template prompt dilengkapi contoh adegan drama Indonesia (ruang tamu, teras, kantor, dapur) dan aturan kamera diam.
- Kartu kasus asli (eksperimen 5 Okt 2026) tetap disertakan sebagai referensi — isinya masih bahasa Mandarin; kasus baru ditulis dalam Bahasa Indonesia.
- Skill pendamping (`cinematic-shot-design`, `ai-director-video-review`) TIDAK termasuk dalam paket ini — keduanya opsional.

## Isi paket
```
muse-video-prompt-drama-indonesia/
├── SKILL.md                  # Pintu masuk: workflow + aturan operasional
├── CONSTITUTION.md           # Lima prinsip desain workflow ini
├── README.md                 # File ini
├── LICENSE                   # MIT (dari repo asli)
├── references/               # Pengetahuan detail (dibaca saat dibutuhkan)
│   ├── prompt-template.md    # Template prompt 6 bagian + varian
│   ├── dialogue.md           # Aturan dialog Bahasa Indonesia
│   ├── consistency.md        # Strategi konsistensi tokoh
│   ├── stitch-workflow.md    # Pecah segmen → generate → gabung → verifikasi
│   ├── model-notes.md        # Batas kemampuan Muse Video (terukur)
│   ├── integration.md        # Alur dengan skill pendamping
│   └── cases/                # Kartu kasus (pelajaran dari tiap eksperimen)
└── bin/
    └── extract_frames.py     # Script extract frame untuk verifikasi
```

## Cara install (di akun Muse yang bisa bikin video)
1. Lampirkan file ZIP ini di chat Muse tersebut.
2. Minta Muse untuk menyimpan dan mengikuti skill ini sebagai skill yang bisa dipakai ulang.
3. Mulai pakai dengan kalimat biasa, misalnya: "Buatkan video drama 8 detik dari prompt ini" atau "Bikinkan prompt adegan ruang tamu untuk episode 3".

## Yang penting diingat
- Satu klip maksimal 10 detik — adegan drama standar 8 detik, film panjang dipecah per segmen lalu digabung ffmpeg.
- Video bawaan Muse **tidak bisa menjanjikan kunci muka** — konsistensi dijaga lewat deskripsi tokoh yang disalin kata-per-kata di semua segmen + sambungan snapshot.
- Tiap hasil generate harus dicek frame-nya dulu sebelum diserahkan; audio dan gerakan bibir harus diverifikasi user.
