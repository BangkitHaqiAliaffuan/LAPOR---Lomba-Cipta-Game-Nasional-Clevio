# 🔧 PANDUAN INTEGRASI ASSET PNG KE GAME

## 📂 Struktur Folder Project

```
project/
├── game.html                          # File game utama
├── assets/
│   └── characters/
│       ├── hakim/
│       ├── raka/
│       ├── suryo/
│       ├── ratna/
│       ├── dirga/
│       ├── budi/
│       ├── sari/
│       └── irwan/
├── PROMPTS_KARAKTER_GEMINI.md        # Prompt untuk generate asset
└── INTEGRASI_ASSET.md                # File ini
```

---

## 🎯 LANGKAH INTEGRASI

### 1️⃣ PERSIAPAN ASSET

Setelah generate semua PNG dari Gemini AI:

1. **Rename file** sesuai konvensi:
   - Format: `[nama]_[ekspresi].png`
   - Contoh: `raka_objection.png`, `hakim_marah.png`

2. **Optimize PNG** (opsional tapi direkomendasikan):
   - Gunakan TinyPNG.com atau ImageOptim
   - Target: < 100KB per file
   - Tetap pertahankan transparansi

3. **Organize ke folder** sesuai struktur di atas

---

## 🔨 MODIFIKASI KODE GAME

### A. Tambahkan Mapping Asset di JavaScript

Tambahkan setelah line `const DEFENDANTS = {`:

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

### B. Update CSS untuk Image Display

Ganti section `.char-fig svg` dengan:

```css
/* Character images */
.char-fig img {
  width: auto;
  height: 180px; /* Sesuaikan dengan kebutuhan */
  filter: drop-shadow(0 4px 8px rgba(0,0,0,.5));
  transition: transform .3s, filter .3s;
  image-rendering: crisp-edges; /* Untuk pixel art style */
}

.char-fig.talking img {
  animation: charTalk .15s steps(2) infinite;
}

.char-fig.shake img {
  animation: charShake .4s ease;
}

/* Adjust character slot sizes */
.char-slot.judge .char-fig img {
  height: 200px; /* Hakim lebih besar */
}

.char-slot.witness .char-fig img {
  height: 160px; /* Saksi lebih kecil */
}
```

---

### C. Buat Helper Function untuk Load Image

Tambahkan function baru:

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
  
  // Clear existing content
  figElement.innerHTML = '';
  
  // Create and append image
  const img = document.createElement('img');
  img.src = assetPath;
  img.alt = `${characterKey} ${expression}`;
  img.onerror = function() {
    console.error(`Failed to load: ${assetPath}`);
    // Fallback to placeholder or SVG
    figElement.innerHTML = '<div style="width:128px;height:180px;background:#333;display:flex;align-items:center;justify-content:center;color:#999;">?</div>';
  };
  
  figElement.appendChild(img);
}

function changeExpression(characterKey, expression, duration = 0) {
  const elementId = `fig-${characterKey}`;
  setCharacterImage(elementId, characterKey, expression);
  
  // Auto-revert to netral after duration
  if (duration > 0) {
    setTimeout(() => {
      setCharacterImage(elementId, characterKey, 'netral');
    }, duration);
  }
}
```

---

### D. Update Function `loadCase()`

Modifikasi bagian yang set SVG karakter:

```javascript
function loadCase(){
  const caseId = G.caseOrder[G.caseIdx];
  const def = DEFENDANTS[caseId];
  const wit = WITNESSES[caseId];

  // Update case title
  document.getElementById('tb-case').textContent = def.caseTitle;

  // Load defendant image (ganti SVG dengan PNG)
  setCharacterImage('fig-defendant', caseId, 'netral');
  document.getElementById('defendant-name-tag').textContent = def.name;

  // Load witness image
  if(wit){
    setCharacterImage('fig-witness', caseId.toLowerCase(), 'netral'); // budi/sari/irwan
    document.getElementById('witness-name-tag').textContent = wit.tag;
    document.getElementById('char-witness').style.display = 'flex';
  } else {
    document.getElementById('char-witness').style.display = 'none';
  }

  // Load prosecutor (Raka) and judge
  setCharacterImage('fig-prosecutor', 'raka', 'netral');
  setCharacterImage('fig-judge', 'hakim', 'netral');

  // ... rest of function
}
```

---

### E. Update Animasi Ekspresi

Modifikasi function `processBantah()`:

```javascript
function processBantah(docId){
  // ... existing code ...

  if(isCorrect){
    G.correctBantah++;
    
    // Change prosecutor to objection pose
    changeExpression('raka', 'objection', 1500);
    
    // Defendant shows panic/cornered expression
    const caseId = G.caseOrder[G.caseIdx];
    const panicExpr = caseId === 'suryo' ? 'terpojok' : 
                      caseId === 'ratna' ? 'panik' : 'kalah';
    changeExpression(caseId, panicExpr, 2000);
    
    // Judge shows serious expression
    changeExpression('hakim', 'serius', 1800);
    
    // ... rest of code ...
  } else {
    G.wrongBantah++;
    
    // Prosecutor disappointed
    changeExpression('raka', 'kecewa', 1500);
    
    // Defendant smirks/defensive
    const caseId = G.caseOrder[G.caseIdx];
    const defExpr = caseId === 'dirga' ? 'sombong' : 'marah';
    changeExpression(caseId, defExpr, 1500);
    
    // ... rest of code ...
  }
}
```

---

### F. Tambahkan Expression Triggers di Statement

Update `renderStatement()` untuk trigger ekspresi otomatis:

```javascript
function renderStatement(stmt){
  // ... existing code ...

  // Auto-trigger expressions based on speaker and content
  if(stmt.speaker === 'HAKIM WIBOWO'){
    if(stmt.text.includes('Cukup!') || stmt.text.includes('GAME OVER')){
      changeExpression('hakim', 'marah', 0);
    } else if(stmt.text.includes('Majelis mencatat')){
      changeExpression('hakim', 'serius', 0);
    } else {
      changeExpression('hakim', 'netral', 0);
    }
  }

  if(stmt.speaker === 'RAKA'){
    if(stmt.text.includes('buktikan') || stmt.text.includes('Penutup')){
      changeExpression('raka', 'tersenyum', 0);
    } else if(stmt.text.includes('?')){
      changeExpression('raka', 'berpikir', 0);
    } else {
      changeExpression('raka', 'netral', 0);
    }
  }

  // Defendant expressions
  const caseId = G.caseOrder[G.caseIdx];
  if(stmt.speaker === DEFENDANTS[caseId]?.name){
    if(stmt.canBantah){
      // Lying/nervous when statement can be objected
      changeExpression(caseId, 'gugup', 0);
    } else if(stmt.text.includes('keberatan') || stmt.text.includes('tidak')){
      changeExpression(caseId, 'marah', 0);
    } else {
      changeExpression(caseId, 'netral', 0);
    }
  }

  // Witness expressions
  const witKey = caseId; // budi/sari/irwan
  const witName = WITNESSES[caseId]?.name;
  if(stmt.speaker === witName){
    if(stmt.canBantah){
      changeExpression(witKey, 'gugup', 0);
    } else if(stmt.text.includes('tidak tahu') || stmt.text.includes('tidak ingat')){
      changeExpression(witKey, 'tidak_yakin', 0);
    } else {
      changeExpression(witKey, 'netral', 0);
    }
  }

  // ... rest of function ...
}
```

---

## 🎨 OPTIMASI TAMBAHAN

### Preload Images

Tambahkan di awal game untuk loading lebih smooth:

```javascript
// Preload all character images
function preloadAssets(){
  const images = [];
  Object.keys(CHARACTER_ASSETS).forEach(char => {
    Object.values(CHARACTER_ASSETS[char]).forEach(path => {
      const img = new Image();
      img.src = path;
      images.push(img);
    });
  });
  return images;
}

// Call on game init
window.addEventListener('DOMContentLoaded', () => {
  preloadAssets();
});
```

---

### Loading Screen (Opsional)

Tambahkan loading indicator saat asset dimuat:

```html
<!-- Add to HTML -->
<div id="loading-screen" style="position:fixed;inset:0;background:#1c1a14;display:flex;align-items:center;justify-content:center;z-index:9999;">
  <div style="text-align:center;color:#c9a84c;">
    <div style="font-size:3rem;margin-bottom:16px;">⚖️</div>
    <div style="font-family:'Courier Prime',monospace;letter-spacing:3px;">MEMUAT ASSET...</div>
  </div>
</div>
```

```javascript
// Hide loading screen after assets loaded
Promise.all(preloadAssets().map(img => {
  return new Promise(resolve => {
    if(img.complete) resolve();
    else {
      img.onload = resolve;
      img.onerror = resolve;
    }
  });
})).then(() => {
  document.getElementById('loading-screen').style.display = 'none';
});
```

---

## 🐛 TROUBLESHOOTING

### Asset tidak muncul?
1. Cek path di console browser (F12)
2. Pastikan struktur folder benar
3. Cek case-sensitive filename (Linux/Mac)
4. Pastikan file PNG valid dan tidak corrupt

### Ukuran tidak pas?
- Adjust `height` di CSS `.char-fig img`
- Gunakan `object-fit: contain` jika perlu

### Performance lambat?
- Optimize PNG dengan TinyPNG
- Gunakan lazy loading
- Reduce resolution jika perlu (128x256 cukup)

---

## ✅ CHECKLIST INTEGRASI

- [ ] Generate semua 30 PNG dari Gemini AI
- [ ] Optimize ukuran file PNG
- [ ] Organize ke folder structure
- [ ] Tambahkan `CHARACTER_ASSETS` mapping
- [ ] Update CSS untuk image display
- [ ] Implementasi `setCharacterImage()` function
- [ ] Update `loadCase()` function
- [ ] Implementasi `changeExpression()` triggers
- [ ] Tambahkan preload function
- [ ] Test semua karakter dan ekspresi
- [ ] Test di berbagai browser
- [ ] Deploy dengan asset folder

---

**SELAMAT MENGINTEGRASIKAN! 🚀**
