# Workflow Pecah Segmen → Gabung → Verifikasi

## Pecah Segmen
- Pecah per ketukan, tiap segmen ≤10 detik (adegan drama standar 8 detik), tiap segmen 2–3 shot.
- Tiap prompt segmen dibuka dengan pernyataan hubungan lanjutannya (lihat template multi-segmen di prompt-template.md).

## Generate
- Segmen 1 digenerate seperti biasa, catat `snapshot_id` yang dikembalikan.
- Segmen ke-N+1 dikirim dengan `resume_from_snapshot_id = snapshot_id segmen ke-N`, tanpa mengirim ulang gambar referensi.
- Pastikan tiap segmen ukurannya sama (cek width/height pakai ffprobe); kalau tidak sama, jangan digabung dulu.

## Gabung
```bash
cd <folder eksperimen>
printf "file 'seg1.mp4'\nfile 'seg2.mp4'\nfile 'seg3.mp4'\n" > concat-list.txt
ffmpeg -y -loglevel error -f concat -safe 0 -i concat-list.txt -c copy <nama-film>-full.mp4
ffprobe -v error -show_entries stream=duration -of default=noprint_wrappers=1 <nama-film>-full.mp4
```
- Kalau codec dan ukuran sama, `-c copy` menggabung tanpa kehilangan kualitas dan cepat; kalau ada segmen yang ukurannya beda, samakan dulu dengan transcode baru digabung.

## Verifikasi
- Tiap segmen dicek pakai `bin/extract_frames.py <file-segmen> 3` (ambil 3 frame): apakah tokoh / pakaian / lokasi sesuai prompt.
- Film penuh dicek frame-nya di tiap sambungan segmen ±1 detik dan di tiap titik ketukan penting: cari ganti wajah, pakaian berubah mendadak, atau lokasi terputus.
- Tulis kesimpulan: mana yang sesuai / mana yang menyimpang / perkiraan penyebab penyimpangan; audio dan detail gerakan masuk daftar "menunggu verifikasi user".

## Penyerahan
- File per segmen tetap disimpan (user mungkin mau melihat satu segmen saja), film gabungan adalah penyerahan utama.
- Semua disimpan di `workspace/prompt-experiments/<tanggal>/`, penamaan: `<judul>-segN.mp4` / `<judul>-full.mp4`.
