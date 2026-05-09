# 📸 FORMAT VISUAL SCENE - SISTEM DIALOG DINAMIS

## 🎭 KONSEP SISTEM DIALOG

Game menggunakan **full scene format** (960×544px) dengan background yang berubah sesuai siapa yang berbicara:

```
┌─────────────────────────────────────────────────────────────┐
│  SAAT JAKSA BICARA:                                         │
│  → Background: Wooden courtroom wall                        │
│  → Karakter: Jaksa menghadap KIRI ←                        │
│  → Posisi: Di podium jaksa                                  │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│  SAAT TERDAKWA BICARA:                                      │
│  → Background: Gallery dengan penonton duduk                │
│  → Karakter: Terdakwa menghadap KANAN →                    │
│  → Posisi: Di podium terdakwa                               │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│  SAAT SAKSI BICARA:                                         │
│  → Background: Gallery dengan penonton duduk                │
│  → Karakter: Saksi menghadap KIRI ←                        │
│  → Posisi: Di podium saksi                                  │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│  SAAT HAKIM BICARA:                                         │
│  → Background: Wooden courtroom wall + emblem               │
│  → Karakter: Hakim menghadap DEPAN/CENTER                   │
│  → Posisi: Di belakang meja hakim                           │
└─────────────────────────────────────────────────────────────┘
```

---

## 📐 LAYOUT SCENE FORMAT

### Full Scene Composition (960×544 pixels)

```
╔═══════════════════════════════════════════════════════════════╗
║                        960 pixels                             ║
║  ┌─────────────────────────────────────────────────────────┐ ║
║  │                                                           │ ║
║  │              BACKGROUND LAYER                            │ ║
║  │   (Wooden wall ATAU Gallery dengan penonton)            │ ║
║  │                                                           │ ║
║  │                                                           │ ║
║  │         ┌─────────────────────┐                          │ ║
║  │         │                     │                          │ ║
║  │         │   CHARACTER LAYER   │                          │ ║
║  │         │   (Waist-up)        │                          │ ║
║  │         │                     │                          │ ║
║  │         │                     │                          │ ║
║  │         └─────────────────────┘                          │ ║
║  │                                                           │ ║
║  │         ┌─────────────────────┐                          │ ║
║  │         │   PODIUM/DESK       │                          │ ║
║  │         └─────────────────────┘                          │ ║
║  └─────────────────────────────────────────────────────────┘ ║
║                       544 pixels                              ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 🎨 BACKGROUND DETAIL

### Background Type 1: WOODEN COURTROOM WALL
**Digunakan untuk:** Hakim & Jaksa

```
╔═══════════════════════════════════════════════════════════════╗
║  ┌─────────────────────────────────────────────────────────┐ ║
║  │  ╔═══════════════════════════════════════════════════╗  │ ║
║  │  ║  [Garuda Pancasila Emblem] (untuk Hakim)         ║  │ ║
║  │  ╚═══════════════════════════════════════════════════╝  │ ║
║  │                                                           │ ║
║  │  ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║  │ ║
║  │  ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║  │ ║
║  │  ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║  │ ║
║  │  ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║  │ ║
║  │  ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║ ║  │ ║
║  │                                                           │ ║
║  │  Dark brown vertical wood panels                         │ ║
║  │  Ornate carved trim at top                               │ ║
║  │  Subtle wood grain texture                               │ ║
║  │  Warm lighting from above                                │ ║
║  └─────────────────────────────────────────────────────────┘ ║
╚═══════════════════════════════════════════════════════════════╝
```

**Elemen:**
- Panel kayu vertikal warna coklat tua (#5c3d1e, #3b2410)
- Ukiran/trim ornamental di bagian atas
- Tekstur wood grain halus
- Lighting warm dari atas
- Untuk Hakim: Tambahkan emblem Garuda Pancasila di tengah atas

---

### Background Type 2: COURTROOM GALLERY (AUDIENCE)
**Digunakan untuk:** Terdakwa & Saksi

```
╔═══════════════════════════════════════════════════════════════╗
║  ┌─────────────────────────────────────────────────────────┐ ║
║  │                                                           │ ║
║  │   👤 👤 👤 👤 👤 👤 👤   ← Row 3 (paling belakang)      │ ║
║  │   ═══════════════════════                                │ ║
║  │                                                           │ ║
║  │    👤 👤 👤 👤 👤 👤     ← Row 2 (tengah)               │ ║
║  │    ══════════════════                                    │ ║
║  │                                                           │ ║
║  │     👤 👤 👤 👤 👤       ← Row 1 (depan, blur)          │ ║
║  │     ═════════════                                        │ ║
║  │                                                           │ ║
║  │  Wooden benches dengan orang duduk                       │ ║
║  │  5-7 orang Indonesia (simplified/blurred)                │ ║
║  │  Mix pria & wanita, formal attire                        │ ║
║  └─────────────────────────────────────────────────────────┘ ║
╚═══════════════════════════════════════════════════════════════╝
```

**Elemen:**
- 3 baris kursi kayu (benches)
- 5-7 orang duduk di background (simplified, blurred)
- Mix pria dan wanita Indonesia
- Pakaian formal (kemeja, blazer)
- Ekspresi: curious, serious, whispering, taking notes
- Depth of field: Baris belakang lebih blur
- Warm courtroom lighting

**Variasi Audience per Karakter:**
- **Terdakwa:** Audience netral hingga skeptis
- **Saksi:** Audience curious dan attentive

---

## 👥 DETAIL AUDIENCE (Background Gallery)

### Komposisi Audience:

```
ROW 1 (Foreground - Blurred):
┌────────┬────────┬────────┬────────┬────────┐
│ Pria 1 │ Wanita │ Pria 2 │ Wanita │ Pria 3 │
│ Kemeja │ Blazer │ Batik  │ Hijab  │ Jas    │
│ Blur   │ Blur   │ Blur   │ Blur   │ Blur   │
└────────┴────────┴────────┴────────┴────────┘

ROW 2 (Midground - Semi-detailed):
┌────────┬────────┬────────┬────────┬────────┬────────┐
│ Wanita │ Pria   │ Wanita │ Pria   │ Wanita │ Pria   │
│ Hijab  │ Kemeja │ Blazer │ Batik  │ Kemeja │ Jas    │
│ Notes  │ Watch  │ Whisper│ Lean   │ Arms × │ Serious│
└────────┴────────┴────────┴────────┴────────┴────────┘

ROW 3 (Background - Simplified):
┌────────┬────────┬────────┬────────┬────────┬────────┬────────┐
│ Siluet │ Siluet │ Siluet │ Siluet │ Siluet │ Siluet │ Siluet │
│ Blur   │ Blur   │ Blur   │ Blur   │ Blur   │ Blur   │ Blur   │
└────────┴────────┴────────┴────────┴────────┴────────┴────────┘
```

### Pose & Ekspresi Audience:
1. **Taking notes** - Menulis di notepad
2. **Leaning forward** - Condong ke depan, curious
3. **Whispering** - Berbisik ke sebelah
4. **Arms crossed** - Tangan dilipat, skeptis
5. **Watching intently** - Menatap serius
6. **Neutral** - Duduk tenang

### Pakaian Audience:
- Kemeja putih/biru (formal)
- Blazer/jas (business)
- Batik (Indonesian formal)
- Hijab (untuk wanita Muslim)
- Mix warna: putih, biru, abu-abu, coklat

---

## 🎯 ARAH HADAP KARAKTER

### Visual Guide:

```
JAKSA (Facing LEFT ←)          TERDAKWA (Facing RIGHT →)
┌─────────────────┐            ┌─────────────────┐
│                 │            │                 │
│      ╱◯╲        │            │        ╱◯╲      │
│     ╱ │ ╲       │            │       ╱ │ ╲     │
│    ╱  │  ╲      │            │      ╱  │  ╲    │
│   ╱   │   ╲     │            │     ╱   │   ╲   │
│  ╱    │    ╲    │            │    ╱    │    ╲  │
│ ╱     │     ╲   │            │   ╱     │     ╲ │
│       │         │            │         │       │
│   ←───┘         │            │         └───→   │
│                 │            │                 │
│  Pointing LEFT  │            │  Pointing RIGHT │
└─────────────────┘            └─────────────────┘

SAKSI (Facing LEFT ←)          HAKIM (Facing FORWARD)
┌─────────────────┐            ┌─────────────────┐
│                 │            │                 │
│      ╱◯╲        │            │      ╱◯╲        │
│     ╱ │ ╲       │            │     ╱ │ ╲       │
│    ╱  │  ╲      │            │    ╱  │  ╲      │
│   ╱   │   ╲     │            │   ╱   │   ╲     │
│  ╱    │    ╲    │            │  ╱    │    ╲    │
│ ╱     │     ╲   │            │ ╱     │     ╲   │
│       │         │            │       │         │
│   ←───┘         │            │       ↓         │
│                 │            │                 │
│  Facing LEFT    │            │  Facing FRONT   │
└─────────────────┘            └─────────────────┘
```

---

## 📏 CROP COORDINATES (Updated)

### 4 Scene Layout (Hakim, Suryo, Ratna, Dirga)
```
Scene 1: X=0,    Y=0, W=960, H=544
Scene 2: X=992,  Y=0, W=960, H=544  (960 + 32 spacing)
Scene 3: X=1984, Y=0, W=960, H=544  (992 × 2)
Scene 4: X=2976, Y=0, W=960, H=544  (992 × 3)

Total Canvas: 4032 × 544 pixels
```

### 5 Scene Layout (Raka)
```
Scene 1: X=0,    Y=0, W=960, H=544
Scene 2: X=992,  Y=0, W=960, H=544
Scene 3: X=1984, Y=0, W=960, H=544
Scene 4: X=2976, Y=0, W=960, H=544
Scene 5: X=3968, Y=0, W=960, H=544  (992 × 4)

Total Canvas: 5024 × 544 pixels
```

### 3 Scene Layout (Budi, Sari, Irwan)
```
Scene 1: X=0,    Y=0, W=960, H=544
Scene 2: X=992,  Y=0, W=960, H=544
Scene 3: X=1984, Y=0, W=960, H=544

Total Canvas: 3040 × 544 pixels
```

**Formula:** X = (960 + 32) × index = 992 × index

---

## 🎬 IMPLEMENTASI DI GAME

### CSS Update:
```css
#statement-area {
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  transition: background-image 0.3s ease;
}

.scene-image {
  width: 100%;
  height: auto;
  display: block;
}
```

### JavaScript Logic:
```javascript
function renderStatement(stmt) {
  // Determine which character is speaking
  const speaker = stmt.speaker;
  
  // Load appropriate scene image
  let sceneImage = '';
  if (speaker === 'HAKIM WIBOWO') {
    sceneImage = 'assets/scenes/hakim_netral.png';
  } else if (speaker === 'RAKA') {
    sceneImage = 'assets/scenes/raka_netral.png';
  } else if (speaker === currentDefendant) {
    sceneImage = 'assets/scenes/suryo_netral.png'; // or ratna/dirga
  } else if (speaker === currentWitness) {
    sceneImage = 'assets/scenes/budi_netral.png'; // or sari/irwan
  }
  
  // Update scene display
  document.getElementById('court-scene').style.backgroundImage = `url(${sceneImage})`;
}
```

---

## ✅ QUALITY CHECKLIST

### Background Quality:
- [ ] Wooden wall: Panel vertikal jelas
- [ ] Wooden wall: Tekstur wood grain visible
- [ ] Gallery: 5-7 orang terlihat
- [ ] Gallery: Kursi kayu terlihat
- [ ] Gallery: Depth of field (blur background)
- [ ] Lighting konsisten (warm, dari atas)

### Character Quality:
- [ ] Arah hadap BENAR (sesuai role)
- [ ] Posisi konsisten di semua scene
- [ ] Ukuran proporsional
- [ ] Ekspresi jelas dan berbeda
- [ ] Waist-up composition
- [ ] Podium/desk visible di bawah

### Integration:
- [ ] Background + character terintegrasi natural
- [ ] Lighting match antara BG dan character
- [ ] Perspective consistent
- [ ] No awkward cutoff atau overlap

---

**FORMAT SCENE LENGKAP! 🎬**
