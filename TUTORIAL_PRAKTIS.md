# 🎓 TUTORIAL PRAKTIS TAILWIND CSS - WEBSITE PENGINAPAN

---

## 📌 BAGIAN 1: MEMAHAMI STRUKTUR NAVBAR

### Kode Navbar:
```html
<nav id="navbar" class="fixed top-0 left-0 right-0 z-50 bg-white shadow-sm border-b border-gray-100">
```

### Penjelasan Perbaris:

| Class | Arti |
|-------|------|
| `fixed` | Navbar menempel di atas, tidak bergerak saat scroll |
| `top-0` | Posisi dari atas = 0 (pas di tepi atas layar) |
| `left-0 right-0` | Mulai dari kiri tepi sampai kanan tepi (full width) |
| `z-50` | Layer paling atas agar menu tidak tertutup elemen lain |
| `bg-white` | Background putih |
| `shadow-sm` | Bayangan tipis di bawah navbar |
| `border-b` | Ada garis di bawah navbar |
| `border-gray-100` | Garis warna abu-abu sangat muda (tipis) |

---

## 📌 BAGIAN 2: FLEXBOX UNTUK ALIGNMENT

### Kode:
```html
<div class="flex items-center justify-between h-16">
```

### Penjelasan:

```
┌─────────────────────────────────────────┐
│  flex: membuat layout baris (horizontal) │
│                                         │
│  [Logo]      [Menu-Menu]      [Button]  │ items-center (center vertikal)
│                                         │
│  justify-between (pisahkan ke ujung)    │
└─────────────────────────────────────────┘

h-16 = tinggi 64px
```

**Hasil:**
- Logo di kiri
- Menu di tengah
- Button di kanan
- Semua center vertikal

---

## 📌 BAGIAN 3: RESPONSIVE GRID (ADAPTIVE LAYOUT)

### Kode:
```html
<div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
    <!-- Card 1 -->
    <!-- Card 2 -->
    <!-- ... -->
</div>
```

### Visualisasi:

**Mobile (grid-cols-1):**
```
┌───────────────┐
│   Card 1      │
├───────────────┤
│   Card 2      │
├───────────────┤
│   Card 3      │
├───────────────┤
│   Card 4      │
└───────────────┘
```

**Tablet (sm:grid-cols-2):**
```
┌──────────┬──────────┐
│ Card 1   │ Card 2   │
├──────────┼──────────┤
│ Card 3   │ Card 4   │
└──────────┴──────────┘
```

**Desktop (lg:grid-cols-4):**
```
┌──────┬──────┬──────┬──────┐
│Card1 │Card2 │Card3 │Card4 │
└──────┴──────┴──────┴──────┘
```

---

## 📌 BAGIAN 4: MEMBUAT CARD DENGAN HOVER EFFECT

### Kode Lengkap:
```html
<div class="card-hover bg-white rounded-2xl overflow-hidden shadow-md cursor-pointer group">
    <!-- Image -->
    <img src="..." class="w-full h-52 object-cover group-hover:scale-105 transition-transform duration-500">
    
    <!-- Info -->
    <div class="p-4">
        <h3 class="font-semibold text-gray-800 text-sm">Rumah di Jakarta</h3>
        <p class="text-xs text-gray-400">Jakarta Selatan</p>
        <p class="text-sm"><span class="font-bold">Rp 450.000</span><span class="text-gray-400 text-xs"> / malam</span></p>
    </div>
</div>
```

### Penjelasan Detail:

**1. Container Card:**
```css
bg-white          /* Background putih */
rounded-2xl       /* Sudut membulat 1rem */
overflow-hidden   /* Gambar tidak keluar dari border */
shadow-md         /* Bayangan medium */
cursor-pointer    /* Cursor berubah jadi pointer (clickable) */
group             /* Grouping untuk parent hover effect */
```

**2. Hover Effect di CSS Custom:**
```css
.card-hover:hover {
    transform: scale(1.05);                        /* Membesar 5% */
    box-shadow: 0 20px 40px rgba(0,0,0,0.15);     /* Bayangan lebih besar */
}
```

**3. Gambar:**
```css
w-full            /* Lebar penuh container */
h-52              /* Tinggi 13rem (208px) */
object-cover      /* Gambar cover area, tetap proposi */
group-hover:scale-105    /* Zoom gambar saat hover parent */
transition-transform     /* Zoom smooth */
duration-500             /* Durasi 500ms */
```

**4. Info Box:**
```css
p-4               /* Padding 1rem */

/* Title */
font-semibold     /* Bold tebal */
text-gray-800     /* Warna teks hitam */
text-sm           /* Ukuran font kecil */

/* Location */
text-xs           /* Ukuran sangat kecil */
text-gray-400     /* Warna abu-abu medium */

/* Price */
font-bold         /* Bold */
text-gray-400 text-xs    /* Ukuran kecil dan abu-abu untuk '/malam' */
```

### Hasil Visual:
```
SEBELUM HOVER:
┌──────────────────┐
│  [GAMBAR RUMAH]  │  shadow-md (bayangan biasa)
├──────────────────┤
│ Rumah di Jakarta │
│ Jakarta Selatan  │
│ Rp 450.000/malam │
└──────────────────┘

SAAT HOVER:
┌──────────────────┐
│ [GAMBAR ZOOM105%]│  shadow lebih besar
├──────────────────┤
│ Rumah di Jakarta │
│ Jakarta Selatan  │
│ Rp 450.000/malam │
└──────────────────┘
```

---

## 📌 BAGIAN 5: INPUT FORM DENGAN FOCUS EFFECT

### Kode:
```html
<div class="border border-gray-200 rounded-2xl px-4 py-3 hover:border-rose-300 focus-within:border-rose-400 focus-within:ring-2 focus-within:ring-rose-50 transition-all">
    <label class="block text-xs font-bold text-gray-500 mb-1 uppercase tracking-wide">Lokasi</label>
    
    <div class="flex items-center space-x-2">
        <i class="fa-solid fa-location-dot text-rose-400 text-sm"></i>
        <input type="text" class="flex-1 text-sm text-gray-800 font-medium outline-none bg-transparent placeholder-gray-400" placeholder="Cari lokasi...">
    </div>
</div>
```

### Penjelasan State:

**DEFAULT (Initial State):**
```
┌─────────────────────────────┐
│ LOKASI                      │
│ 📍 Cari lokasi...           │
└─────────────────────────────┘
border-gray-200  = border abu-abu muda
```

**SAAT HOVER (Hover State):**
```
┌─────────────────────────────┐  border berubah jadi rose-300
│ LOKASI                      │
│ 📍 Cari lokasi...           │
└─────────────────────────────┘
```

**SAAT FOKUS (Focus State):**
```
┌═════════════════════════════┐  ring-rose-50 (glow effect)
┃ LOKASI                      ┃  border-rose-400 (warna merah)
┃ 📍 [CURSOR HERE]            ┃
┗═════════════════════════════┛
```

### Class Penjelasan:

```css
border              /* Border 1px */
border-gray-200     /* Border abu-abu muda */
rounded-2xl         /* Sudut membulat */

px-4 py-3           /* Padding dalam */

hover:border-rose-300       /* Border berubah saat hover */

focus-within:border-rose-400  /* Border berubah saat input fokus */
focus-within:ring-2           /* Ring border ganda saat fokus */
focus-within:ring-rose-50     /* Warna ring adalah rose sangat muda */

transition-all      /* Transisi smooth semua property */
```

**Input Field:**
```css
flex-1              /* Ambil ruang tersisa (flex) */
outline-none        /* Hilangkan outline bawaan browser */
bg-transparent      /* Background transparan (tidak ada warna) */
placeholder-gray-400 /* Warna placeholder abu-abu */
```

---

## 📌 BAGIAN 6: STATISTIK CARDS LAYOUT

### Kode:
```html
<div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
    <div class="stat-card bg-white rounded-2xl p-6 shadow-sm">
        <div class="flex items-start space-x-4">
            <div class="w-14 h-14 rounded-2xl flex items-center justify-center flex-shrink-0" style="background-color:#FFF0F3">
                <i class="fa-solid fa-house-chimney text-xl" style="color:#FF385C"></i>
            </div>
            
            <div>
                <p class="text-4xl font-extrabold text-gray-900 mb-1">1,060</p>
                <p class="text-sm font-bold text-gray-700 mb-1">Total sewa tempat</p>
                <p class="text-xs text-gray-400">Temukan 1,060 sewa tempat di Depok</p>
            </div>
        </div>
    </div>
</div>
```

### Breakdown:

**Grid Layout:**
```
MOBILE (1 kolom):
┌─────────────────────────┐
│     STAT CARD 1         │
├─────────────────────────┤
│     STAT CARD 2         │
├─────────────────────────┤
│     STAT CARD 3         │
└─────────────────────────┘

TABLET (2 kolom):
┌──────────────────┬──────────────────┐
│   STAT CARD 1    │   STAT CARD 2    │
├──────────────────┼──────────────────┤
│   STAT CARD 3    │   STAT CARD 4    │
└──────────────────┴──────────────────┘

DESKTOP (3 kolom):
┌──────────────┬──────────────┬──────────────┐
│ STAT CARD 1  │ STAT CARD 2  │ STAT CARD 3  │
├──────────────┼──────────────┼──────────────┤
│ STAT CARD 4  │ STAT CARD 5  │ STAT CARD 6  │
└──────────────┴──────────────┴──────────────┘
```

**Card Interior:**
```
┌──────────────────────────────┐
│ ┌────┐  1,060               │
│ │ 🏠 │  Total sewa tempat   │  flex + items-start
│ │    │  Temukan 1,060 sewa  │  space-x-4 (jarak icon & text)
│ └────┘                      │
└──────────────────────────────┘

Icon box:
w-14 h-14           = 56px x 56px (icon besar)
rounded-2xl         = border radius
flex items-center justify-center = icon center
flex-shrink-0       = jangan mengecil

Text:
text-4xl            = ukuran 36px
font-extrabold      = paling tebal (weight 800)
text-gray-900       = hitam
mb-1                = jarak ke teks berikutnya
```

---

## 📌 BAGIAN 7: TABEL DENGAN HOVER EFFECT

### Kode:
```html
<table class="w-full text-sm min-w-[600px]">
    <thead>
        <tr class="bg-gray-50 border-b border-gray-200">
            <th class="text-left px-6 py-4 font-semibold text-gray-500 text-xs uppercase tracking-wide">Bulan</th>
            <th class="text-center px-6 py-4 font-semibold text-gray-500 text-xs uppercase tracking-wide">Harga</th>
            <th class="text-center px-6 py-4 font-semibold text-gray-500 text-xs uppercase tracking-wide">Suhu</th>
            <th class="text-center px-6 py-4 font-semibold text-gray-500 text-xs uppercase tracking-wide">Musim</th>
        </tr>
    </thead>
    <tbody class="divide-y divide-gray-100">
        <tr class="row-hover transition-colors duration-200">
            <td class="px-6 py-4 font-semibold text-gray-800">Januari</td>
            <td class="px-6 py-4 text-center text-gray-600">Rp 376.359</td>
            <td class="px-6 py-4 text-center text-gray-600">28°C</td>
            <td class="px-6 py-4 text-center">
                <span class="bg-blue-50 text-blue-600 text-xs font-semibold px-3 py-1 rounded-full">Hujan</span>
            </td>
        </tr>
    </tbody>
</table>
```

### Visualisasi Tabel:

```
┌─────────────────────────────────────────────────────────┐
│ Bulan    │ Harga rata-rata │ Suhu rata-rata │ Musim     │ bg-gray-50 (header)
├─────────────────────────────────────────────────────────┤
│ Januari  │ Rp 376.359      │ 28°C           │ [Hujan]   │ row-hover (bisa di-hover)
├─────────────────────────────────────────────────────────┤
│ Februari │ Rp 376.359      │ 28°C           │ [Hujan]   │ divide-y divide-gray-100
├─────────────────────────────────────────────────────────┤
│ Maret    │ Rp 376.359      │ 29°C           │ [Cerah]   │ (garis horizontal)
└─────────────────────────────────────────────────────────┘
```

### Class Penjelasan:

**Header:**
```css
bg-gray-50              /* Background abu-abu muda */
border-b border-gray-200 /* Garis bawah */

text-left/center        /* Alignment */
px-6 py-4               /* Padding */
font-semibold           /* Bold */
text-gray-500           /* Warna abu-abu */
text-xs uppercase tracking-wide  /* Semua HURUF BESAR dengan jarak antar huruf */
```

**Body:**
```css
divide-y divide-gray-100  /* Garis horizontal antar row */

row-hover               /* Custom class untuk hover effect */
transition-colors       /* Transisi warna smooth */
duration-200            /* Durasi 200ms */
```

**Data Cell:**
```css
px-6 py-4               /* Padding */
text-center             /* Center alignment */
text-gray-600           /* Warna abu-abu gelap */
```

**Status Badge:**
```css
bg-blue-50              /* Background biru sangat muda */
text-blue-600           /* Warna teks biru */
text-xs                 /* Ukuran sangat kecil */
font-semibold           /* Bold */
px-3 py-1               /* Padding kecil */
rounded-full            /* Border radius 50% (pill shape) */
```

**Hover Effect (CSS Custom):**
```css
.row-hover:hover {
    background-color: #fef9fa;  /* Background pink sangat muda */
}
```

---

## 📌 BAGIAN 8: FOOTER GRID LAYOUT

### Kode:
```html
<div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-10 pb-12 border-b border-gray-200">
    <!-- Brand Section -->
    <div class="sm:col-span-2 lg:col-span-1">
        <!-- Logo dan deskripsi -->
    </div>
    
    <!-- About Links -->
    <div>
        <h4 class="font-bold text-gray-800 mb-5 text-sm uppercase tracking-wide">About</h4>
        <ul class="space-y-3">
            <li><a href="#" class="text-sm text-gray-500 hover:text-rose-500 transition-colors">About Us</a></li>
            <li><a href="#" class="text-sm text-gray-500 hover:text-rose-500 transition-colors">Careers</a></li>
        </ul>
    </div>
    
    <!-- Help Center -->
    <div>
        <h4 class="font-bold text-gray-800 mb-5 text-sm uppercase tracking-wide">Help Center</h4>
        <ul class="space-y-3">
            <li><a href="#" class="text-sm text-gray-500 hover:text-rose-500 transition-colors">How It Works</a></li>
        </ul>
    </div>
    
    <!-- Legal -->
    <div>
        <h4 class="font-bold text-gray-800 mb-5 text-sm uppercase tracking-wide">Legal</h4>
        <ul class="space-y-3">
            <li><a href="#" class="text-sm text-gray-500 hover:text-rose-500 transition-colors">Terms</a></li>
        </ul>
    </div>
</div>
```

### Layout Responsif:

**MOBILE (1 kolom):**
```
┌──────────────────────────┐
│ [BRAND SECTION]          │
├──────────────────────────┤
│ ABOUT                    │
│ • About Us               │
│ • Careers                │
├──────────────────────────┤
│ HELP CENTER              │
│ • How It Works           │
├──────────────────────────┤
│ LEGAL                    │
│ • Terms                  │
└──────────────────────────┘
```

**TABLET (2 kolom, Brand span 2):**
```
┌──────────────────────────┬──────────────────────────┐
│ [BRAND SECTION - SPAN 2]                           │
├──────────────────────────┬──────────────────────────┤
│ ABOUT                    │ HELP CENTER              │
│ • About Us               │ • How It Works           │
│ • Careers                │                          │
└──────────────────────────┴──────────────────────────┘
│ LEGAL (full width bawah)                           │
└──────────────────────────────────────────────────────┘
```

**DESKTOP (4 kolom, Brand span 1):**
```
┌────────────┬────────────┬────────────┬────────────┐
│   BRAND    │   ABOUT    │   HELP     │   LEGAL    │
│ [Logo]     │ • About Us │ • How It   │ • Terms    │
│ [Deskripsi]│ • Careers  │   Works    │ • Privacy  │
│ [Social]   │ • Press    │ • FAQs     │ • Cookies  │
└────────────┴────────────┴────────────┴────────────┘
```

### Class Penjelasan:

```css
grid                    /* CSS Grid */
grid-cols-1             /* 1 kolom mobile */
sm:grid-cols-2          /* 2 kolom tablet */
lg:grid-cols-4          /* 4 kolom desktop */
gap-10                  /* Jarak 2.5rem */
pb-12                   /* Padding bottom 3rem */
border-b border-gray-200 /* Garis bawah */

sm:col-span-2           /* Brand span 2 kolom di tablet */
lg:col-span-1           /* Brand span 1 kolom di desktop */
```

**Section Title:**
```css
font-bold               /* Bold */
text-gray-800           /* Warna hitam */
mb-5                    /* Margin bottom 1.25rem */
text-sm                 /* Ukuran font kecil */
uppercase tracking-wide /* HURUF BESAR dengan jarak antar huruf */
```

**Link List:**
```css
space-y-3               /* Jarak vertikal 0.75rem antar link */

text-sm                 /* Ukuran kecil */
text-gray-500           /* Warna abu-abu */
hover:text-rose-500     /* Berubah merah saat hover */
transition-colors       /* Transisi warna smooth */
```

---

## 🎯 TIPS KOMBINASI CLASS

### 1. Membuat Button Cantik:
```html
<button class="px-6 py-3 bg-rose-500 text-white font-semibold rounded-lg hover:opacity-90 active:scale-95 transition-all shadow-md">
    Click Me
</button>
```

**Breakdown:**
- `px-6 py-3` = Padding nyaman
- `bg-rose-500` = Warna latar
- `text-white` = Teks putih
- `font-semibold` = Bold
- `rounded-lg` = Sudut membulat
- `hover:opacity-90` = Sedikit transparan saat hover
- `active:scale-95` = Kecil saat diklik
- `transition-all` = Smooth semua transisi
- `shadow-md` = Bayangan

### 2. Container Responsive:
```html
<div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
    <!-- Content inside -->
</div>
```

**Penjelasan:**
- `max-w-7xl` = Maksimal lebar 1280px
- `mx-auto` = Center horizontal
- `px-4` = Padding mobile 1rem
- `sm:px-6` = Padding tablet 1.5rem
- `lg:px-8` = Padding desktop 2rem

### 3. Hero Section:
```html
<section class="min-h-screen bg-gradient-to-br from-blue-50 to-white flex items-center">
    <div class="max-w-7xl mx-auto px-4 w-full">
        <!-- Content -->
    </div>
</section>
```

---

## 💡 DEBUGGING TIPS

### Problem: Layout tidak responsive
**Solusi:** Cek apakah sudah ada prefix responsive (sm:, md:, lg:)

### Problem: Text overlapping
**Solusi:** Tambahkan `leading-relaxed` atau `leading-normal`

### Problem: Image pecah/blur
**Solusi:** Gunakan `object-cover` atau `object-contain`

### Problem: Tidak ada efek hover
**Solusi:** Pastikan punya `cursor-pointer` dan `hover:property`

### Problem: Spacing tidak konsisten
**Solusi:** Gunakan scale Tailwind (0, 1, 2, 3, 4, 6, 8, 12, 16, 20, 24, etc)

---

Semoga tutorial ini membantu! 🎉
