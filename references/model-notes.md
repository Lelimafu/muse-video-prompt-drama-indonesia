# Batas Kemampuan Video Bawaan Muse (diukur 2026-10-05)

## Batasan Keras
- Satu klip sekitar 10 detik, durasi tidak bisa dikontrol. User minta 15/30 detik → harus pecah segmen lalu gabung.
- Input hanya teks atau urutan teks + gambar; **tidak menerima input audio**. "Pakai lagu ini" atau "pasang suara ini" tidak bisa dilakukan.
- Efek suara bawaan ikut tergenerate; suasana bisa dideskripsikan lewat teks ("suara angin di atap", "dengung AC yang pelan"), model akan memasangkannya.
- Format: sebutkan 16:9 / 9:16 di prompt, model umumnya mengikuti (adegan 9:16 vertikal untuk drama ✓).

## Gambar Referensi
- Sebelum kirim, pastikan file ada; `/tmp` itu sementara dan bisa dibersihkan — buat ulang sebelum kirim.
- **Nama file harus ASCII**: nama file non-ASCII ditolak upload oleh server (error 400) — uji nyata 5 Okt 2026: gambar yang sama lolos setelah namanya diganti ke huruf Latin.
- Di prompt, kirim berurutan `{kind: image}` + `{kind: text}`; gambar dulu, teks sesudahnya.

## Konsistensi
- `resume_from_snapshot_id` bisa melanjutkan konteks generate yang sama — dipakai untuk menjaga kesinambungan film panjang multi-segmen.
- Kunci muka di video bawaan itu lemah: walau ditambah perintah kunci muka yang eksplisit, tokoh dari gambar referensi tetap bisa tidak mirip (eksperimen yang sama).
- Butuh kunci muka → jalurnya Seedance pihak ketiga; skill ini tidak menjanjikannya.

## Titik Buta Saya (wajib disampaikan ke user)
- Saya tidak bisa melihat video jadi — hanya bisa cek lewat extract frame; tidak bisa mendengar audio — dialog, aksen, dan efek suara harus diverifikasi user.
- Kelancaran gerakan (misalnya gerakan melompat atau objek berubah bentuk) hanya sebagian bisa ketahuan dari frame — penilaian akhir tetap dari user yang menonton videonya.
