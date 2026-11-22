# Strategi Konsistensi Tokoh (Drama Indonesia)

> Garis jujur: tidak ada trik prompt yang bisa memaksa platform mengunci wajah. Konsistensi adalah "disiplin + peluang", bukan jaminan.

## Cara yang Efektif (urut dari yang paling terbukti)
1. **Deskripsi tokoh disalin kata-per-kata**: deskripsi tokoh yang sama ditempel apa adanya ke setiap prompt segmen — menulis ulang adalah penyebab nomor satu muka berubah.
2. **Gambar referensi (lemah)**: gambar referensi di video bawaan hanya sedikit membantu mengunci wajah (eksperimen 5 Okt 2026: perintah kunci muka yang kuat pun hasilnya tetap tidak mirip orangnya). Boleh dipakai, tapi jangan berharap banyak.
3. **Perintah kunci muka yang kuat** (lebih baik daripada tidak ada, taruh di awal prompt):
   ```
   Tokoh dalam video ini harus orang yang sama dengan di gambar referensi.
   Bentuk wajah, fitur, jarak antar mata, proporsi hidung dan bibir,
   serta garis wajah harus sama persis dengan gambar referensi, tidak boleh
   berubah di tengah jalan, tidak boleh jadi wajah orang lain, tidak boleh
   jadi wajah ala selebgram. Identitas wajah di gambar referensi adalah
   prioritas tertinggi.
   ```
4. **Pernyataan batas gambar referensi**: sebutkan hanya bagian mana yang dirujuk ("hanya rujuk fitur wajah, jangan rujuk pakaian, aksesori, gaya rambut, atau latar") supaya model tidak meniru sembarangan.
5. **Sambungan snapshot**: film panjang multi-segmen pakai `resume_from_snapshot_id` berantai (uji nyata 30 detik: tiga segmen tokohnya tetap nyambung).
6. **Jangkar larangan**: `jangan ada perubahan wajah, jangan ada perubahan proporsi tubuh, jangan ada pakaian berubah bentuk, jangan ada jari cacat` masukkan ke daftar larangan.

## Jalur Upgrade (skill ini tidak mengerjakannya, sampaikan ke user)
- Butuh kunci muka yang serius → Seedance 2.0 omni-reference / model video pihak ketiga (user sudah punya asetnya).
- Tokoh jangka panjang → LoRA / FaceID (skema berat, dinilai terpisah).

## Template Kalimat (sampaikan sebelum mulai)
> Konsistensi tokoh di video bawaan itu lemah: antar segmen bisa ganti wajah, gambar referensi bisa tidak mirip. Saya akan pakai salinan kata-per-kata + sambungan snapshot + perintah kunci muka supaya sebisa mungkin stabil, tapi saya tidak janji 100%. Kalau mau kunci muka, jalurnya Seedance.
