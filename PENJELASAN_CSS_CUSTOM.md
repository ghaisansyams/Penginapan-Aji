# 🎨 PENJELASAN LENGKAP CUSTOM CSS STYLING

## 📋 Bagian `<style>` Tag HTML

Bagian ini berisi **CSS Custom** yang tidak bisa dibuat hanya dengan Tailwind Class. Perlu ditulis manual di `<style>`.

---

## 1️⃣ FONT DEFAULT UNTUK SEMUA ELEMEN

```css
* { font-family: 'Poppins', sans-serif; }
```

### Penjelasan:

| Bagian | Arti |
|--------|------|
| `*` | Selector universal = SEMUA elemen di halaman |
| `font-family` | Property untuk mengganti jenis font |
| `'Poppins'` | Nama font custom (sudah di-import dari Google Fonts) |
| `sans-serif` | Font fallback jika Poppins tidak tersedia (jenis sans-serif generik) |

### Analogi:
```
* { font-family: 'Poppins', sans-serif; }
↓
"Untuk SEMUA elemen, gunakan font Poppins. Jika tidak ada, gunakan font sans-serif generik"
```

### Hasil:
- Semua text di website pakai font Poppins
- Jika browser tidak punya Poppins, akan auto pakai sans-serif (Arial, Helvetica, dll)

---

## 2️⃣ SMOOTH SCROLL BEHAVIOR

```css
html { scroll-behavior: smooth; }
```

### Penjelasan:

| Bagian | Arti |
|--------|------|
| `html` | Target elemen `<html>` (seluruh halaman) |
| `scroll-behavior` | Property untuk mengatur gaya scroll |
| `smooth` | Scroll dengan animasi halus (bukan langsung loncat) |

### Contoh Praktik:

**TANPA `smooth`:**
```
Klik link "#home"
↓
Halaman langsung LONCAT ke section home (kaku)
```

**DENGAN `smooth`:**
```
Klik link "#home"
↓
Halaman scroll PERLAHAN ke section home (smooth/halus)
```

### Kode yang Memanfaatkan:
```html
<a href="#home">Ke Home</a>
<a href="#destinations">Ke Destinasi</a>
<a href="#contact">Ke Kontak</a>

<!-- Saat diklik, page akan scroll smooth ke section tersebut -->
<section id="home">...</section>
<section id="destinations">...</section>
<section id="contact">...</section>
```

---

## 3️⃣ CARD HOVER ANIMATION

```css
.card-hover { transition: all 300ms ease; }
```

### Penjelasan:

| Bagian | Arti |
|--------|------|
| `.card-hover` | Custom class untuk card element |
| `transition` | Property untuk animasi perubahan |
| `all` | Berlaku untuk SEMUA property yang berubah |
| `300ms` | Durasi animasi 300 milidetik (0.3 detik) |
| `ease` | Timing function = smooth dari awal sampai akhir |

### Breakdown timing function:
```
linear    = perubahan konstan (kecepatan sama)
ease      = perubahan smooth (mulai lambat, cepat, lambat) ← YANG DIPAKAI
ease-in   = lambat di awal, cepat di akhir
ease-out  = cepat di awal, lambat di akhir
```

### Visualisasi:
```
TANPA transition (instant):
Normal  → [LANGSUNG] → Hover
size=1x              size=1.05x

DENGAN transition (smooth):
Normal  → [0ms] → [100ms] → [200ms] → [300ms] → Hover
size=1x    1.01x   1.02x    1.03x    1.04x   size=1.05x
```

---

## 4️⃣ CARD HOVER TRANSFORM EFFECT

```css
.card-hover:hover { 
    transform: scale(1.05); 
    box-shadow: 0 20px 40px rgba(0,0,0,0.15); 
}
```

### Penjelasan Detil:

**Bagian 1: Selector**
```css
.card-hover:hover
│      │        │
│      │        └─ Pseudo-class = saat di-hover (mouse over)
│      └─────────── Class yang di-target
└────────────────── Custom class
```

**Bagian 2: Transform Scale**
```css
transform: scale(1.05);
│          │     │
│          │     └─ 1.05 = 105% dari ukuran asli (5% lebih besar)
│          └─────── CSS property untuk transformasi
└────────────────── Tipe transformasi = scale (zoom/perbesar)

Contoh nilai scale:
scale(0.95)  = 95% (lebih kecil 5%)
scale(1.0)   = 100% (ukuran normal)
scale(1.05)  = 105% (lebih besar 5%)
scale(1.1)   = 110% (lebih besar 10%)
scale(1.5)   = 150% (lebih besar 50%)
```

**Bagian 3: Box Shadow**
```css
box-shadow: 0 20px 40px rgba(0,0,0,0.15);
│           │  │   │   │
│           │  │   │   └─ Warna bayangan = hitam transparan 15%
│           │  │   └───── Blur radius = 40px (bayangan blur)
│           │  └───────── Spread = 20px (jarak bayangan dari element)
│           └──────────── Offset X = 0 (tidak geser horizontal)

Format box-shadow:
box-shadow: offset-x offset-y blur-radius color;
          │  X-axis  Y-axis   blur       warna bayangan
```

### Visualisasi Box Shadow:

```
SHADOW NORMAL (shadow-md):
┌──────────────┐
│   CARD       │
└──────────────┘
  ▒▒▒▒▒▒▒▒▒▒▒▒  (bayangan kecil)


SHADOW HOVER (20px 40px):
┌──────────────┐
│   CARD       │
└──────────────┘
     ▒▒▒▒▒▒▒▒▒▒▒▒
     ▒▒▒▒▒▒▒▒▒▒▒▒   (bayangan lebih besar & blur)
     ▒▒▒▒▒▒▒▒▒▒▒▒
```

### rgba(0,0,0,0.15) Penjelasan:
```
rgba( R   G   B   A  )
     │   │   │   │
     0   0   0  0.15
     │   │   │   │
     └───┴───┴───┴─ Hitam dengan opacity 15% (transparan)

A (Alpha) values:
0    = transparan penuh (tidak terlihat)
0.15 = 15% opacity (sangat transparan)
0.5  = 50% opacity (setengah transparan)
1.0  = 100% opacity (tidak transparan)
```

---

## 5️⃣ NAVIGATION LINK HOVER

```css
.nav-link { transition: color 300ms ease; }
```

### Penjelasan:

```css
.nav-link { transition: color 300ms ease; }
           │           │
           │           └─ Hanya warna (color) yang di-animate
           └───────────── Bukan semua property (all)
```

Bedanya:
```css
transition: all 300ms ease;     /* Animate SEMUA property */
transition: color 300ms ease;   /* Animate hanya COLOR */
```

### Hasil:
- Hanya mengubah warna teks yang smooth
- Property lain tidak di-animate
- Lebih efisien untuk performa

---

## 6️⃣ NAV LINK HOVER COLOR

```css
.nav-link:hover { color: #FF385C; }
```

### Penjelasan:

```
.nav-link:hover       = Link di navbar saat di-hover
{ color: #FF385C; }   = Berubah jadi warna merah custom

#FF385C = Warna merah (hex code)
         = FF (merah max), 38 (hijau sedikit), 5C (biru sedikit)
```

### Kombinasi dengan transition:
```
DEFAULT (tidak hover):
[Home] [Destinations] [Stays]
(warna abu-abu gray-600)

SAAT HOVER:
[Home] [Destinations👈] [Stays]
(300ms smooth berubah jadi warna merah FF385C)
```

---

## 7️⃣ FACILITY CARD HOVER EFFECT

```css
.facility-card { transition: all 300ms ease; }
```

Sama seperti `.card-hover`, tapi untuk facility card.

```css
.facility-card:hover { 
    box-shadow: 0 10px 30px rgba(0,0,0,0.1); 
    border-color: #FFCDD6 !important; 
    transform: translateY(-2px); 
}
```

### Penjelasan Detil:

**1. Box Shadow:**
```css
box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            │  │   │   │
            0  10  30  0.1
            │  px  px  opacity
            └─ Tidak ada offset X (0)
```

**2. Border Color:**
```css
border-color: #FFCDD6 !important;
```

| Bagian | Arti |
|--------|------|
| `border-color` | Ubah warna border card |
| `#FFCDD6` | Warna pink muda custom |
| `!important` | **PAKSA** property ini (override yang lain) |

**Kenapa `!important`?**
```
Tanpa !important:
- CSS class mungkin override property ini
- Border color tidak berubah

Dengan !important:
- Paksa property ini di-apply no matter what
- Border color PASTI berubah jadi pink
```

**3. Translate Y:**
```css
transform: translateY(-2px);
           │         │
           │         └─ -2px = naik 2 pixel
           └───────────── Transform = perubahan posisi/ukuran

translateY(-2px) = naik 2px dari posisi normal
translateY(2px)  = turun 2px dari posisi normal
```

### Visualisasi Gabungan Hover:

```
NORMAL (default):
┌──────────────┐
│ FACILITY     │  border-color: gray
│ 🍽️ Dapur    │  position: normal
└──────────────┘

SAAT HOVER (300ms smooth):
     ┌──────────────┐ ← naik 2px (translateY(-2px))
     │ FACILITY     │  border-color: pink (#FFCDD6)
     │ 🍽️ Dapur    │  shadow: lebih besar (10px 30px)
     └──────────────┘
```

---

## 8️⃣ ROW HOVER (TABLE ROWS)

```css
.row-hover:hover { background-color: #fef9fa; }
```

### Penjelasan:

| Bagian | Arti |
|--------|------|
| `.row-hover` | Class untuk table row (`<tr>`) |
| `:hover` | Saat mouse hover di baris |
| `background-color: #fef9fa` | Background berubah jadi pink sangat muda |

### Visualisasi Table:

```
┌─────────────────────────────────────┐
│ Bulan    │ Harga       │ Suhu       │
├─────────────────────────────────────┤
│ Januari  │ Rp 376.359  │ 28°C       │
├─────────────────────────────────────┤
│ Februari │ Rp 376.359  │ 28°C       │ ← Hover di sini
├─────────────────────────────────────┤
│ Maret    │ Rp 376.359  │ 29°C       │
└─────────────────────────────────────┘

SAAT HOVER FEBRUARY:
┌─────────────────────────────────────┐
│ Bulan    │ Harga       │ Suhu       │
├─────────────────────────────────────┤
│ Januari  │ Rp 376.359  │ 28°C       │
├─────────────────────────────────────┤
│ Februari │ Rp 376.359  │ 28°C       │ ← Background jadi pink (#fef9fa)
├─────────────────────────────────────┤
│ Maret    │ Rp 376.359  │ 29°C       │
└─────────────────────────────────────┘
```

**#fef9fa = Warna Pink Sangat Muda:**
```
#fef9fa
 │││
 fe = merah max (254)
   f9 = hijau hampir max (249)
     fa = biru max (250)

Hasil = warna pink sangat terang/muda
```

---

## 9️⃣ MOBILE MENU VISIBILITY

```css
#mobile-menu { display: none; }
```

### Penjelasan:

| Bagian | Arti |
|--------|------|
| `#mobile-menu` | ID element = menu mobile |
| `display: none` | **Sembunyikan** element (tidak terlihat, tidak ada space) |

### Hasil:
- Mobile menu disembunyikan default di halaman

```css
#mobile-menu.open { display: block; }
```

| Bagian | Arti |
|--------|------|
| `#mobile-menu.open` | Element dengan ID mobile-menu + class 'open' |
| `display: block` | **Tampilkan** element |

### Cara Kerja di JavaScript:

```javascript
// Saat hamburger button diklik:
function toggleMenu() {
    const menu = document.getElementById('mobile-menu');
    menu.classList.toggle('open');  // Tambah/hapus class 'open'
}

// Jika class 'open' ada:
// → CSS .open { display: block } → Menu tampil

// Jika class 'open' tidak ada:
// → CSS #mobile-menu { display: none } → Menu sembunyikan
```

### Visualisasi:

```
DEFAULT (halaman pertama):
┌─────────────┐
│ NAVBAR      │  #mobile-menu { display: none; }
├─────────────┤  Menu tidak ada
│ CONTENT     │
└─────────────┘


SAAT KLIK HAMBURGER (class 'open' ditambahkan):
┌─────────────┐
│ NAVBAR      │  #mobile-menu.open { display: block; }
├─────────────┤
│ [Menu]      │  ← Menu tampil!
│ • Home      │
│ • Destinasi │
│ • Stays     │
├─────────────┤
│ CONTENT     │
└─────────────┘
```

---

## 🔟 STAT CARD HOVER EFFECT

```css
.stat-card { transition: all 300ms ease; }
```

Transisi smooth untuk semua property yang berubah.

```css
.stat-card:hover { 
    transform: translateY(-4px); 
    box-shadow: 0 12px 30px rgba(255,56,92,0.1); 
}
```

### Penjelasan:

**1. Translate Y:**
```css
transform: translateY(-4px);
           │         │
           │         └─ -4px = naik 4px dari posisi normal
           └───────────── Lebih besar dari facility-card (-2px)
```

**2. Box Shadow dengan Warna Custom:**
```css
box-shadow: 0 12px 30px rgba(255,56,92,0.1);
            │  │   │   │
            0  12  30  rgba(255,56,92,0.1)
            │  px  px  │
            │         └─ Warna merah (#FF385C) dengan opacity 10%
            └─ Tidak ada offset X

rgba(255,56,92,0.1):
- 255 = merah max (FF dalam hex)
- 56  = hijau sedikit (38 dalam hex)
- 92  = biru sedikit (5C dalam hex)
- 0.1 = opacity 10% (transparan)

Hasilnya = bayangan merah muda transparan
```

### Visualisasi:

```
NORMAL STAT CARD:
┌──────────────────┐
│ 1,060            │
│ Total sewa       │  shadow: none atau kecil
│ tempat liburan   │
└──────────────────┘

SAAT HOVER:
┌──────────────────┐ ← naik 4px
│ 1,060            │
│ Total sewa       │  shadow: bayangan merah muda
│ tempat liburan   │
└──────────────────┘
   ╱╱╱╱╱╱╱╱╱╱╱╱╱╱  (bayangan merah 10% opacity)
```

---

## 1️⃣1️⃣ DESTINATION CARD IMAGE ZOOM

```css
.dest-card:hover img { transform: scale(1.1); }
```

### Penjelasan:

```css
.dest-card:hover img
│          │      │
│          │      └─ Target elemen <img> DALAM .dest-card
│          └───────── Saat parent (.dest-card) di-hover
└──────────────────── Custom class destination card

transform: scale(1.1)
           └─ Zoom gambar 10% lebih besar
```

### Visualisasi:

```
DESTINATION CARD:
┌──────────────────┐
│ [GAMBAR KOTA]    │  100% ukuran normal
│ [Jakarta]        │
│ Sewa tempat...   │
└──────────────────┘

SAAT HOVER CARD:
┌──────────────────┐
│ [GAMBAR ZOOM110%]│  ← Gambar zoom 10%
│ [Jakarta]        │
│ Sewa tempat...   │
└──────────────────┘
```

---

## 1️⃣2️⃣ IMAGE TRANSITION SMOOTH

```css
.dest-card img { transition: transform 400ms ease; }
```

### Penjelasan:

| Bagian | Arti |
|--------|------|
| `.dest-card img` | Gambar dalam destination card |
| `transition: transform` | Animate hanya transform (scale, rotate, dll) |
| `400ms` | Durasi 400 milidetik (lebih lambat dari 300ms) |

### Mengapa 400ms untuk image?
```
.card-hover (card)       = 300ms (responsif cepat)
.dest-card img (image)   = 400ms (smooth lebih halus)

Image perlu lebih lambat agar terasa smooth/enak di mata
```

---

## 1️⃣3️⃣ TAB BUTTON ACTIVE STATE

```css
.tab-btn.active { 
    background-color: #FF385C; 
    color: white; 
}
```

### Penjelasan:

```css
.tab-btn.active
│       │
│       └─ Class 'active' ditambahkan (biasanya via JavaScript)
└───────── Custom class tab button

background-color: #FF385C  → Background jadi merah
color: white               → Text jadi putih
```

### Visualisasi Tab:

```
TAB DEFAULT (tidak active):
┌────────────┬────────────┬────────────┬────────────┐
│ Destinasi  │ Tipe       │ Perbandingan│ Panduan   │
│ (abu-abu)  │ (abu-abu)  │ (abu-abu)   │ (abu-abu) │
└────────────┴────────────┴────────────┴────────────┘

TAB SAAT DIKLIK (active):
┌────────────┬────────────┬────────────┬────────────┐
│ Destinasi  │ Tipe       │ Perbandingan│ Panduan   │
│ (MERAH+PUTIH)│(abu-abu)  │ (abu-abu)   │ (abu-abu) │
└────────────┴────────────┴────────────┴────────────┘
  ↑ Active tab berubah warna
```

---

## 1️⃣4️⃣ TAB BUTTON TRANSITION

```css
.tab-btn { transition: all 200ms ease; }
```

### Penjelasan:

```css
transition: all 200ms ease
            │   │
            │   └─ 200ms (cepat, responsif)
            └───── all = semua property berubah smooth
```

---

## 1️⃣5️⃣ DATE INPUT STYLING

```css
input[type="date"]::-webkit-calendar-picker-indicator { 
    opacity: 0.5; 
    cursor: pointer; 
}
```

### Penjelasan Complex:

**Selector:**
```css
input[type="date"]
│     │      │
│     │      └─ Value = "date"
│     └───────── Attribute selector (cari attribute tertentu)
└─────────────── Element = input

::-webkit-calendar-picker-indicator
│         │
│         └─ Calendar icon yang tampil di date input
└──────────── Pseudo-element vendor prefix (untuk browser webkit)

Apa itu Webkit?
= Engine browser: Chrome, Safari, Edge
```

**Property:**
```css
opacity: 0.5     → Calendar icon transparan 50% (lebih redup)
cursor: pointer  → Cursor berubah jadi pointer (clickable)
```

### Visualisasi Date Input:

```
NORMAL DATE INPUT:
┌──────────────────────────┐
│ [2024-01-15]        📅   │  Calendar icon 100% opacity (terang)
└──────────────────────────┘

DENGAN CSS STYLING:
┌──────────────────────────┐
│ [2024-01-15]        📅   │  Calendar icon 50% opacity (redup)
└──────────────────────────┘

SAAT HOVER ICON:
┌──────────────────────────┐
│ [2024-01-15]        👆   │  Cursor = pointer (bisa diklik)
└──────────────────────────┘
```

---

## 📚 RINGKASAN SEMUA CSS CUSTOM

| No | Class/Selector | Fungsi | Effect |
|----|---|---|---|
| 1 | `*` | Font default | Semua text pakai Poppins |
| 2 | `html` | Scroll smooth | Scroll halus ke anchor |
| 3 | `.card-hover` | Transition card | 300ms smooth all property |
| 4 | `.card-hover:hover` | Hover effect | Scale 1.05 + shadow besar |
| 5 | `.nav-link` | Transition link | 300ms smooth color |
| 6 | `.nav-link:hover` | Hover link | Text jadi merah |
| 7 | `.facility-card` | Transition facility | 300ms smooth all |
| 8 | `.facility-card:hover` | Hover facility | Shadow + border pink + naik 2px |
| 9 | `.row-hover:hover` | Hover table row | Background jadi pink muda |
| 10 | `#mobile-menu` | Sembunyikan | display: none |
| 11 | `#mobile-menu.open` | Tampilkan | display: block |
| 12 | `.stat-card` | Transition stat | 300ms smooth all |
| 13 | `.stat-card:hover` | Hover stat | Naik 4px + shadow merah |
| 14 | `.dest-card:hover img` | Image zoom | Scale 1.1 (zoom 10%) |
| 15 | `.dest-card img` | Image transition | 400ms smooth transform |
| 16 | `.tab-btn.active` | Tab aktif | Background merah + text putih |
| 17 | `.tab-btn` | Tab transition | 200ms smooth all |
| 18 | `input[type="date"]::-webkit` | Date icon | Opacity 50% + pointer cursor |

---

## 💡 TIPS PENTING

### 1. Mengapa Perlu CSS Custom?
Tailwind CSS hanya untuk utility classes (padding, margin, color, dll). Untuk hal kompleks seperti:
- Transition dengan timing
- Pseudo-element (`:hover`, `:active`, dll)
- Responsive behavior kompleks
- Animation custom

Perlu ditulis manual di `<style>`.

### 2. !important Kapan Digunakan?
```css
!important  ← Gunakan HANYA jika benar-benar diperlukan

Sebab:
- Override styling lain (bisa buat masalah)
- Buat debug lebih sulit
- Anti-pattern dalam CSS

Gunakan jika:
- Library punya styling yang conflicting
- Need to override 3rd party styles
```

### 3. Prefix -webkit- Apa?
```css
::-webkit-calendar-picker-indicator
 │       │
 │       └─ Vendor prefix (spesifik untuk webkit browsers)
 └────────── Tanda double colon (pseudo-element)

Mengapa?
- Browser punya engine berbeda
- Webkit (Chrome, Safari, Edge) = -webkit-
- Mozilla (Firefox) = -moz-
- Opera = -o-
```

---

## 🎯 CONTOH IMPLEMENTASI LENGKAP

### Membuat Smooth Hover Card:

```html
<!-- HTML -->
<div class="card-hover bg-white rounded-2xl overflow-hidden shadow-md cursor-pointer">
    <img src="photo.jpg" class="w-full h-52 object-cover">
    <div class="p-4">
        <h3>Judul Card</h3>
    </div>
</div>
```

```css
<!-- CSS Custom -->
<style>
    /* Setup: semua property smooth 300ms */
    .card-hover { 
        transition: all 300ms ease; 
    }
    
    /* Effect: saat hover */
    .card-hover:hover { 
        transform: scale(1.05);                        /* Zoom 5% */
        box-shadow: 0 20px 40px rgba(0,0,0,0.15);     /* Shadow besar */
    }
</style>
```

**Hasilnya:**
- Saat mouse over card → card zoom smooth & shadow membesar
- Saat mouse out → card kembali normal smooth

---

Semoga penjelasan ini lebih lengkap! 🚀
