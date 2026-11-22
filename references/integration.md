# Integrasi Alur (CueShot)

Skill ini membentuk satu alur lengkap bersama dua skill pendamping buatan Mason (tidak termasuk dalam paket ini — keduanya opsional):

```
cinematic-shot-design (sebelum generate)
  Lokasi / emosi → pencocokan gaya sutradara → keputusan kamera → prompt yang bisa dijalankan
  (default satu shot; 2-3 shot hanya untuk rantai reveal-reaction-action,
   konfrontasi, pengungkapan lokasi yang bermakna, atau perubahan tempat/waktu)
        │
        ▼
muse-video-prompt-drama-indonesia (saat generate) ← skill ini
  Template 6 bagian → media.generate_video → sambungan snapshot multi-segmen → gabung ffmpeg
        │
        ▼
ai-director-video-review (sesudah generate)
  Tiga mode: single / variants / sequence
  → cek kelengkapan teknis + kontinuitas + jejak hasil generate
  → kesimpulan rilis (ready / post_fix / regenerate_segment / reject)
  → rencana perbaikan minimal (menunjuk ke titik waktu yang tepat, misal "jadikan 00:03.2 sebagai referensi lalu generate ulang 00:04.2–00:05.8")
```

## Aturan Penyambungan
- Output prompt dari cinematic-shot-design dipetakan dulu ke field template 6 bagian skill ini, baru diserahkan ke user untuk disahkan.
- Saat review, serahkan prompt, storyboard, gambar referensi, dan maksud cerita sekaligus ke ai-director-video-review — supaya perubahan narasi yang disengaja tidak salah dinilai sebagai kesalahan kontinuitas.
- Kalau kesimpulan review meminta "generate ulang sebagian", kembali ke langkah generate skill ini dan jalankan ulang hanya segmen itu (disambung dari snapshot segmen sebelumnya).
- Pisahkan pengamatan dan dugaan: yang tidak bisa dipastikan di laporan review jangan ditulis sebagai fakta — tandai sebagai "menunggu konfirmasi".
