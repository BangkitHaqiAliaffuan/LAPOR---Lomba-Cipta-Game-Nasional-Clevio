# 📸 CONTOH VISUAL SPRITE SHEET

## Format Sprite Sheet yang Diharapkan

```
┌─────────────────────────────────────────────────────────────────────────┐
│  TRANSPARENT CHECKERED BACKGROUND (Alpha Channel)                       │
│                                                                          │
│  ┌──────┐  32px  ┌──────┐  32px  ┌──────┐  32px  ┌──────┐             │
│  │      │  gap   │      │  gap   │      │  gap   │      │             │
│  │ 256  │        │ 256  │        │ 256  │        │ 256  │             │
│  │  ×   │        │  ×   │        │  ×   │        │  ×   │             │
│  │ 384  │        │ 384  │        │ 384  │        │ 384  │             │
│  │  px  │        │  px  │        │  px  │        │  px  │             │
│  │      │        │      │        │      │        │      │             │
│  │ SPR1 │        │ SPR2 │        │ SPR3 │        │ SPR4 │             │
│  └──────┘        └──────┘        └──────┘        └──────┘             │
│                                                                          │
│  Total Width: (256 × 4) + (32 × 3) = 1120px                            │
│  Total Height: 384px                                                    │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## Contoh Layout: HAKIM WIBOWO (4 Ekspresi)

```
╔═══════════════════════════════════════════════════════════════════════╗
║                    HAKIM_SPRITESHEET.PNG                              ║
║                    (1152 × 384 pixels)                                ║
╠═══════════════════════════════════════════════════════════════════════╣
║                                                                        ║
║   ┌─────────┐      ┌─────────┐      ┌─────────┐      ┌─────────┐   ║
║   │  👨‍⚖️    │      │  👨‍⚖️😠   │      │  👨‍⚖️🤔   │      │  👨‍⚖️😲   │   ║
║   │  Wig    │      │  Wig    │      │  Wig    │      │  Wig    │   ║
║   │ Glasses │      │ Glasses │      │ Glasses │      │ Glasses │   ║
║   │  Robe   │      │  Robe   │      │  Robe   │      │  Robe   │   ║
║   │ Gavel ⚖ │      │ Gavel ⬆ │      │ Gavel ⚖ │      │ Gavel ⬇ │   ║
║   │         │      │ ANGRY!  │      │ Thinking│      │ SHOCKED!│   ║
║   │ Neutral │      │ Shouting│      │ Chin    │      │ Recoil  │   ║
║   │ Calm    │      │ Forward │      │ Stroke  │      │ Sweat   │   ║
║   └─────────┘      └─────────┘      └─────────┘      └─────────┘   ║
║    256×384          256×384          256×384          256×384        ║
║                                                                        ║
║   NETRAL           MARAH            SERIUS           TERKEJUT        ║
╚═══════════════════════════════════════════════════════════════════════╝
```

---

## Contoh Layout: RAKA (5 Ekspresi)

```
╔════════════════════════════════════════════════════════════════════════════════╗
║                         RAKA_SPRITESHEET.PNG                                   ║
║                         (1440 × 384 pixels)                                    ║
╠════════════════════════════════════════════════════════════════════════════════╣
║                                                                                 ║
║  ┌────────┐   ┌────────┐   ┌────────┐   ┌────────┐   ┌────────┐            ║
║  │  👔     │   │  👔👉   │   │  👔🤔   │   │  👔😏   │   │  👔😞   │            ║
║  │ Suit   │   │ Suit   │   │ Suit   │   │ Suit   │   │ Suit   │            ║
║  │ Badge  │   │ Badge  │   │ Badge  │   │ Badge  │   │ Badge  │            ║
║  │ Tie    │   │ Tie    │   │ Tie    │   │ Tie    │   │ Tie    │            ║
║  │ Arms × │   │ Point! │   │ Chin   │   │ Arms × │   │ Face   │            ║
║  │        │   │ ⚡⚡⚡  │   │ Think  │   │ Smirk  │   │ Cover  │            ║
║  │Neutral │   │BANTAH! │   │ Look ↗ │   │Confident│  │ Slump  │            ║
║  │Confident│  │Dynamic │   │        │   │        │   │ Sweat  │            ║
║  └────────┘   └────────┘   └────────┘   └────────┘   └────────┘            ║
║   256×384      256×384      256×384      256×384      256×384               ║
║                                                                                 ║
║  NETRAL      OBJECTION    BERPIKIR    TERSENYUM     KECEWA                   ║
╚════════════════════════════════════════════════════════════════════════════════╝
```

---

## Contoh Layout: BUDI (3 Ekspresi - Saksi)

```
╔═══════════════════════════════════════════════════════════════╗
║              BUDI_SPRITESHEET.PNG                             ║
║              (864 × 384 pixels)                               ║
╠═══════════════════════════════════════════════════════════════╣
║                                                                ║
║    ┌──────────┐      ┌──────────┐      ┌──────────┐         ║
║    │   👨‍💼    │      │   👨‍💼😰   │      │   👨‍💼😅   │         ║
║    │  Blazer  │      │  Blazer  │      │  Blazer  │         ║
║    │ ID Card  │      │ ID Card  │      │ ID Card  │         ║
║    │          │      │ Fidget   │      │ Scratch  │         ║
║    │ Nervous  │      │ Sweat💧  │      │ Look ←   │         ║
║    │ Anxious  │      │ Shake    │      │ Awkward  │         ║
║    │          │      │ Wide 👀  │      │ Smile 😅 │         ║
║    └──────────┘      └──────────┘      └──────────┘         ║
║     256×384          256×384          256×384                ║
║                                                                ║
║    NETRAL           GUGUP           BERBOHONG                ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## ✅ CHECKLIST KUALITAS SPRITE SHEET

### 1. **Konsistensi Karakter**
- [ ] Tinggi kepala SAMA di semua sprite
- [ ] Posisi bahu SAMA (baseline alignment)
- [ ] Ukuran tubuh PROPORSIONAL
- [ ] Warna pakaian IDENTIK
- [ ] Style rambut KONSISTEN (kecuali disheveled)

### 2. **Transparansi**
- [ ] Background benar-benar transparan (checkered pattern visible)
- [ ] Tidak ada white/gray box di sekitar karakter
- [ ] Alpha channel berfungsi dengan baik

### 3. **Spacing & Layout**
- [ ] Jarak antar sprite konsisten (~32px)
- [ ] Sprite tidak terpotong
- [ ] Tidak ada overlap antar sprite
- [ ] Grid alignment rapi

### 4. **Style Ace Attorney**
- [ ] Bold black outlines (2-3px)
- [ ] Cel-shaded colors (flat, minimal gradient)
- [ ] Anime proportions (large eyes, expressive)
- [ ] Clean linework
- [ ] Proper shading placement

### 5. **Ekspresi Jelas**
- [ ] Setiap ekspresi BERBEDA dan JELAS
- [ ] Gesture mendukung emosi
- [ ] Facial features expressive
- [ ] Body language sesuai mood

---

## 🎨 CONTOH WARNA PALETTE (Referensi)

### Hakim Wibowo
```
Robe:      #1a1a2e (hitam kebiruan)
Lining:    #8B1538 (maroon)
Collar:    #f0e8d0 (krem)
Wig:       #f5f0e0 (putih kekuningan)
Skin:      #c8a070 (tan Indonesia)
Glasses:   #c9a84c (gold frame)
```

### Raka (Jaksa)
```
Suit:      #0d2840 (navy blue)
Tie:       #b71c1c (merah)
Shirt:     #f0ece0 (putih)
Badge:     #c9a84c (gold)
Hair:      #2c1a0e (hitam)
Skin:      #c8956c (tan Indonesia)
```

### Terdakwa (General)
```
Suit:      #4a5568 (abu-abu) / #2d5a1b (hijau tua)
Shirt:     #e8e0cc (krem)
Skin:      #c8a882 (tan Indonesia)
Hair:      #5c4030 (coklat) / #3d2010 (hitam kecoklatan)
```

---

## 🔍 CARA VERIFIKASI SPRITE SHEET

### Test di Photoshop/GIMP:
1. Buka file PNG
2. Check layer transparency (harus ada alpha channel)
3. Zoom 100% - cek outline quality
4. Measure sprite width (harus 256px exact)
5. Check spacing dengan ruler/guide

### Test di Browser:
```html
<!DOCTYPE html>
<html>
<body style="background: repeating-conic-gradient(#ddd 0% 25%, #fff 0% 50%) 50% / 20px 20px;">
  <img src="hakim_spritesheet.png" style="image-rendering: crisp-edges;">
</body>
</html>
```
Jika transparan benar, akan terlihat checkered pattern di background.

---

## 📏 TEMPLATE CROP COORDINATES

Untuk crop sprite sheet menjadi individual PNG:

### 4 Sprite Layout (Hakim, Suryo, Ratna, Dirga)
```
Sprite 1: X=0,    Y=0, W=256, H=384
Sprite 2: X=288,  Y=0, W=256, H=384
Sprite 3: X=576,  Y=0, W=256, H=384
Sprite 4: X=864,  Y=0, W=256, H=384
```

### 5 Sprite Layout (Raka)
```
Sprite 1: X=0,    Y=0, W=256, H=384
Sprite 2: X=288,  Y=0, W=256, H=384
Sprite 3: X=576,  Y=0, W=256, H=384
Sprite 4: X=864,  Y=0, W=256, H=384
Sprite 5: X=1152, Y=0, W=256, H=384
```

### 3 Sprite Layout (Budi, Sari, Irwan)
```
Sprite 1: X=0,   Y=0, W=256, H=384
Sprite 2: X=288, Y=0, W=256, H=384
Sprite 3: X=576, Y=0, W=256, H=384
```

---

## 🚨 COMMON ISSUES & FIXES

### Issue: Sprite tidak aligned
**Fix:** Tambahkan ke prompt: "align all sprites at the same baseline, consistent head height"

### Issue: Background tidak transparan
**Fix:** Tambahkan ke prompt: "transparent checkered background with alpha channel, no white background"

### Issue: Ukuran sprite tidak konsisten
**Fix:** Tambahkan ke prompt: "each sprite exactly 256×384 pixels, consistent proportions"

### Issue: Warna berbeda antar sprite
**Fix:** Tambahkan ke prompt: "use identical colors for clothing and skin across all sprites"

### Issue: Spacing tidak rata
**Fix:** Tambahkan ke prompt: "32 pixels spacing between each sprite, evenly distributed"

---

**REFERENSI VISUAL LENGKAP! 🎨**
