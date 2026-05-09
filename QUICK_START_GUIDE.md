# ⚡ QUICK START GUIDE - Generate Asset Karakter

## 🎯 WORKFLOW 3 LANGKAH

```
┌─────────────────────────────────────────────────────────────┐
│  STEP 1: GENERATE     →    STEP 2: CROP    →    STEP 3: INTEGRATE  │
│  (Gemini AI)               (Tool)                (Game Code)         │
│                                                                       │
│  8 Sprite Sheets      →    30 Individual    →    Update game.html   │
│  (~10-15 menit)            PNG Files             (~30 menit)         │
│                            (~5 menit)                                 │
└─────────────────────────────────────────────────────────────┘
```

---

## 📋 STEP 1: GENERATE DI GEMINI AI

### Persiapan:
1. Buka: https://gemini.google.com
2. Buka file: `PROMPTS_KARAKTER_GEMINI.md`
3. Siapkan folder download

### Generate Order (Prioritas):
```
✅ WAJIB (Core Characters):
1. Hakim Wibowo    → 4 ekspresi
2. Raka (Jaksa)    → 5 ekspresi
3. Pak Suryo       → 4 ekspresi

⭐ PENTING (Level 1 & 2):
4. Bu Ratna        → 4 ekspresi
5. Budi Santoso    → 3 ekspresi
6. Bu Sari         → 3 ekspresi

🔹 OPSIONAL (Level 3):
7. Pak Dirga       → 4 ekspresi
8. Irwan Prasetyo  → 3 ekspresi
```

### Cara Generate:
1. **Copy prompt** dari `PROMPTS_KARAKTER_GEMINI.md`
2. **Paste ke Gemini AI** (jangan edit!)
3. **Tunggu hasil** (~30-60 detik)
4. **Download PNG** → rename: `[nama]_spritesheet.png`
5. **Ulangi** untuk karakter berikutnya

### Tips Generate:
- ✅ Generate 1 karakter per prompt
- ✅ Tunggu sampai selesai sebelum next
- ✅ Jika gagal, retry dengan prompt yang sama
- ✅ Save sprite sheet asli ke folder `spritesheets/`

---

## ✂️ STEP 2: CROP SPRITE SHEET

### Opsi A: Online Tool (TERMUDAH)
```
1. Buka: https://www.imgonline.com.ua/eng/cut-photo-into-pieces.php
2. Upload: hakim_spritesheet.png
3. Settings:
   - Columns: 4 (atau sesuai jumlah ekspresi)
   - Rows: 1
   - Output format: PNG
4. Download hasil crop
5. Rename sesuai konvensi:
   - hakim_netral.png
   - hakim_marah.png
   - hakim_serius.png
   - hakim_terkejut.png
```

### Opsi B: Photoshop (Manual)
```
1. Open sprite sheet
2. Select → Slice Tool
3. Right-click → Divide Slice
   - Horizontal: [jumlah ekspresi]
   - Vertical: 1
4. File → Export → Save for Web
5. Save All Slices
```

### Opsi C: ImageMagick (Command Line)
```bash
# Install ImageMagick dulu
# Windows: choco install imagemagick
# Mac: brew install imagemagick

# Crop 4 sprite (Hakim)
magick hakim_spritesheet.png -crop 256x384+0+0 hakim_netral.png
magick hakim_spritesheet.png -crop 256x384+288+0 hakim_marah.png
magick hakim_spritesheet.png -crop 256x384+576+0 hakim_serius.png
magick hakim_spritesheet.png -crop 256x384+864+0 hakim_terkejut.png

# Crop 5 sprite (Raka)
magick raka_spritesheet.png -crop 256x384+0+0 raka_netral.png
magick raka_spritesheet.png -crop 256x384+288+0 raka_objection.png
magick raka_spritesheet.png -crop 256x384+576+0 raka_berpikir.png
magick raka_spritesheet.png -crop 256x384+864+0 raka_tersenyum.png
magick raka_spritesheet.png -crop 256x384+1152+0 raka_kecewa.png

# Crop 3 sprite (Saksi)
magick budi_spritesheet.png -crop 256x384+0+0 budi_netral.png
magick budi_spritesheet.png -crop 256x384+288+0 budi_gugup.png
magick budi_spritesheet.png -crop 256x384+576+0 budi_berbohong.png
```

### Organize Files:
```
assets/
├── characters/
│   ├── spritesheets/          # Backup sprite sheet asli
│   │   ├── hakim_spritesheet.png
│   │   ├── raka_spritesheet.png
│   │   └── ...
│   ├── hakim/                 # Individual sprites
│   │   ├── hakim_netral.png
│   │   ├── hakim_marah.png
│   │   └── ...
│   ├── raka/
│   └── ...
```

---

## 🔧 STEP 3: INTEGRATE KE GAME

### 3.1 Update CSS (game.html)

**Cari section ini** (sekitar line 300):
```css
/* Character images */
.char-fig svg {
  width: 64px;
  height: 90px;
  ...
}
```

**Ganti dengan:**
```css
/* Character images */
.char-fig img {
  width: auto;
  height: 180px;
  filter: drop-shadow(0 4px 8px rgba(0,0,0,.5));
  transition: transform .3s, filter .3s;
  image-rendering: crisp-edges;
}

.char-fig.talking img {
  animation: charTalk .15s steps(2) infinite;
}

.char-fig.shake img {
  animation: charShake .4s ease;
}

.char-slot.judge .char-fig img {
  height: 200px;
}

.char-slot.witness .char-fig img {
  height: 160px;
}
```

---

### 3.2 Tambahkan Asset Mapping (JavaScript)

**Cari line** `const DEFENDANTS = {` (sekitar line 900)

**Tambahkan SEBELUM line tersebut:**
```javascript
// ══════════════════════════════════
// ASSET PATHS
// ══════════════════════════════════
const ASSET_BASE = 'assets/characters/';

const CHARACTER_ASSETS = {
  hakim: {
    netral: ASSET_BASE + 'hakim/hakim_netral.png',
    marah: ASSET_BASE + 'hakim/hakim_marah.png',
    serius: ASSET_BASE + 'hakim/hakim_serius.png',
    terkejut: ASSET_BASE + 'hakim/hakim_terkejut.png'
  },
  raka: {
    netral: ASSET_BASE + 'raka/raka_netral.png',
    objection: ASSET_BASE + 'raka/raka_objection.png',
    berpikir: ASSET_BASE + 'raka/raka_berpikir.png',
    tersenyum: ASSET_BASE + 'raka/raka_tersenyum.png',
    kecewa: ASSET_BASE + 'raka/raka_kecewa.png'
  },
  suryo: {
    netral: ASSET_BASE + 'suryo/suryo_netral.png',
    gugup: ASSET_BASE + 'suryo/suryo_gugup.png',
    marah: ASSET_BASE + 'suryo/suryo_marah.png',
    terpojok: ASSET_BASE + 'suryo/suryo_terpojok.png'
  },
  ratna: {
    netral: ASSET_BASE + 'ratna/ratna_netral.png',
    menyangkal: ASSET_BASE + 'ratna/ratna_menyangkal.png',
    panik: ASSET_BASE + 'ratna/ratna_panik.png',
    menangis: ASSET_BASE + 'ratna/ratna_menangis.png'
  },
  dirga: {
    netral: ASSET_BASE + 'dirga/dirga_netral.png',
    sombong: ASSET_BASE + 'dirga/dirga_sombong.png',
    marah: ASSET_BASE + 'dirga/dirga_marah.png',
    kalah: ASSET_BASE + 'dirga/dirga_kalah.png'
  },
  budi: {
    netral: ASSET_BASE + 'budi/budi_netral.png',
    gugup: ASSET_BASE + 'budi/budi_gugup.png',
    berbohong: ASSET_BASE + 'budi/budi_berbohong.png'
  },
  sari: {
    netral: ASSET_BASE + 'sari/sari_netral.png',
    khawatir: ASSET_BASE + 'sari/sari_khawatir.png',
    terkejut: ASSET_BASE + 'sari/sari_terkejut.png'
  },
  irwan: {
    netral: ASSET_BASE + 'irwan/irwan_netral.png',
    serius: ASSET_BASE + 'irwan/irwan_serius.png',
    tidak_yakin: ASSET_BASE + 'irwan/irwan_tidak_yakin.png'
  }
};
```

---

### 3.3 Tambahkan Helper Functions

**Cari line** `function loadCase(){` (sekitar line 1500)

**Tambahkan SEBELUM function tersebut:**
```javascript
// ══════════════════════════════════
// IMAGE LOADING HELPERS
// ══════════════════════════════════

function setCharacterImage(elementId, characterKey, expression = 'netral') {
  const figElement = document.getElementById(elementId);
  if (!figElement) return;
  
  const assetPath = CHARACTER_ASSETS[characterKey]?.[expression];
  if (!assetPath) {
    console.warn(`Asset not found: ${characterKey}_${expression}`);
    return;
  }
  
  figElement.innerHTML = '';
  
  const img = document.createElement('img');
  img.src = assetPath;
  img.alt = `${characterKey} ${expression}`;
  img.onerror = function() {
    console.error(`Failed to load: ${assetPath}`);
    figElement.innerHTML = '<div style="width:128px;height:180px;background:#333;display:flex;align-items:center;justify-content:center;color:#999;">?</div>';
  };
  
  figElement.appendChild(img);
}

function changeExpression(characterKey, expression, duration = 0) {
  const elementId = `fig-${characterKey}`;
  setCharacterImage(elementId, characterKey, expression);
  
  if (duration > 0) {
    setTimeout(() => {
      setCharacterImage(elementId, characterKey, 'netral');
    }, duration);
  }
}
```

---

### 3.4 Update loadCase() Function

**Cari bagian ini** dalam `function loadCase()`:
```javascript
// Load defendant image
document.getElementById('fig-defendant').innerHTML = def.svg;
```

**Ganti dengan:**
```javascript
// Load defendant image
setCharacterImage('fig-defendant', caseId, 'netral');
```

**Cari bagian ini:**
```javascript
// Load witness image
if(wit){
  document.getElementById('fig-witness').innerHTML = wit.svg;
  ...
}
```

**Ganti dengan:**
```javascript
// Load witness image
if(wit){
  const witnessKey = caseId; // budi/sari/irwan
  setCharacterImage('fig-witness', witnessKey, 'netral');
  ...
}
```

**Tambahkan di akhir function loadCase():**
```javascript
// Load prosecutor and judge
setCharacterImage('fig-prosecutor', 'raka', 'netral');
setCharacterImage('fig-judge', 'hakim', 'netral');
```

---

### 3.5 Update processBantah() untuk Ekspresi

**Cari function** `processBantah(docId)` (sekitar line 1700)

**Tambahkan setelah** `if(isCorrect){`:
```javascript
// Change expressions
changeExpression('raka', 'objection', 1500);

const caseId = G.caseOrder[G.caseIdx];
const panicExpr = caseId === 'suryo' ? 'terpojok' : 
                  caseId === 'ratna' ? 'panik' : 'kalah';
changeExpression(caseId, panicExpr, 2000);

changeExpression('hakim', 'serius', 1800);
```

**Tambahkan di** `else {` block:
```javascript
// Wrong objection expressions
changeExpression('raka', 'kecewa', 1500);

const caseId = G.caseOrder[G.caseIdx];
const defExpr = caseId === 'dirga' ? 'sombong' : 'marah';
changeExpression(caseId, defExpr, 1500);
```

---

## ✅ TESTING CHECKLIST

### Test Lokal:
```
1. [ ] Buka game.html di browser
2. [ ] Cek console (F12) untuk error loading
3. [ ] Mulai game → cek karakter muncul
4. [ ] Test objection → cek ekspresi berubah
5. [ ] Test semua 3 level
```

### Test Asset:
```
1. [ ] Semua karakter load dengan benar
2. [ ] Transparansi background berfungsi
3. [ ] Ukuran proporsional
4. [ ] Ekspresi berubah saat objection
5. [ ] Tidak ada broken image (?)
```

### Troubleshooting:
```
❌ Gambar tidak muncul
   → Cek path di CHARACTER_ASSETS
   → Cek nama file (case-sensitive!)
   → Cek folder structure

❌ Background putih
   → PNG tidak transparan
   → Re-generate dengan prompt yang benar

❌ Ukuran tidak pas
   → Adjust height di CSS .char-fig img
```

---

## 📦 DEPLOYMENT

### GitHub Pages:
```bash
git add .
git commit -m "Add character sprites"
git push origin main
```

### Netlify Drag & Drop:
```
1. Zip seluruh folder project
2. Drag ke netlify.com/drop
3. Done!
```

### Local Server (Test):
```bash
# Python
python -m http.server 8000

# Node.js
npx http-server

# Buka: http://localhost:8000
```

---

## 🎉 SELESAI!

Total waktu: **~45-60 menit**
- Generate: 15 menit
- Crop: 5 menit
- Integrate: 30 menit
- Test: 10 menit

**Next Steps:**
- [ ] Test di berbagai browser
- [ ] Optimize PNG size (TinyPNG)
- [ ] Add loading screen
- [ ] Deploy online

---

**GOOD LUCK! 🚀**
