<div align="center">

<img src="https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white" alt="Tailwind CSS">
<img src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white" alt="HTML5">
<img src="https://img.shields.io/badge/Font_Awesome-528DD7?style=for-the-badge&logo=font-awesome&logoColor=white" alt="Font Awesome">
<img src="https://img.shields.io/badge/Google_Fonts-4285F4?style=for-the-badge&logo=google&logoColor=white" alt="Google Fonts">

# 🏡 Penginapan Aji

**Landing page platform sewa penginapan berbasis Tailwind CSS**
*Terinspirasi dari Airbnb — dibuat sebagai proyek belajar Tailwind CSS*

</div>

---

## 📋 Tentang Proyek

**Penginapan Aji** adalah landing page modern untuk platform sewa penginapan di wilayah Depok, Jawa Barat. Proyek ini dibuat untuk mempelajari dan mempraktikkan **Tailwind CSS** secara mendalam mulai dari layout responsif, komponen interaktif, hingga animasi halus.

Tampilan dan konsep terinspirasi dari platform populer **Airbnb**, dengan warna tema merah khas (`#FF385C`).

---

## ✨ Fitur Halaman

| Bagian | Deskripsi |
|---|---|
| **Navbar Fixed** | Navigasi sticky dengan mobile hamburger menu |
| **Hero Section** | Form pencarian (lokasi, check-in, check-out, tamu) dengan gambar hero |
| **Destinasi Unggulan** | Grid 4 kolom property card dengan hover animation |
| **Fasilitas Populer** | Icon card: Dapur, WiFi, Kolam renang, Parkir, AC |
| **Atraksi Terdekat** | List tempat wisata populer di sekitar Depok |
| **Lebih Banyak Penginapan** | Grid 8 properti dengan rating dan harga |
| **Waktu Terbaik Berkunjung** | Tabel 12 bulan dengan info harga, suhu, dan cuaca |
| **Statistik Cepat** | 6 kartu statistik (1.060+ properti, 3.890+ ulasan, dll.) |
| **Jelajahi Destinasi** | Tab interaktif + grid 10 kota di Indonesia |
| **Footer** | 4 kolom link + social media + copyright |

---

## 🛠️ Teknologi yang Digunakan

- **[Tailwind CSS](https://tailwindcss.com/)** — via CDN, utility-first CSS framework
- **HTML5** — struktur halaman semantik
- **[Font Awesome 6.5](https://fontawesome.com/)** — library icon (rumah, bintang, wifi, dll.)
- **[Google Fonts - Poppins](https://fonts.google.com/specimen/Poppins)** — tipografi utama
- **Vanilla JavaScript** — mobile menu toggle, tab aktif, navbar shadow on scroll

---

## 📁 Struktur Proyek

```
Penginapan-Aji/
├── index.html                  # Landing page utama
├── PENJELASAN_TAILWIND.md      # Penjelasan kelas Tailwind perbaris
├── PENJELASAN_CSS_CUSTOM.md    # Penjelasan CSS custom yang digunakan
├── TUTORIAL_PRAKTIS.md         # Tutorial praktis step-by-step
└── README.md                   # Dokumentasi proyek ini
```

---

## 🚀 Cara Menjalankan

Proyek ini tidak memerlukan instalasi apapun karena menggunakan CDN.

**Langkah 1 — Clone repository:**
```bash
git clone https://github.com/ghaisansyams/Penginapan-Aji.git
cd Penginapan-Aji
```

**Langkah 2 — Buka di browser:**
```bash
# Cukup buka file langsung di browser
open index.html

# Atau gunakan Live Server di VS Code
# Klik kanan index.html → Open with Live Server
```

> Tidak perlu `npm install`, tidak perlu build step — langsung buka dan jalan!

---

## 🧠 Yang Dipelajari

### Tailwind CSS Core Concepts
- **Utility-first** — membangun UI dengan class kecil tanpa custom CSS berlebihan
- **Responsive design** dengan breakpoints: `sm:`, `md:`, `lg:`, `xl:`
- **Flexbox** (`flex`, `items-center`, `justify-between`) dan **CSS Grid** (`grid-cols-4`, `gap-6`)
- **Custom config** — menambah warna dan font ke `tailwind.config`
- **Hover & group-hover** — efek interaktif pada card dan tombol
- **Arbitrary values** — `h-[520px]`, `min-w-[600px]`

### Komponen yang Dibangun
- Navbar fixed dengan mobile menu responsif
- Search form card dengan focus states
- Property card dengan image zoom on hover
- Floating badge (absolute positioning)
- Data table dengan hover row
- Pill badge (status cuaca)
- Social media icon button dengan hover color change
- Tab navigation dengan JavaScript

### CSS Custom yang Digunakan
```css
.card-hover:hover    → scale(1.05) + box-shadow
.facility-card:hover → translateY(-2px) + border color change
.stat-card:hover     → translateY(-4px) + rose shadow
.dest-card:hover img → scale(1.1) image zoom
```

---

## 🎨 Palet Warna

| Nama | Hex | Penggunaan |
|---|---|---|
| **Airbnb Red** | `#FF385C` | Tombol utama, icon aktif, aksen |
| **Airbnb Dark** | `#E31C5F` | Hover tombol, gradient akhir |
| **Rose Light** | `#FFF0F3` | Background icon container |
| **Gray 900** | `#111827` | Judul utama |
| **Gray 500** | `#6B7280` | Teks deskripsi |
| **White** | `#FFFFFF` | Background card, navbar |

---

## 📐 Responsive Breakpoints

```
Mobile   (default)  : < 640px    → 1 kolom
Tablet   (sm:)      : ≥ 640px    → 2 kolom
Desktop  (md:)      : ≥ 768px    → tampilkan navbar full
Desktop  (lg:)      : ≥ 1024px   → 4–5 kolom
```

---

## 📸 Layout Preview

```
┌─────────────────────────────────────────┐
│  🏠 NAVBAR  (Logo | Links | Login/Signup) │
├─────────────────────────────────────────┤
│  HERO   [Search Form]  |  [Hero Image]  │
│         (Lokasi, Tanggal, Tamu, CTA)    │
├─────────────────────────────────────────┤
│  ⭐ DESTINASI UNGGULAN (4 Property Cards) │
├─────────────────────────────────────────┤
│  🏊 FASILITAS POPULER (5 Icon Cards)    │
├─────────────────────────────────────────┤
│  📍 ATRAKSI TERDEKAT (6 Lokasi)         │
├─────────────────────────────────────────┤
│  🏘️ LEBIH BANYAK PENGINAPAN (8 Cards)   │
├─────────────────────────────────────────┤
│  📅 WAKTU TERBAIK BERKUNJUNG (Tabel)    │
├─────────────────────────────────────────┤
│  📊 STATISTIK (6 Stat Cards)            │
├─────────────────────────────────────────┤
│  🗺️ JELAJAHI DESTINASI (Tabs + 10 Kota) │
├─────────────────────────────────────────┤
│  📬 FOOTER (Brand | Links | Socials)    │
└─────────────────────────────────────────┘
```

---

## 👤 Author

**Ghaisan Syams**
- GitHub: [@ghaisansyams](https://github.com/ghaisansyams)
- Email: ghaisansyams@gmail.com

---

<div align="center">

</div>
