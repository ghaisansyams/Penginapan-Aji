# 📚 Penjelasan Lengkap Tailwind CSS untuk Website Penginapan

## 🎯 Panduan Belajar Tailwind CSS Perbaris

---

## 1️⃣ STRUKTUR HTML DASAR

```html
<!DOCTYPE html>
<!-- Deklarasi tipe dokumen HTML5 -->

<html lang="id">
<!-- Tag pembuka HTML dengan bahasa Indonesia (lang="id") -->

<head>
    <meta charset="UTF-8">
    <!-- Encoding karakter UTF-8 untuk mendukung karakter Indonesia -->
    
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- Setting responsive untuk mobile devices -->
    
    <title>Penginapan Aji - Sewa Tempat di Indonesia</title>
    <!-- Judul yang tampil di tab browser -->
    
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Import Tailwind CSS dari CDN (bukan perlu install) -->
    
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
    <!-- Import icon library Font Awesome untuk icon (rumah, hati, dll) -->
    
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <!-- Import font Poppins dari Google Fonts dengan berbagai ketebalan (wght) -->
```

---

## 2️⃣ KONFIGURASI TAILWIND CSS CUSTOM

```javascript
<script>
    tailwind.config = {
        theme: {
            extend: {
                // Extend = memperluas warna dan font default Tailwind
                
                colors: {
                    airbnb: '#FF385C',          // Warna merah custom bernama 'airbnb'
                    'airbnb-dark': '#E31C5F',   // Warna merah gelap custom
                },
                
                fontFamily: {
                    poppins: ['Poppins', 'sans-serif'], // Font custom bernama 'poppins'
                },
            }
        }
    }
</script>
```

---

## 3️⃣ CUSTOM STYLING DENGAN CSS

```css
<style>
    * { font-family: 'Poppins', sans-serif; }
    <!-- Gunakan font Poppins untuk semua elemen (*) -->
    
    html { scroll-behavior: smooth; }
    <!-- Scroll halus saat click anchor link (#) -->
    
    .card-hover { transition: all 300ms ease; }
    <!-- Transisi smooth selama 300ms untuk semua properti -->
    
    .card-hover:hover { 
        transform: scale(1.05);                              <!-- Perbesar 5% saat di-hover -->
        box-shadow: 0 20px 40px rgba(0,0,0,0.15);          <!-- Bayangan halus membesar -->
    }
    
    .nav-link { transition: color 300ms ease; }
    <!-- Transisi warna smooth 300ms -->
    
    .nav-link:hover { color: #FF385C; }
    <!-- Warna berubah jadi merah saat di-hover -->
    
    .facility-card:hover { 
        box-shadow: 0 10px 30px rgba(0,0,0,0.1);           <!-- Bayangan card -->
        border-color: #FFCDD6 !important;                    <!-- Border jadi merah muda -->
        transform: translateY(-2px);                         <!-- Naik 2px saat di-hover -->
    }
    
    #mobile-menu { display: none; }
    <!-- Menu mobile disembunyikan default -->
    
    #mobile-menu.open { display: block; }
    <!-- Menu mobile tampil saat ada class 'open' -->
```

---

## 4️⃣ NAVBAR / MENU ATAS

```html
<nav id="navbar" class="fixed top-0 left-0 right-0 z-50 bg-white shadow-sm border-b border-gray-100 transition-shadow duration-300">
    <!-- 
    fixed              = Fixed di atas saat scroll (tidak bergerak)
    top-0 left-0 right-0 = Mengisi penuh dari atas sampai tepi kanan
    z-50              = Layer paling atas (priority)
    bg-white          = Background putih
    shadow-sm         = Bayangan kecil di bawah
    border-b          = Garis bawah
    border-gray-100   = Garis warna abu-abu sangat muda
    transition-shadow = Transisi smooth shadow saat scroll
    duration-300      = Durasi 300 milidetik
    -->
    
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <!-- 
        max-w-7xl       = Maksimal lebar container (1280px)
        mx-auto         = Margin kiri-kanan auto (center)
        px-4            = Padding horizontal 1rem (16px) di mobile
        sm:px-6         = Padding 1.5rem pada ukuran tablet kecil
        lg:px-8         = Padding 2rem pada ukuran desktop besar
        -->
        
        <div class="flex items-center justify-between h-16">
            <!-- 
            flex                = Flexbox layout (baris)
            items-center        = Vertikal center
            justify-between     = Pisahkan elemen ke kiri dan kanan
            h-16                = Tinggi 4rem (64px)
            -->
            
            <!-- LOGO -->
            <a href="#home" class="flex items-center space-x-2 flex-shrink-0">
                <!-- 
                flex              = Flexbox baris
                items-center      = Vertikal center
                space-x-2         = Jarak horizontal antar child 0.5rem
                flex-shrink-0     = Jangan mengecil saat diperas
                -->
            </a>
            
            <!-- MENU DESKTOP -->
            <div class="hidden md:flex items-center space-x-8">
                <!-- 
                hidden             = Disembunyikan di mobile
                md:flex            = Tampil sebagai flex pada ukuran medium (768px+)
                items-center       = Vertikal center
                space-x-8          = Jarak antar link 2rem
                -->
                
                <a href="#home" class="nav-link text-gray-600 font-medium text-sm">
                    <!-- 
                    nav-link         = Custom class dengan transition
                    text-gray-600    = Warna teks abu-abu medium
                    font-medium      = Font weight 500 (medium)
                    text-sm          = Ukuran teks kecil (14px)
                    -->
                </a>
            </div>
            
            <!-- TOMBOL LOGIN/SIGNUP DESKTOP -->
            <div class="hidden md:flex items-center space-x-2">
                <button class="text-sm font-semibold text-gray-700 px-4 py-2 rounded-xl hover:bg-gray-50 transition-colors">
                    <!-- 
                    text-sm          = Ukuran teks kecil
                    font-semibold    = Font weight 600 (bold)
                    text-gray-700    = Warna teks abu-abu gelap
                    px-4             = Padding horizontal 1rem
                    py-2             = Padding vertikal 0.5rem
                    rounded-xl       = Border radius 0.75rem (bulat)
                    hover:bg-gray-50 = Background abu-abu cerah saat hover
                    transition-colors = Transisi warna smooth
                    -->
                </button>
                
                <button style="background-color:#FF385C">
                    <!-- Menggunakan inline style untuk warna custom -->
                </button>
            </div>
            
            <!-- HAMBURGER MENU (MOBILE) -->
            <button id="hamburger-btn" class="md:hidden p-2 rounded-xl hover:bg-gray-100 transition-colors">
                <!-- 
                md:hidden        = Sembunyikan di desktop medium+
                p-2              = Padding semua sisi 0.5rem
                rounded-xl       = Border radius 0.75rem
                hover:bg-gray-100 = Background abu-abu terang saat hover
                -->
            </button>
        </div>
    </div>
    
    <!-- MOBILE MENU -->
    <div id="mobile-menu" class="md:hidden bg-white border-t border-gray-100 px-4 py-5">
        <!-- 
        md:hidden       = Hanya tampil di mobile (disembunyikan di md+)
        bg-white        = Background putih
        border-t        = Garis atas
        border-gray-100 = Garis warna abu-abu sangat muda
        px-4            = Padding horizontal 1rem
        py-5            = Padding vertikal 1.25rem
        -->
    </div>
</nav>
```

---

## 5️⃣ HERO SECTION (BAGIAN UTAMA)

```html
<section id="home" class="pt-16 min-h-screen bg-gradient-to-br from-white via-rose-50/30 to-white flex items-center">
    <!-- 
    pt-16               = Padding top 4rem (untuk navbar fixed)
    min-h-screen        = Minimal tinggi = tinggi layar
    bg-gradient-to-br   = Background gradient dari kiri atas ke kanan bawah
    from-white          = Mulai dari putih
    via-rose-50/30      = Transisi warna rose sangat muda dengan opacity 30%
    to-white            = Akhir dengan putih
    flex                = Flexbox layout
    items-center        = Vertikal center
    -->
    
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-16 lg:py-20 w-full">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-10 lg:gap-16 items-center">
            <!-- 
            grid                = CSS Grid layout
            grid-cols-1         = 1 kolom di mobile
            lg:grid-cols-2      = 2 kolom di desktop (1024px+)
            gap-10              = Jarak antar kolom 2.5rem
            lg:gap-16           = Jarak antar kolom 4rem di desktop
            items-center        = Vertikal center
            -->
            
            <!-- SEARCH CARD (FORM PENCARIAN) -->
            <div class="order-2 lg:order-1 flex justify-center lg:justify-start">
                <!-- 
                order-2         = Urutan ke-2 (default order-1, jadi ini pindah ke bawah di mobile)
                lg:order-1      = Urutan ke-1 di desktop (kembali ke kiri)
                flex            = Flexbox layout
                justify-center  = Horizontal center
                lg:justify-start = Ke kiri di desktop
                -->
                
                <div class="bg-white rounded-3xl shadow-2xl p-8 w-full max-w-md">
                    <!-- 
                    bg-white        = Background putih
                    rounded-3xl     = Border radius besar 1.5rem
                    shadow-2xl      = Bayangan besar
                    p-8             = Padding semua sisi 2rem
                    w-full          = Lebar penuh parent
                    max-w-md        = Maksimal lebar 28rem (medium)
                    -->
                    
                    <!-- JUDUL PENCARIAN -->
                    <h1 class="text-3xl lg:text-4xl font-bold text-gray-900 leading-tight">
                        <!-- 
                        text-3xl        = Ukuran font 1.875rem (30px)
                        lg:text-4xl     = Ukuran font 2.25rem (36px) di desktop
                        font-bold       = Font weight 700
                        text-gray-900   = Warna teks hitam (abu-abu paling gelap)
                        leading-tight   = Line height rapat (1.25)
                        -->
                        Sewa tempat<br>di <span style="color:#FF385C">Jawa</span>
                    </h1>
                    
                    <!-- INPUT PENCARIAN -->
                    <div class="space-y-3">
                        <!-- 
                        space-y-3 = Jarak vertikal antar child 0.75rem
                        -->
                        
                        <!-- LOKASI INPUT -->
                        <div class="border border-gray-200 rounded-2xl px-4 py-3 hover:border-rose-300 focus-within:border-rose-400 focus-within:ring-2 focus-within:ring-rose-50 transition-all">
                            <!-- 
                            border              = Border 1px
                            border-gray-200     = Border warna abu-abu muda
                            rounded-2xl         = Border radius 1rem
                            px-4                = Padding horizontal 1rem
                            py-3                = Padding vertikal 0.75rem
                            hover:border-rose-300 = Border berubah saat hover
                            focus-within:border-rose-400 = Border berubah saat input fokus
                            focus-within:ring-2 = Ring border ganda saat fokus
                            focus-within:ring-rose-50 = Warna ring sangat muda
                            transition-all      = Transisi smooth semua properti
                            -->
                            
                            <label class="block text-xs font-bold text-gray-500 mb-1 uppercase tracking-wide">
                                <!-- 
                                block           = Display block (full width)
                                text-xs         = Ukuran font sangat kecil (12px)
                                font-bold       = Bold
                                text-gray-500   = Warna abu-abu medium
                                mb-1            = Margin bottom 0.25rem
                                uppercase       = HURUF BESAR
                                tracking-wide   = Letter spacing lebar
                                -->
                                Lokasi
                            </label>
                            
                            <div class="flex items-center space-x-2">
                                <!-- 
                                flex           = Flexbox baris
                                items-center   = Vertikal center
                                space-x-2      = Jarak horizontal 0.5rem
                                -->
                                
                                <i class="fa-solid fa-location-dot text-rose-400 text-sm w-4"></i>
                                <!-- Icon lokasi dari Font Awesome -->
                                
                                <input type="text" class="flex-1 text-sm text-gray-800 font-medium outline-none bg-transparent placeholder-gray-400">
                                <!-- 
                                flex-1              = Ambil space tersisa
                                text-sm             = Ukuran font kecil
                                text-gray-800       = Warna teks hitam
                                font-medium         = Font weight 500
                                outline-none        = Hilangkan outline saat fokus
                                bg-transparent      = Background transparan
                                placeholder-gray-400 = Warna placeholder abu-abu
                                -->
                            </div>
                        </div>
                        
                        <!-- CHECK-IN & CHECK-OUT -->
                        <div class="grid grid-cols-2 gap-3">
                            <!-- 
                            grid         = CSS Grid
                            grid-cols-2  = 2 kolom
                            gap-3        = Jarak 0.75rem
                            -->
                            
                            <div class="border border-gray-200 rounded-2xl px-4 py-3 hover:border-rose-300 focus-within:border-rose-400 transition-all">
                                <label class="block text-xs font-bold text-gray-500 mb-1 uppercase tracking-wide">Check-in</label>
                                <div class="flex items-center space-x-2">
                                    <i class="fa-regular fa-calendar text-rose-400 text-xs w-4"></i>
                                    <input type="date" class="flex-1 text-xs text-gray-700 outline-none bg-transparent w-full">
                                </div>
                            </div>
                        </div>
                        
                        <!-- TOMBOL PENCARIAN -->
                        <button class="w-full text-white font-bold py-4 rounded-2xl text-sm flex items-center justify-center space-x-2 transition-all hover:opacity-90 active:scale-[0.98] shadow-lg" style="background: linear-gradient(135deg, #FF385C, #E31C5F)">
                            <!-- 
                            w-full              = Lebar penuh 100%
                            text-white          = Warna teks putih
                            font-bold           = Bold
                            py-4                = Padding vertikal 1rem
                            rounded-2xl         = Border radius 1rem
                            text-sm             = Ukuran font kecil
                            flex                = Flexbox
                            items-center        = Vertikal center
                            justify-center      = Horizontal center
                            space-x-2           = Jarak horizontal 0.5rem
                            transition-all      = Transisi smooth
                            hover:opacity-90    = Opacity 90% saat hover (transparan sedikit)
                            active:scale-[0.98] = Kecil 98% saat diklik
                            shadow-lg           = Bayangan besar
                            gradient            = Gradient merah custom
                            -->
                            <i class="fa-solid fa-magnifying-glass text-base"></i>
                            <span>Cari Penginapan</span>
                        </button>
                    </div>
                </div>
            </div>
            
            <!-- HERO IMAGE -->
            <div class="order-1 lg:order-2 relative">
                <!-- 
                order-1      = Urutan ke-1 (tampil di atas form di mobile)
                lg:order-2   = Urutan ke-2 di desktop (kanan)
                relative     = Positioning relative (untuk absolute child)
                -->
                
                <div class="relative overflow-hidden" style="border-radius:30px; box-shadow: 0 30px 80px rgba(0,0,0,0.2)">
                    <!-- 
                    relative       = Positioning relative
                    overflow-hidden = Sembunyikan isi yang melampaui border
                    border-radius  = Border radius bulat
                    box-shadow     = Bayangan custom
                    -->
                    
                    <img src="..." class="w-full h-80 lg:h-[520px] object-cover">
                    <!-- 
                    w-full         = Lebar penuh 100%
                    h-80           = Tinggi 20rem (320px) di mobile
                    lg:h-[520px]   = Tinggi 520px di desktop (arbitrary value)
                    object-cover   = Gambar cover seluruh area tanpa distorsi
                    -->
                    
                    <!-- GRADIENT OVERLAY -->
                    <div class="absolute inset-0 bg-gradient-to-t from-black/40 via-transparent to-transparent"></div>
                    <!-- 
                    absolute   = Positioning absolute
                    inset-0    = Isi semua sisi (top/right/bottom/left = 0)
                    bg-gradient-to-t = Gradient dari bawah ke atas
                    from-black/40 = Mulai dari hitam dengan opacity 40%
                    -->
                </div>
                
                <!-- RATING BADGE (FLOATING) -->
                <div class="absolute bottom-6 left-6 bg-white rounded-2xl shadow-xl px-4 py-3 flex items-center space-x-3">
                    <!-- 
                    absolute   = Floating / absolute position
                    bottom-6   = Posisi bawah 1.5rem
                    left-6     = Posisi kiri 1.5rem
                    bg-white   = Background putih
                    rounded-2xl = Border radius 1rem
                    shadow-xl  = Bayangan besar
                    px-4       = Padding horizontal 1rem
                    py-3       = Padding vertikal 0.75rem
                    flex       = Flexbox
                    items-center = Vertikal center
                    space-x-3  = Jarak horizontal 0.75rem
                    -->
                    
                    <div class="w-10 h-10 rounded-xl flex items-center justify-center" style="background-color:#FFF0F3">
                        <!-- Icon container -->
                    </div>
                </div>
            </div>
        </div>
    </div>
</section>
```

---

## 6️⃣ FEATURED DESTINATIONS (DESTINASI UNGGULAN)

```html
<section id="destinations" class="py-20 bg-white">
    <!-- 
    py-20    = Padding vertikal top & bottom 5rem
    bg-white = Background putih
    -->
    
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <!-- Container max width dengan padding responsive -->
        
        <!-- HEADER SECTION -->
        <div class="text-center mb-12">
            <!-- 
            text-center = Text align center
            mb-12       = Margin bottom 3rem
            -->
            
            <h2 class="text-3xl lg:text-4xl font-bold text-gray-900 mb-3">
                Tempat berlibur bernilai tinggi di Depok
            </h2>
            <p class="text-gray-500 text-base">
                Tamu setuju: penginapan ini dinilai tinggi...
            </p>
        </div>
        
        <!-- GRID CARD DESTINASI -->
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
            <!-- 
            grid          = CSS Grid
            grid-cols-1   = 1 kolom di mobile
            sm:grid-cols-2 = 2 kolom di tablet
            lg:grid-cols-4 = 4 kolom di desktop
            gap-6         = Jarak 1.5rem antar card
            -->
            
            <!-- PROPERTY CARD -->
            <div class="card-hover bg-white rounded-2xl overflow-hidden shadow-md cursor-pointer group">
                <!-- 
                card-hover   = Custom class dengan animation hover (scale)
                bg-white     = Background putih
                rounded-2xl  = Border radius 1rem
                overflow-hidden = Sembunyikan isi yang melampaui
                shadow-md    = Bayangan medium
                cursor-pointer = Cursor berubah jadi pointer (clickable)
                group        = Grouping untuk group-hover effect pada child
                -->
                
                <div class="relative overflow-hidden">
                    <img src="..." class="w-full h-52 object-cover group-hover:scale-105 transition-transform duration-500">
                    <!-- 
                    group-hover:scale-105 = Zoom gambar 5% saat parent di-hover
                    transition-transform  = Transisi smooth transform
                    duration-500          = Durasi 500ms
                    -->
                    
                    <!-- BADGE -->
                    <span class="absolute top-3 left-3 bg-white text-xs font-bold text-gray-700 px-3 py-1 rounded-full shadow-sm">
                        Pilihan Tamu
                    </span>
                    
                    <!-- HEART BUTTON -->
                    <button class="absolute top-3 right-3 w-8 h-8 bg-white rounded-full flex items-center justify-center shadow hover:scale-110 transition-transform">
                        <!-- 
                        absolute       = Absolute position
                        top-3          = Posisi atas 0.75rem
                        right-3        = Posisi kanan 0.75rem
                        w-8            = Lebar 2rem
                        h-8            = Tinggi 2rem
                        bg-white       = Background putih
                        rounded-full   = Border radius 50% (lingkaran)
                        flex           = Flexbox
                        items-center   = Vertikal center
                        justify-center = Horizontal center
                        shadow         = Bayangan
                        hover:scale-110 = Membesar 10% saat hover
                        -->
                        <i class="fa-regular fa-heart text-gray-400 text-sm"></i>
                    </button>
                </div>
                
                <!-- CARD INFO -->
                <div class="p-4">
                    <!-- 
                    p-4 = Padding semua sisi 1rem
                    -->
                    
                    <div class="flex items-start justify-between gap-2 mb-1">
                        <!-- 
                        flex            = Flexbox
                        items-start     = Vertikal ke atas (align-items: flex-start)
                        justify-between = Pisahkan ke kiri dan kanan
                        gap-2           = Jarak 0.5rem
                        mb-1            = Margin bottom 0.25rem
                        -->
                        
                        <h3 class="font-semibold text-gray-800 text-sm leading-snug">
                            Rumah di Jakarta Selatan
                        </h3>
                        
                        <div class="flex items-center space-x-1 flex-shrink-0">
                            <!-- 
                            flex-shrink-0 = Jangan mengecil
                            -->
                            <i class="fa-solid fa-star text-xs" style="color:#FF385C"></i>
                            <span class="text-xs font-bold text-gray-700">4.98</span>
                        </div>
                    </div>
                    
                    <p class="text-xs text-gray-400 mb-3">Jakarta Selatan, Indonesia</p>
                    <p class="text-sm">
                        <span class="font-bold text-gray-900">Rp 450.000</span>
                        <span class="text-gray-400 text-xs"> / malam</span>
                    </p>
                </div>
            </div>
        </div>
    </div>
</section>
```

---

## 7️⃣ FACILITIES (FASILITAS POPULER)

```html
<section class="py-20 bg-gray-50">
    <!-- 
    py-20     = Padding vertikal 5rem
    bg-gray-50 = Background abu-abu sangat muda
    -->
    
    <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-5 gap-4">
        <!-- 
        grid-cols-2     = 2 kolom di mobile
        sm:grid-cols-3  = 3 kolom di tablet
        lg:grid-cols-5  = 5 kolom di desktop
        gap-4           = Jarak 1rem antar item
        -->
        
        <!-- FACILITY CARD -->
        <div class="facility-card bg-white border border-gray-200 rounded-2xl p-6 flex flex-col items-center cursor-pointer">
            <!-- 
            facility-card  = Custom class dengan hover effect (shadow & border)
            bg-white       = Background putih
            border         = Border 1px
            border-gray-200 = Border abu-abu muda
            rounded-2xl    = Border radius 1rem
            p-6            = Padding semua sisi 1.5rem
            flex           = Flexbox
            flex-col       = Arah kolom (vertikal)
            items-center   = Horizontal center
            cursor-pointer = Cursor pointer
            -->
            
            <div class="w-16 h-16 rounded-2xl flex items-center justify-center mb-4" style="background-color:#FFF0F3">
                <!-- 
                w-16       = Lebar 4rem
                h-16       = Tinggi 4rem
                rounded-2xl = Border radius 1rem
                flex       = Flexbox
                items-center = Vertikal center
                justify-center = Horizontal center
                mb-4       = Margin bottom 1rem
                -->
                
                <i class="fa-solid fa-utensils text-2xl" style="color:#FF385C"></i>
                <!-- Icon besar dari Font Awesome -->
            </div>
            
            <span class="text-sm font-semibold text-gray-700">Dapur</span>
        </div>
    </div>
</section>
```

---

## 8️⃣ TABLE (JADWAL BERKUNJUNG)

```html
<div class="overflow-x-auto rounded-2xl shadow-sm border border-gray-200">
    <!-- 
    overflow-x-auto  = Bisa scroll horizontal di mobile
    rounded-2xl      = Border radius 1rem
    shadow-sm        = Bayangan kecil
    border           = Border 1px
    border-gray-200  = Border abu-abu muda
    -->
    
    <table class="w-full text-sm min-w-[600px]">
        <!-- 
        w-full       = Lebar penuh 100%
        text-sm      = Ukuran font kecil
        min-w-[600px] = Minimal lebar 600px (arbitrary)
        -->
        
        <thead>
            <tr class="bg-gray-50 border-b border-gray-200">
                <!-- 
                bg-gray-50     = Background abu-abu sangat muda
                border-b       = Border bawah
                border-gray-200 = Border abu-abu muda
                -->
                
                <th class="text-left px-6 py-4 font-semibold text-gray-500 text-xs uppercase tracking-wide">
                    <!-- 
                    text-left      = Align left
                    px-6           = Padding horizontal 1.5rem
                    py-4           = Padding vertikal 1rem
                    font-semibold  = Font weight 600
                    text-gray-500  = Warna abu-abu medium
                    text-xs        = Ukuran font sangat kecil
                    uppercase      = HURUF BESAR
                    tracking-wide  = Letter spacing lebar
                    -->
                    Bulan
                </th>
            </tr>
        </thead>
        
        <tbody class="divide-y divide-gray-100">
            <!-- 
            divide-y        = Garis pemisah vertikal antar child
            divide-gray-100 = Garis warna abu-abu sangat cerah
            -->
            
            <tr class="row-hover transition-colors duration-200">
                <!-- 
                row-hover           = Custom class hover background
                transition-colors   = Transisi smooth warna
                duration-200        = Durasi 200ms
                -->
                
                <td class="px-6 py-4 font-semibold text-gray-800">Januari</td>
                <td class="px-6 py-4 text-center text-gray-600">Rp 376.359</td>
                <td class="px-6 py-4 text-center text-gray-600">28°C</td>
                
                <td class="px-6 py-4 text-center">
                    <span class="bg-blue-50 text-blue-600 text-xs font-semibold px-3 py-1 rounded-full">
                        <!-- 
                        bg-blue-50       = Background biru sangat muda
                        text-blue-600    = Warna teks biru
                        text-xs          = Ukuran font sangat kecil
                        font-semibold    = Bold
                        px-3             = Padding horizontal 0.75rem
                        py-1             = Padding vertikal 0.25rem
                        rounded-full     = Border radius 50% (pill shape)
                        -->
                        Hujan
                    </span>
                </td>
            </tr>
        </tbody>
    </table>
</div>
```

---

## 9️⃣ STATISTICS CARDS (KARTU STATISTIK)

```html
<div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
    <!-- 
    grid-cols-1     = 1 kolom di mobile
    sm:grid-cols-2  = 2 kolom di tablet
    lg:grid-cols-3  = 3 kolom di desktop
    gap-6           = Jarak 1.5rem
    -->
    
    <!-- STAT CARD -->
    <div class="stat-card bg-white rounded-2xl p-6 shadow-sm">
        <!-- 
        stat-card    = Custom class dengan hover effect (translateY)
        bg-white     = Background putih
        rounded-2xl  = Border radius 1rem
        p-6          = Padding semua sisi 1.5rem
        shadow-sm    = Bayangan kecil
        -->
        
        <div class="flex items-start space-x-4">
            <!-- 
            flex        = Flexbox baris
            items-start = Vertikal ke atas
            space-x-4   = Jarak horizontal 1rem
            -->
            
            <div class="w-14 h-14 rounded-2xl flex items-center justify-center flex-shrink-0" style="background-color:#FFF0F3">
                <!-- 
                w-14        = Lebar 3.5rem
                h-14        = Tinggi 3.5rem
                rounded-2xl = Border radius 1rem
                flex        = Flexbox
                items-center = Vertikal center
                justify-center = Horizontal center
                flex-shrink-0 = Jangan mengecil
                -->
                
                <i class="fa-solid fa-house-chimney text-xl" style="color:#FF385C"></i>
            </div>
            
            <div>
                <p class="text-4xl font-extrabold text-gray-900 mb-1">
                    <!-- 
                    text-4xl       = Ukuran font 2.25rem (36px)
                    font-extrabold = Font weight 800
                    text-gray-900  = Warna teks hitam
                    mb-1           = Margin bottom 0.25rem
                    -->
                    1,060
                </p>
                
                <p class="text-sm font-bold text-gray-700 mb-1">Total sewa tempat liburan</p>
                <p class="text-xs text-gray-400 leading-relaxed">
                    <!-- 
                    text-xs         = Ukuran font sangat kecil (12px)
                    text-gray-400   = Warna abu-abu medium
                    leading-relaxed = Line height 1.625
                    -->
                    Temukan 1,060 sewa tempat liburan di Depok
                </p>
            </div>
        </div>
    </div>
</div>
```

---

## 🔟 DESTINATIONS TABS (DESTINASI DENGAN TABS)

```html
<div class="flex flex-wrap justify-center gap-2">
    <!-- 
    flex        = Flexbox baris
    flex-wrap   = Wrap ke baris baru jika overflow
    justify-center = Horizontal center
    gap-2       = Jarak 0.5rem antar item
    -->
    
    <!-- TAB BUTTON -->
    <button onclick="setTab(this)" class="tab-btn active text-xs font-semibold px-4 py-2 rounded-full transition-all border border-transparent">
        <!-- 
        tab-btn               = Custom class untuk tab styling
        active                = Class aktif default
        text-xs               = Ukuran font sangat kecil
        font-semibold         = Bold
        px-4                  = Padding horizontal 1rem
        py-2                  = Padding vertikal 0.5rem
        rounded-full          = Border radius 50% (pill button)
        transition-all        = Transisi smooth semua properti
        border                = Border 1px
        border-transparent    = Border transparan (tidak terlihat)
        -->
        Destinasi di sekitar
    </button>
</div>

<div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-5 gap-3">
    <!-- DESTINATION CARD -->
    <a href="#" class="dest-card group text-center p-4 rounded-2xl hover:bg-rose-50 transition-all duration-300 cursor-pointer">
        <!-- 
        dest-card           = Custom class untuk destination card
        group               = Grouping untuk group-hover effect
        text-center         = Text align center
        p-4                 = Padding semua sisi 1rem
        rounded-2xl         = Border radius 1rem
        hover:bg-rose-50    = Background rose sangat muda saat hover
        transition-all      = Transisi smooth semua properti
        duration-300        = Durasi 300ms
        cursor-pointer      = Cursor pointer
        -->
        
        <div class="w-16 h-16 mx-auto mb-3 rounded-2xl overflow-hidden shadow-sm ring-2 ring-transparent group-hover:ring-rose-200 transition-all">
            <!-- 
            mx-auto              = Margin horizontal auto (center)
            mb-3                 = Margin bottom 0.75rem
            overflow-hidden      = Sembunyikan isi yang melampaui
            shadow-sm            = Bayangan kecil
            ring-2               = Ring border ganda
            ring-transparent     = Ring transparan default
            group-hover:ring-rose-200 = Ring berubah saat parent hover
            transition-all       = Transisi smooth
            -->
            
            <img src="..." class="w-full h-full object-cover">
        </div>
        
        <h3 class="font-bold text-gray-800 group-hover:text-rose-500 transition-colors text-sm">
            Jakarta
        </h3>
        <p class="text-xs text-gray-400 mt-0.5">Sewa tempat liburan</p>
    </a>
</div>
```

---

## 1️⃣1️⃣ FOOTER

```html
<footer id="contact" class="bg-gray-50 border-t border-gray-200 pt-16 pb-8">
    <!-- 
    bg-gray-50     = Background abu-abu sangat muda
    border-t       = Border atas
    border-gray-200 = Border abu-abu muda
    pt-16          = Padding top 4rem
    pb-8           = Padding bottom 2rem
    -->
    
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <!-- Container max width dengan padding responsive -->
        
        <!-- FOOTER GRID -->
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-10 pb-12 border-b border-gray-200">
            <!-- 
            grid-cols-1      = 1 kolom di mobile
            sm:grid-cols-2   = 2 kolom di tablet
            lg:grid-cols-4   = 4 kolom di desktop
            gap-10           = Jarak 2.5rem
            pb-12            = Padding bottom 3rem
            border-b         = Border bawah
            border-gray-200  = Border abu-abu muda
            -->
            
            <!-- BRAND SECTION -->
            <div class="sm:col-span-2 lg:col-span-1">
                <!-- 
                sm:col-span-2  = Span 2 kolom di tablet
                lg:col-span-1  = Span 1 kolom di desktop
                -->
                
                <div class="flex items-center space-x-2 mb-4">
                    <!-- Logo dan nama brand -->
                </div>
                
                <p class="text-sm text-gray-500 leading-relaxed mb-5">
                    <!-- 
                    text-sm          = Ukuran font kecil
                    text-gray-500    = Warna abu-abu medium
                    leading-relaxed  = Line height 1.625
                    mb-5             = Margin bottom 1.25rem
                    -->
                    Platform terpercaya untuk menemukan penginapan unik...
                </p>
                
                <!-- SOCIAL MEDIA -->
                <div class="flex space-x-3">
                    <!-- 
                    flex    = Flexbox baris
                    space-x-3 = Jarak horizontal 0.75rem
                    -->
                    
                    <a href="#" class="w-9 h-9 rounded-xl flex items-center justify-center bg-gray-200 hover:bg-rose-500 transition-colors group">
                        <!-- 
                        w-9              = Lebar 2.25rem
                        h-9              = Tinggi 2.25rem
                        rounded-xl       = Border radius 0.75rem
                        flex             = Flexbox
                        items-center     = Vertikal center
                        justify-center   = Horizontal center
                        bg-gray-200      = Background abu-abu terang
                        hover:bg-rose-500 = Background rose saat hover
                        transition-colors = Transisi warna smooth
                        group            = Grouping untuk group effect
                        -->
                        
                        <i class="fa-brands fa-facebook-f text-sm text-gray-600 group-hover:text-white transition-colors"></i>
                        <!-- 
                        text-gray-600         = Warna abu-abu medium
                        group-hover:text-white = Warna putih saat parent hover
                        -->
                    </a>
                </div>
            </div>
            
            <!-- FOOTER LINKS SECTIONS -->
            <div>
                <h4 class="font-bold text-gray-800 mb-5 text-sm uppercase tracking-wide">
                    About
                </h4>
                
                <ul class="space-y-3">
                    <!-- 
                    space-y-3 = Jarak vertikal 0.75rem antar list item
                    -->
                    
                    <li>
                        <a href="#" class="text-sm text-gray-500 hover:text-rose-500 transition-colors">
                            About Us
                        </a>
                    </li>
                </ul>
            </div>
        </div>
        
        <!-- FOOTER BOTTOM -->
        <div class="pt-8 flex flex-col sm:flex-row items-center justify-between gap-4">
            <!-- 
            pt-8          = Padding top 2rem
            flex          = Flexbox
            flex-col      = Arah kolom di mobile
            sm:flex-row   = Arah baris di tablet
            items-center  = Vertikal center
            justify-between = Pisahkan ke kiri dan kanan
            gap-4         = Jarak 1rem
            -->
            
            <p class="text-sm text-gray-400">© 2026 StayFinder. All rights reserved.</p>
            
            <div class="flex items-center space-x-1.5 text-sm text-gray-400 cursor-pointer hover:text-gray-600 transition-colors">
                <!-- 
                space-x-1.5  = Jarak horizontal 0.375rem
                cursor-pointer = Cursor pointer
                hover:text-gray-600 = Warna berubah saat hover
                transition-colors = Transisi warna smooth
                -->
                <i class="fa-solid fa-globe text-xs"></i>
                <span>Indonesia (IDR)</span>
            </div>
        </div>
    </div>
</footer>
```

---

## 1️⃣2️⃣ RESPONSIVE BREAKPOINTS (UKURAN LAYAR)

Tailwind CSS menggunakan mobile-first approach:

```
- Mobile (default)   : 0px - 639px
- sm (small)         : 640px - 767px   |  sm:
- md (medium)        : 768px - 1023px  |  md:
- lg (large)         : 1024px - 1279px |  lg:
- xl (extra large)   : 1280px - 1535px |  xl:
- 2xl (2x large)     : 1536px+         |  2xl:
```

**Contoh:**
```html
<div class="w-full md:w-1/2 lg:w-1/4">
    <!-- 
    w-full   = Lebar penuh 100% di mobile
    md:w-1/2 = Lebar 50% di tablet (768px+)
    lg:w-1/4 = Lebar 25% di desktop (1024px+)
    -->
</div>
```

---

## 1️⃣3️⃣ SPACING SCALE (UKURAN JARAK)

```
0    = 0
0.5  = 0.125rem = 2px
1    = 0.25rem = 4px
1.5  = 0.375rem = 6px
2    = 0.5rem = 8px
2.5  = 0.625rem = 10px
3    = 0.75rem = 12px
4    = 1rem = 16px
5    = 1.25rem = 20px
6    = 1.5rem = 24px
8    = 2rem = 32px
10   = 2.5rem = 40px
12   = 3rem = 48px
16   = 4rem = 64px
20   = 5rem = 80px
```

---

## 1️⃣4️⃣ COLOR PALETTE (PALET WARNA)

**Skala Abu-abu:**
- gray-50 (paling cerah)
- gray-100
- gray-200
- ...
- gray-900 (paling gelap)

**Warna Lainnya:**
- rose-50 (pink sangat muda)
- rose-400 (pink medium)
- rose-500 (pink)
- blue-50, blue-600
- emerald-50, emerald-600
- amber-50, amber-600

---

## 1️⃣5️⃣ COMMON TAILWIND CLASSES (CLASS YANG SERING DIGUNAKAN)

### Display & Layout
```
block, inline-block, inline, flex, grid, hidden
```

### Spacing
```
p-4    = padding all
px-4   = padding horizontal
py-4   = padding vertical
m-4    = margin all
mx-auto = margin horizontal auto (center)
```

### Sizing
```
w-full, h-full   = lebar/tinggi 100%
w-1/2, h-1/2     = lebar/tinggi 50%
w-1/3, h-1/3     = lebar/tinggi 33.33%
min-w-max, max-w-md
```

### Typography
```
text-xs, text-sm, text-base, text-lg, text-xl, text-2xl, text-3xl, text-4xl
font-light, font-normal, font-medium, font-semibold, font-bold, font-extrabold
text-gray-700, text-white, text-rose-500
uppercase, lowercase, capitalize
```

### Borders & Shadows
```
border, border-gray-200
rounded, rounded-lg, rounded-2xl, rounded-full
shadow-sm, shadow-md, shadow-lg, shadow-xl, shadow-2xl
```

### Effects & Transforms
```
opacity-50, opacity-75, opacity-90
scale-95, scale-100, scale-105, scale-110
translate-x-2, translateY(-2px), translateY(-4px)
rotate-45, skew-x-3
```

### Transitions & Animations
```
transition, transition-all
transition-colors, transition-transform
duration-200, duration-300, duration-500
ease, ease-in, ease-out
```

### Interactive States
```
hover:bg-gray-100
focus:outline-none, focus:ring-2
active:scale-95
group-hover:scale-110
disabled:opacity-50
```

---

## 📝 TIPS BELAJAR TAILWIND

1. **Mobile First**: Selalu mulai dari class tanpa prefix (mobile)
2. **Responsive**: Gunakan breakpoints (sm:, md:, lg:) untuk resize
3. **Utility First**: Kombinasikan class kecil daripada buat custom CSS
4. **Color Scale**: Abu-abu 50-900, warna lain punya skala serupa
5. **Spacing**: Gunakan scale konsisten (4px base = 0.25rem per unit)
6. **Hover/Focus**: Selalu tambahkan interactive states
7. **Dark Mode**: Gunakan `dark:` prefix untuk dark theme

---

## 🎨 CHEAT SHEET QUICK REFERENCE

| Purpose | Example |
|---------|---------|
| Container | `max-w-7xl mx-auto px-4` |
| Flexbox | `flex items-center justify-between` |
| Grid 2 Kolom | `grid grid-cols-2 gap-4` |
| Card Dasar | `bg-white rounded-2xl p-6 shadow-md` |
| Tombol | `px-4 py-2 rounded-lg bg-blue-500 text-white hover:opacity-90` |
| Input | `border border-gray-200 rounded-lg px-4 py-2 focus:outline-none focus:ring-2` |
| Text | `text-sm text-gray-600 font-medium` |
| Responsive Text | `text-3xl md:text-4xl lg:text-5xl` |
| Badge | `bg-rose-50 text-rose-600 text-xs font-semibold px-3 py-1 rounded-full` |
| Overlay | `absolute inset-0 bg-black/50` |

---

**Semoga penjelasan ini membantu Anda memahami Tailwind CSS! 🚀**
