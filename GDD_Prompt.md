# Prompt: Buat Game Design Document untuk SIDANG!

Gunakan prompt ini di Claude untuk menghasilkan Game Design Document (GDD) yang lengkap dan profesional.

---

## PROMPT UNTUK CLAUDE

```
Buatkan Game Design Document (GDD) yang lengkap, terstruktur, dan profesional untuk game berikut. Gunakan format dokumen formal dengan heading, subheading, tabel, dan daftar yang rapi. Tulis dalam Bahasa Indonesia.

---

## DATA GAME

**Judul:** SIDANG! — Pengadilan Anti-Korupsi
**Genre:** Visual Novel / Courtroom Drama / Edukasi
**Platform:** Web Browser (HTML5)
**Target Pemain:** Siswa SMA Indonesia (usia 15-18 tahun)
**Tema:** Indonesia Tanpa Korupsi — #BERJUMPADIKERTAS
**Nilai yang diusung:** Berani · Jujur · Mandiri · Peduli · Adil · Disiplin · Kerja Keras · Tanggung Jawab · Sederhana

---

## KONSEP INTI

Pemain berperan sebagai **Jaksa** (nama diinput sendiri oleh pemain, julukan: *Corruptor's Nightmare*) yang harus membuktikan kesalahan terdakwa korupsi di ruang sidang. Terinspirasi mekanik Ace Attorney, namun seluruh konten adalah original Indonesia.

Mekanik utama: pemain membaca dialog sidang, menemukan pernyataan bohong, menekan tombol **BANTAH!**, lalu memilih dokumen bukti yang tepat untuk mematahkan kebohongan tersebut.

---

## KARAKTER

| Nama | Peran | Kasus |
|------|-------|-------|
| Hakim Wibowo | Ketua Majelis (NPC) | Semua kasus |
| Jaksa (nama pemain) | Protagonis / Player Character | Semua kasus |
| Pak Suryo Wibowo | Terdakwa | Kasus 1 |
| Budi Santoso | Saksi | Kasus 1 |
| Bu Ratna Kusumawati | Terdakwa | Kasus 2 |
| Bu Sari | Saksi (Kepala Sekolah) | Kasus 2 |
| Pak Dirga Mahardika | Terdakwa | Kasus 3 |
| Irwan Prasetyo | Saksi (Pengawas Lapangan) | Kasus 3 |

---

## TIGA KASUS (LEVEL)

### Kasus #1 — Tender Buku Abal-Abal
- **No. Sidang:** 023/PDN/2026
- **Terdakwa:** Pak Suryo Wibowo (Kepala Dinas Pendidikan)
- **Dakwaan:** Korupsi pengadaan buku Rp 2,1 miliar
- **Jumlah dialog:** 24 dialog, 5 dapat dibantah
- **Dokumen bukti:**
  - Dokumen Tender: Pemenang ditetapkan 10 Maret, tender dibuka 15 Maret — 5 hari sebelumnya
  - Data Rekening: Transfer Rp 420 juta ke istri terdakwa sehari setelah penetapan pemenang
  - Email Internal: Instruksi "pastikan PT Maju Jaya yang menang" dikirim 8 Maret sebelum tender dibuka
- **Tingkat kesulitan:** Normal (tombol BANTAH! hanya aktif saat ada pernyataan yang bisa dibantah, ada highlight kata kunci)

### Kasus #2 — Dana BOS
- **No. Sidang:** 024/PDN/2026
- **Terdakwa:** Bu Ratna Kusumawati (Bendahara Sekolah)
- **Dakwaan:** Penyelewengan Dana BOS Rp 485 juta
- **Jumlah dialog:** 24 dialog, 6 dapat dibantah
- **Dokumen bukti:**
  - LPJ Dana BOS: Klaim 10.000 buku dibeli, stok fisik hanya 1.200 — selisih 8.800 buku
  - Nota Pembelian: Harga 3x lipat dari toko milik keponakan terdakwa yang tidak terdaftar
  - Catatan CCTV: Akses brankas malam hari (22:14 dan 21:53) di luar jam kerja, saldo berkurang keesokan harinya
- **Tingkat kesulitan:** Normal (sama dengan Kasus 1, ada highlight kata kunci)

### Kasus #3 — Proyek Jembatan Nusantara
- **No. Sidang:** 025/PDN/2026
- **Terdakwa:** Pak Dirga Mahardika (Direktur PT Cipta Bangun Nusantara)
- **Dakwaan:** Korupsi infrastruktur Rp 48,5 miliar
- **Jumlah dialog:** 24 dialog, 4 dapat dibantah
- **Dokumen bukti:**
  - Kontrak Proyek: Perusahaan baru berdiri 3 bulan sebelum memenangkan tender Rp 48,5 miliar
  - Uji Material (BPPT): Beton K-175 (standar K-350), besi 6mm (standar 12mm) — setengah dari standar
  - Aliran Dana (PPATK): Rp 8,35 miliar dipecah ke 12 rekening pribadi untuk sembunyikan jejak
- **Tingkat kesulitan:** Hard (tombol BANTAH! selalu aktif di semua dialog kecuali hakim/jaksa, tidak ada highlight kata kunci, membantah dialog yang salah tidak mengurangi kredibilitas)

---

## SISTEM GAMEPLAY

### Mekanik Bantah (Objection System)
1. Dialog muncul satu per satu dengan efek typewriter
2. Pemain menekan **BANTAH!** saat menemukan pernyataan bohong
3. Modal dokumen terbuka — pemain memilih dokumen yang tepat
4. Jika **tepat**: flash hijau "TEPAT!", Jaksa membacakan bantahan, Hakim bereaksi, skor naik
5. Jika **salah**: flash merah "SALAH!", Jaksa mengakui kesalahan (ekspresi kecewa), kredibilitas berkurang

### Sistem Kredibilitas (Pips)
- Pemain memiliki 3 pip kredibilitas
- Setiap bantahan salah (pada statement yang memang bisa dibantah): -1 pip
- Jika 0 pip: Game Over (Kredibilitas Habis)
- Kasus 3: membantah dialog yang tidak perlu dibantah tidak mengurangi pip

### Sistem Skor
- Formula: `Skor = (bantahan tepat / total bantahan) × 100 - (salah × 5, max -30)`
- Skor maksimal per kasus: 100 (semua tepat, 0 salah)
- Disimpan per kasus di localStorage

### Sistem Bintang
| Bintang | Kondisi |
|---------|---------|
| ★★★ | Skor ≥ 80 (akurasi tinggi) |
| ★★☆ | Skor ≥ 50 |
| ★☆☆ | Ada minimal 1 bantahan tepat |
| ☆☆☆ | Gagal / belum selesai |

### Sistem Hint
- Muncul saat pemain gagal 2 kali menggunakan dokumen yang sama
- Menampilkan nama dokumen yang benar + kalimat kunci
- Tidak mengurangi skor

### Sistem Highlight Kata Kunci
- Kasus 1 & 2: kata kunci penting di-highlight gold setelah typewriter selesai
- Kasus 3: tidak ada highlight (mode hard)

### Sistem Level Select & Progress
- Kasus 1 terbuka dari awal
- Kasus 2 terbuka setelah Kasus 1 lulus (minimal 1 bantahan tepat)
- Kasus 3 terbuka setelah Kasus 2 lulus
- Progress disimpan di localStorage
- Bintang terupdate otomatis jika skor lebih baik dari percobaan sebelumnya

---

## FITUR PENDUKUNG

### Kamus Istilah (Glossary)
- 25 istilah hukum Indonesia dengan penjelasan bahasa sederhana
- Dapat dicari (search)
- Kategori: Umum, Kasus 1, Kasus 2, Kasus 3
- Contoh: Tender, Gratifikasi, LPJ, Mark-up, PPATK, BPPT, Dana BOS

### Catatan Sidang (Notes/Logs)
- Mencatat semua dialog secara otomatis
- Filter: Semua / Bantahan / Ditandai
- Pemain bisa menandai dialog penting dengan bintang ★
- Bantahan tepat/salah ditandai dengan warna berbeda

### Quiz Refleksi
- Muncul setelah setiap kasus selesai (sebelum layar hasil)
- 1 soal pilihan ganda per kasus
- Tidak ada penalti untuk jawaban salah
- Tujuan: reinforcement learning

### Tutorial Interaktif
- Hanya muncul di Kasus 1 (pertama kali)
- 10 step dengan gambar tombol
- Bisa di-skip
- Disimpan di localStorage (tidak muncul lagi setelah selesai)

### Voice Over
- Semua karakter memiliki voice over untuk dialog utama
- Voice over khusus untuk bantahan tepat dan salah per dokumen
- Hakim memiliki voice over reaksi per urutan bantahan
- Tombol mute/unmute terpisah untuk VO dan BGM

---

## ALUR GAME (FLOW)

```
Loading Screen (preload assets)
    ↓ [Click Anywhere to Continue]
Main Menu
    ├── PLAY → Input Username → Level Select → Sidang → Quiz → Hasil Kasus
    ├── HOW TO PLAY → Layar Cara Bermain
    └── CREDITS → Layar Credits

Sidang (Court Session):
    Dialog → [BANTAH!] → Pilih Dokumen → Tepat/Salah → Dialog Lanjut
    → Kasus Selesai → Quiz → Hasil Kasus
        ├── Lulus → Simpan progress → Pilih: Lanjut / Level Select / Main Menu
        └── Gagal → Simpan gagal → Pilih: Ulangi / Level Select / Main Menu

Game Over (Kredibilitas Habis):
    → Tunggu dialog Jaksa selesai → Tampilkan Game Over
    → Pilih: Ulangi / Level Select / Main Menu

Hasil Akhir (setelah Kasus 3):
    → Baca data dari localStorage (semua kasus)
    → Tampilkan: total bantahan, rata-rata trust & opini, skor total
    → Simpan Laporan PNG
```

---

## ANTARMUKA (UI/UX)

### Layar Utama
- **Main Menu:** Background courtroom anime, logo SIDANG!, 3 tombol (PLAY, HOW TO PLAY, CREDITS)
- **Level Select:** 3 kartu kasus horizontal dengan gambar, status, bintang
- **Username Screen:** Karakter Jaksa di kiri, form input di kanan, dialog box perkenalan di bawah

### Court Session
- **Top Bar:** Logo + tombol VO + tombol BGM | Judul kasus | HUD (pip, trust bar, opini bar, skor)
- **Scene:** Background courtroom full screen, karakter dengan transisi crossfade smooth
- **Dialog Box:** Navy gelap, border gold, speaker name gold, teks Playfair Display
- **Action Bar:** Tombol PNG (LANJUT, BANTAH!, DOKUMEN, LOGS, ISTILAH, MENU), background kayu

### Warna & Font
- **Palet:** Navy `#0d1a2e`, Gold `#c9a84c`, Merah `#b71c1c`, Cream `#f0eadc`
- **Font UI:** Impact (bold, kapital)
- **Font Dialog:** Playfair Display (serif, elegan)
- **Font Dokumen:** Special Elite (typewriter)

---

## AUDIO

- **BGM Main Menu:** Loop ambient courtroom (MainMenu.mpeg)
- **BGM Court Session:** Loop dramatic court music (Court.mpeg)
- **Sound Effects:** Procedural via Web Audio API (gavel, objection flash, correct/wrong, pip lose)
- **Voice Over:** 8 karakter, semua dialog utama + bantahan tepat/salah per dokumen

---

## TEKNOLOGI

- **Engine:** Vanilla HTML5 + CSS3 + JavaScript (tanpa framework)
- **Storage:** localStorage untuk progress, username, tutorial state
- **Audio:** Web Audio API (SFX) + HTML Audio (VO & BGM)
- **Aset Visual:** Gemini AI (karakter, background, UI)
- **Platform:** Browser (desktop & mobile responsive)

---

## NILAI EDUKASI (#BERJUMPADIKERTAS)

| Nilai | Implementasi dalam Game |
|-------|------------------------|
| Berani | Menekan BANTAH! saat menemukan kebohongan |
| Jujur | Memilih dokumen yang benar, tidak menebak |
| Mandiri | Menganalisis sendiri di Kasus 3 (tanpa highlight) |
| Peduli | Kasus Dana BOS — uang yang seharusnya untuk murid |
| Adil | Hakim menilai berdasarkan bukti, bukan asumsi |
| Disiplin | Membaca setiap dialog dengan teliti |
| Kerja Keras | Menyelesaikan 3 kasus dengan skor tinggi |
| Tanggung Jawab | Jaksa bertanggung jawab atas setiap bantahan |
| Sederhana | Kasus korupsi dimulai dari hal-hal sederhana di sekitar kita |

---

## INSTRUKSI UNTUK CLAUDE

Berdasarkan semua data di atas, buatkan Game Design Document (GDD) yang lengkap dengan struktur berikut:

1. **Executive Summary** — ringkasan singkat game, visi, dan proposisi nilai unik
2. **Game Overview** — genre, platform, target audience, tone & mood
3. **Core Gameplay Loop** — diagram alur gameplay inti
4. **Mechanics Design** — penjelasan detail setiap mekanik (bantah, kredibilitas, skor, bintang, hint, highlight, quiz)
5. **Level Design** — breakdown detail setiap kasus (narrative arc, dokumen, difficulty curve)
6. **Character Design** — profil setiap karakter (latar belakang, motivasi, kepribadian)
7. **UI/UX Design** — wireframe deskriptif setiap layar, color palette, typography
8. **Audio Design** — deskripsi BGM, SFX, VO per scene
9. **Progression System** — sistem level unlock, bintang, localStorage
10. **Educational Design** — bagaimana setiap nilai #BERJUMPADIKERTAS diimplementasikan
11. **Technical Specifications** — stack teknologi, performance requirements
12. **Future Development** — fitur yang bisa dikembangkan (multiplayer, lebih banyak kasus, dll)

Buat GDD ini seprofesional mungkin, seolah-olah akan dipresentasikan kepada publisher game atau juri lomba. Gunakan bahasa formal namun mudah dipahami.
```

---

## CATATAN PENGGUNAAN

- Salin seluruh isi dalam blok kode di atas ke Claude
- Jika ingin fokus pada bagian tertentu, tambahkan di akhir: *"Fokus pada bagian [nama bagian] saja"*
- Untuk versi lebih singkat, tambahkan: *"Buat versi ringkas 2-3 halaman saja"*
- Untuk presentasi lomba, tambahkan: *"Format untuk presentasi 5 menit kepada juri lomba game edukasi"*
