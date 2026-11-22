# Muse Video Studio — Konstitusi Desain (Versi Drama Indonesia)

> Diadaptasi dari masonmosen/muse-video-prompt-skill (MIT). Gagasan rekayasa dari LuoJiangYong/muse-video-skill (thin center + muat saat dibutuhkan + script yang pasti). Isi dari pengalaman nyata workflow ini.

## Lima Prinsip

### 1. JUJUR DULU — Sampaikan batas dulu, baru bicara hasil
- Batas keras video bawaan Muse: satu klip sekitar 10 detik, kunci muka lemah, gambar referensi belum tentu mirip, saya tidak bisa melihat video jadi dan tidak bisa mendengar audio.
- Semua itu disampaikan ke user SEBELUM mulai — jangan bungkus "trik prompt" seolah itu janji kemampuan.
- Kartu kasus menulis "pelajaran yang didapat", bukan cuma keberhasilan.

### 2. USER YANG MENGESAHKAN — Prompt final milik user
- Prompt yang dikirim ke model adalah versi final user, dipakai apa adanya tanpa diubah, ditambah, atau diperhalus.
- Default jangka panjang (dialog Bahasa Indonesia) adalah instruksi tetap user, bukan kreasi saya — ditulis terpisah dan jelas.

### 3. LINGKARAN PENDEK — Tulis → generate → cek, tiap putaran bisa diserahkan
- Jangan bikin "perencanaan berminggu-minggu baru generate"; tiap putaran 8–10 detik bisa dicek.
- Tiap putaran diserahkan = file video + kesimpulan cek frame + daftar yang harus diverifikasi user.

### 4. MENUMPUK PELAJARAN — Tiap eksperimen jadi kartu kasus
- Tiap eksperimen ditulis jadi kartu kasus: poin prompt, hasil, penyimpangan, pelajaran.
- Pustaka kasus adalah aset utama skill ini — makin dipakai makin bertambah; kasus baru disimpan dulu sebelum bicara "optimasi template".

### 5. RINGAN — SKILL.md hanya jadi pengarah
- SKILL.md maksimal 3000 karakter; detail masuk references; hal mekanis masuk scripts/bin.
- Sesuatu baru dijadikan template kalau sudah dipakai di tiga tempat atau lebih; jangan terlalu cepat mengabstraksi.
