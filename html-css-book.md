# 🎨 Belajar HTML & CSS — Dari 0 Sampai Professional Designer & Developer

> **by Riz-dev × Claude Sonnet 4.6**  
> *Diajarin dari fondasi beneran, dipraktekin di Acode & Termux, dijelasin kenapa — bukan cuma gimana.*

---

## 📋 Daftar Isi

### 🟧 BAGIAN 1 — HTML: Struktur Halaman Web
1. [Apa itu HTML?](#1-apa-itu-html)
2. [Setup — Acode & Termux](#2-setup--acode--termux)
3. [Struktur Dasar HTML](#3-struktur-dasar-html)
4. [Tag & Elemen — Bata-bata Halaman](#4-tag--elemen--bata-bata-halaman)
5. [Atribut — Pengaturan Tag](#5-atribut--pengaturan-tag)
6. [Teks & Tipografi](#6-teks--tipografi)
7. [Link & Navigasi](#7-link--navigasi)
8. [Gambar & Media](#8-gambar--media)
9. [List — Daftar-daftaran](#9-list--daftar-daftaran)
10. [Tabel — Data Terstruktur](#10-tabel--data-terstruktur)
11. [Form & Input — Ambil Data dari User](#11-form--input--ambil-data-dari-user)
12. [Semantic HTML — Kode yang Bermakna](#12-semantic-html--kode-yang-bermakna)
13. [HTML5 — Fitur Modern](#13-html5--fitur-modern)

### 🟦 BAGIAN 2 — CSS: Tampilan & Gaya
14. [Apa itu CSS?](#14-apa-itu-css)
15. [3 Cara Pakai CSS](#15-3-cara-pakai-css)
16. [Selektor — Incaran yang Tepat](#16-selektor--incaran-yang-tepat)
17. [Box Model — Inti dari Segalanya](#17-box-model--inti-dari-segalanya)
18. [Teks & Font — Tipografi Web](#18-teks--font--tipografi-web)
19. [Warna & Background](#19-warna--background)
20. [Display & Positioning — Posisi Elemen](#20-display--positioning--posisi-elemen)
21. [Flexbox — Tata Letak 1 Dimensi](#21-flexbox--tata-letak-1-dimensi)
22. [CSS Grid — Tata Letak 2 Dimensi](#22-css-grid--tata-letak-2-dimensi)
23. [Responsive Design & Media Query](#23-responsive-design--media-query)
24. [Transisi & Animasi](#24-transisi--animasi)
25. [CSS Variables — Custom Properties](#25-css-variables--custom-properties)
26. [Pseudo-class & Pseudo-element](#26-pseudo-class--pseudo-element)
27. [CSS Architecture & BEM](#27-css-architecture--bem)
28. [Tips Pro & Best Practice](#28-tips-pro--best-practice)
29. [Mini Projects — Latihan Nyata](#29-mini-projects--latihan-nyata)

---

# 🟧 BAGIAN 1 — HTML

## 1. Apa itu HTML?

Bayangin lo lagi bikin rumah.

- **HTML** itu **kerangka dan dindingnya** — yang menentukan ada berapa kamar, di mana pintunya, di mana jendelanya.
- **CSS** itu **cat, furnitur, dan dekorasinya** — yang bikin rumah itu keliatan bagus.
- **JavaScript** itu **listrik dan sistemnya** — yang bikin rumah bisa nyalain lampu, buka kunci otomatis, dll.

**HTML** singkatan dari **HyperText Markup Language**. Ini bukan bahasa pemrograman (nggak ada logika, nggak ada kalkulasi), tapi **bahasa markup** — artinya lo "menandai" konten supaya browser tau ini judulnya, ini paragrafnya, ini gambarnya, ini tombolnya.

### Kenapa harus belajar HTML dulu?

Karena semua yang ada di internet — Google, Instagram, YouTube, Twitter — semuanya dibangun di atas HTML. Mau jadi web developer? Frontend engineer? UI designer? Semuanya mulai dari sini.

### HTML bekerja gimana?

```
Lo nulis file .html
        ↓
Browser baca file itu
        ↓
Browser tampilkan hasilnya di layar
```

Sesimple itu. Nggak perlu server, nggak perlu install apa-apa. Bikin file, buka di browser — selesai.

### HTML versi berapa yang dipelajari?

**HTML5** — versi paling modern, yang jalan di semua browser modern sekarang. Kita nggak akan bahas HTML 4 atau XHTML karena itu udah kuno.

---

## 2. Setup — Acode & Termux

### 📱 Setup di Acode (Android)

Acode adalah code editor Android yang powerful dan gratis. Ini yang paling direkomendasiin buat coding di HP.

**Langkah-langkah:**

**1. Install Acode**
- Buka Play Store
- Cari "Acode - Code Editor"
- Install (developer: Foxdebug)

**2. Bikin project pertama**
```
1. Buka Acode
2. Klik ikon folder di kiri atas
3. Pilih "New File"
4. Beri nama: index.html
5. Pilih lokasi: Storage/Documents/belajar-web/
```

**3. Aktifkan fitur berguna di Acode**
```
Settings → Editor:
✅ Word Wrap            — biar kode nggak kepotong
✅ Auto Close Tags      — ketik <div>, langsung muncul </div>
✅ Emmet               — shortcut bikin HTML super cepet
✅ Line Numbers         — biar gampang debug
✅ Syntax Highlighting  — warna-warni kode
```

**4. Preview langsung di Acode**
```
Setelah nulis kode HTML:
→ Klik tombol ▶ (Run) di kanan atas
→ Pilih "Browser" atau "In-app preview"
→ Langsung keliatan hasilnya!
```

> 💡 **Tips Emmet di Acode:** Ketik `html:5` lalu tekan **Tab** — langsung keluar template HTML5 lengkap. Ketik `div.kartu>h2+p` lalu Tab — keluar struktur div dengan class "kartu", isi h2 dan p.

**Emmet shortcuts yang paling berguna:**

| Emmet | Hasil |
|-------|-------|
| `!` atau `html:5` | Template HTML5 lengkap |
| `div.nama-class` | `<div class="nama-class"></div>` |
| `div#nama-id` | `<div id="nama-id"></div>` |
| `ul>li*5` | ul dengan 5 li di dalamnya |
| `p{Teks isi}` | `<p>Teks isi</p>` |
| `a[href=#]` | `<a href="#"></a>` |
| `input:email` | `<input type="email">` |

---

### 💻 Setup di Termux (Terminal Android)

Termux buat yang mau lebih serius — bisa jalanin web server lokal, buka file HTML lewat server, dan kerja kayak developer beneran.

**1. Install Termux**
- Download dari **F-Droid** (bukan Play Store — versi Play Store sudah deprecated dan tidak dapat update)
- Link: `https://f-droid.org/packages/com.termux/`

**2. Setup awal Termux**
```bash
# Update dulu semua package
pkg update && pkg upgrade -y

# Install text editor
pkg install nano -y      # editor simpel, enak buat pemula
pkg install vim -y       # editor pro (opsional)
pkg install neovim -y    # editor modern (opsional)

# Install web server ringan
pkg install python -y    # python punya web server built-in

# Install Node.js (buat live-server nanti)
pkg install nodejs -y

# Izinkan Termux akses storage HP
termux-setup-storage
# Tap "Allow" di notifikasi
```

**3. Bikin folder project**
```bash
# Bikin folder belajar
mkdir -p ~/storage/downloads/belajar-web
cd ~/storage/downloads/belajar-web

# Bikin file HTML pertama
nano index.html
```

**4. Nulis HTML di nano**
```
Di dalam nano:
- Ketik kode HTML lo
- Ctrl + O   → Save file
- Enter      → Konfirmasi nama file
- Ctrl + X   → Keluar dari nano
```

**5. Jalanin web server lokal**
```bash
# Masuk ke folder project
cd ~/storage/downloads/belajar-web

# Jalanin web server Python (port 8080)
python -m http.server 8080

# Buka browser Android
# Ketik di address bar: http://localhost:8080
# Website lo jalan secara lokal!

# Tekan Ctrl+C di Termux untuk stop server
```

**6. Live Server — auto-refresh saat file berubah**
```bash
# Install live-server via npm (sekali aja)
npm install -g live-server

# Jalanin di folder project
cd ~/storage/downloads/belajar-web
live-server --port=8080 --no-browser

# Buka browser: http://localhost:8080
# Setiap kali save file → browser otomatis refresh!
```

**7. Workflow harian di Termux**
```bash
# Terminal 1 (server):
cd ~/storage/downloads/belajar-web
live-server --port=8080 --no-browser

# Terminal 2 (edit file):
# Buka Acode, edit file, save
# ATAU langsung edit di Termux:
nano index.html
# atau
vim index.html
```

> 💡 **Tips Termux:** Gunakan gesture swipe dari kiri untuk buka panel session baru. Bisa punya beberapa terminal sekaligus — satu buat server, satu buat edit file.

---

## 3. Struktur Dasar HTML

Setiap file HTML yang valid harus punya struktur ini. Ini kayak "aturan main" yang harus diikutin.

```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Judul Halaman di Tab Browser</title>
</head>
<body>
    <!-- Semua konten yang keliatan user ada di sini -->
    <h1>Halo Dunia!</h1>
    <p>Ini paragraf pertama gue.</p>
</body>
</html>
```

### Penjelasan baris per baris:

| Baris | Penjelasan |
|-------|-----------|
| `<!DOCTYPE html>` | Deklarasi ke browser: "Ini file HTML5." Wajib ada di baris pertama. |
| `<html lang="id">` | Elemen akar (root). `lang="id"` = bahasa Indonesia. Penting untuk SEO & screen reader. |
| `<head>` | Kepala dokumen — berisi info tentang halaman (tidak tampil ke user). |
| `<meta charset="UTF-8">` | Character encoding — supaya huruf Indonesia tampil benar. |
| `<meta name="viewport" ...>` | Bikin halaman responsive di mobile. **Wajib selalu ada.** |
| `<title>` | Judul yang muncul di tab browser dan hasil pencarian Google. |
| `<body>` | Tubuh dokumen — semua konten yang kelihatan user ada di sini. |
| `<!-- komentar -->` | Komentar HTML — tidak ditampilkan browser, hanya catatan programmer. |

### ❌ Kesalahan umum pemula:

```html
<!-- ❌ SALAH — lupa DOCTYPE -->
<html>
<head><title>Test</title></head>
<body><p>Halo</p></body>
</html>

<!-- ❌ SALAH — lupa meta viewport (website rusak di HP!) -->
<head>
    <meta charset="UTF-8">
    <title>Test</title>
    <!-- TIDAK ADA viewport! -->
</head>

<!-- ❌ SALAH — tag tidak ditutup dengan benar -->
<p>Ini paragraf
<p>Ini paragraf lain

<!-- ✅ BENAR — lengkap dan rapi -->
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Judul Halaman</title>
</head>
<body>
    <h1>Halo!</h1>
    <p>Ini paragraf pertama.</p>
    <p>Ini paragraf kedua.</p>
</body>
</html>
```

> 💡 **Tips Acode:** Ketik `!` lalu tekan **Tab** — langsung keluar struktur HTML5 lengkap!

---

## 4. Tag & Elemen — Bata-bata Halaman

**Tag** itu seperti perintah yang dibungkus tanda kurung sudut `< >`.

**Elemen** = tag pembuka + konten + tag penutup.

```
    Tag Pembuka      Konten           Tag Penutup
        ↓               ↓                 ↓
    <h1>      Ini judul halaman      </h1>
    └──────────────────────────────────────┘
                     ELEMEN
```

### Dua jenis tag:

**1. Tag berpasangan (Paired Tags)** — punya pembuka dan penutup
```html
<h1>Ini judul</h1>
<p>Ini paragraf</p>
<div>Ini kotak pembungkus</div>
<strong>Ini teks tebal</strong>
<a href="#">Ini link</a>
```

**2. Tag mandiri (Self-closing Tags)** — tidak butuh penutup
```html
<br>         <!-- ganti baris -->
<hr>         <!-- garis horizontal -->
<img src="foto.jpg" alt="Foto">
<input type="text">
<meta charset="UTF-8">
<link rel="stylesheet" href="style.css">
```

> 📝 **Catatan HTML5:** Self-closing tag tidak perlu `/>` di akhir. `<br>` valid, `<br />` juga valid. Tapi pilih satu dan konsisten.

### Tag-tag yang WAJIB lo hafal:

#### Heading (Judul — H1 sampai H6)
```html
<h1>Judul Utama — Paling Besar, Hanya SATU per halaman</h1>
<h2>Subjudul — Satu Level di Bawah h1</h2>
<h3>Sub-subjudul</h3>
<h4>Level 4</h4>
<h5>Level 5</h5>
<h6>Judul Terkecil — Level 6</h6>
```

**Aturan penting heading:**
- Satu halaman hanya boleh punya **satu `<h1>`** — untuk SEO Google
- Heading harus urut — jangan lompat dari `<h1>` langsung ke `<h4>`
- Jangan pakai heading hanya untuk bikin teks besar — itu tugas CSS

```html
<!-- ❌ SALAH — heading dipakai untuk gaya, bukan struktur -->
<h3>Teks ini gue bikin h3 biar agak besar</h3>
<p>Paragraf biasa</p>
<h5>h5 karena gue mau kecil</h5>

<!-- ✅ BENAR — heading sesuai hierarki konten -->
<h1>Judul Artikel</h1>
<h2>Bagian 1</h2>
<p>Isi bagian 1...</p>
<h2>Bagian 2</h2>
<h3>Sub-bagian 2.1</h3>
<p>Isi sub-bagian...</p>
```

#### Paragraf & Teks
```html
<p>Ini paragraf. Browser otomatis kasih jarak atas-bawah.</p>
<p>Paragraf kedua. Jarak paragraf dikontrol CSS.</p>

<br>    <!-- baris baru TANPA membuat paragraf baru -->
<hr>    <!-- garis horizontal pemisah -->

<!-- pre — menjaga spasi dan enter aslinya -->
<pre>
    Teks ini
    menjaga     spasi
        dan enter aslinya
</pre>
```

#### Pembungkus (Container)
```html
<!-- div — pembungkus blok (tidak punya makna semantik) -->
<div class="kartu">
    <h2>Judul Kartu</h2>
    <p>Isi kartu</p>
</div>

<!-- span — pembungkus inline (untuk sedikit teks dalam paragraf) -->
<p>Teks biasa <span style="color:red">teks merah</span> lanjut lagi.</p>
```

**Perbedaan `<div>` vs `<span>`:**

| | `<div>` | `<span>` |
|---|---|---|
| Tipe | Block — mulai baris baru | Inline — ngikut dalam teks |
| Kegunaan | Bungkus section besar | Bungkus sedikit teks |
| Contoh pakai | Kartu, section, layout | Warnain kata, tambah class pada teks |

---

## 5. Atribut — Pengaturan Tag

**Atribut** itu pengaturan tambahan di dalam tag pembuka. Format: `nama="nilai"`.

```
       Nama       Nilai         Nama       Nilai
         ↓           ↓            ↓           ↓
<img  src="foto.jpg"  alt="Foto profil"  width="300">
 ↑
Tag
```

### Atribut Universal (berlaku di semua tag):

```html
<!-- id — identitas unik. Satu halaman SATU id yang sama. -->
<h1 id="judul-utama">Selamat Datang</h1>
<section id="tentang">...</section>

<!-- class — kategori. BOLEH dipakai banyak elemen. -->
<p class="teks-kecil">Paragraf pertama</p>
<p class="teks-kecil">Paragraf kedua juga pakai class yang sama</p>

<!-- style — CSS langsung di elemen. Hindari jika bisa. -->
<p style="color: blue; font-size: 20px;">Teks biru</p>

<!-- title — tooltip saat mouse hover -->
<abbr title="Hypertext Markup Language">HTML</abbr>

<!-- hidden — sembunyikan elemen -->
<div hidden>Ini tidak akan tampil</div>

<!-- lang — bahasa konten elemen ini -->
<p lang="en">This paragraph is in English.</p>

<!-- tabindex — urutan fokus saat tekan Tab -->
<button tabindex="1">Tombol Pertama</button>
<button tabindex="2">Tombol Kedua</button>
```

### Perbedaan `id` vs `class` — ini PENTING:

```html
<!--
    id   → UNIK. Satu halaman, SATU id dengan nama yang sama.
             Dipakai untuk target spesifik (anchor link, JavaScript).

    class → BISA BERULANG. Satu class boleh dipakai banyak elemen.
             Dipakai untuk styling yang sama di banyak elemen.
-->

<!-- Contoh id yang benar -->
<header id="header-utama">...</header>
<section id="tentang-kami">...</section>
<footer id="footer-site">...</footer>

<!-- Contoh class yang benar -->
<div class="kartu">Kartu 1</div>
<div class="kartu">Kartu 2</div>
<div class="kartu">Kartu 3</div>

<!-- Satu elemen boleh punya BANYAK class — pisah spasi -->
<div class="kartu kartu-featured kartu-besar">Kartu Spesial</div>

<!-- ❌ SALAH — id duplikat! -->
<div id="kartu">Kartu 1</div>
<div id="kartu">Kartu 2</div>  <!-- sama id-nya, ini error! -->
```

---

## 6. Teks & Tipografi

### Pemformatan teks — beserta maknanya:

```html
<p>
    <!-- PENEKANAN SEMANTIK — bermakna bagi screen reader dan SEO -->
    Ini teks <strong>tebal dan penting (semantik)</strong>.
    Ini teks <em>miring dengan penekanan (semantik)</em>.

    <!-- GAYA VISUAL SAJA — tidak bermakna untuk aksesibilitas -->
    Ini teks <b>tebal visual saja</b>.
    Ini teks <i>miring visual saja</i>.
</p>

<p>Ini teks <u>bergaris bawah</u>.</p>
<p>Harga lama: <s>Rp 150.000</s> → Sekarang: Rp 99.000</p>
<p>Cari kata: <mark>HTML</mark> di dokumen ini.</p>
<p>Rumus air: H<sub>2</sub>O</p>
<p>Einstein: E = mc<sup>2</sup></p>
<p>Pakai fungsi <code>console.log()</code> untuk debug.</p>

<!-- Blok kode (multi-baris) -->
<pre><code>
function sapa(nama) {
    return `Halo, ${nama}!`;
}
</code></pre>

<!-- Kutipan blok -->
<blockquote cite="https://sumber.com/artikel">
    <p>"The best way to predict the future is to create it."</p>
    <footer>— <cite>Peter Drucker</cite></footer>
</blockquote>

<!-- Kutipan inline -->
<p>Steve Jobs pernah bilang <q>Stay hungry, stay foolish</q>.</p>

<!-- Singkatan dengan penjelasan -->
<p>Gue lagi belajar <abbr title="Hypertext Markup Language">HTML</abbr>.</p>

<!-- Tanggal — mesin bisa baca format datetime -->
<p>Diterbitkan: <time datetime="2024-11-15">15 November 2024</time></p>

<!-- Keyboard shortcut -->
<p>Tekan <kbd>Ctrl</kbd> + <kbd>S</kbd> untuk save.</p>
```

### `<strong>` vs `<b>` dan `<em>` vs `<i>` — kapan pakai yang mana:

| Tag | Tujuan | Tampilan | Screen Reader |
|-----|--------|----------|--------------|
| `<strong>` | Konten ini PENTING secara semantik | **Tebal** | Baca dengan penekanan |
| `<b>` | Tebal secara visual saja | **Tebal** | Tidak diberi penekanan |
| `<em>` | Penekanan semantik — baca dengan nada berbeda | *Miring* | Baca dengan intonasi berbeda |
| `<i>` | Miring visual (judul buku, istilah asing, dll) | *Miring* | Tidak ada penekanan |

> 💡 **Aturan simpel:** Kalau lo mau kasih tahu "ini bagian penting dari konten" → pakai `<strong>` atau `<em>`. Kalau cuma mau ubah tampilan → pakai `<b>` atau `<i>`. Dalam praktiknya, `<strong>` dan `<em>` jauh lebih sering dipakai.

---

## 7. Link & Navigasi

Link adalah jiwa dari web — *World Wide Web* adalah jaringan halaman yang saling terhubung lewat hyperlink.

```html
<!-- Link dasar — atribut href wajib ada -->
<a href="https://google.com">Pergi ke Google</a>

<!-- Link buka tab baru — SELALU sertakan rel="noopener noreferrer" -->
<a href="https://github.com/rixz-dev" target="_blank" rel="noopener noreferrer">
    GitHub Gue (tab baru)
</a>

<!-- Link ke halaman lain di website yang sama (relative URL) -->
<a href="/tentang.html">Tentang Kami</a>
<a href="./artikel/html-dasar.html">Artikel HTML Dasar</a>
<a href="../index.html">Kembali ke Home</a>

<!-- Link ke section di halaman yang sama (anchor) -->
<a href="#kontak">Scroll ke Bagian Kontak</a>
<!-- ... konten lain ... -->
<section id="kontak">
    <h2>Kontak</h2>
</section>

<!-- Link download file -->
<a href="/files/panduan.pdf" download>Download Panduan (PDF)</a>
<a href="/files/data.xlsx" download="laporan-q3.xlsx">Download Laporan</a>

<!-- Link ke email -->
<a href="mailto:rixz@aners.dev">Kirim Email ke Rixz</a>
<a href="mailto:rixz@aners.dev?subject=Halo&body=Gue%20mau%20tanya...">
    Email dengan Subject
</a>

<!-- Link ke nomor telepon (berguna di mobile) -->
<a href="tel:+6281234567890">+62 812-3456-7890</a>

<!-- Link ke WhatsApp -->
<a href="https://wa.me/6281234567890?text=Halo%20Rixz!" 
   target="_blank" rel="noopener noreferrer">
    Chat WhatsApp
</a>
```

### Penjelasan atribut `<a>`:

| Atribut | Penjelasan |
|---------|-----------|
| `href` | *HyperText Reference* — tujuan link. Wajib ada. |
| `target="_blank"` | Buka di tab baru. |
| `target="_self"` | Buka di tab yang sama (default). |
| `rel="noopener noreferrer"` | Keamanan — WAJIB disertakan saat `target="_blank"`. Tanpa ini, halaman tujuan bisa akses halaman asal via `window.opener`. |
| `download` | Trigger download file, bukan buka file. |
| `hreflang="en"` | Bahasa dokumen tujuan — berguna untuk SEO multibahasa. |

### ❌ Kesalahan umum link:

```html
<!-- ❌ SALAH — tanpa rel keamanan (security risk!) -->
<a href="https://site.com" target="_blank">Klik</a>

<!-- ✅ BENAR -->
<a href="https://site.com" target="_blank" rel="noopener noreferrer">Klik</a>

<!-- ❌ SALAH — teks link tidak deskriptif (buruk untuk SEO & aksesibilitas) -->
<p>Untuk lihat produk, <a href="/produk">klik di sini</a>.</p>

<!-- ✅ BENAR — teks link menjelaskan tujuannya -->
<p><a href="/produk">Lihat semua produk kami</a>.</p>

<!-- ❌ SALAH — pakai <a href="#"> sebagai tombol -->
<a href="#">Hapus Item</a>

<!-- ✅ BENAR — kalau mau tombol, pakai <button> -->
<button type="button">Hapus Item</button>

<!-- ❌ SALAH — link dalam link (tidak valid HTML) -->
<a href="/artikel">
    <h2>Judul</h2>
    <a href="/penulis">Nama Penulis</a>  <!-- nested link = INVALID -->
</a>
```

---

## 8. Gambar & Media

### Gambar (`<img>`)

```html
<!-- Format dasar — src dan alt WAJIB ada -->
<img src="foto.jpg" alt="Deskripsi foto yang informatif">

<!-- Dengan ukuran — selalu tentukan width dan height (cegah layout shift) -->
<img src="logo.png" alt="Logo ANERS" width="200" height="60">

<!-- Dari URL internet -->
<img src="https://picsum.photos/800/400" alt="Gambar placeholder">

<!-- Lazy loading — gambar tidak di-load sampai hampir masuk viewport -->
<img src="foto-besar.jpg" alt="Foto landscape" loading="lazy" 
     width="1200" height="800">

<!-- Responsive image — browser pilih ukuran yang paling cocok -->
<img
    src="foto-medium.jpg"
    alt="Foto produk"
    srcset="
        foto-480.jpg 480w,
        foto-768.jpg 768w,
        foto-1200.jpg 1200w
    "
    sizes="
        (max-width: 480px) 100vw,
        (max-width: 768px) 80vw,
        600px
    "
    width="1200"
    height="800"
>
```

**Kenapa atribut `alt` itu WAJIB:**
- Ditampilkan jika gambar gagal dimuat
- Dibaca oleh screen reader untuk tuna netra
- Diindeks oleh Google Images (SEO)
- `alt=""` (kosong) valid — gunakan untuk gambar dekoratif yang tidak punya makna konten

### Figure + Figcaption (gambar + keterangan):
```html
<figure>
    <img src="grafik-penjualan.png" 
         alt="Grafik batang menunjukkan pertumbuhan penjualan Q3 2024"
         width="800" height="500">
    <figcaption>
        Gambar 1: Pertumbuhan penjualan Q3 2024 mencapai 40% 
        dibanding Q3 2023.
    </figcaption>
</figure>
```

### Video:
```html
<!-- Video lokal dengan kontrol -->
<video controls width="640" height="360" poster="thumbnail.jpg">
    <source src="video.mp4" type="video/mp4">
    <source src="video.webm" type="video/webm">
    <p>Browser lo tidak mendukung video HTML5. 
       <a href="video.mp4">Download videonya di sini</a>.
    </p>
</video>

<!-- Video background (hero section) -->
<video autoplay muted loop playsinline width="1920" height="1080">
    <source src="bg-video.mp4" type="video/mp4">
</video>

<!-- Embed YouTube -->
<iframe
    width="560"
    height="315"
    src="https://www.youtube.com/embed/VIDEO_ID"
    title="Judul video YouTube"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope"
    allowfullscreen>
</iframe>
```

### Audio:
```html
<audio controls>
    <source src="podcast.mp3" type="audio/mpeg">
    <source src="podcast.ogg" type="audio/ogg">
    Browser lo tidak mendukung audio HTML5.
</audio>
```

### Format gambar — mana yang dipilih:

| Format | Kegunaan Terbaik | Kelebihan | Kekurangan |
|--------|-----------------|-----------|-----------|
| **JPG/JPEG** | Foto, gambar kompleks | Ukuran kecil | Tidak ada transparansi |
| **PNG** | Logo, screenshot | Mendukung transparansi | Ukuran lebih besar |
| **SVG** | Logo, ikon, ilustrasi | Scalable, ukuran sangat kecil, editable CSS | Tidak cocok untuk foto |
| **WebP** | Semua tujuan modern | 25-35% lebih kecil dari JPG, mendukung transparansi | Dukungan browser lama terbatas |
| **AVIF** | Semua tujuan (2024+) | Ukuran terkecil | Dukungan browser masih berkembang |
| **GIF** | Animasi sederhana | Mendukung animasi | Kualitas buruk, ukuran besar |

> 💡 **Rekomendasi 2024:** Gunakan **WebP** untuk foto, **SVG** untuk logo/ikon. Sediakan fallback JPG/PNG untuk browser lama dengan tag `<picture>`.

---

## 9. List — Daftar-daftaran

### Unordered List — `<ul>` (daftar tanpa nomor)
```html
<ul>
    <li>HTML — Struktur</li>
    <li>CSS — Tampilan</li>
    <li>JavaScript — Interaktivitas</li>
</ul>
```

### Ordered List — `<ol>` (daftar bernomor)
```html
<ol>
    <li>Belajar HTML dulu — fondasi</li>
    <li>Kemudian CSS — tampilan</li>
    <li>Baru JavaScript — logika</li>
</ol>
```

### Ordered List — variasi penomoran
```html
<!-- Huruf kapital -->
<ol type="A">
    <li>Opsi A</li>
    <li>Opsi B</li>
</ol>

<!-- Huruf kecil -->
<ol type="a">
    <li>Opsi a</li>
    <li>Opsi b</li>
</ol>

<!-- Angka romawi kapital -->
<ol type="I">
    <li>Bab I</li>
    <li>Bab II</li>
</ol>

<!-- Mulai dari nomor tertentu -->
<ol start="5">
    <li>Ini nomor 5</li>
    <li>Ini nomor 6</li>
</ol>

<!-- Urutan terbalik -->
<ol reversed>
    <li>Posisi 3</li>
    <li>Posisi 2</li>
    <li>Posisi 1</li>
</ol>
```

### Description List — `<dl>` (daftar istilah & definisi)
```html
<dl>
    <dt>HTML</dt>
    <dd>Bahasa markup untuk membangun struktur halaman web.</dd>

    <dt>CSS</dt>
    <dd>Bahasa styling untuk mengontrol tampilan elemen HTML.</dd>

    <dt>JavaScript</dt>
    <dd>Bahasa pemrograman yang membuat halaman web menjadi interaktif.</dd>

    <!-- Satu term bisa punya banyak definisi -->
    <dt>API</dt>
    <dd>Application Programming Interface.</dd>
    <dd>Antarmuka yang memungkinkan dua program berkomunikasi.</dd>
</dl>
```

**Kapan pakai `<dl>`:** Glossary, FAQ (pertanyaan + jawaban), metadata (author: nama, tanggal: tgl), pasangan key-value.

### Nested List (list di dalam list)
```html
<ul>
    <li>Frontend
        <ul>
            <li>HTML</li>
            <li>CSS</li>
            <li>JavaScript
                <ul>
                    <li>React</li>
                    <li>Vue</li>
                    <li>Svelte</li>
                </ul>
            </li>
        </ul>
    </li>
    <li>Backend
        <ul>
            <li>Node.js (Express, Fastify)</li>
            <li>Python (FastAPI, Django)</li>
            <li>Go</li>
        </ul>
    </li>
</ul>
```

> ⚠️ **Aturan nesting:** Elemen `<li>` adalah satu-satunya yang boleh langsung di dalam `<ul>` atau `<ol>`. Jangan taruh `<div>` atau `<p>` langsung di dalam `<ul>`.

---

## 10. Tabel — Data Terstruktur

Tabel **hanya untuk data tabular** — data yang secara alami berbentuk baris dan kolom. Jangan pakai tabel untuk layout halaman.

### Struktur tabel yang lengkap dan semantik:
```html
<table>
    <!-- caption — judul tabel, sangat penting untuk aksesibilitas -->
    <caption>Rincian Paket Hosting ANERS (per Desember 2024)</caption>

    <!-- thead — baris header kolom -->
    <thead>
        <tr>
            <th scope="col">Paket</th>
            <th scope="col">Storage</th>
            <th scope="col">Bandwidth</th>
            <th scope="col">Harga/bulan</th>
        </tr>
    </thead>

    <!-- tbody — isi data utama -->
    <tbody>
        <tr>
            <th scope="row">Starter</th>  <!-- th untuk row header -->
            <td>5 GB</td>
            <td>50 GB</td>
            <td>Rp 25.000</td>
        </tr>
        <tr>
            <th scope="row">Pro</th>
            <td>25 GB</td>
            <td>250 GB</td>
            <td>Rp 75.000</td>
        </tr>
        <tr>
            <th scope="row">Business</th>
            <td>100 GB</td>
            <td>Unlimited</td>
            <td>Rp 200.000</td>
        </tr>
    </tbody>

    <!-- tfoot — baris ringkasan atau total -->
    <tfoot>
        <tr>
            <td colspan="3">Harga belum termasuk PPN 11%</td>
            <td>Mulai Rp 25.000</td>
        </tr>
    </tfoot>
</table>
```

### Merge sel — colspan dan rowspan:
```html
<table>
    <caption>Jadwal Pelajaran</caption>
    <thead>
        <tr>
            <th scope="col">Jam</th>
            <th scope="col">Senin</th>
            <th scope="col">Selasa</th>
            <th scope="col">Rabu</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>08.00</td>
            <td colspan="2">HTML & CSS (2 jam)</td>  <!-- isi 2 kolom -->
            <td>JavaScript</td>
        </tr>
        <tr>
            <td>10.00</td>
            <td>Review</td>
            <td rowspan="2">Project</td>  <!-- isi 2 baris -->
            <td>CSS Grid</td>
        </tr>
        <tr>
            <td>13.00</td>
            <td>Flexbox</td>
            <!-- sel kedua diisi oleh rowspan di atas -->
            <td>Animasi</td>
        </tr>
    </tbody>
</table>
```

**Elemen tabel dan fungsinya:**

| Elemen | Fungsi |
|--------|--------|
| `<table>` | Container utama tabel |
| `<caption>` | Judul tabel — taruh tepat setelah `<table>` |
| `<thead>` | Grup baris header |
| `<tbody>` | Grup baris isi data |
| `<tfoot>` | Grup baris footer/total |
| `<tr>` | Baris (table row) |
| `<th>` | Sel header — tebal dan tengah secara default |
| `<td>` | Sel data biasa |
| `scope="col"` | `<th>` ini adalah header untuk kolom |
| `scope="row"` | `<th>` ini adalah header untuk baris |
| `colspan="n"` | Sel ini mengisi n kolom |
| `rowspan="n"` | Sel ini mengisi n baris |

---

## 11. Form & Input — Ambil Data dari User

Form adalah cara utama halaman web mengumpulkan data dari user.

### Struktur form dasar:
```html
<form action="/proses" method="POST" novalidate>
    <!-- Elemen form di sini -->
    <button type="submit">Kirim</button>
</form>
```

**Atribut `<form>`:**

| Atribut | Nilai | Penjelasan |
|---------|-------|-----------|
| `action` | URL | Ke mana data dikirim saat disubmit. Kosong = halaman itu sendiri. |
| `method` | `GET` / `POST` | `GET` = data tampil di URL (tidak sensitif). `POST` = data di body request (password, upload file). |
| `enctype` | `multipart/form-data` | Wajib jika ada input file upload. |
| `novalidate` | — | Matikan validasi bawaan browser (buat validasi sendiri via JS). |
| `autocomplete` | `on` / `off` | Aktif/matikan autocomplete browser. |

### Semua jenis input yang perlu lo tahu:

```html
<form action="/daftar" method="POST">

    <!-- ── TEXT INPUTS ── -->

    <!-- Teks biasa -->
    <div class="form-group">
        <label for="nama">Nama Lengkap</label>
        <input type="text" id="nama" name="nama"
               placeholder="Masukkan nama lengkap"
               autocomplete="name"
               required>
    </div>

    <!-- Email — otomatis validasi format @domain.com -->
    <div class="form-group">
        <label for="email">Email</label>
        <input type="email" id="email" name="email"
               placeholder="nama@email.com"
               autocomplete="email"
               required>
    </div>

    <!-- Password — teks tersembunyi -->
    <div class="form-group">
        <label for="password">Password</label>
        <input type="password" id="password" name="password"
               placeholder="Minimal 8 karakter"
               minlength="8"
               maxlength="64"
               autocomplete="new-password"
               required>
    </div>

    <!-- Nomor -->
    <div class="form-group">
        <label for="umur">Umur</label>
        <input type="number" id="umur" name="umur"
               min="1" max="120" step="1"
               placeholder="Contoh: 20">
    </div>

    <!-- Telepon -->
    <div class="form-group">
        <label for="telp">No. Telepon</label>
        <input type="tel" id="telp" name="telp"
               placeholder="08xxxxxxxxxx"
               pattern="[0-9]{10,13}"
               autocomplete="tel">
    </div>

    <!-- URL -->
    <div class="form-group">
        <label for="website">Website</label>
        <input type="url" id="website" name="website"
               placeholder="https://website-lo.com">
    </div>

    <!-- Pencarian -->
    <div class="form-group">
        <label for="cari">Cari</label>
        <input type="search" id="cari" name="q"
               placeholder="Ketik untuk mencari...">
    </div>

    <!-- ── DATE & TIME ── -->

    <div class="form-group">
        <label for="tanggal">Tanggal Lahir</label>
        <input type="date" id="tanggal" name="tanggal"
               min="1950-01-01" max="2010-12-31">
    </div>

    <div class="form-group">
        <label for="jam">Jam Meeting</label>
        <input type="time" id="jam" name="jam"
               min="09:00" max="17:00">
    </div>

    <div class="form-group">
        <label for="datetime">Tanggal & Jam</label>
        <input type="datetime-local" id="datetime" name="datetime">
    </div>

    <div class="form-group">
        <label for="bulan">Bulan</label>
        <input type="month" id="bulan" name="bulan">
    </div>

    <!-- ── SPECIAL INPUTS ── -->

    <!-- Range / Slider -->
    <div class="form-group">
        <label for="rating">Rating: <output for="rating" id="rating-output">5</output>/10</label>
        <input type="range" id="rating" name="rating"
               min="1" max="10" value="5" step="1"
               oninput="document.getElementById('rating-output').value = this.value">
    </div>

    <!-- Color picker -->
    <div class="form-group">
        <label for="warna">Warna Favorit</label>
        <input type="color" id="warna" name="warna" value="#f59e0b">
    </div>

    <!-- File upload -->
    <div class="form-group">
        <label for="foto">Upload Foto Profil</label>
        <input type="file" id="foto" name="foto"
               accept="image/jpeg, image/png, image/webp"
               multiple>
    </div>

    <!-- Hidden — data yang dikirim tapi tidak tampil ke user -->
    <input type="hidden" name="csrf_token" value="abc123xyz">
    <input type="hidden" name="sumber" value="halaman-daftar">

    <!-- ── SELECTION INPUTS ── -->

    <!-- Checkbox — bisa pilih banyak -->
    <div class="form-group">
        <fieldset>
            <legend>Keahlian (pilih semua yang sesuai)</legend>
            <label>
                <input type="checkbox" name="keahlian" value="html">
                HTML
            </label>
            <label>
                <input type="checkbox" name="keahlian" value="css">
                CSS
            </label>
            <label>
                <input type="checkbox" name="keahlian" value="js">
                JavaScript
            </label>
        </fieldset>
    </div>

    <!-- Radio — hanya bisa pilih SATU dari kelompok yang sama (name sama) -->
    <div class="form-group">
        <fieldset>
            <legend>Level Pengalaman</legend>
            <label>
                <input type="radio" name="level" value="pemula" required>
                Pemula (0-1 tahun)
            </label>
            <label>
                <input type="radio" name="level" value="menengah">
                Menengah (1-3 tahun)
            </label>
            <label>
                <input type="radio" name="level" value="mahir">
                Mahir (3+ tahun)
            </label>
        </fieldset>
    </div>

    <!-- Select dropdown -->
    <div class="form-group">
        <label for="kota">Kota</label>
        <select id="kota" name="kota" required>
            <option value="">-- Pilih Kota --</option>
            <option value="jakarta">Jakarta</option>
            <option value="bandung">Bandung</option>
            <option value="surabaya" selected>Surabaya</option>
            <option value="yogyakarta">Yogyakarta</option>
        </select>
    </div>

    <!-- Select dengan optgroup (pengelompokan) -->
    <div class="form-group">
        <label for="bahasa">Bahasa Favorit</label>
        <select id="bahasa" name="bahasa" multiple size="6">
            <optgroup label="Frontend">
                <option value="html">HTML</option>
                <option value="css">CSS</option>
                <option value="js">JavaScript</option>
                <option value="ts">TypeScript</option>
            </optgroup>
            <optgroup label="Backend">
                <option value="node">Node.js</option>
                <option value="python">Python</option>
                <option value="go">Go</option>
            </optgroup>
        </select>
    </div>

    <!-- Textarea — input teks panjang -->
    <div class="form-group">
        <label for="bio">Bio</label>
        <textarea id="bio" name="bio"
                  rows="5"
                  placeholder="Ceritain sedikit tentang dirimu..."
                  maxlength="500"></textarea>
    </div>

    <!-- Datalist — input teks dengan autocomplete suggestion -->
    <div class="form-group">
        <label for="framework">Framework yang Dipelajari</label>
        <input type="text" id="framework" name="framework"
               list="framework-list"
               placeholder="Ketik atau pilih...">
        <datalist id="framework-list">
            <option value="React">
            <option value="Vue">
            <option value="Svelte">
            <option value="Angular">
            <option value="Next.js">
            <option value="Nuxt.js">
        </datalist>
    </div>

    <!-- ── BUTTONS ── -->
    <button type="submit">Daftar Sekarang</button>
    <button type="reset">Reset Form</button>
    <button type="button" onclick="preview()">Preview</button>

</form>
```

### Kenapa `<label>` itu WAJIB ada:

```html
<!-- ❌ SALAH — input tanpa label -->
<input type="text" placeholder="Nama">
<!-- Masalah: screen reader tidak tahu ini input untuk apa.
              Placeholder menghilang saat diketik.
              Klik teks "Nama" tidak memindahkan fokus ke input. -->

<!-- ✅ BENAR — cara 1: label dihubungkan via for dan id -->
<label for="nama">Nama Lengkap</label>
<input type="text" id="nama" name="nama">

<!-- ✅ BENAR — cara 2: label membungkus input -->
<label>
    Nama Lengkap
    <input type="text" name="nama">
</label>
```

Dengan label yang benar:
- Klik teks label → cursor otomatis masuk ke input
- Screen reader membaca "Nama Lengkap — input teks"
- Area klik lebih besar → UX lebih baik di mobile

### Validasi bawaan HTML5:

```html
<!-- required — harus diisi sebelum submit -->
<input type="text" name="nama" required>

<!-- minlength & maxlength — batas panjang teks -->
<input type="password" name="pass" minlength="8" maxlength="64" required>

<!-- min & max — batas nilai angka atau tanggal -->
<input type="number" name="qty" min="1" max="100" required>
<input type="date" name="tgl" min="2024-01-01" max="2025-12-31">

<!-- pattern — validasi dengan regular expression -->
<input type="text" name="kode_pos"
       pattern="[0-9]{5}"
       title="Kode pos harus 5 angka"
       required>

<input type="text" name="username"
       pattern="[a-zA-Z0-9_]{3,20}"
       title="3-20 karakter, huruf, angka, atau underscore"
       required>

<!-- step — kelipatan nilai yang valid -->
<input type="number" name="berat" min="0" max="500" step="0.5">
<!-- Valid: 0, 0.5, 1, 1.5, ... — tidak valid: 0.3, 1.7 -->
```

---

## 12. Semantic HTML — Kode yang Bermakna

**Semantic HTML** adalah menggunakan tag yang sesuai dengan **makna kontennya**, bukan sekadar tampilannya.

### Mengapa semantic HTML penting:

| Alasan | Penjelasan |
|--------|-----------|
| **SEO** | Google memahami hierarki dan konten dengan lebih baik |
| **Aksesibilitas** | Screen reader tahu mana navigasi, mana artikel, mana konten utama |
| **Maintainability** | Kode lebih mudah dibaca dan dipelihara |
| **Semantik browser** | Browser bisa render dengan benar tanpa CSS |

### Perbandingan: Tanpa vs Dengan Semantic HTML

```html
<!-- ❌ TANPA SEMANTIC — "div soup" yang tidak bermakna -->
<div id="header">
    <div id="logo">ANERS</div>
    <div id="nav">
        <div class="nav-item"><a href="/">Home</a></div>
        <div class="nav-item"><a href="/about">About</a></div>
    </div>
</div>
<div id="wrapper">
    <div id="main-content">
        <div class="post">
            <div class="post-header">Judul Post</div>
            <div class="post-body">Isi post...</div>
        </div>
    </div>
    <div id="sidebar">
        <div class="widget">Artikel Terkait</div>
    </div>
</div>
<div id="footer">© 2024 ANERS</div>


<!-- ✅ DENGAN SEMANTIC — jelas, bermakna, accessible -->
<header>
    <a href="/" class="logo">ANERS</a>
    <nav aria-label="Navigasi utama">
        <ul>
            <li><a href="/">Home</a></li>
            <li><a href="/about">About</a></li>
        </ul>
    </nav>
</header>
<div class="wrapper">
    <main>
        <article>
            <h1>Judul Post</h1>
            <p>Isi post...</p>
        </article>
    </main>
    <aside>
        <h2>Artikel Terkait</h2>
    </aside>
</div>
<footer>
    <p>© 2024 ANERS</p>
</footer>
```

### Daftar lengkap tag semantik HTML5:

```html
<!-- STRUKTUR HALAMAN -->
<header>    <!-- Header halaman atau section. Bisa ada lebih dari satu. -->
<nav>       <!-- Blok navigasi utama -->
<main>      <!-- Konten utama. HANYA SATU per halaman. -->
<aside>     <!-- Konten sampingan: sidebar, callout, info terkait -->
<footer>    <!-- Footer halaman atau section -->
<section>   <!-- Pengelompokan konten tematik (perlu heading di dalamnya) -->
<article>   <!-- Konten mandiri: artikel blog, postingan, komentar, widget -->

<!-- KONTEN BERMAKNA -->
<figure>            <!-- Gambar, diagram, atau ilustrasi yang direferensikan -->
<figcaption>        <!-- Keterangan figure -->
<time datetime="">  <!-- Tanggal/waktu yang bisa dibaca mesin -->
<address>           <!-- Info kontak si penulis/pemilik -->
<details>           <!-- Konten yang bisa di-expand/collapse -->
<summary>           <!-- Ringkasan/header dari <details> -->
<dialog>            <!-- Dialog/modal window bawaan browser -->
<mark>              <!-- Teks yang di-highlight karena relevan -->
<del datetime="">   <!-- Teks yang dihapus (dengan tanggal jika perlu) -->
<ins datetime="">   <!-- Teks yang ditambahkan -->
```

### Layout halaman yang benar — contoh nyata:

```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Blog ANERS — Artikel Tech Indonesia</title>
    <meta name="description" content="Blog tentang web development dan AI dari Indonesia">
</head>
<body>

    <header>
        <a href="/" aria-label="ANERS — Halaman Utama">
            <img src="logo.svg" alt="ANERS" height="40" width="120">
        </a>

        <!-- Tombol hamburger menu untuk mobile -->
        <button type="button"
                aria-expanded="false"
                aria-controls="menu-utama"
                id="hamburger-btn">
            Menu
        </button>

        <nav id="menu-utama" aria-label="Navigasi utama">
            <ul>
                <li><a href="/" aria-current="page">Home</a></li>
                <li><a href="/artikel">Artikel</a></li>
                <li><a href="/tentang">Tentang</a></li>
                <li><a href="/kontak">Kontak</a></li>
            </ul>
        </nav>
    </header>

    <main>

        <!-- Breadcrumb navigasi -->
        <nav aria-label="Breadcrumb">
            <ol>
                <li><a href="/">Home</a></li>
                <li><a href="/artikel">Artikel</a></li>
                <li aria-current="page">Belajar HTML dari Nol</li>
            </ol>
        </nav>

        <article>
            <header>
                <h1>Belajar HTML dari Nol — Panduan Lengkap 2024</h1>
                <p>
                    Ditulis oleh <a href="/author/rixz" rel="author">Rixz</a> •
                    <time datetime="2024-11-15" pubdate>15 November 2024</time> •
                    Waktu baca: 12 menit
                </p>
            </header>

            <section id="pendahuluan">
                <h2>Pendahuluan</h2>
                <p>HTML adalah fondasi dari semua halaman web...</p>
            </section>

            <section id="apa-itu-html">
                <h2>Apa itu HTML?</h2>
                <p>HTML singkatan dari...</p>

                <aside>
                    <h3>Tahukah kamu?</h3>
                    <p>HTML pertama kali dikembangkan oleh Tim Berners-Lee pada 1991.</p>
                </aside>
            </section>

            <footer>
                <p>Tags:
                    <a href="/tag/html" rel="tag">HTML</a>,
                    <a href="/tag/web" rel="tag">Web Development</a>
                </p>
            </footer>
        </article>

        <!-- Komentar — juga bisa pakai article -->
        <section aria-label="Komentar pembaca">
            <h2>3 Komentar</h2>

            <article id="komentar-1">
                <header>
                    <strong>Budi</strong> •
                    <time datetime="2024-11-16">16 November 2024</time>
                </header>
                <p>Artikelnya sangat membantu, terima kasih!</p>
            </article>
        </section>

    </main>

    <aside aria-label="Artikel terkait dan info tambahan">
        <section>
            <h2>Artikel Terkait</h2>
            <nav aria-label="Artikel terkait">
                <ul>
                    <li><a href="/css-dasar">Belajar CSS dari Nol</a></li>
                    <li><a href="/js-dasar">JavaScript untuk Pemula</a></li>
                </ul>
            </nav>
        </section>
    </aside>

    <footer>
        <nav aria-label="Navigasi footer">
            <ul>
                <li><a href="/privacy">Kebijakan Privasi</a></li>
                <li><a href="/syarat">Syarat & Ketentuan</a></li>
            </ul>
        </nav>
        <address>
            Dibuat oleh <a href="mailto:rixz@aners.dev">Rixz</a> •
            Jakarta, Indonesia
        </address>
        <p>© 2024 ANERS — AI-Native Engineering & Research Systems</p>
    </footer>

</body>
</html>
```

---

## 13. HTML5 — Fitur Modern

### Data Attributes — Simpan Data Kustom di Elemen

```html
<!-- Simpan data apapun menggunakan prefix data-* -->
<div class="kartu-produk"
     data-id="prod-001"
     data-harga="150000"
     data-stok="42"
     data-kategori="hosting"
     data-diskon="0.2">
    <h3>Hosting Basic</h3>
    <p>Rp 150.000/bulan</p>
    <button class="btn-beli">Beli Sekarang</button>
</div>
```

```javascript
// Akses data attributes via JavaScript
const kartu = document.querySelector('.kartu-produk');

// via dataset (camelCase otomatis)
console.log(kartu.dataset.id);          // "prod-001"
console.log(kartu.dataset.harga);       // "150000" (string, bukan number)
console.log(kartu.dataset.stok);        // "42"

// Set nilai baru
kartu.dataset.stok = "41";

// Hapus data attribute
delete kartu.dataset.diskon;

// via getAttribute (nama asli dengan dash)
console.log(kartu.getAttribute('data-kategori'));  // "hosting"
```

### `<dialog>` — Modal Bawaan HTML (tanpa JavaScript eksternal)

```html
<dialog id="modal-konfirmasi" aria-labelledby="modal-judul">
    <h2 id="modal-judul">Konfirmasi Hapus</h2>
    <p>Apakah lo yakin mau menghapus data ini? Tindakan ini tidak bisa dibatalkan.</p>
    <div class="modal-actions">
        <button autofocus
                onclick="document.getElementById('modal-konfirmasi').close('cancel')">
            Batal
        </button>
        <button onclick="document.getElementById('modal-konfirmasi').close('confirm')">
            Ya, Hapus
        </button>
    </div>
</dialog>

<button onclick="document.getElementById('modal-konfirmasi').showModal()">
    Hapus Data
</button>

<script>
    const modal = document.getElementById('modal-konfirmasi');
    modal.addEventListener('close', () => {
        if (modal.returnValue === 'confirm') {
            console.log('User konfirmasi hapus');
        } else {
            console.log('User batal');
        }
    });
</script>
```

### `<details>` & `<summary>` — Accordion Tanpa JavaScript

```html
<details>
    <summary>Apa itu HTML?</summary>
    <div class="details-content">
        <p>HTML (HyperText Markup Language) adalah bahasa markup standar
        untuk membuat halaman web. Klik untuk expand/collapse 
        tanpa JavaScript!</p>
    </div>
</details>

<details open>  <!-- open = terbuka secara default -->
    <summary>Apa itu CSS?</summary>
    <p>CSS (Cascading Style Sheets) adalah bahasa untuk mendeskripsikan
    tampilan dokumen HTML.</p>
</details>

<!-- Event listener jika dibutuhkan -->
<script>
    document.querySelectorAll('details').forEach(detail => {
        detail.addEventListener('toggle', () => {
            console.log('Status:', detail.open ? 'buka' : 'tutup');
        });
    });
</script>
```

### `<template>` — HTML Reusable yang Tidak Di-render

```html
<!-- Template tidak ditampilkan browser sampai di-clone via JS -->
<template id="kartu-template">
    <article class="kartu">
        <img class="kartu__gambar" src="" alt="">
        <div class="kartu__konten">
            <h3 class="kartu__judul"></h3>
            <p class="kartu__deskripsi"></p>
            <a class="kartu__link btn">Lihat Detail</a>
        </div>
    </article>
</template>

<!-- Container untuk kartu -->
<div id="grid-kartu" class="kartu-grid"></div>

<script>
    const data = [
        { judul: "ANERS Bot", deskripsi: "Bot AI otomatis", link: "/bot", gambar: "bot.jpg" },
        { judul: "Aria c11", deskripsi: "AI Chat Platform", link: "/aria", gambar: "aria.jpg" },
    ];

    const template = document.getElementById('kartu-template');
    const grid = document.getElementById('grid-kartu');

    data.forEach(item => {
        const clone = template.content.cloneNode(true);  // deep clone
        clone.querySelector('.kartu__gambar').src = item.gambar;
        clone.querySelector('.kartu__gambar').alt = item.judul;
        clone.querySelector('.kartu__judul').textContent = item.judul;
        clone.querySelector('.kartu__deskripsi').textContent = item.deskripsi;
        clone.querySelector('.kartu__link').href = item.link;
        grid.appendChild(clone);
    });
</script>
```

### `<progress>` & `<meter>`

```html
<!-- Progress — kemajuan task yang sedang berjalan -->
<label for="upload-progress">Upload file:</label>
<progress id="upload-progress" max="100" value="68">68%</progress>
<!-- Jika tidak ada value → indeterminate (animasi loading) -->
<progress>Sedang memproses...</progress>

<!-- Meter — nilai terukur dalam range yang diketahui -->
<label for="disk-usage">Penggunaan Disk:</label>
<meter id="disk-usage"
       min="0" max="100"
       low="60" high="80" optimum="20"
       value="85">
    85%
</meter>
<!-- value > high → warna kuning/merah (tergantung browser) -->
```

### Atribut HTML Modern yang Berguna:

```html
<!-- contenteditable — buat elemen bisa diedit langsung -->
<div contenteditable="true" id="editor">
    Klik teks ini untuk mengedit langsung di browser.
</div>

<!-- spellcheck — aktifkan cek ejaan -->
<textarea spellcheck="true" lang="id">Tulis di sini...</textarea>

<!-- translate — tandai untuk tidak diterjemahkan (nama brand, kode) -->
<span translate="no">ANERS Platform</span>

<!-- draggable — aktifkan drag & drop -->
<div draggable="true" id="item-1">Drag item ini</div>

<!-- loading lazy — untuk gambar dan iframe -->
<img src="foto.jpg" alt="Foto" loading="lazy">
<iframe src="https://map.embed" loading="lazy" title="Peta"></iframe>

<!-- decoding — cara decode gambar -->
<img src="foto.jpg" alt="Foto" decoding="async">

<!-- fetchpriority — prioritas fetch resource -->
<img src="hero.jpg" alt="Hero" fetchpriority="high">  <!-- LCP image -->
<img src="footer-logo.jpg" alt="Logo" fetchpriority="low">

<!-- inputmode — keyboard yang muncul di mobile -->
<input type="text" inputmode="numeric" pattern="[0-9]*">  <!-- keyboard angka -->
<input type="text" inputmode="email">      <!-- keyboard email -->
<input type="text" inputmode="url">        <!-- keyboard URL -->
<input type="text" inputmode="tel">        <!-- keyboard telepon -->
<input type="text" inputmode="search">     <!-- keyboard pencarian -->
```

---

# 🟦 BAGIAN 2 — CSS

## 14. Apa itu CSS?

Masih ingat analogi rumah? HTML itu dindingnya. Nah **CSS** itu yang ngasih cat warna, pilih furniture, atur pencahayaan, dan bikin tata letak ruangan.

**CSS** singkatan dari **Cascading Style Sheets**.
- **Cascading** = aturan mengalir dan bisa saling menimpa (ada hierarki)
- **Style** = tampilan visual
- **Sheets** = lembaran aturan styling

Tanpa CSS, semua website keliatan kayak dokumen teks lama — teks hitam, background putih, link biru underline. CSS yang bikin web jadi indah dan berkarakter.

### Sintaks dasar CSS:

```css
/* Ini komentar CSS */

selektor {
    properti: nilai;
    properti-lain: nilai-lain;
}
```

Contoh nyata:
```css
/* Semua <h1> berwarna amber dan ukuran 2.5rem */
h1 {
    color: #f59e0b;
    font-size: 2.5rem;
    font-weight: 700;
}

/* Semua elemen dengan class "kartu" */
.kartu {
    background-color: #1e293b;
    border: 1px solid rgba(255,255,255,0.08);
    border-radius: 12px;
    padding: 24px;
    transition: transform 0.2s ease;
}

.kartu:hover {
    transform: translateY(-4px);
}
```

---

## 15. 3 Cara Pakai CSS

### Cara 1: Inline CSS
```html
<h1 style="color: #f59e0b; font-size: 2rem;">Judul Amber</h1>
<p style="background: #1e293b; padding: 16px; color: white;">Teks di atas background gelap</p>
```

**Kapan dipakai:** Hampir tidak pernah. Hanya untuk testing cepat atau nilai dinamis via JavaScript.

**Masalah inline CSS:**
- Tidak bisa pakai pseudo-class (`:hover`, `:focus`, `:nth-child`)
- Tidak bisa dibuat responsive (tidak bisa pakai media query)
- Susah di-maintain — harus ubah satu per satu di tiap elemen
- Tidak bisa di-cache browser
- Spesifisitas sangat tinggi — susah di-override

### Cara 2: Internal CSS
```html
<!DOCTYPE html>
<html>
<head>
    <style>
        body {
            font-family: sans-serif;
            background: #0f172a;
            color: #e2e8f0;
        }
        h1 { color: #f59e0b; }
    </style>
</head>
<body>
    <h1>Judul</h1>
</body>
</html>
```

**Kapan dipakai:** Email HTML, prototyping, halaman single-page yang sangat sederhana.

### Cara 3: External CSS — ✅ Selalu Gunakan Ini
```html
<!-- Di file HTML, di dalam <head>, sebelum </head> -->
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Judul</title>
    <!-- Link ke file CSS eksternal -->
    <link rel="stylesheet" href="style.css">
    <!-- Bisa lebih dari satu file CSS -->
    <link rel="stylesheet" href="components.css">
</head>
```

```css
/* file: style.css */
body {
    font-family: sans-serif;
    background: #0f172a;
    color: #e2e8f0;
}

h1 { color: #f59e0b; }
```

**Kenapa ini terbaik:**
- Satu file CSS bisa mengatur ratusan halaman HTML
- Browser cache CSS → website jauh lebih cepat di kunjungan berikutnya
- Pemisahan bersih antara struktur (HTML) dan tampilan (CSS)
- Mudah di-maintain dan dikembangkan secara tim

### Urutan prioritas CSS (Cascade):

```
Inline style         → Paling kuat (specificity: 1,0,0,0)
↓
<style> internal     → Kuat (lebih kuat jika ditulis belakangan)
↓
File .css external   → Normal
↓
Browser default      → Paling lemah
```

Dalam level yang sama, **yang ditulis belakangan menang:**
```css
p { color: red; }
p { color: blue; }    /* INI yang dipakai — ditulis belakangan */
```

---

## 16. Selektor — Incaran yang Tepat

Selektor adalah cara lo menarget elemen HTML mana yang mau diubah tampilannya.

### Selektor Dasar:

```css
/* 1. ELEMENT SELECTOR — target semua tag jenis tertentu */
p      { color: #94a3b8; line-height: 1.6; }
h1     { font-size: 3rem; }
button { cursor: pointer; }
input  { outline: none; }

/* 2. CLASS SELECTOR — target elemen dengan class tertentu */
/* Diawali tanda titik . */
.kartu      { background: #1e293b; border-radius: 12px; }
.hidden     { display: none; }
.teks-amber { color: #f59e0b; }

/* 3. ID SELECTOR — target elemen dengan id tertentu */
/* Diawali tanda pagar # */
#navbar  { position: fixed; top: 0; }
#hero    { min-height: 100vh; }

/* 4. UNIVERSAL SELECTOR — target SEMUA elemen */
* { box-sizing: border-box; }

/* 5. GROUP SELECTOR — target beberapa sekaligus, pisah koma */
h1, h2, h3, h4, h5, h6 {
    font-family: 'Playfair Display', Georgia, serif;
    line-height: 1.2;
}

button, input, textarea, select {
    font-family: inherit;
}
```

### Selektor Kombinasi:

```css
/* DESCENDANT — B di dalam A (tidak harus langsung) */
.nav a { text-decoration: none; color: inherit; }
/* Artinya: semua <a> di dalam elemen .nav, di semua level */

/* CHILD (>) — B yang LANGSUNG anak dari A */
.nav > li { display: inline-block; }
/* Artinya: hanya <li> yang langsung anak .nav,
            bukan <li> yang ada di dalam .nav .submenu */

/* ADJACENT SIBLING (+) — B yang langsung setelah A (satu induk) */
h2 + p { font-size: 1.1rem; color: #94a3b8; }
/* Artinya: <p> pertama yang langsung setelah <h2> */

/* GENERAL SIBLING (~) — semua B yang menjadi saudara setelah A */
h2 ~ p { text-indent: 1em; }
/* Artinya: semua <p> yang menjadi saudara setelah <h2> */
```

### Selektor Atribut:

```css
/* Punya atribut ini */
[disabled]       { opacity: 0.5; cursor: not-allowed; }
[required]       { border-left: 3px solid #f59e0b; }

/* Nilai atribut sama persis */
[type="submit"]  { background: #f59e0b; color: #000; }
[type="text"]    { border: 1px solid #334155; }
[lang="id"]      { quotes: '"' '"' "'" "'"; }

/* Nilai mengandung kata (dibatasi spasi) */
[class~="kartu"] { border-radius: 12px; }

/* Nilai diawali dengan... */
[href^="https"]  { /* link https */ }
[href^="mailto"] { /* link email */ }
[src^="data:"]   { /* gambar base64 */ }

/* Nilai diakhiri dengan... */
[href$=".pdf"]   { /* link ke PDF */ }
[href$=".zip"]   { /* link ke zip */ }
[src$=".svg"]    { /* gambar SVG */ }

/* Nilai mengandung substring... */
[href*="github.com"] { /* link ke github */ }
[class*="btn-"]      { /* class yang ada "btn-" di dalamnya */ }
```

### Selektor Atribut — contoh nyata yang berguna:

```css
/* Gambar tanpa alt text — highlight visual untuk debugging */
img:not([alt]),
img[alt=""] {
    outline: 4px solid red;
    outline-offset: 2px;
}

/* Link eksternal — kasih visual indikator */
a[href^="http"]:not([href*="aners.dev"])::after {
    content: " ↗";
    font-size: 0.75em;
    opacity: 0.6;
    vertical-align: super;
}

/* Input disabled — styling konsisten */
input[disabled],
textarea[disabled],
button[disabled] {
    opacity: 0.4;
    cursor: not-allowed;
    user-select: none;
}

/* Download link — kasih icon */
a[download]::before {
    content: "⬇ ";
}
```

### Specificity — Siapa yang Menang?

Specificity menentukan aturan CSS mana yang dipakai ketika ada konflik.

```
Cara hitung: (a, b, c, d)

a = Inline style        → nilainya 1,0,0,0
b = ID selector (#id)   → nilainya 0,1,0,0
c = Class, pseudo-class, atribut → 0,0,1,0
d = Element, pseudo-element → 0,0,0,1
```

```css
/* Contoh dengan skor specificity */
*              { }                /* 0,0,0,0 — paling lemah */
p              { }                /* 0,0,0,1 */
.kartu         { }                /* 0,0,1,0 */
p.highlight    { }                /* 0,0,1,1 */
#hero          { }                /* 0,1,0,0 */
#hero p        { }                /* 0,1,0,1 */
#hero .kartu   { }                /* 0,1,1,0 */
style="..."    /* inline */       /* 1,0,0,0 — paling kuat */
```

```html
<!-- Contoh konflik dan pemenangnya -->
<p class="teks" id="intro" style="color: pink;">Teks ini</p>
```

```css
p       { color: blue; }     /* 0,0,0,1 → kalah */
.teks   { color: green; }    /* 0,0,1,0 → kalah */
#intro  { color: orange; }   /* 0,1,0,0 → kalah dari inline */
/* style="color: pink" → 1,0,0,0 → MENANG → teks berwarna pink */
```

```css
/* !important — menang dari semua, termasuk inline style */
/* JANGAN disalahgunakan. Tanda arsitektur CSS yang bermasalah. */
p { color: red !important; }
```

> ⚠️ **Aturan emas:** Kalau lo sering butuh `!important`, itu tanda struktur CSS lo bermasalah dan perlu direfaktor. `!important` seharusnya jarang sekali dipakai.

---

## 17. Box Model — Inti dari Segalanya

Ini konsep **PALING FUNDAMENTAL** di CSS. Pahami ini, lo pahami CSS.

**Setiap elemen HTML adalah sebuah kotak persegi.** Kotak itu punya 4 lapisan dari dalam ke luar:

```
╔══════════════════════════════════════════════════╗
║                     MARGIN                        ║  ← Jarak ke elemen LAIN
║   (transparan, tidak berwarna)                    ║
║  ╔══════════════════════════════════════════════╗ ║
║  ║                   BORDER                     ║ ║  ← Garis tepi / bingkai
║  ║  ╔══════════════════════════════════════════╗║ ║
║  ║  ║                PADDING                   ║║ ║  ← Ruang antara konten & border
║  ║  ║  ╔══════════════════════════════════════╗║║ ║
║  ║  ║  ║              CONTENT                 ║║║ ║  ← Isi elemen (teks, gambar)
║  ║  ║  ║   ← width × height berlaku di sini → ║║║ ║
║  ║  ║  ╚══════════════════════════════════════╝║║ ║
║  ║  ╚══════════════════════════════════════════╝║ ║
║  ╚══════════════════════════════════════════════╝ ║
╚══════════════════════════════════════════════════╝
```

### Properti box model:

```css
.kotak {
    /* ── CONTENT ── */
    width: 300px;
    height: 150px;
    min-width: 200px;     /* lebar minimal */
    max-width: 600px;     /* lebar maksimal */
    min-height: 100px;    /* tinggi minimal */
    max-height: 400px;    /* tinggi maksimal */

    /* ── PADDING (jarak konten ke border) ── */
    padding: 20px;                        /* semua sisi sama */
    padding: 10px 20px;                   /* atas-bawah | kiri-kanan */
    padding: 10px 20px 15px 25px;         /* atas | kanan | bawah | kiri */
    padding-top: 10px;
    padding-right: 20px;
    padding-bottom: 15px;
    padding-left: 25px;
    /* shorthand modern */
    padding-block: 10px 15px;            /* atas | bawah */
    padding-inline: 20px 25px;           /* kiri | kanan */

    /* ── BORDER ── */
    border: 2px solid #334155;            /* ukuran | gaya | warna */
    border-radius: 8px;                   /* sudut melengkung (semua sudut) */
    border-radius: 8px 0 8px 0;          /* kiri-atas | kanan-atas | kanan-bawah | kiri-bawah */
    border-radius: 50%;                   /* lingkaran (jika lebar = tinggi) */
    border-top: 3px dashed #f59e0b;       /* border per sisi */
    border-bottom: none;
    /* gaya border: solid | dashed | dotted | double | groove | ridge | inset | outset */

    /* ── MARGIN (jarak ke elemen lain) ── */
    margin: 20px;                         /* semua sisi */
    margin: 10px auto;                    /* atas-bawah: 10px, kiri-kanan: auto (center horizontal) */
    margin: 0 auto;                       /* centering horizontal klasik */
    margin-top: 10px;
    margin-bottom: 32px;
    margin-left: 0;
    margin-right: auto;                   /* dorong ke kiri */

    /* Margin negatif — bisa overlapping! */
    margin-top: -20px;                    /* overlap elemen di atasnya */
}
```

### `box-sizing` — HARUS LO TAHU DAN SELALU PAKAI:

```css
/* ── DEFAULT (content-box) — MEMBINGUNGKAN ── */
/* width/height TIDAK termasuk padding dan border */
.kotak-default {
    width: 300px;
    padding: 20px;       /* kiri 20 + kanan 20 = 40 */
    border: 5px solid;   /* kiri 5 + kanan 5 = 10 */
    /* Lebar TOTAL yang ditempati = 300 + 40 + 10 = 350px */
    /* Beda dari nilai width yang lo tulis! */
}

/* ── border-box — INTUITIF & DIREKOMENDASIKAN ── */
/* width/height SUDAH termasuk padding dan border */
.kotak-border-box {
    box-sizing: border-box;
    width: 300px;
    padding: 20px;
    border: 5px solid;
    /* Lebar TOTAL = 300px (sesuai yang lo tulis!) */
    /* Ruang content = 300 - 40 - 10 = 250px */
}

/* ✅ SELALU TERAPKAN INI DI AWAL FILE CSS — GLOBAL RESET */
*,
*::before,
*::after {
    box-sizing: border-box;
}
```

### Margin Collapsing — yang sering bikin bingung:

```css
/*
    MARGIN COLLAPSING terjadi antara margin vertikal (atas-bawah)
    dua elemen BLOCK yang berdekatan.

    Margin yang dipakai = yang TERBESAR (bukan dijumlah).
*/

.artikel { margin-bottom: 40px; }
.artikel-berikutnya { margin-top: 24px; }

/*
    Jarak antara keduanya BUKAN 64px (40+24).
    Tapi 40px (yang lebih besar).
    Inilah yang disebut margin collapsing.
*/
```

Cara menghindari margin collapsing:
```css
/* Tambahkan padding ke parent (bukan margin) */
.parent { padding-top: 1px; }  /* sedikit saja sudah cukup */

/* Atau gunakan display flex/grid pada parent */
.parent { display: flex; flex-direction: column; }

/* Atau gunakan gap pada flex/grid parent */
.parent { display: flex; flex-direction: column; gap: 40px; }
```

### Outline vs Border:

```css
/* Border — bagian dari box model, mengambil ruang */
.tombol { border: 2px solid #f59e0b; }

/* Outline — TIDAK mengambil ruang, untuk focus state */
.tombol:focus {
    outline: 2px solid #f59e0b;
    outline-offset: 2px;   /* jarak outline dari elemen */
}

/* ❌ JANGAN PERNAH HAPUS OUTLINE TANPA GANTINYA */
/* Ini merusak aksesibilitas keyboard navigation */
* { outline: none; }   /* BERBAHAYA! */

/* ✅ BOLEH mengubah tampilan outline, tapi jangan dihapus */
:focus-visible {
    outline: 2px solid #f59e0b;
    outline-offset: 3px;
}
```

---

## 18. Teks & Font — Tipografi Web

Tipografi yang bagus berkontribusi 70% terhadap kesan visual keseluruhan desain. Ini bukan hiperbola.

### Load Font dari Google Fonts:

```html
<!-- Di <head>, SEBELUM link ke file CSS -->
<!-- preconnect — koneksi awal biar lebih cepat -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>

<!-- Load beberapa font sekaligus, weight yang dipakai saja -->
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:ital,wght@0,300;0,400;0,600;1,400&family=JetBrains+Mono:wght@400;600&display=swap" rel="stylesheet">
```

```css
/* Lalu di CSS, pakai langsung */
:root {
    --font-display: 'Bebas Neue', 'Arial Black', sans-serif;
    --font-body: 'DM Sans', Helvetica, sans-serif;
    --font-mono: 'JetBrains Mono', 'Courier New', monospace;
}

h1, h2, h3 { font-family: var(--font-display); }
body        { font-family: var(--font-body); }
code, pre   { font-family: var(--font-mono); }
```

### `font-display: swap` — kenapa penting:

```css
/* Jika font dari Google Fonts, parameter display=swap sudah otomatis.
   Tapi jika lo host font sendiri (@font-face): */
@font-face {
    font-family: 'DM Sans';
    src: url('/fonts/dm-sans.woff2') format('woff2');
    font-weight: 400;
    font-style: normal;
    font-display: swap;  /* ← tampilkan font sistem dulu, ganti setelah font web load */
}

/*
    font-display options:
    auto     — biarkan browser yang memutuskan
    block    — blok render sampai font selesai load (bisa FOIT = Flash of Invisible Text)
    swap     — tampilkan font fallback dulu, ganti setelah selesai (bisa FOUT = Flash of Unstyled Text)
    fallback — singkat block period, lalu swap
    optional — singkat block period, tidak swap jika lambat
*/
```

### Properti font dasar:

```css
.teks {
    /* Font family — selalu sediakan fallback stack */
    font-family: 'DM Sans', Helvetica, Arial, sans-serif;

    /* Ukuran font */
    font-size: 16px;        /* pixels — absolut */
    font-size: 1rem;        /* relative to root (html font-size) — DIREKOMENDASIKAN */
    font-size: 1.2em;       /* relative to PARENT element — hati-hati dengan nesting */
    font-size: 2vw;         /* relative to viewport width */
    font-size: clamp(1rem, 2.5vw, 1.5rem);  /* min | preferred | max — fluid typography */

    /* Ketebalan font */
    font-weight: 100;   /* Thin */
    font-weight: 300;   /* Light */
    font-weight: 400;   /* Normal / Regular */
    font-weight: 500;   /* Medium */
    font-weight: 600;   /* SemiBold */
    font-weight: 700;   /* Bold */
    font-weight: 800;   /* ExtraBold */
    font-weight: 900;   /* Black */
    /* Gunakan angka, bukan kata kunci bold/normal — lebih presisi */

    /* Gaya font */
    font-style: normal;
    font-style: italic;
    font-style: oblique;

    /* Tinggi baris — ukuran tanpa satuan (multiplier) lebih baik */
    line-height: 1;      /* tanpa spasi antar baris */
    line-height: 1.5;    /* 1.5x ukuran font — nyaman untuk body teks */
    line-height: 1.6;    /* ideal untuk paragraf panjang */
    line-height: 1.2;    /* untuk heading besar */

    /* Jarak antar huruf */
    letter-spacing: 0.05em;   /* agak renggang */
    letter-spacing: -0.02em;  /* lebih rapat (sering untuk heading display) */
    letter-spacing: 0.15em;   /* sangat renggang (all caps label) */

    /* Jarak antar kata */
    word-spacing: 0.05em;

    /* Shorthand font */
    /* font: style weight size/line-height family */
    font: italic 700 1.2rem/1.4 'DM Sans', sans-serif;
}
```

### Properti teks:

```css
.judul {
    /* Transformasi */
    text-transform: uppercase;   /* SEMUA KAPITAL */
    text-transform: lowercase;   /* semua kecil */
    text-transform: capitalize;  /* Setiap Kata Kapital Depan */
    text-transform: none;        /* default */

    /* Perataan */
    text-align: left;            /* default untuk LTR */
    text-align: center;
    text-align: right;
    text-align: justify;         /* rata kanan-kiri (hati-hati di mobile) */
    text-align: start;           /* LTR = kiri, RTL = kanan — lebih baik untuk multibahasa */

    /* Dekorasi */
    text-decoration: none;              /* hapus underline (sering untuk link) */
    text-decoration: underline;
    text-decoration: underline dotted;  /* underline gaya dotted */
    text-decoration: underline wavy #f59e0b 2px;  /* warna dan ketebalan kustom */
    text-decoration: line-through;      /* coret */

    /* Shadow */
    text-shadow: 2px 4px 8px rgba(0,0,0,0.5);
    /* x-offset | y-offset | blur-radius | warna */

    /* Multiple shadow */
    text-shadow:
        0 0 20px rgba(245,158,11,0.5),
        0 0 40px rgba(245,158,11,0.2);

    /* Potong teks panjang dengan ellipsis */
    white-space: nowrap;         /* jangan wrap ke baris baru */
    overflow: hidden;            /* sembunyikan yang melebihi */
    text-overflow: ellipsis;     /* tambahkan "..." di akhir */

    /* Potong banyak baris (multi-line ellipsis) */
    display: -webkit-box;
    -webkit-line-clamp: 3;       /* batasi 3 baris */
    -webkit-box-orient: vertical;
    overflow: hidden;

    /* Indentasi baris pertama */
    text-indent: 2em;

    /* Balancing teks (baru, CSS 2023) */
    text-wrap: balance;          /* distribusi teks yang seimbang */
    text-wrap: pretty;           /* hindari orphan di akhir paragraf */
}
```

### Sistem skala tipografi yang konsisten:

```css
:root {
    /* Skala berbasis rasio 1.25 (Major Third) */
    /* Base: 16px = 1rem */
    --text-xs:    0.64rem;    /* ≈ 10px — label sangat kecil */
    --text-sm:    0.8rem;     /* ≈ 13px — caption, helper text */
    --text-base:  1rem;       /* 16px — body text */
    --text-md:    1.25rem;    /* 20px — sub-lead */
    --text-lg:    1.563rem;   /* 25px — lead paragraph */
    --text-xl:    1.953rem;   /* 31px — h4 / h3 kecil */
    --text-2xl:   2.441rem;   /* 39px — h3 / h2 kecil */
    --text-3xl:   3.052rem;   /* 49px — h2 / h1 kecil */
    --text-4xl:   3.815rem;   /* 61px — h1 */
    --text-display: clamp(3rem, 8vw, 6rem);  /* hero display */
}

/* Penerapan */
body    { font-size: var(--text-base); }
small   { font-size: var(--text-sm); }
h6      { font-size: var(--text-md); }
h5      { font-size: var(--text-lg); }
h4      { font-size: var(--text-xl); }
h3      { font-size: var(--text-2xl); }
h2      { font-size: var(--text-3xl); }
h1      { font-size: var(--text-4xl); }
.hero-title { font-size: var(--text-display); }
```

### `em` vs `rem` — ini penting dipahami:

```css
/* Setup */
html { font-size: 16px; }  /* Root = 16px */

.parent {
    font-size: 20px;
}

/* em — relative terhadap font-size ELEMEN ITU SENDIRI */
.child-em {
    font-size: 1.5em;   /* 1.5 × 20px (parent) = 30px */
    padding: 1em;       /* 1 × 30px (font-size elemen ini) = 30px */
    margin-bottom: 0.5em; /* 0.5 × 30px = 15px */
}

/* rem — relative terhadap font-size ROOT (html) — KONSISTEN */
.child-rem {
    font-size: 1.5rem;  /* 1.5 × 16px (root) = 24px — SELALU sama */
    padding: 1rem;      /* 1 × 16px = 16px — tidak berubah dengan nesting */
}

/*
    REKOMENDASI:
    font-size   → rem (konsisten, tidak terpengaruh nesting)
    padding     → rem atau em (em jika mau scale proporsional dengan font)
    margin      → rem (konsisten)
    border      → px (tidak perlu scale)
    border-radius → px atau em
    media query → em (untuk aksesibilitas browser zoom)
*/
```

---

## 19. Warna & Background

### Semua format warna di CSS:

```css
.elemen {
    /* Named colors — 140+ nama */
    color: tomato;
    color: royalblue;
    color: mediumseagreen;
    color: cornflowerblue;

    /* HEX — paling umum dipakai */
    color: #ff6600;       /* oranye — format lengkap */
    color: #f60;          /* shorthand — tiap karakter dobel → #ff6600 */
    color: #ff660080;     /* 8 digit — 2 terakhir = alpha (00=transparan, ff=opak) */

    /* RGB */
    color: rgb(255, 102, 0);
    color: rgb(255 102 0);          /* spasi, tanpa koma — CSS modern */

    /* RGBA — A = alpha (0=transparan, 1=opak) */
    color: rgba(255, 102, 0, 0.5);      /* 50% transparan */
    color: rgba(0, 0, 0, 0.85);         /* hitam 85% */
    color: rgb(255 102 0 / 50%);        /* sintaks modern */

    /* HSL — Hue Saturation Lightness (paling intuitif untuk desainer) */
    /* Hue: 0-360 (derajat warna di color wheel) */
    /* Saturation: 0-100% (0% = abu-abu, 100% = penuh warna) */
    /* Lightness: 0-100% (0% = hitam, 50% = normal, 100% = putih) */
    color: hsl(24, 100%, 50%);      /* oranye */
    color: hsl(220, 70%, 50%);      /* biru */
    color: hsl(142, 71%, 45%);      /* hijau */

    /* HSLA — dengan alpha */
    color: hsla(24, 100%, 50%, 0.7);
    color: hsl(24 100% 50% / 70%);  /* sintaks modern */

    /* OKLCH — perceptually uniform, CSS modern (2023+) */
    /* L = lightness (0-1), C = chroma (0-0.4), H = hue (0-360) */
    color: oklch(0.7 0.15 145);     /* hijau yang enak di mata */
    color: oklch(0.65 0.2 30);      /* oranye */
}
```

### `hsl()` — kenapa ini bagus untuk desainer:

```css
/* Warna yang sama, variasi lightness */
.primary     { color: hsl(220, 70%, 50%); }  /* biru normal */
.primary-light { color: hsl(220, 70%, 70%); } /* biru terang */
.primary-dark  { color: hsl(220, 70%, 30%); } /* biru gelap */
/* Cukup ubah lightness (angka ketiga)! */

/* Warna yang sama, variasi saturation */
.vivid   { color: hsl(220, 100%, 50%); }  /* sangat vivid */
.muted   { color: hsl(220, 20%, 60%); }   /* pucat/muted */
/* Cukup ubah saturation (angka kedua)! */
```

### Background:

```css
.elemen {
    /* ── WARNA SOLID ── */
    background-color: #0f172a;
    background-color: rgba(255,255,255,0.05);  /* semi-transparan */

    /* ── GRADIENT LINEAR ── */
    background: linear-gradient(to right, #0f0c29, #302b63);
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);

    /* Dengan stops lebih kompleks */
    background: linear-gradient(
        to bottom,
        #0f172a 0%,
        #1e293b 40%,
        #0f172a 100%
    );

    /* Transparent gradient (untuk overlay di atas gambar) */
    background: linear-gradient(
        to bottom,
        transparent 0%,
        rgba(0,0,0,0.8) 100%
    );

    /* ── GRADIENT RADIAL ── */
    background: radial-gradient(circle at center, #1e293b, #0f172a);
    background: radial-gradient(ellipse at top left, #667eea 0%, transparent 60%);

    /* ── GRADIENT CONIC ── */
    background: conic-gradient(from 45deg, red, yellow, green, blue, red);

    /* ── GAMBAR BACKGROUND ── */
    background-image: url('bg.jpg');
    background-size: cover;           /* isi seluruh area (terpotong jika perlu) */
    background-size: contain;         /* seluruh gambar tampil (ada ruang kosong) */
    background-size: 400px 300px;     /* ukuran spesifik */
    background-size: 50% auto;        /* lebar 50%, tinggi otomatis */
    background-position: center center;
    background-position: top right;
    background-position: 20% 80%;
    background-repeat: no-repeat;     /* tidak diulang */
    background-repeat: repeat;        /* diulang (default) */
    background-repeat: repeat-x;      /* hanya horizontal */
    background-attachment: scroll;    /* scroll bersama halaman (default) */
    background-attachment: fixed;     /* fixed (parallax effect) */

    /* ── SHORTHAND BACKGROUND ── */
    /* image position/size repeat attachment color */
    background: url('bg.jpg') center/cover no-repeat fixed #0f172a;

    /* ── OVERLAY GAMBAR + WARNA ── */
    /* Background bisa tumpuk! Yang pertama = yang paling depan */
    background:
        linear-gradient(rgba(0,0,0,0.6), rgba(0,0,0,0.6)),
        url('hero.jpg') center/cover no-repeat;

    /* ── MULTIPLE BACKGROUNDS ── */
    background:
        url('noise.png') repeat,           /* layer terdepan */
        radial-gradient(circle at 20% 50%, rgba(99,102,241,0.15), transparent 50%),
        radial-gradient(circle at 80% 20%, rgba(245,158,11,0.1), transparent 50%),
        #0f172a;                           /* layer belakang */
}
```

### Properti lain yang menggunakan warna:

```css
.elemen {
    /* Box shadow */
    box-shadow: 0 4px 12px rgba(0,0,0,0.4);
    /* x | y | blur | spread | warna */
    box-shadow: 2px 4px 8px 0 rgba(0,0,0,0.3);

    /* Inner shadow */
    box-shadow: inset 0 2px 4px rgba(0,0,0,0.5);

    /* Multiple shadows */
    box-shadow:
        0 1px 2px rgba(0,0,0,0.3),
        0 8px 24px rgba(0,0,0,0.2),
        0 0 0 1px rgba(255,255,255,0.05);

    /* Glow effect */
    box-shadow: 0 0 20px rgba(245,158,11,0.4), 0 0 60px rgba(245,158,11,0.1);

    /* Opacity — mempengaruhi SELURUH elemen termasuk children */
    opacity: 0;      /* transparan total */
    opacity: 0.5;    /* 50% transparan */
    opacity: 1;      /* opak total (default) */

    /* Filter */
    filter: blur(4px);
    filter: brightness(0.8);
    filter: grayscale(100%);
    filter: drop-shadow(0 4px 8px rgba(0,0,0,0.5));
    filter: blur(2px) brightness(0.9) grayscale(50%);

    /* Backdrop filter — blur elemen di belakang */
    backdrop-filter: blur(12px);
    backdrop-filter: blur(8px) saturate(180%);
    -webkit-backdrop-filter: blur(12px);  /* Safari */
}
```

---

## 20. Display & Positioning — Posisi Elemen

### Property `display`:

```css
/* ── DISPLAY VALUES ── */

/* block — ambil full lebar parent, mulai baris baru */
/* Default untuk: div, p, h1-h6, section, article, header, footer, ul, ol */
.block { display: block; }

/* inline — ikut aliran teks, width/height tidak berlaku */
/* Default untuk: span, a, strong, em, img, button, input */
.inline { display: inline; }

/* inline-block — inline tapi width/height bisa diatur */
/* Berguna untuk: badge, tag, tombol dengan ukuran spesifik */
.inline-block {
    display: inline-block;
    width: 120px;
    height: 40px;
    vertical-align: middle;
}

/* none — sembunyikan elemen TOTAL (tidak ada di layout) */
.hidden { display: none; }

/* flex — layout 1 dimensi (bab 21) */
.flex { display: flex; }

/* grid — layout 2 dimensi (bab 22) */
.grid { display: grid; }

/* contents — elemen sendiri tidak dirender, hanya children-nya */
.wrapper { display: contents; }

/* table, table-row, table-cell — perilaku seperti tabel */
/* (jarang dipakai di era modern) */
```

**`display: none` vs metode lain untuk sembunyikan:**

| Cara | Ruang di Layout | Aksesibilitas |
|------|----------------|---------------|
| `display: none` | ❌ Tidak ada | Screen reader tidak membacanya |
| `visibility: hidden` | ✅ Masih ada | Screen reader tidak membacanya |
| `opacity: 0` | ✅ Masih ada | Screen reader MASIH membacanya |
| `height: 0; overflow: hidden` | ✅ Praktis tidak ada | Screen reader masih membacanya |

```css
/* Untuk elemen yang tersembunyi tapi perlu dibaca screen reader */
.sr-only {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    margin: -1px;
    overflow: hidden;
    clip: rect(0, 0, 0, 0);
    white-space: nowrap;
    border-width: 0;
}
```

### Property `position`:

```css
/* ── POSITION VALUES ── */

/* static — default. Ikut aliran normal dokumen.
   top/right/bottom/left/z-index TIDAK BERLAKU */
.a { position: static; }

/* relative — posisi digeser dari POSISI NORMALNYA.
   top/right/bottom/left berlaku.
   Elemen MASIH mengambil ruang di posisi aslinya. */
.b {
    position: relative;
    top: 10px;    /* geser 10px ke bawah dari posisi normal */
    left: -20px;  /* geser 20px ke kiri dari posisi normal */
}

/* absolute — diposisikan relatif terhadap ANCESTOR terdekat
   yang position-nya bukan static.
   Elemen TIDAK mengambil ruang di layout normal. */
.parent {
    position: relative;       /* ← menjadi anchor/reference */
    width: 300px;
    height: 200px;
}
.child-absolute {
    position: absolute;
    top: 0;
    right: 0;                /* pojok kanan atas parent */
}
.child-center {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);  /* centering trick */
}

/* fixed — diposisikan relatif terhadap VIEWPORT.
   Tetap di tempatnya saat halaman di-scroll. */
.navbar-fixed {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;        /* span full width */
    z-index: 100;
}
.fab {
    position: fixed;
    bottom: 24px;
    right: 24px;
    z-index: 50;
}

/* sticky — hybrid relative + fixed.
   Berperilaku relative SAMPAI mencapai titik tertentu,
   lalu berperilaku fixed. */
.header-sticky {
    position: sticky;
    top: 0;          /* nempel di top: 0 saat di-scroll ke titik itu */
    z-index: 50;
}
.sidebar-sticky {
    position: sticky;
    top: 80px;       /* nempel 80px dari atas (bawah navbar) */
    align-self: start; /* penting untuk grid/flex container */
}
```

### `z-index` — siapa yang tampil di depan:

```css
/*
    z-index hanya bekerja pada elemen yang position-nya
    relative, absolute, fixed, atau sticky.
    Nilai lebih besar = lebih di depan.
*/

.modal-backdrop { position: fixed; z-index: 300; }
.modal          { position: fixed; z-index: 301; }
.navbar         { position: fixed; z-index: 200; }
.dropdown       { position: absolute; z-index: 100; }
.tooltip        { position: absolute; z-index: 150; }

/* ✅ Best practice — pakai skala dan CSS variables */
:root {
    --z-base:     0;
    --z-raised:   10;
    --z-dropdown: 100;
    --z-sticky:   200;
    --z-modal:    300;
    --z-toast:    400;
    --z-overlay:  500;
}
```

### `overflow` — konten melebihi kotak:

```css
.kotak {
    width: 200px;
    height: 100px;

    overflow: visible;    /* default — konten meluber keluar kotak */
    overflow: hidden;     /* konten dipotong tepat di batas kotak */
    overflow: scroll;     /* selalu tampilkan scrollbar (meski tidak butuh) */
    overflow: auto;       /* scrollbar hanya jika diperlukan ← TERBAIK */
    overflow: clip;       /* seperti hidden tapi tidak buat stacking context */

    overflow-x: hidden;   /* sumbu horizontal */
    overflow-y: auto;     /* sumbu vertikal */
}

/* Kasus khusus: teks panjang di dalam container sempit */
.teks-terpotong {
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;   /* tampilkan "..." */
}
```

---

## 21. Flexbox — Tata Letak 1 Dimensi

Flexbox adalah sistem layout paling sering dipakai untuk mengatur elemen dalam **satu dimensi** — baris atau kolom.

### Konsep dasar:

```
FLEX CONTAINER (display: flex)
┌───────────────────────────────────────────────────────┐
│  FLEX ITEM 1  ││  FLEX ITEM 2  ││  FLEX ITEM 3  │    │
│               ││               ││               │    │
└───────────────────────────────────────────────────────┘
        ──────────────────────────────────→
                   MAIN AXIS (flex-direction: row)
        │
        ↓  CROSS AXIS
```

```html
<div class="container">    <!-- ← FLEX CONTAINER -->
    <div class="item">A</div>  <!-- ← FLEX ITEM -->
    <div class="item">B</div>
    <div class="item">C</div>
</div>
```

### Properti pada FLEX CONTAINER:

```css
.container {
    display: flex;   /* atau inline-flex */

    /* ── ARAH ── */
    flex-direction: row;              /* → horizontal (default) */
    flex-direction: row-reverse;      /* ← horizontal terbalik */
    flex-direction: column;           /* ↓ vertikal */
    flex-direction: column-reverse;   /* ↑ vertikal terbalik */

    /* ── WRAP ── */
    flex-wrap: nowrap;        /* semua dalam satu baris (default) */
    flex-wrap: wrap;          /* item pindah ke baris baru jika tidak muat */
    flex-wrap: wrap-reverse;  /* wrap tapi baris baru di atas */

    /* Shorthand: direction + wrap */
    flex-flow: row wrap;
    flex-flow: column nowrap;

    /* ── ALIGNMENT MAIN AXIS (justify-content) ── */
    justify-content: flex-start;      /* |ABC..........| (default) */
    justify-content: flex-end;        /* |..........ABC| */
    justify-content: center;          /* |.....ABC.....| */
    justify-content: space-between;   /* |A.....B.....C| */
    justify-content: space-around;    /* |..A....B....C..| */
    justify-content: space-evenly;    /* |...A...B...C...| */

    /* ── ALIGNMENT CROSS AXIS (align-items) ── */
    align-items: stretch;      /* item direntangkan mengisi tinggi container (default) */
    align-items: flex-start;   /* item sejajar di ujung awal cross axis */
    align-items: flex-end;     /* item sejajar di ujung akhir cross axis */
    align-items: center;       /* item di tengah cross axis */
    align-items: baseline;     /* item sejajar berdasarkan garis teks */

    /* ── ALIGNMENT MULTIPLE BARIS (align-content) ── */
    /* Hanya berlaku saat flex-wrap: wrap dan ada lebih dari 1 baris */
    align-content: flex-start;
    align-content: flex-end;
    align-content: center;
    align-content: space-between;
    align-content: space-around;
    align-content: stretch;    /* default */

    /* ── JARAK ANTAR ITEM (gap) ── */
    gap: 24px;              /* baris dan kolom sama */
    gap: 16px 24px;         /* row-gap | column-gap */
    row-gap: 16px;
    column-gap: 24px;
}
```

### Properti pada FLEX ITEM:

```css
.item {
    /* ── URUTAN TAMPIL ── */
    order: 0;     /* default — urutan di HTML */
    order: -1;    /* tampil paling awal */
    order: 1;     /* tampil setelah yang order: 0 */
    /* Tidak mengubah DOM, hanya tampilan visual */

    /* ── GROW — seberapa item bisa tumbuh mengisi ruang kosong ── */
    flex-grow: 0;     /* tidak tumbuh (default) */
    flex-grow: 1;     /* tumbuh proporsional dengan item lain yang flex-grow: 1 */
    flex-grow: 2;     /* tumbuh dua kali lipat dibanding flex-grow: 1 */

    /* ── SHRINK — seberapa item bisa menyusut saat ruang kurang ── */
    flex-shrink: 1;   /* menyusut proporsional (default) */
    flex-shrink: 0;   /* tidak boleh menyusut */
    flex-shrink: 2;   /* menyusut dua kali lebih cepat */

    /* ── BASIS — ukuran awal sebelum tumbuh/menyusut ── */
    flex-basis: auto;     /* ikut width/height (default) */
    flex-basis: 0;        /* mulai dari 0 */
    flex-basis: 200px;    /* ukuran awal 200px */
    flex-basis: 25%;      /* 25% dari container */

    /* ── SHORTHAND flex ── */
    /* flex: grow shrink basis */
    flex: 1;              /* setara: 1 1 0% — tumbuh dan menyusut proporsional */
    flex: 0 0 200px;      /* tidak tumbuh, tidak menyusut, lebar tetap 200px */
    flex: 1 1 auto;       /* tumbuh dan menyusut, ukuran awal auto */
    flex: none;           /* setara: 0 0 auto — fixed size */
    flex: 2;              /* grow 2 kali lebih cepat dari flex: 1 */

    /* ── SELF ALIGNMENT — override align-items untuk item ini saja ── */
    align-self: auto;         /* ikut align-items container (default) */
    align-self: flex-start;
    align-self: flex-end;
    align-self: center;
    align-self: stretch;
    align-self: baseline;
}
```

### Pattern Flexbox yang paling sering dipakai:

```css
/* ✨ 1. CENTERING SEMPURNA */
.center-content {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;   /* atau height tertentu */
}

/* ✨ 2. NAVBAR — logo kiri, menu kanan */
.navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 24px;
    height: 64px;
}

/* ✨ 3. CARD ROW — kartu berjajar, sama tinggi */
.card-row {
    display: flex;
    gap: 24px;
    flex-wrap: wrap;
}
.card {
    flex: 1 1 280px;   /* minimum 280px, boleh grow */
    /* ini auto-responsive! tidak butuh media query */
}

/* ✨ 4. STICKY FOOTER — footer tetap di bawah */
body {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
}
main {
    flex: 1;   /* main mengisi sisa ruang */
}
footer {
    /* tetap di bawah, ukuran natural */
}

/* ✨ 5. DORONG ITEM KE UJUNG */
.nav {
    display: flex;
    align-items: center;
    gap: 16px;
}
.nav .btn-cta {
    margin-left: auto;   /* dorong tombol ini ke kanan */
}

/* ✨ 6. ICON + TEKS SEJAJAR */
.menu-item {
    display: flex;
    align-items: center;
    gap: 12px;
}

/* ✨ 7. GRID RESPONSIF SIMPEL */
.grid-items {
    display: flex;
    flex-wrap: wrap;
    gap: 16px;
}
.grid-item {
    flex: 1 1 calc(33.33% - 16px);   /* 3 kolom */
}

/* ✨ 8. GANTI URUTAN DI MOBILE */
.card {
    display: flex;
    flex-direction: column;
}
.card__gambar {
    order: -1;   /* gambar selalu di atas, apapun urutan di HTML */
}
```

---

## 22. CSS Grid — Tata Letak 2 Dimensi

CSS Grid adalah sistem layout untuk mengontrol **baris DAN kolom** sekaligus. Ideal untuk layout halaman dan komponen kompleks.

### Konsep dasar:

```
GRID CONTAINER
         Col 1      Col 2      Col 3
       ┌──────────┬──────────┬──────────┐
Row 1  │  ITEM 1  │  ITEM 2  │  ITEM 3  │
       ├──────────┼──────────┼──────────┤
Row 2  │  ITEM 4  │  ITEM 5  │  ITEM 6  │
       └──────────┴──────────┴──────────┘

Grid Lines (garis):
       1          2          3          4
       ↓          ↓          ↓          ↓
Row:   ─  ─  ─  ─  ─  ─  ─  ─  ─  ─  ─
       1
       ─  ─  ─  ─  ─  ─  ─  ─  ─  ─  ─
       2
       ─  ─  ─  ─  ─  ─  ─  ─  ─  ─  ─
       3
```

### Properti pada GRID CONTAINER:

```css
.grid {
    display: grid;   /* atau inline-grid */

    /* ── DEFINISI KOLOM ── */
    grid-template-columns: 200px 1fr 200px;
    /* 3 kolom: fixed 200px | fleksibel isi sisa | fixed 200px */

    grid-template-columns: repeat(3, 1fr);
    /* 3 kolom sama lebar */

    grid-template-columns: repeat(4, minmax(200px, 1fr));
    /* 4 kolom, minimal 200px, sisanya dibagi rata */

    grid-template-columns: repeat(auto-fill, 200px);
    /* Buat kolom 200px sebanyak yang muat. Kolom kosong tetap ada. */

    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    /* RESPONSIF TANPA MEDIA QUERY. Kolom kosong diciutkan. */

    grid-template-columns: 260px 1fr;
    /* Sidebar 260px + konten utama isi sisa */

    /* ── DEFINISI BARIS ── */
    grid-template-rows: 64px 1fr 60px;
    /* 3 baris: header 64px | konten isi sisa | footer 60px */

    grid-template-rows: auto;
    /* Tinggi baris ditentukan konten (default) */

    grid-template-rows: repeat(3, 200px);
    /* 3 baris, masing-masing 200px */

    /* ── TEMPLATE AREA — cara visual paling mudah ── */
    grid-template-areas:
        "header  header  header"
        "sidebar main    main  "
        "sidebar main    main  "
        "footer  footer  footer";
    /* Spasi = garis antar kolom, nama yang sama = satu area */
    /* Gunakan . untuk sel kosong */
    grid-template-areas:
        "header  header"
        ".       main  "
        "footer  footer";

    /* ── JARAK ── */
    gap: 24px;           /* baris dan kolom sama */
    row-gap: 16px;
    column-gap: 24px;

    /* ── ALIGNMENT ITEM DALAM SEL ── */
    justify-items: start | end | center | stretch;    /* horizontal */
    align-items: start | end | center | stretch;      /* vertikal */

    /* ── ALIGNMENT GRID DALAM CONTAINER ── */
    justify-content: start | end | center | stretch | space-between | space-around | space-evenly;
    align-content: start | end | center | stretch | space-between | space-around | space-evenly;
}
```

### Properti pada GRID ITEM:

```css
/* ── CARA 1: PAKAI LINE NUMBER ── */
.item {
    /* Grid lines dihitung dari 1 */
    grid-column: 1 / 3;      /* dari garis kolom 1 sampai garis kolom 3 (2 kolom) */
    grid-column: 1 / -1;     /* dari kolom 1 sampai akhir (semua kolom) */
    grid-column: span 2;     /* ambil 2 kolom dari posisi saat ini */

    grid-row: 1 / 3;         /* dari garis baris 1 sampai garis baris 3 (2 baris) */
    grid-row: 2 / span 3;    /* mulai baris 2, ambil 3 baris */
    grid-row: span 2;        /* ambil 2 baris dari posisi saat ini */
}

/* ── CARA 2: PAKAI TEMPLATE AREA ── */
header  { grid-area: header; }
.sidebar { grid-area: sidebar; }
main    { grid-area: main; }
footer  { grid-area: footer; }

/* ── SELF ALIGNMENT — override untuk item ini saja ── */
.item-khusus {
    justify-self: center;    /* horizontal */
    align-self: end;         /* vertikal */
    place-self: center end;  /* shorthand: align | justify */
}
```

### Contoh layout halaman dengan Grid:

```css
/* Layout website dengan sidebar */
.layout {
    display: grid;
    grid-template-columns: 260px 1fr;
    grid-template-rows: 64px 1fr 60px;
    grid-template-areas:
        "sidebar header"
        "sidebar main  "
        "sidebar footer";
    min-height: 100vh;
}

/* Layout dashboard 3 kolom */
.dashboard {
    display: grid;
    grid-template-columns: 220px 1fr 300px;
    grid-template-areas:
        "nav header  header"
        "nav content aside "
        "nav footer  footer";
    min-height: 100vh;
}

/* Layout majalah kompleks */
.magazine-grid {
    display: grid;
    grid-template-columns: repeat(12, 1fr);
    gap: 24px;
}

.artikel-utama {
    grid-column: 1 / 8;   /* 7 dari 12 kolom */
}
.artikel-samping {
    grid-column: 8 / 13;  /* 5 dari 12 kolom */
}
.artikel-kecil {
    grid-column: span 4;  /* 4 kolom setiap artikel */
}
```

### `fr` unit — fractional unit:

```css
/* fr = sisa ruang yang tersedia dibagi rata */
.grid {
    display: grid;
    grid-template-columns: 200px 1fr 1fr;
    /* 200px (fixed) + sisa ruang dibagi 2 sama rata */

    grid-template-columns: 200px 2fr 1fr;
    /* 200px (fixed) + sisa ruang: kolom kedua 2x lebih lebar dari ketiga */
}
```

### Auto-responsive dengan `auto-fit` dan `minmax()`:

```css
/* Ini MAGIC FORMULA yang paling berguna di CSS Grid */
.grid-responsif {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 24px;
}

/*
    Penjelasan:
    repeat(auto-fit, ...)  → buat kolom sebanyak yang muat
    minmax(280px, 1fr)     → setiap kolom minimal 280px, maksimal 1fr

    Di layar besar (1200px): bisa muat 4 kolom masing-masing ~300px
    Di tablet (768px): bisa muat 2 kolom masing-masing ~384px
    Di HP (360px): 1 kolom 360px
    SEMUA OTOMATIS! Tidak butuh media query.
*/
```

### Kapan pakai Flexbox vs Grid:

| Situasi | Gunakan |
|---------|---------|
| Layout halaman secara keseluruhan | **Grid** |
| Komponen dengan baris DAN kolom | **Grid** |
| Komponen satu arah (horizontal atau vertikal) | **Flexbox** |
| Navbar, header | **Flexbox** |
| Card dalam satu baris | **Flexbox** |
| Gallery foto / grid produk | **Grid** |
| Centering satu elemen | **Flexbox** |
| Dashboard kompleks | **Grid** |
| Tombol dengan icon | **Flexbox** |
| Holy Grail Layout | **Grid** |

> 💡 **Tip:** Gunakan Grid untuk layout makro (kerangka halaman), Flexbox untuk layout mikro (komponen di dalam layout).

---

## 23. Responsive Design & Media Query

**Responsive design** adalah filosofi bahwa website harus berfungsi dengan baik di semua ukuran layar — dari smartwatch 200px sampai monitor 4K 3840px.

### Mobile-first approach (cara yang benar):

```css
/*
    MOBILE FIRST = mulai dengan styles untuk layar kecil,
    kemudian tambahkan styles untuk layar lebih besar.

    Keuntungan:
    - Performance lebih baik (browser load CSS secara default minimal)
    - Memaksa prioritas konten (apa yang penting di mobile?)
    - Lebih mudah di-maintain
*/

/* ── BASE STYLES — untuk semua ukuran termasuk mobile ── */
.container {
    width: 100%;
    padding: 0 16px;
}

.grid {
    display: grid;
    grid-template-columns: 1fr;   /* 1 kolom di mobile */
    gap: 16px;
}

.navbar__nav {
    display: none;   /* menu disembunyikan di mobile */
}

/* ── TABLET (≥ 640px) ── */
@media (min-width: 640px) {
    .container {
        padding: 0 24px;
    }
    .grid {
        grid-template-columns: repeat(2, 1fr);   /* 2 kolom */
    }
}

/* ── TABLET BESAR / LAPTOP (≥ 1024px) ── */
@media (min-width: 1024px) {
    .container {
        max-width: 1200px;
        margin: 0 auto;
        padding: 0 48px;
    }
    .grid {
        grid-template-columns: repeat(3, 1fr);   /* 3 kolom */
    }
    .navbar__nav {
        display: flex;   /* tampilkan menu di desktop */
    }
}

/* ── DESKTOP BESAR (≥ 1280px) ── */
@media (min-width: 1280px) {
    .grid {
        grid-template-columns: repeat(4, 1fr);   /* 4 kolom */
    }
}
```

### Breakpoints yang umum digunakan:

```css
/*
    Breakpoints bukanlah angka ajaib yang harus sama persis.
    Sesuaikan dengan desain lo. Ini hanya panduan umum.
*/
:root {
    --bp-xs:  375px;    /* HP kecil */
    --bp-sm:  640px;    /* HP besar / landscape */
    --bp-md:  768px;    /* Tablet portrait */
    --bp-lg:  1024px;   /* Tablet landscape / laptop */
    --bp-xl:  1280px;   /* Desktop */
    --bp-2xl: 1536px;   /* Desktop besar */
}

/* Media query shortcuts yang sering dipakai */
/* Mobile only */
@media (max-width: 639px) { }

/* Tablet only */
@media (min-width: 640px) and (max-width: 1023px) { }

/* Desktop+ */
@media (min-width: 1024px) { }

/* Mobile + tablet (bukan desktop) */
@media (max-width: 1023px) { }
```

### Media features selain `min-width`:

```css
/* ── ORIENTASI ── */
@media (orientation: portrait)  { /* layar tegak */ }
@media (orientation: landscape) { /* layar miring */ }

/* ── DARK MODE ── */
@media (prefers-color-scheme: dark) {
    :root {
        --color-bg: #0f172a;
        --color-text: #e2e8f0;
        --color-surface: #1e293b;
    }
}
@media (prefers-color-scheme: light) {
    :root {
        --color-bg: #ffffff;
        --color-text: #1e293b;
        --color-surface: #f8fafc;
    }
}

/* ── REDUCED MOTION — aksesibilitas untuk yang sensitif gerakan ── */
@media (prefers-reduced-motion: reduce) {
    *,
    *::before,
    *::after {
        animation-duration: 0.01ms !important;
        animation-iteration-count: 1 !important;
        transition-duration: 0.01ms !important;
        scroll-behavior: auto !important;
    }
}

/* ── HIGH CONTRAST MODE ── */
@media (forced-colors: active) {
    .btn { border: 2px solid ButtonText; }
}

/* ── PRINT ── */
@media print {
    .navbar, .sidebar, .iklan, .btn { display: none !important; }
    body { font-size: 12pt; color: black; background: white; }
    a::after { content: " (" attr(href) ")"; }  /* tampilkan URL */
}

/* ── LAYAR RETINA / HIGH DPI ── */
@media (-webkit-min-device-pixel-ratio: 2), (min-resolution: 192dpi) {
    .logo {
        background-image: url('logo@2x.png');
        background-size: 120px 40px;
    }
}

/* ── POINTER (touch vs mouse) ── */
@media (hover: hover) and (pointer: fine) {
    /* user pakai mouse — hover effects aman */
    .btn:hover { transform: translateY(-2px); }
}
@media (hover: none) and (pointer: coarse) {
    /* user pakai touchscreen — tidak ada hover */
    .btn { padding: 16px 24px; }  /* tombol lebih besar untuk jari */
}
```

### Unit responsif penting:

```css
/* vw — viewport width (1vw = 1% lebar layar) */
.hero { height: 100vh; min-height: 600px; }
.full-width { width: 100vw; margin-left: calc(-50vw + 50%); }

/* dvh — dynamic viewport height (mobile browser) */
.hero { height: 100dvh; }  /* memperhitungkan address bar mobile */

/* clamp() — nilai fluid dengan batas min dan max */
h1 { font-size: clamp(1.8rem, 5vw, 4rem); }
/* min 1.8rem | preferred 5vw | max 4rem */

.container { width: clamp(320px, 90vw, 1200px); }

/* min() dan max() */
.gambar { width: min(600px, 100%); }      /* ambil yang lebih kecil */
.sidebar { width: max(200px, 25%); }       /* ambil yang lebih besar */

/* Contoh penggunaan nyata */
:root {
    --container-width: min(1200px, 90vw);
    --font-hero: clamp(2rem, 6vw, 5rem);
    --padding-section: clamp(48px, 8vw, 120px);
}

.container {
    width: var(--container-width);
    margin: 0 auto;
}

.section { padding-block: var(--padding-section); }
```

---

## 24. Transisi & Animasi

### CSS Transition — perubahan halus antara dua state:

```css
/* Sintaks: properti | durasi | timing-function | delay */
.btn {
    background: #f59e0b;
    color: #000;
    transform: translateY(0);
    box-shadow: 0 2px 4px rgba(0,0,0,0.2);

    /* Transisi spesifik properti (LEBIH BAIK untuk performance) */
    transition:
        background-color 0.2s ease,
        transform 0.15s ease,
        box-shadow 0.2s ease;
}

.btn:hover {
    background: #d97706;
    transform: translateY(-2px);
    box-shadow: 0 8px 20px rgba(245,158,11,0.3);
}

/* Transisi semua properti (HINDARI jika bisa — kurang optimal) */
.btn { transition: all 0.3s ease; }
```

### Timing Functions:

```css
transition-timing-function: linear;          /* kecepatan konstan */
transition-timing-function: ease;            /* lambat-cepat-lambat (default) */
transition-timing-function: ease-in;         /* lambat di awal, cepat di akhir */
transition-timing-function: ease-out;        /* cepat di awal, lambat di akhir */
transition-timing-function: ease-in-out;     /* lambat di keduanya */
transition-timing-function: step-start;      /* langsung ke nilai akhir */
transition-timing-function: step-end;        /* tetap di nilai awal, langsung pindah */
transition-timing-function: steps(4, end);   /* 4 langkah */

/* Custom cubic-bezier — cek di cubic-bezier.com */
transition-timing-function: cubic-bezier(0.34, 1.56, 0.64, 1);   /* bouncy */
transition-timing-function: cubic-bezier(0.68, -0.55, 0.265, 1.55); /* overshoot */
```

### CSS Animation — sequence gerakan kompleks:

```css
/* ── STEP 1: Definisikan keyframes ── */

@keyframes fadeIn {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
}

@keyframes fadeInLeft {
    from { opacity: 0; transform: translateX(-30px); }
    to   { opacity: 1; transform: translateX(0); }
}

@keyframes slideDown {
    from { transform: translateY(-100%); opacity: 0; }
    to   { transform: translateY(0); opacity: 1; }
}

@keyframes spin {
    to { transform: rotate(360deg); }
}

@keyframes pulse {
    0%, 100% { transform: scale(1); opacity: 1; }
    50%       { transform: scale(1.05); opacity: 0.8; }
}

@keyframes bounce {
    0%, 100% {
        transform: translateY(0);
        animation-timing-function: cubic-bezier(0.8, 0, 1, 1);
    }
    50% {
        transform: translateY(-16px);
        animation-timing-function: cubic-bezier(0, 0, 0.2, 1);
    }
}

@keyframes shimmer {
    0%   { background-position: -200% center; }
    100% { background-position: 200% center; }
}

@keyframes float {
    0%, 100% { transform: translateY(0px); }
    50%       { transform: translateY(-10px); }
}

/* ── STEP 2: Terapkan ke elemen ── */
.hero-title {
    animation: fadeIn 0.7s ease-out 0.2s both;
    /* name | duration | timing | delay | fill-mode */
}

.loader-spin {
    animation: spin 0.8s linear infinite;
}

.floating-element {
    animation: float 3s ease-in-out infinite;
}
```

### Semua properti animation:

```css
.elemen {
    animation-name: fadeIn;
    animation-duration: 0.7s;
    animation-timing-function: ease-out;
    animation-delay: 0.2s;
    animation-iteration-count: 1;           /* atau: infinite, 3 */
    animation-direction: normal;            /* atau: reverse, alternate, alternate-reverse */
    animation-fill-mode: both;              /* none | forwards | backwards | both */
    /* forwards = pertahankan state akhir */
    /* backwards = terapkan state awal selama delay */
    /* both = keduanya */
    animation-play-state: running;          /* atau: paused */

    /* Shorthand */
    animation: fadeIn 0.7s ease-out 0.2s 1 normal both;
    /* name | duration | timing | delay | iteration | direction | fill-mode */

    /* Multiple animations */
    animation:
        fadeIn 0.7s ease-out both,
        float 3s ease-in-out 0.7s infinite;
}
```

### Staggered animation — muncul bergantian:

```css
/* Cara 1: Manual nth-child */
.card:nth-child(1) { animation: fadeIn 0.5s ease-out 0.0s both; }
.card:nth-child(2) { animation: fadeIn 0.5s ease-out 0.1s both; }
.card:nth-child(3) { animation: fadeIn 0.5s ease-out 0.2s both; }
.card:nth-child(4) { animation: fadeIn 0.5s ease-out 0.3s both; }
.card:nth-child(5) { animation: fadeIn 0.5s ease-out 0.4s both; }

/* Cara 2: CSS custom property (lebih elegan) */
.card {
    animation: fadeIn 0.5s ease-out calc(var(--delay, 0) * 100ms) both;
}
```
```html
<!-- Set delay via style inline -->
<div class="card" style="--delay: 1">Kartu 1</div>
<div class="card" style="--delay: 2">Kartu 2</div>
<div class="card" style="--delay: 3">Kartu 3</div>
```

### Transform — properti kunci untuk animasi:

```css
/* ── TRANSLATE (geser) ── */
transform: translateX(100px);         /* geser kanan */
transform: translateY(-50%);          /* geser atas 50% tinggi sendiri */
transform: translate(10px, 20px);     /* x, y */
transform: translate(-50%, -50%);     /* centering trick */

/* ── SCALE (perbesar/perkecil) ── */
transform: scale(1.2);                /* 120% */
transform: scale(0.8);                /* 80% */
transform: scaleX(1.5);              /* hanya horizontal */
transform: scaleY(0.5);              /* hanya vertikal */
transform: scale(1.1, 0.9);          /* x, y berbeda */

/* ── ROTATE (putar) ── */
transform: rotate(45deg);
transform: rotate(-90deg);
transform: rotate(0.5turn);           /* 0.5 putaran = 180° */
transform: rotateX(30deg);            /* putar 3D sumbu X */
transform: rotateY(45deg);            /* putar 3D sumbu Y */

/* ── SKEW (miring) ── */
transform: skewX(15deg);
transform: skewY(-10deg);
transform: skew(15deg, -10deg);

/* ── GABUNGKAN (URUTAN PENTING!) ── */
/* Transform diproses dari kanan ke kiri */
transform: translateY(-10px) scale(1.02) rotate(5deg);
/* Pertama rotate, lalu scale, lalu translate */

/* ── TRANSFORM ORIGIN ── */
transform-origin: center;              /* default */
transform-origin: top left;
transform-origin: 0% 0%;
transform-origin: 50% 100%;            /* bawah tengah — untuk flip animation */
```

### Skeleton loading — efek loading modern:

```css
@keyframes skeleton {
    0%   { background-position: -200% center; }
    100% { background-position: 200% center; }
}

.skeleton {
    background: linear-gradient(
        90deg,
        #1e293b 25%,
        #334155 50%,
        #1e293b 75%
    );
    background-size: 200% 100%;
    animation: skeleton 1.5s ease-in-out infinite;
    border-radius: 4px;
}

/* Penggunaan */
<div class="skeleton" style="height: 200px; width: 100%;"></div>
<div class="skeleton" style="height: 20px; width: 60%; margin-top: 12px;"></div>
<div class="skeleton" style="height: 14px; width: 40%; margin-top: 8px;"></div>
```

---

## 25. CSS Variables — Custom Properties

CSS Variables adalah fondasi dari design system modern. Memungkinkan nilai disimpan dan dipakai ulang di seluruh stylesheet.

### Sintaks dasar:

```css
/* Deklarasi — pakai prefix -- */
:root {
    --nama-variable: nilai;
}

/* Penggunaan */
.elemen {
    properti: var(--nama-variable);
    properti: var(--nama-variable, nilai-fallback);  /* dengan fallback */
}
```

### Design token lengkap untuk project:

```css
:root {

    /* ════════════════════════════
       WARNA
    ════════════════════════════ */

    /* Warna dasar */
    --color-white: #ffffff;
    --color-black: #000000;

    /* Background */
    --color-bg-primary:   #070b14;   /* latar belakang utama */
    --color-bg-secondary: #0f172a;   /* latar belakang layer 2 */
    --color-bg-tertiary:  #1e293b;   /* latar belakang layer 3 */

    /* Surface (kartu, panel) */
    --color-surface-1: #1e293b;
    --color-surface-2: #334155;
    --color-surface-3: #475569;

    /* Border */
    --color-border:       rgba(148, 163, 184, 0.08);
    --color-border-hover: rgba(148, 163, 184, 0.20);
    --color-border-focus: rgba(245, 158, 11, 0.50);

    /* Teks */
    --color-text-primary: #e2e8f0;
    --color-text-secondary: #94a3b8;
    --color-text-tertiary: #64748b;
    --color-text-disabled: #475569;

    /* Accent / Brand */
    --color-accent:        #f59e0b;
    --color-accent-hover:  #d97706;
    --color-accent-light:  #fcd34d;
    --color-accent-dim:    rgba(245, 158, 11, 0.12);

    /* Status */
    --color-success:     #10b981;
    --color-success-dim: rgba(16, 185, 129, 0.12);
    --color-warning:     #f59e0b;
    --color-warning-dim: rgba(245, 158, 11, 0.12);
    --color-error:       #ef4444;
    --color-error-dim:   rgba(239, 68, 68, 0.12);
    --color-info:        #3b82f6;
    --color-info-dim:    rgba(59, 130, 246, 0.12);

    /* ════════════════════════════
       TIPOGRAFI
    ════════════════════════════ */

    --font-display: 'Bebas Neue', 'Arial Black', sans-serif;
    --font-body:    'DM Sans', Helvetica, Arial, sans-serif;
    --font-mono:    'JetBrains Mono', 'Courier New', monospace;

    /* Skala ukuran font */
    --text-xs:   0.75rem;    /* 12px */
    --text-sm:   0.875rem;   /* 14px */
    --text-base: 1rem;       /* 16px */
    --text-lg:   1.125rem;   /* 18px */
    --text-xl:   1.25rem;    /* 20px */
    --text-2xl:  1.5rem;     /* 24px */
    --text-3xl:  1.875rem;   /* 30px */
    --text-4xl:  2.25rem;    /* 36px */
    --text-5xl:  3rem;       /* 48px */
    --text-6xl:  clamp(3rem, 7vw, 5rem);  /* fluid */

    /* Font weight */
    --fw-light:     300;
    --fw-regular:   400;
    --fw-medium:    500;
    --fw-semibold:  600;
    --fw-bold:      700;
    --fw-extrabold: 800;
    --fw-black:     900;

    /* Line height */
    --lh-tight:  1.1;    /* heading display */
    --lh-snug:   1.3;    /* heading normal */
    --lh-normal: 1.5;    /* default */
    --lh-relaxed: 1.7;   /* body text */
    --lh-loose:  2;      /* spasi besar */

    /* Letter spacing */
    --ls-tight:  -0.025em;
    --ls-normal: 0em;
    --ls-wide:   0.025em;
    --ls-wider:  0.05em;
    --ls-widest: 0.15em;

    /* ════════════════════════════
       SPACING
    ════════════════════════════ */

    /* Skala berbasis 4px */
    --space-0:  0;
    --space-1:  4px;
    --space-2:  8px;
    --space-3:  12px;
    --space-4:  16px;
    --space-5:  20px;
    --space-6:  24px;
    --space-8:  32px;
    --space-10: 40px;
    --space-12: 48px;
    --space-16: 64px;
    --space-20: 80px;
    --space-24: 96px;
    --space-32: 128px;

    /* ════════════════════════════
       BORDER
    ════════════════════════════ */

    --radius-none: 0;
    --radius-sm:   4px;
    --radius-md:   8px;
    --radius-lg:   12px;
    --radius-xl:   16px;
    --radius-2xl:  24px;
    --radius-3xl:  32px;
    --radius-full: 9999px;

    /* ════════════════════════════
       SHADOW
    ════════════════════════════ */

    --shadow-sm:   0 1px 2px rgba(0,0,0,0.3);
    --shadow-md:   0 4px 12px rgba(0,0,0,0.4);
    --shadow-lg:   0 8px 24px rgba(0,0,0,0.5);
    --shadow-xl:   0 16px 48px rgba(0,0,0,0.6);
    --shadow-glow: 0 0 24px rgba(245, 158, 11, 0.3);
    --shadow-inset: inset 0 1px 3px rgba(0,0,0,0.4);

    /* ════════════════════════════
       TRANSISI
    ════════════════════════════ */

    --transition-fast:   150ms cubic-bezier(0.4, 0, 0.2, 1);
    --transition-base:   250ms cubic-bezier(0.4, 0, 0.2, 1);
    --transition-slow:   400ms cubic-bezier(0.4, 0, 0.2, 1);
    --transition-bounce: 300ms cubic-bezier(0.34, 1.56, 0.64, 1);

    /* ════════════════════════════
       Z-INDEX
    ════════════════════════════ */

    --z-below:    -1;
    --z-base:      0;
    --z-raised:    10;
    --z-dropdown:  100;
    --z-sticky:    200;
    --z-fixed:     300;
    --z-modal:     400;
    --z-popover:   500;
    --z-tooltip:   600;
    --z-toast:     700;

    /* ════════════════════════════
       LAYOUT
    ════════════════════════════ */

    --container-sm:  640px;
    --container-md:  768px;
    --container-lg:  1024px;
    --container-xl:  1280px;
    --container-2xl: 1536px;
    --navbar-height: 64px;
    --sidebar-width: 260px;
}

/* ═══════════════════════════════
   CONTOH PENGGUNAAN
═══════════════════════════════ */

body {
    background-color: var(--color-bg-primary);
    color: var(--color-text-primary);
    font-family: var(--font-body);
    font-size: var(--text-base);
    line-height: var(--lh-normal);
}

.kartu {
    background: var(--color-surface-1);
    border: 1px solid var(--color-border);
    border-radius: var(--radius-lg);
    padding: var(--space-6);
    box-shadow: var(--shadow-md);
    transition: all var(--transition-base);
}

.kartu:hover {
    border-color: var(--color-border-hover);
    box-shadow: var(--shadow-glow);
    transform: translateY(-4px);
}

.btn-primary {
    background: var(--color-accent);
    color: var(--color-bg-primary);
    padding: var(--space-3) var(--space-6);
    border-radius: var(--radius-md);
    font-size: var(--text-sm);
    font-weight: var(--fw-semibold);
    transition: all var(--transition-fast);
}

.btn-primary:hover {
    background: var(--color-accent-hover);
    box-shadow: var(--shadow-glow);
}
```

### Variabel bisa di-override per komponen/scope:

```css
/* ── Variables bisa di-override di dalam elemen tertentu ── */
:root {
    --btn-bg:     var(--color-accent);
    --btn-text:   var(--color-bg-primary);
    --btn-radius: var(--radius-md);
    --btn-shadow: none;
}

.btn {
    background:    var(--btn-bg);
    color:         var(--btn-text);
    border-radius: var(--btn-radius);
    box-shadow:    var(--btn-shadow);
}

/* Override untuk varian danger */
.btn-danger {
    --btn-bg:   var(--color-error);
    --btn-text: white;
}

/* Override untuk varian pill */
.btn-pill {
    --btn-radius: var(--radius-full);
}

/* Override untuk konteks dark yang berbeda */
.section-hero {
    --color-text-primary: white;   /* semua teks di dalam .section-hero jadi putih */
}
```

### `calc()`, `min()`, `max()`, `clamp()` dengan variables:

```css
:root {
    --navbar-height: 64px;
    --sidebar-width: 260px;
    --footer-height: 80px;
}

/* calc() — kalkulasi matematis */
.main-content {
    margin-top: var(--navbar-height);
    margin-left: var(--sidebar-width);
    min-height: calc(100vh - var(--navbar-height) - var(--footer-height));
    width: calc(100% - var(--sidebar-width));
    padding: var(--space-8) calc(var(--space-6) * 2);
}

/* clamp(min, preferred, max) — nilai fluid */
h1 {
    font-size: clamp(var(--text-3xl), 5vw, var(--text-6xl));
}
```

---

## 26. Pseudo-class & Pseudo-element

### Pseudo-class — target elemen berdasarkan state atau posisi:

```css
/* ── STATE INTERAKSI ── */
a:link      { color: var(--color-accent); }        /* link belum dikunjungi */
a:visited   { color: #9333ea; }                    /* link sudah dikunjungi */
a:hover     { color: var(--color-accent-light); }  /* mouse di atas */
a:active    { opacity: 0.8; }                      /* sedang ditekan */
a:focus     { outline: 2px solid var(--color-accent); outline-offset: 2px; }
a:focus-visible { /* hanya saat fokus via keyboard, bukan mouse */ }

/* ── STATE FORM ── */
input:focus          { border-color: var(--color-border-focus); box-shadow: 0 0 0 3px var(--color-accent-dim); }
input:disabled       { opacity: 0.4; cursor: not-allowed; }
input:read-only      { background: var(--color-surface-2); }
input:placeholder-shown { /* saat placeholder tampil (belum diisi) */ }
input:not(:placeholder-shown) { /* sudah diisi */ }
input:checked        { accent-color: var(--color-accent); }
input:valid          { border-color: var(--color-success); }
input:invalid        { border-color: var(--color-error); }
input:required       { border-left: 3px solid var(--color-accent); }
input:optional       { /* field tidak wajib diisi */ }
input:in-range       { /* nilai dalam range min-max */ }
input:out-of-range   { /* nilai di luar range */ }

/* ── POSISI STRUKTURAL ── */
li:first-child        { border-top: none; }
li:last-child         { border-bottom: none; }
li:nth-child(2)       { background: var(--color-surface-2); }
li:nth-child(odd)     { background: var(--color-surface-1); }
li:nth-child(even)    { background: var(--color-surface-2); }
li:nth-child(3n)      { /* setiap kelipatan 3: ke-3, 6, 9, 12... */ }
li:nth-child(3n+1)    { /* ke-1, 4, 7, 10... */ }
li:nth-child(-n+3)    { /* 3 item pertama */ }
li:nth-last-child(1)  { /* item terakhir */ }
li:nth-last-child(2)  { /* item kedua dari akhir */ }
li:only-child         { /* jika hanya ada 1 item */ }

p:first-of-type { font-size: 1.1em; }   /* p pertama dari jenisnya di parent */
p:last-of-type  { margin-bottom: 0; }
p:only-of-type  { font-style: italic; }

/* ── SELEKSI LOGIS ── */
/* :not() — semua elemen KECUALI */
button:not(.btn-primary) { background: transparent; }
li:not(:last-child) { border-bottom: 1px solid var(--color-border); }
input:not([type="submit"]):not([type="button"]) { /* semua input kecuali tombol */ }

/* :is() — shortcut untuk multiple selector */
/* Specificity = specificity dari selector terkuat di dalamnya */
:is(h1, h2, h3, h4, h5, h6) { font-family: var(--font-display); }
:is(.card, .panel, .dialog) > .header { padding: 20px; }

/* :where() — sama seperti :is() tapi specificity SELALU 0 */
/* Lebih mudah di-override */
:where(h1, h2, h3) { line-height: 1.2; }

/* :has() — parent selector (game changer!) — CSS 2023 */
/* Target parent berdasarkan kondisi child-nya */
.form-group:has(input:invalid) {
    border: 1px solid var(--color-error);  /* form-group yang punya input invalid */
}
.card:has(img) {
    padding-top: 0;   /* card yang punya gambar, padding top dihapus */
}
.nav:has(.active) {   /* nav yang ada item active-nya */ }
label:has(+ input:required)::after {
    content: " *";
    color: var(--color-error);
}

/* :empty — elemen yang tidak ada konten */
p:empty { display: none; }
.placeholder:empty::before { content: attr(data-placeholder); color: var(--color-text-tertiary); }
```

### Pseudo-element — bagian virtual dari elemen:

```css
/* ── ::before dan ::after ── */
/* Konten virtual sebelum/sesudah konten asli elemen */
/* Harus punya property 'content' (bisa kosong: content: "") */

/* Dekorasi section title */
.section-title::before {
    content: "";           /* kosong — hanya dekorasi */
    display: block;
    width: 48px;
    height: 3px;
    background: var(--color-accent);
    border-radius: var(--radius-full);
    margin-bottom: 16px;
}

/* Badge "BARU" otomatis */
.produk-baru::after {
    content: "BARU";
    position: absolute;
    top: 12px;
    right: 12px;
    background: var(--color-accent);
    color: #000;
    font-size: var(--text-xs);
    font-weight: var(--fw-bold);
    padding: 2px 8px;
    border-radius: var(--radius-full);
    letter-spacing: var(--ls-wider);
}

/* Tooltip via CSS */
[data-tooltip] {
    position: relative;
    cursor: help;
}
[data-tooltip]::before {
    content: attr(data-tooltip);  /* ambil teks dari atribut data-tooltip */
    position: absolute;
    bottom: calc(100% + 8px);
    left: 50%;
    transform: translateX(-50%);
    background: var(--color-surface-2);
    color: var(--color-text-primary);
    font-size: var(--text-sm);
    white-space: nowrap;
    padding: 6px 12px;
    border-radius: var(--radius-md);
    border: 1px solid var(--color-border);
    opacity: 0;
    transition: opacity var(--transition-fast);
    pointer-events: none;
}
[data-tooltip]:hover::before {
    opacity: 1;
}

/* Counter otomatis */
.daftar-bernomor {
    counter-reset: item-counter;  /* reset counter ke 0 */
}
.daftar-bernomor .item::before {
    counter-increment: item-counter;  /* tambah counter setiap item */
    content: counter(item-counter, decimal-leading-zero) ".";
    color: var(--color-accent);
    font-family: var(--font-mono);
    font-weight: var(--fw-bold);
    margin-right: 12px;
}

/* ── ::first-line — baris pertama teks ── */
article p::first-line {
    font-weight: var(--fw-semibold);
    letter-spacing: var(--ls-wide);
}

/* ── ::first-letter — huruf pertama (dropcap) ── */
article > p:first-child::first-letter {
    font-family: var(--font-display);
    font-size: 3.5em;
    font-weight: var(--fw-bold);
    line-height: 0.8;
    float: left;
    margin: 0 8px 4px 0;
    color: var(--color-accent);
}

/* ── ::placeholder — styling placeholder input ── */
::placeholder {
    color: var(--color-text-tertiary);
    font-style: italic;
    opacity: 1;  /* Firefox perlu ini */
}
input:focus::placeholder {
    opacity: 0.5;  /* placeholder memudar saat fokus */
}

/* ── ::selection — teks yang di-select user ── */
::selection {
    background: var(--color-accent);
    color: var(--color-bg-primary);
}

/* ── ::marker — bullet/number di list ── */
li::marker {
    color: var(--color-accent);
    font-size: 1.2em;
}

/* ── ::backdrop — latar di belakang <dialog> ── */
dialog::backdrop {
    background: rgba(7, 11, 20, 0.85);
    backdrop-filter: blur(6px);
}

/* ── ::cue — subtitle/caption styling ── */
video::cue {
    background: rgba(0,0,0,0.8);
    color: white;
    font-size: 1.1em;
}
```

---

## 27. CSS Architecture & BEM

Saat project besar, tanpa struktur yang jelas CSS bisa jadi spaghetti. BEM adalah metodologi penamaan paling populer.

### BEM — Block Element Modifier:

```
.block               → Komponen/modul mandiri
.block__element      → Bagian dari block (dua underscore)
.block--modifier     → Variasi atau state (dua dash)
```

```html
<!-- Contoh implementasi BEM yang benar -->

<!-- BLOCK: nav -->
<nav class="nav nav--dark">

    <!-- ELEMENT: nav__logo -->
    <a href="/" class="nav__logo">ANERS</a>

    <!-- ELEMENT: nav__list dan nav__item -->
    <ul class="nav__list">
        <li class="nav__item">
            <!-- nav__link dengan modifier --active -->
            <a href="/" class="nav__link nav__link--active">Home</a>
        </li>
        <li class="nav__item">
            <a href="/about" class="nav__link">About</a>
        </li>
    </ul>

    <!-- ELEMENT: nav__cta -->
    <a href="/kontak" class="nav__cta btn btn--primary btn--sm">
        Hubungi
    </a>

</nav>

<!-- BLOCK: card dengan modifier -->
<article class="card card--featured card--horizontal">

    <!-- ELEMENTS -->
    <div class="card__media">
        <img class="card__image" src="foto.jpg" alt="Foto">
        <span class="card__badge card__badge--baru">BARU</span>
    </div>

    <div class="card__body">
        <span class="card__category">Tutorial</span>
        <h2 class="card__title">Belajar CSS Grid</h2>
        <p class="card__desc">Panduan lengkap CSS Grid dari dasar...</p>

        <footer class="card__footer">
            <div class="card__meta">
                <time class="card__date">15 Nov 2024</time>
                <span class="card__read-time">12 menit</span>
            </div>
            <a href="/artikel" class="card__link btn btn--ghost btn--sm">
                Baca →
            </a>
        </footer>
    </div>

</article>
```

```css
/* CSS BEM yang rapi dan scalable */

/* ── BLOCK: card ── */
.card {
    position: relative;
    background: var(--color-surface-1);
    border: 1px solid var(--color-border);
    border-radius: var(--radius-lg);
    overflow: hidden;
    transition:
        transform var(--transition-base),
        box-shadow var(--transition-base),
        border-color var(--transition-base);
}

.card:hover {
    transform: translateY(-4px);
    box-shadow: var(--shadow-lg);
    border-color: var(--color-border-hover);
}

/* ── MODIFIERS: card ── */
.card--featured {
    border-color: rgba(245, 158, 11, 0.3);
    box-shadow: 0 0 0 1px rgba(245, 158, 11, 0.1);
}

.card--featured:hover {
    border-color: var(--color-accent);
    box-shadow: var(--shadow-glow);
}

.card--horizontal {
    display: flex;
    flex-direction: row;
}

.card--compact {
    padding: var(--space-4);
}

/* ── ELEMENTS: card ── */
.card__media {
    position: relative;
    overflow: hidden;
}

.card__image {
    width: 100%;
    height: 220px;
    object-fit: cover;
    display: block;
    transition: transform var(--transition-slow);
}

.card:hover .card__image {
    transform: scale(1.05);  /* zoom gambar saat hover */
}

.card--horizontal .card__media {
    width: 280px;
    flex-shrink: 0;
}

.card--horizontal .card__image {
    height: 100%;
}

.card__badge {
    position: absolute;
    top: 12px;
    left: 12px;
    padding: 4px 10px;
    border-radius: var(--radius-full);
    font-family: var(--font-mono);
    font-size: var(--text-xs);
    font-weight: var(--fw-bold);
    letter-spacing: var(--ls-wider);
}

.card__badge--baru { background: var(--color-accent); color: #000; }
.card__badge--hot  { background: var(--color-error); color: white; }

.card__body {
    padding: var(--space-6);
    display: flex;
    flex-direction: column;
    flex: 1;
}

.card__category {
    font-family: var(--font-mono);
    font-size: var(--text-xs);
    color: var(--color-accent);
    letter-spacing: var(--ls-wider);
    text-transform: uppercase;
    margin-bottom: var(--space-2);
}

.card__title {
    font-size: var(--text-xl);
    font-weight: var(--fw-bold);
    line-height: var(--lh-snug);
    margin-bottom: var(--space-3);
    color: var(--color-text-primary);
}

.card__desc {
    font-size: var(--text-sm);
    color: var(--color-text-secondary);
    line-height: var(--lh-relaxed);
    flex: 1;
    display: -webkit-box;
    -webkit-line-clamp: 3;
    -webkit-box-orient: vertical;
    overflow: hidden;
}

.card__footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: var(--space-6);
    padding-top: var(--space-4);
    border-top: 1px solid var(--color-border);
}

.card__meta {
    display: flex;
    gap: var(--space-3);
    font-size: var(--text-xs);
    color: var(--color-text-tertiary);
}
```

### Struktur file CSS yang scalable:

```
styles/
├── base/
│   ├── _reset.css           # CSS reset / normalize
│   ├── _variables.css       # Design tokens (CSS custom properties)
│   ├── _typography.css      # Font loading, base text styles, heading scale
│   └── _global.css          # Body, html, link, selection styles
│
├── components/
│   ├── _button.css
│   ├── _card.css
│   ├── _navbar.css
│   ├── _sidebar.css
│   ├── _modal.css
│   ├── _form.css
│   ├── _badge.css
│   ├── _toast.css
│   └── _skeleton.css
│
├── layouts/
│   ├── _container.css       # Max-width container
│   ├── _grid.css            # Grid system
│   └── _section.css         # Section padding system
│
├── utilities/               # Helper classes (pakai sparingly)
│   ├── _spacing.css         # .mt-4, .px-6, dll
│   ├── _flex.css            # .flex, .flex-col, .items-center, dll
│   ├── _text.css            # .text-sm, .font-bold, .text-center, dll
│   └── _colors.css          # .text-accent, .bg-surface, dll
│
└── main.css                 # Import semua file
```

```css
/* main.css */
/* ── BASE ── */
@import './base/_reset.css';
@import './base/_variables.css';
@import './base/_typography.css';
@import './base/_global.css';

/* ── COMPONENTS ── */
@import './components/_button.css';
@import './components/_card.css';
@import './components/_navbar.css';
@import './components/_form.css';
@import './components/_modal.css';

/* ── LAYOUTS ── */
@import './layouts/_container.css';
@import './layouts/_grid.css';
@import './layouts/_section.css';

/* ── UTILITIES ── */
@import './utilities/_spacing.css';
@import './utilities/_text.css';
```

### CSS Reset yang proper:

```css
/* _reset.css — fondasi yang bersih */

/* Box model global */
*,
*::before,
*::after {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

/* Root */
html {
    font-size: 16px;
    scroll-behavior: smooth;
    -webkit-text-size-adjust: 100%;  /* cegah font resize di iOS landscape */
    hanging-punctuation: first last;  /* tipografi lebih baik */
}

/* Body */
body {
    min-height: 100dvh;              /* dynamic viewport height */
    line-height: 1.5;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-rendering: optimizeSpeed;
}

/* Media */
img,
picture,
video,
canvas,
svg {
    display: block;
    max-width: 100%;
}

/* Inherit font untuk form elements */
input,
button,
textarea,
select,
optgroup {
    font: inherit;
}

/* Prevent word overflow */
p,
h1, h2, h3, h4, h5, h6 {
    overflow-wrap: break-word;
}

/* List */
ul, ol {
    list-style: none;
}

/* Link */
a {
    color: inherit;
    text-decoration: none;
}

/* Button */
button {
    cursor: pointer;
    background: none;
    border: none;
    appearance: none;
}

/* Table */
table {
    border-collapse: collapse;
    border-spacing: 0;
}

/* Fieldset */
fieldset {
    border: none;
}

/* HR */
hr {
    border: none;
    border-top: 1px solid;
    color: inherit;
}

/* Iframe */
iframe {
    border: none;
}

/* Prevent animation for motion sensitive users */
@media (prefers-reduced-motion: reduce) {
    html:focus-within {
        scroll-behavior: auto;
    }
    *,
    *::before,
    *::after {
        animation-duration: 0.01ms !important;
        animation-iteration-count: 1 !important;
        transition-duration: 0.01ms !important;
    }
}
```

---

## 28. Tips Pro & Best Practice

### ✅ Yang Harus Dilakukan:

```css
/* 1. Pakai CSS variables untuk semua nilai yang berulang */
.tombol { background: var(--color-accent); }             /* ✅ */
.tombol { background: #f59e0b; }                         /* ❌ hardcoded */

/* 2. box-sizing: border-box di semua elemen */
*, *::before, *::after { box-sizing: border-box; }       /* ✅ WAJIB */

/* 3. Pakai rem untuk font-size, bukan px */
body { font-size: 1rem; }                                /* ✅ */
body { font-size: 16px; }                                /* ❌ tidak scalable */

/* 4. Pakai gap bukan margin untuk spacing dalam flex/grid */
.flex-container { display: flex; gap: 16px; }            /* ✅ */
.flex-item { margin-right: 16px; }                       /* ❌ */

/* 5. Pakai logical properties untuk support RTL */
margin-inline: auto;      /* kiri-kanan — support RTL */  /* ✅ */
padding-block: 24px;      /* atas-bawah */                /* ✅ */
margin: 0 auto;                                           /* ❌ hanya LTR */

/* 6. Pakai aspect-ratio untuk media */
.thumbnail {
    aspect-ratio: 16 / 9;
    object-fit: cover;
    width: 100%;
}

/* 7. Fluid typography dengan clamp() */
h1 { font-size: clamp(1.8rem, 4vw, 3.5rem); }           /* ✅ */
h1 { font-size: 48px; }                                   /* ❌ tidak responsif */

/* 8. Animasi hanya properti yang GPU-accelerated */
/* ✅ Murah di GPU */
.item { transition: transform 0.3s, opacity 0.3s; }

/* ❌ Mahal — trigger layout recalculation */
.item { transition: width 0.3s, height 0.3s, margin 0.3s, top 0.3s; }

/* 9. Jangan hilangkan focus style */
/* ✅ Custom focus yang accessible */
:focus-visible {
    outline: 2px solid var(--color-accent);
    outline-offset: 3px;
}
/* ❌ JANGAN PERNAH */
* { outline: none; }

/* 10. Gunakan min-height bukan height untuk container */
.section { min-height: 400px; }    /* ✅ konten bisa lebih besar */
.section { height: 400px; }        /* ❌ konten terpotong jika lebih besar */
```

### ❌ Yang Harus Dihindari:

```css
/* 1. Jangan pakai !important sembarangan */
.tombol { color: red !important; }    /* ❌ susah di-maintain, tanda arsitektur buruk */

/* 2. Jangan selector terlalu dalam (max 3 level) */
.nav .nav-list .nav-item .nav-link span { }  /* ❌ overly specific */
.nav-link span { }                           /* ✅ cukup */

/* 3. Jangan pakai ID untuk styling */
#navbar { background: var(--color-bg-secondary); }   /* ❌ specificity terlalu tinggi */
.navbar { background: var(--color-bg-secondary); }   /* ✅ */

/* 4. Jangan * { transition: all } */
* { transition: all 0.3s; }    /* ❌ sangat boros, bisa bug */

/* 5. Jangan float untuk layout */
.kolom { float: left; width: 33.33%; }  /* ❌ pola lama */
/* Pakai flex atau grid */

/* 6. Jangan hardcode warna dan spacing */
.btn { background: #f59e0b; padding: 12px 24px; }  /* ❌ */
.btn { background: var(--color-accent); padding: var(--space-3) var(--space-6); }  /* ✅ */

/* 7. Jangan ukuran font terlalu kecil */
.caption { font-size: 10px; }         /* ❌ tidak terbaca */
.caption { font-size: var(--text-xs); }  /* ✅ 12px — minimum */

/* 8. Jangan animasi properti yang butuh reflow */
.card { transition: width 0.3s, height 0.3s; }   /* ❌ lambat */
.card { transition: transform 0.3s; }             /* ✅ GPU-accelerated */
```

### Performance CSS:

```css
/* Properti aman untuk animasi (diproses di GPU) */
/* ✅ Gunakan untuk animasi */
transform: translate() scale() rotate();
opacity: 0 to 1;
filter: blur() brightness();

/* Properti MAHAL — trigger layout recalculation */
/* ❌ Hindari animasi ini */
width, height           → pakai transform: scale()
top, left, right, bottom → pakai transform: translate()
margin, padding         → pakai transform: translate()
font-size               → pakai transform: scale()

/* will-change — hint ke browser (pakai HATI-HATI) */
.animasi-berat {
    will-change: transform, opacity;  /* hanya elemen yang PASTI beranimasi */
}
/* Jangan pakai di banyak elemen — boroskan VRAM */

/* contain — batasi scope rendering */
.widget {
    contain: layout paint;  /* perubahan di dalam tidak mempengaruhi luar */
}

/* content-visibility — skip rendering di luar viewport */
.section-panjang {
    content-visibility: auto;
    contain-intrinsic-size: 0 500px;  /* estimasi tinggi */
}
```

### Checklist sebelum deploy:

```
HTML:
✅ DOCTYPE dan lang attribute ada
✅ Semua gambar punya alt text yang deskriptif
✅ Form input punya label yang terhubung
✅ Heading hierarkis (h1 → h2 → h3, tidak melompat)
✅ Link teks deskriptif (bukan "klik di sini")
✅ Meta description dan title ada

CSS:
✅ box-sizing: border-box diterapkan global
✅ CSS reset/normalize terpasang
✅ Font loading dengan font-display: swap
✅ Semua warna dan spacing pakai CSS variables
✅ Tidak ada !important kecuali sangat perlu
✅ Responsive di 375px, 768px, 1024px, 1440px
✅ Focus styles ada dan terlihat jelas
✅ prefers-reduced-motion diimplementasikan
✅ Tidak ada CSS dead code (properti yang tidak dipakai)

Aksesibilitas:
✅ Kontras warna WCAG AA: min 4.5:1 untuk teks kecil, 3:1 untuk teks besar
✅ Interactive element (button, link) punya ukuran min 44×44px
✅ Keyboard navigation bisa dipakai (Tab, Shift+Tab, Enter, Space)
✅ ARIA label ada untuk elemen interaktif yang ambigu
```

---

## 29. Mini Projects — Latihan Nyata

### 🎯 Project 1: Landing Page Personal

```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rixz — Full-Stack Developer</title>
    <meta name="description" content="Self-taught developer dari Indonesia. Web, AI, Bot.">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:wght@300;400;600&family=JetBrains+Mono:wght@400;600&display=swap" rel="stylesheet">
    <style>
        /* ═══════════ RESET & VARIABLES ═══════════ */
        *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
        ul { list-style: none; }
        a { color: inherit; text-decoration: none; }
        img { display: block; max-width: 100%; }

        :root {
            --bg:        #070b14;
            --surface:   #0f172a;
            --surface-2: #1e293b;
            --border:    rgba(148, 163, 184, 0.07);
            --text:      #e2e8f0;
            --muted:     #64748b;
            --accent:    #f59e0b;
            --accent-dim: rgba(245, 158, 11, 0.1);
            --green:     #10b981;

            --font-display: 'Bebas Neue', sans-serif;
            --font-body:    'DM Sans', sans-serif;
            --font-mono:    'JetBrains Mono', monospace;
        }

        html { font-size: 16px; scroll-behavior: smooth; }

        body {
            background: var(--bg);
            color: var(--text);
            font-family: var(--font-body);
            line-height: 1.6;
            -webkit-font-smoothing: antialiased;
        }

        /* Noise texture overlay */
        body::after {
            content: "";
            position: fixed;
            inset: 0;
            background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
            opacity: 0.025;
            pointer-events: none;
            z-index: 9999;
        }

        /* ═══════════ ANIMATIONS ═══════════ */
        @keyframes fadeUp {
            from { opacity: 0; transform: translateY(20px); }
            to   { opacity: 1; transform: translateY(0); }
        }
        @keyframes pulseDot {
            0%, 100% { opacity: 1; transform: scale(1); }
            50% { opacity: 0.4; transform: scale(0.7); }
        }

        /* ═══════════ NAVBAR ═══════════ */
        .navbar {
            position: fixed;
            inset: 0 0 auto 0;
            z-index: 100;
            display: flex;
            justify-content: space-between;
            align-items: center;
            height: 60px;
            padding: 0 clamp(16px, 5vw, 64px);
            background: rgba(7, 11, 20, 0.75);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border-bottom: 1px solid var(--border);
        }

        .navbar__logo {
            font-family: var(--font-display);
            font-size: 1.4rem;
            letter-spacing: 0.08em;
            color: var(--accent);
        }

        .navbar__links {
            display: flex;
            gap: 28px;
            align-items: center;
        }

        .navbar__link {
            font-family: var(--font-mono);
            font-size: 0.78rem;
            color: var(--muted);
            transition: color 0.15s;
        }
        .navbar__link:hover { color: var(--accent); }

        /* ═══════════ HERO ═══════════ */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            padding: 60px clamp(16px, 5vw, 64px) 0;
            position: relative;
            overflow: hidden;
        }

        /* Background glow blobs */
        .hero::before {
            content: "";
            position: absolute;
            top: -5%;
            right: -15%;
            width: 700px;
            height: 700px;
            background: radial-gradient(circle, rgba(245,158,11,0.06) 0%, transparent 65%);
            pointer-events: none;
        }
        .hero::after {
            content: "";
            position: absolute;
            bottom: -10%;
            left: -10%;
            width: 600px;
            height: 600px;
            background: radial-gradient(circle, rgba(99,102,241,0.05) 0%, transparent 70%);
            pointer-events: none;
        }

        .hero__content {
            max-width: 820px;
            position: relative;
            z-index: 1;
        }

        .hero__badge {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            padding: 6px 14px;
            background: var(--accent-dim);
            border: 1px solid rgba(245,158,11,0.15);
            border-radius: 999px;
            font-family: var(--font-mono);
            font-size: 0.72rem;
            color: var(--accent);
            margin-bottom: 28px;
            animation: fadeUp 0.5s ease-out both;
        }

        .hero__badge-dot {
            width: 6px;
            height: 6px;
            border-radius: 50%;
            background: var(--green);
            animation: pulseDot 2s ease-in-out infinite;
        }

        .hero__title {
            font-family: var(--font-display);
            font-size: clamp(3.5rem, 10vw, 7.5rem);
            line-height: 0.88;
            letter-spacing: 0.01em;
            margin-bottom: 20px;
            animation: fadeUp 0.5s ease-out 0.1s both;
        }

        .hero__title-accent {
            display: block;
            color: var(--accent);
        }

        .hero__desc {
            font-size: clamp(1rem, 2vw, 1.15rem);
            color: var(--muted);
            max-width: 520px;
            line-height: 1.75;
            margin-bottom: 36px;
            animation: fadeUp 0.5s ease-out 0.2s both;
        }

        .hero__actions {
            display: flex;
            gap: 12px;
            flex-wrap: wrap;
            animation: fadeUp 0.5s ease-out 0.3s both;
        }

        /* ═══════════ BUTTONS ═══════════ */
        .btn {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            padding: 11px 22px;
            border-radius: 6px;
            font-weight: 600;
            font-size: 0.875rem;
            font-family: inherit;
            transition: all 0.15s ease;
            cursor: pointer;
            border: none;
        }

        .btn--primary {
            background: var(--accent);
            color: #000;
        }
        .btn--primary:hover {
            background: #d97706;
            transform: translateY(-2px);
            box-shadow: 0 8px 24px rgba(245,158,11,0.25);
        }

        .btn--ghost {
            background: transparent;
            color: var(--text);
            border: 1px solid var(--border);
        }
        .btn--ghost:hover {
            border-color: rgba(255,255,255,0.2);
            background: rgba(255,255,255,0.04);
        }

        /* ═══════════ SECTION COMMONS ═══════════ */
        .section {
            padding: clamp(64px, 10vw, 120px) clamp(16px, 5vw, 64px);
        }

        .section--alt { background: var(--surface); }

        .section__label {
            font-family: var(--font-mono);
            font-size: 0.72rem;
            color: var(--accent);
            letter-spacing: 0.12em;
            text-transform: uppercase;
            margin-bottom: 12px;
        }

        .section__title {
            font-family: var(--font-display);
            font-size: clamp(2rem, 5vw, 3.5rem);
            line-height: 0.95;
            margin-bottom: 48px;
        }

        /* ═══════════ STACK ═══════════ */
        .stack-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
            gap: 10px;
        }

        .stack-item {
            display: flex;
            align-items: center;
            gap: 10px;
            padding: 14px 18px;
            background: var(--surface);
            border: 1px solid var(--border);
            border-radius: 8px;
            font-family: var(--font-mono);
            font-size: 0.82rem;
            transition: all 0.2s ease;
        }
        .stack-item:hover {
            border-color: rgba(245,158,11,0.25);
            background: var(--accent-dim);
            transform: translateY(-2px);
        }

        .stack-item__dot {
            width: 7px;
            height: 7px;
            border-radius: 50%;
            background: var(--accent);
            flex-shrink: 0;
        }

        /* ═══════════ PROJECTS ═══════════ */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
        }

        .project {
            background: var(--bg);
            border: 1px solid var(--border);
            border-radius: 12px;
            padding: 28px;
            transition: all 0.25s ease;
        }
        .project:hover {
            border-color: rgba(245,158,11,0.2);
            transform: translateY(-4px);
            box-shadow: 0 16px 40px rgba(0,0,0,0.4);
        }

        .project__tag {
            font-family: var(--font-mono);
            font-size: 0.68rem;
            color: var(--accent);
            letter-spacing: 0.1em;
            text-transform: uppercase;
            margin-bottom: 10px;
        }

        .project__title {
            font-size: 1.1rem;
            font-weight: 700;
            margin-bottom: 8px;
        }

        .project__desc {
            color: var(--muted);
            font-size: 0.875rem;
            line-height: 1.65;
            margin-bottom: 20px;
        }

        .project__stack {
            display: flex;
            flex-wrap: wrap;
            gap: 6px;
        }

        .badge {
            padding: 3px 10px;
            background: var(--surface-2);
            border-radius: 4px;
            font-family: var(--font-mono);
            font-size: 0.68rem;
            color: var(--muted);
        }

        /* ═══════════ FOOTER ═══════════ */
        .footer {
            padding: 36px clamp(16px, 5vw, 64px);
            border-top: 1px solid var(--border);
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 12px;
        }

        .footer p {
            font-family: var(--font-mono);
            font-size: 0.78rem;
            color: var(--muted);
        }

        /* ═══════════ RESPONSIVE ═══════════ */
        @media (max-width: 640px) {
            .navbar__links { display: none; }
            .hero__actions { flex-direction: column; }
            .btn { justify-content: center; }
            .footer { justify-content: center; text-align: center; }
        }

        @media (prefers-reduced-motion: reduce) {
            *, *::before, *::after {
                animation-duration: 0.01ms !important;
                transition-duration: 0.01ms !important;
            }
        }
    </style>
</head>
<body>

    <header>
        <nav class="navbar" aria-label="Navigasi utama">
            <span class="navbar__logo">RIZ-DEV</span>
            <div class="navbar__links" role="list">
                <a href="#stack" class="navbar__link" role="listitem">Stack</a>
                <a href="#projects" class="navbar__link" role="listitem">Projects</a>
                <a href="mailto:rixz@aners.dev" class="navbar__link" role="listitem">Contact</a>
            </div>
        </nav>
    </header>

    <main>
        <section class="hero" aria-label="Hero">
            <div class="hero__content">
                <div class="hero__badge" role="status">
                    <span class="hero__badge-dot" aria-hidden="true"></span>
                    Available for projects
                </div>
                <h1 class="hero__title">
                    FULL-STACK
                    <span class="hero__title-accent">DEVELOPER</span>
                </h1>
                <p class="hero__desc">
                    Self-taught developer & security researcher dari Indonesia.
                    Specializing in web apps, AI integrations, dan bot systems.
                    Builder at ANERS.
                </p>
                <div class="hero__actions">
                    <a href="#projects" class="btn btn--primary">Lihat Projects</a>
                    <a href="mailto:rixz@aners.dev" class="btn btn--ghost">Hubungi</a>
                </div>
            </div>
        </section>

        <section class="section" id="stack" aria-labelledby="stack-heading">
            <p class="section__label">// tech stack</p>
            <h2 class="section__title" id="stack-heading">Yang Gue Pakai</h2>
            <div class="stack-grid" role="list">
                <div class="stack-item" role="listitem">
                    <span class="stack-item__dot" aria-hidden="true"></span>Next.js
                </div>
                <div class="stack-item" role="listitem">
                    <span class="stack-item__dot" aria-hidden="true"></span>Node.js
                </div>
                <div class="stack-item" role="listitem">
                    <span class="stack-item__dot" aria-hidden="true"></span>Python
                </div>
                <div class="stack-item" role="listitem">
                    <span class="stack-item__dot" aria-hidden="true"></span>FastAPI
                </div>
                <div class="stack-item" role="listitem">
                    <span class="stack-item__dot" aria-hidden="true"></span>PostgreSQL
                </div>
                <div class="stack-item" role="listitem">
                    <span class="stack-item__dot" aria-hidden="true"></span>Redis
                </div>
                <div class="stack-item" role="listitem">
                    <span class="stack-item__dot" aria-hidden="true"></span>Grammy.js
                </div>
                <div class="stack-item" role="listitem">
                    <span class="stack-item__dot" aria-hidden="true"></span>Tailwind CSS
                </div>
            </div>
        </section>

        <section class="section section--alt" id="projects" aria-labelledby="projects-heading">
            <p class="section__label">// selected work</p>
            <h2 class="section__title" id="projects-heading">Projects</h2>
            <div class="projects-grid">

                <article class="project">
                    <p class="project__tag">AI · Web App</p>
                    <h3 class="project__title">ANERS Aria c11</h3>
                    <p class="project__desc">
                        Dual-AI agentic chat platform. Aria (MiniMax M2.7) 
                        dan Nexus (DeepSeek v3.2) berkolaborasi dalam loop agent.
                        Ditenagai NVIDIA Build API.
                    </p>
                    <div class="project__stack">
                        <span class="badge">Next.js</span>
                        <span class="badge">MiniMax</span>
                        <span class="badge">DeepSeek</span>
                        <span class="badge">NVIDIA</span>
                    </div>
                </article>

                <article class="project">
                    <p class="project__tag">Bot · Automation</p>
                    <h3 class="project__title">ANERS Agent Bot</h3>
                    <p class="project__desc">
                        Autonomous AI Telegram bot dengan intent routing,
                        tool-calling, dan SQL injection protection.
                        Jalan 24/7 di Termux.
                    </p>
                    <div class="project__stack">
                        <span class="badge">Grammy.js</span>
                        <span class="badge">Groq</span>
                        <span class="badge">SQLite</span>
                    </div>
                </article>

                <article class="project">
                    <p class="project__tag">Security · Research</p>
                    <h3 class="project__title">Network Recon — CVSS 7.2</h3>
                    <p class="project__desc">
                        Formal security writeup dari network reconnaissance 
                        finding di infrastruktur Indosat.
                        CVSS v3.1 scoring: 7.2 HIGH.
                    </p>
                    <div class="project__stack">
                        <span class="badge">CVSS 7.2 HIGH</span>
                        <span class="badge">Vulnerability Research</span>
                    </div>
                </article>

            </div>
        </section>
    </main>

    <footer class="footer">
        <p>© 2024 Riz-dev × Claude Sonnet 4.6</p>
        <p>Built with pure HTML & CSS</p>
    </footer>

</body>
</html>
```

---

### 🃏 Project 2: UI Component Kit

```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ANERS UI Kit</title>
    <link href="https://fonts.googleapis.com/css2?family=Syne:wght@700;800&family=DM+Sans:wght@400;500;600&family=JetBrains+Mono&display=swap" rel="stylesheet">
    <style>
        *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
        ul { list-style: none; }

        :root {
            --bg: #0a0a0f;
            --surface: #13131a;
            --surface-2: #1c1c26;
            --border: rgba(255,255,255,0.06);
            --text: #f1f0ff;
            --muted: #6b6b80;
            --accent: #7c3aed;
            --accent-light: #a78bfa;
            --accent-dim: rgba(124,58,237,0.12);
            --green: #34d399;
            --red: #f87171;
            --yellow: #fbbf24;
        }

        html { font-size: 16px; }
        body {
            background: var(--bg);
            color: var(--text);
            font-family: 'DM Sans', sans-serif;
            padding: 48px clamp(16px, 5vw, 64px) 80px;
        }

        /* ── Header ── */
        .page-header { margin-bottom: 64px; }
        .page-title {
            font-family: 'Syne', sans-serif;
            font-size: clamp(2rem, 5vw, 3rem);
            font-weight: 800;
            margin-bottom: 8px;
        }
        .page-subtitle {
            font-family: 'JetBrains Mono', monospace;
            font-size: 0.8rem;
            color: var(--muted);
        }

        /* ── Section ── */
        .section { margin-bottom: 56px; }
        .section-title {
            font-family: 'JetBrains Mono', monospace;
            font-size: 0.7rem;
            color: var(--accent-light);
            letter-spacing: 0.12em;
            text-transform: uppercase;
            padding-bottom: 12px;
            border-bottom: 1px solid var(--border);
            margin-bottom: 24px;
        }
        .showcase {
            display: flex;
            flex-wrap: wrap;
            gap: 12px;
            align-items: flex-start;
        }

        /* ════════════
           BUTTONS
        ════════════ */
        .btn {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            padding: 10px 20px;
            border-radius: 6px;
            font-weight: 600;
            font-size: 0.875rem;
            font-family: inherit;
            border: none;
            cursor: pointer;
            transition: all 0.15s cubic-bezier(0.4, 0, 0.2, 1);
            white-space: nowrap;
            user-select: none;
        }

        .btn:focus-visible {
            outline: 2px solid var(--accent-light);
            outline-offset: 3px;
        }

        .btn:active { transform: scale(0.97); }

        /* Variants */
        .btn--primary {
            background: var(--accent);
            color: white;
        }
        .btn--primary:hover {
            background: #6d28d9;
            transform: translateY(-1px);
            box-shadow: 0 6px 20px rgba(124,58,237,0.35);
        }

        .btn--secondary {
            background: var(--surface-2);
            color: var(--text);
            border: 1px solid var(--border);
        }
        .btn--secondary:hover {
            background: var(--surface);
            border-color: rgba(255,255,255,0.12);
        }

        .btn--ghost {
            background: transparent;
            color: var(--accent-light);
            border: 1px solid rgba(124,58,237,0.3);
        }
        .btn--ghost:hover {
            background: var(--accent-dim);
            border-color: var(--accent-light);
        }

        .btn--danger {
            background: rgba(239,68,68,0.1);
            color: var(--red);
            border: 1px solid rgba(239,68,68,0.2);
        }
        .btn--danger:hover {
            background: rgba(239,68,68,0.2);
            box-shadow: 0 0 16px rgba(239,68,68,0.15);
        }

        .btn--success {
            background: rgba(52,211,153,0.1);
            color: var(--green);
            border: 1px solid rgba(52,211,153,0.2);
        }
        .btn--success:hover { background: rgba(52,211,153,0.2); }

        /* Sizes */
        .btn--xs { padding: 4px 12px; font-size: 0.75rem; }
        .btn--sm { padding: 7px 14px; font-size: 0.8rem; }
        .btn--lg { padding: 13px 28px; font-size: 1rem; }
        .btn--xl { padding: 16px 36px; font-size: 1.1rem; }
        .btn--full { width: 100%; }

        /* Icon button */
        .btn--icon { padding: 10px; }

        /* Loading state */
        @keyframes spin { to { transform: rotate(360deg); } }
        .btn--loading {
            position: relative;
            color: transparent;
            pointer-events: none;
        }
        .btn--loading::after {
            content: "";
            position: absolute;
            width: 16px;
            height: 16px;
            border: 2px solid rgba(255,255,255,0.3);
            border-top-color: white;
            border-radius: 50%;
            animation: spin 0.6s linear infinite;
        }

        /* ════════════
           BADGES
        ════════════ */
        .badge {
            display: inline-flex;
            align-items: center;
            gap: 5px;
            padding: 3px 10px;
            border-radius: 999px;
            font-family: 'JetBrains Mono', monospace;
            font-size: 0.72rem;
            font-weight: 500;
            border: 1px solid transparent;
        }

        .badge::before { content: "●"; font-size: 0.55rem; }

        .badge--default  { background: var(--surface-2); color: var(--muted); border-color: var(--border); }
        .badge--purple   { background: var(--accent-dim); color: var(--accent-light); border-color: rgba(124,58,237,0.2); }
        .badge--green    { background: rgba(52,211,153,0.1); color: var(--green); border-color: rgba(52,211,153,0.2); }
        .badge--yellow   { background: rgba(251,191,36,0.1); color: var(--yellow); border-color: rgba(251,191,36,0.2); }
        .badge--red      { background: rgba(248,113,113,0.1); color: var(--red); border-color: rgba(248,113,113,0.2); }

        /* ════════════
           CARDS
        ════════════ */
        .card {
            background: var(--surface);
            border: 1px solid var(--border);
            border-radius: 12px;
            overflow: hidden;
        }

        /* Basic */
        .card--basic { padding: 24px; width: 280px; }
        .card__title {
            font-family: 'Syne', sans-serif;
            font-size: 1.1rem;
            font-weight: 700;
            margin-bottom: 8px;
        }
        .card__body {
            color: var(--muted);
            font-size: 0.875rem;
            line-height: 1.6;
        }

        /* Glow */
        .card--glow {
            padding: 24px;
            width: 280px;
            position: relative;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        .card--glow::before {
            content: "";
            position: absolute;
            inset: -1px;
            background: linear-gradient(135deg, var(--accent), rgba(124,58,237,0.2), transparent);
            border-radius: 13px;
            z-index: -1;
            opacity: 0;
            transition: opacity 0.3s ease;
        }
        .card--glow:hover::before { opacity: 1; }
        .card--glow:hover {
            transform: translateY(-4px);
            box-shadow: 0 20px 48px rgba(124,58,237,0.15);
        }

        /* Stat */
        .card--stat { padding: 24px; width: 180px; }
        .card__stat-label {
            font-family: 'JetBrains Mono', monospace;
            font-size: 0.68rem;
            color: var(--muted);
            text-transform: uppercase;
            letter-spacing: 0.1em;
            margin-bottom: 6px;
        }
        .card__stat-value {
            font-family: 'Syne', sans-serif;
            font-size: 2.2rem;
            font-weight: 800;
            color: var(--accent-light);
            line-height: 1;
            margin-bottom: 4px;
        }
        .card__stat-trend {
            font-size: 0.78rem;
            color: var(--green);
        }

        /* ════════════
           INPUTS
        ════════════ */
        .input-demo { width: 280px; }

        .form-label {
            display: block;
            font-size: 0.8rem;
            font-weight: 500;
            margin-bottom: 6px;
            color: var(--muted);
        }

        .form-input {
            width: 100%;
            padding: 10px 14px;
            background: rgba(255,255,255,0.03);
            border: 1px solid var(--border);
            border-radius: 6px;
            color: var(--text);
            font-family: inherit;
            font-size: 0.875rem;
            outline: none;
            transition: border-color 0.15s, box-shadow 0.15s;
        }
        .form-input::placeholder { color: var(--muted); }
        .form-input:focus {
            border-color: rgba(124,58,237,0.5);
            box-shadow: 0 0 0 3px var(--accent-dim);
        }

        /* ════════════
           ALERT
        ════════════ */
        .alert {
            display: flex;
            gap: 12px;
            padding: 14px 16px;
            border-radius: 8px;
            font-size: 0.875rem;
            border: 1px solid transparent;
            width: 100%;
            max-width: 480px;
        }

        .alert--info    { background: rgba(59,130,246,0.1); border-color: rgba(59,130,246,0.2); color: #93c5fd; }
        .alert--success { background: rgba(52,211,153,0.1); border-color: rgba(52,211,153,0.2); color: var(--green); }
        .alert--warning { background: rgba(251,191,36,0.1); border-color: rgba(251,191,36,0.2); color: var(--yellow); }
        .alert--error   { background: rgba(248,113,113,0.1); border-color: rgba(248,113,113,0.2); color: var(--red); }
    </style>
</head>
<body>

    <header class="page-header">
        <h1 class="page-title">ANERS UI Kit</h1>
        <p class="page-subtitle">// component library — pure CSS, no dependencies</p>
    </header>

    <section class="section">
        <p class="section-title">Buttons — Variants</p>
        <div class="showcase">
            <button class="btn btn--primary">Primary</button>
            <button class="btn btn--secondary">Secondary</button>
            <button class="btn btn--ghost">Ghost</button>
            <button class="btn btn--danger">Danger</button>
            <button class="btn btn--success">Success</button>
        </div>
    </section>

    <section class="section">
        <p class="section-title">Buttons — Sizes</p>
        <div class="showcase" style="align-items: center;">
            <button class="btn btn--primary btn--xs">XSmall</button>
            <button class="btn btn--primary btn--sm">Small</button>
            <button class="btn btn--primary">Default</button>
            <button class="btn btn--primary btn--lg">Large</button>
            <button class="btn btn--primary btn--xl">XLarge</button>
        </div>
    </section>

    <section class="section">
        <p class="section-title">Buttons — States</p>
        <div class="showcase">
            <button class="btn btn--primary btn--loading">Loading...</button>
            <button class="btn btn--primary" disabled style="opacity:.4;cursor:not-allowed">Disabled</button>
        </div>
    </section>

    <section class="section">
        <p class="section-title">Badges</p>
        <div class="showcase">
            <span class="badge badge--default">Default</span>
            <span class="badge badge--purple">Active</span>
            <span class="badge badge--green">Online</span>
            <span class="badge badge--yellow">Pending</span>
            <span class="badge badge--red">Error</span>
        </div>
    </section>

    <section class="section">
        <p class="section-title">Cards</p>
        <div class="showcase">
            <div class="card card--basic">
                <h3 class="card__title">Basic Card</h3>
                <p class="card__body">
                    Card standar untuk informasi umum. Simple dan bersih.
                </p>
            </div>
            <div class="card card--glow">
                <h3 class="card__title">Hover Glow Card</h3>
                <p class="card__body">
                    Hover untuk efek glow gradient di border. Pure CSS, no JS.
                </p>
            </div>
            <div class="card card--stat">
                <p class="card__stat-label">Total Users</p>
                <p class="card__stat-value">8.4K</p>
                <p class="card__stat-trend">↑ 23.5% this month</p>
            </div>
        </div>
    </section>

    <section class="section">
        <p class="section-title">Form Inputs</p>
        <div class="showcase">
            <div class="input-demo">
                <label class="form-label" for="demo-text">Email</label>
                <input class="form-input" type="email" id="demo-text" placeholder="nama@email.com">
            </div>
            <div class="input-demo">
                <label class="form-label" for="demo-pass">Password</label>
                <input class="form-input" type="password" id="demo-pass" placeholder="••••••••">
            </div>
        </div>
    </section>

    <section class="section">
        <p class="section-title">Alerts</p>
        <div style="display:flex;flex-direction:column;gap:10px;max-width:480px;">
            <div class="alert alert--info">
                ℹ️ Update tersedia. Refresh halaman untuk versi terbaru.
            </div>
            <div class="alert alert--success">
                ✅ Akun berhasil dibuat. Selamat bergabung!
            </div>
            <div class="alert alert--warning">
                ⚠️ Storage lo hampir penuh. Hapus file yang tidak diperlukan.
            </div>
            <div class="alert alert--error">
                ❌ Koneksi gagal. Cek internet lo dan coba lagi.
            </div>
        </div>
    </section>

</body>
</html>
```

---

### 📝 Project 3: Form Login Responsif

```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login — ANERS Platform</title>
    <link href="https://fonts.googleapis.com/css2?family=Syne:wght@700;800&family=DM+Sans:wght@400;500;600&family=JetBrains+Mono&display=swap" rel="stylesheet">
    <style>
        *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

        :root {
            --bg: #080c14;
            --surface: #0f172a;
            --border: rgba(148,163,184,0.08);
            --border-focus: rgba(245,158,11,0.45);
            --text: #e2e8f0;
            --muted: #64748b;
            --accent: #f59e0b;
            --accent-dim: rgba(245,158,11,0.1);
            --error: #ef4444;
        }

        html { font-size: 16px; }

        body {
            min-height: 100dvh;
            background: var(--bg);
            display: grid;
            place-items: center;
            font-family: 'DM Sans', sans-serif;
            color: var(--text);
            padding: 24px;
            position: relative;
            overflow: hidden;
        }

        /* Background decorations */
        body::before {
            content: "";
            position: fixed;
            top: -20%;
            left: -10%;
            width: 600px;
            height: 600px;
            background: radial-gradient(circle, rgba(245,158,11,0.04) 0%, transparent 70%);
            pointer-events: none;
        }
        body::after {
            content: "";
            position: fixed;
            bottom: -20%;
            right: -10%;
            width: 500px;
            height: 500px;
            background: radial-gradient(circle, rgba(99,102,241,0.04) 0%, transparent 70%);
            pointer-events: none;
        }

        /* Animations */
        @keyframes fadeUp {
            from { opacity: 0; transform: translateY(20px); }
            to   { opacity: 1; transform: translateY(0); }
        }

        /* Login card */
        .login-card {
            background: var(--surface);
            border: 1px solid var(--border);
            border-radius: 16px;
            padding: clamp(28px, 5vw, 48px);
            width: 100%;
            max-width: 420px;
            position: relative;
            z-index: 1;
            animation: fadeUp 0.5s ease-out both;
        }

        /* Header */
        .login-header { text-align: center; margin-bottom: 32px; }

        .login-logo {
            font-family: 'JetBrains Mono', monospace;
            font-size: 0.75rem;
            color: var(--accent);
            letter-spacing: 0.2em;
            text-transform: uppercase;
            margin-bottom: 16px;
            display: block;
        }

        .login-title {
            font-family: 'Syne', sans-serif;
            font-size: 1.6rem;
            font-weight: 800;
            margin-bottom: 6px;
        }

        .login-subtitle {
            color: var(--muted);
            font-size: 0.875rem;
        }

        /* Form elements */
        .form-group { margin-bottom: 18px; }

        .form-label {
            display: block;
            font-size: 0.825rem;
            font-weight: 500;
            margin-bottom: 7px;
            color: var(--text);
        }

        .form-label .required {
            color: var(--error);
            margin-left: 2px;
        }

        .input-wrapper { position: relative; }

        .form-input {
            width: 100%;
            padding: 11px 16px;
            background: rgba(255,255,255,0.025);
            border: 1px solid var(--border);
            border-radius: 8px;
            color: var(--text);
            font-family: inherit;
            font-size: 0.9rem;
            outline: none;
            transition: border-color 0.15s, box-shadow 0.15s;
        }

        .form-input::placeholder { color: var(--muted); font-style: italic; }

        .form-input:focus {
            border-color: var(--border-focus);
            box-shadow: 0 0 0 3px var(--accent-dim);
        }

        .form-input:invalid:not(:placeholder-shown) {
            border-color: rgba(239,68,68,0.35);
        }

        /* Password toggle */
        .form-input--has-toggle { padding-right: 52px; }

        .input-toggle {
            position: absolute;
            right: 1px;
            top: 1px;
            bottom: 1px;
            width: 44px;
            background: none;
            border: none;
            border-radius: 0 7px 7px 0;
            color: var(--muted);
            cursor: pointer;
            font-family: 'JetBrains Mono', monospace;
            font-size: 0.65rem;
            letter-spacing: 0.05em;
            transition: color 0.15s, background 0.15s;
        }
        .input-toggle:hover { color: var(--text); background: rgba(255,255,255,0.03); }

        /* Form footer */
        .form-footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        .form-check {
            display: flex;
            align-items: center;
            gap: 8px;
            cursor: pointer;
        }
        .form-check input[type="checkbox"] {
            width: 15px;
            height: 15px;
            accent-color: var(--accent);
            cursor: pointer;
        }
        .form-check span {
            font-size: 0.825rem;
            color: var(--muted);
        }

        .form-link {
            font-size: 0.825rem;
            color: var(--accent);
            transition: opacity 0.15s;
        }
        .form-link:hover { opacity: 0.75; }

        /* Submit */
        .btn-submit {
            width: 100%;
            padding: 12px;
            background: var(--accent);
            color: #000;
            border: none;
            border-radius: 8px;
            font-family: inherit;
            font-size: 0.95rem;
            font-weight: 700;
            cursor: pointer;
            letter-spacing: 0.02em;
            transition: all 0.15s ease;
            margin-bottom: 16px;
        }
        .btn-submit:hover {
            background: #d97706;
            transform: translateY(-1px);
            box-shadow: 0 8px 24px rgba(245,158,11,0.25);
        }
        .btn-submit:active {
            transform: translateY(0);
            box-shadow: none;
        }

        /* Divider */
        .divider {
            display: flex;
            align-items: center;
            gap: 12px;
            margin-bottom: 16px;
            color: var(--muted);
            font-size: 0.75rem;
        }
        .divider::before, .divider::after {
            content: "";
            flex: 1;
            height: 1px;
            background: var(--border);
        }

        /* Signup link */
        .signup-text {
            text-align: center;
            font-size: 0.825rem;
            color: var(--muted);
        }
        .signup-text a {
            color: var(--accent);
            font-weight: 600;
            transition: opacity 0.15s;
        }
        .signup-text a:hover { opacity: 0.75; }

        /* Error message */
        .field-error {
            font-size: 0.75rem;
            color: var(--error);
            margin-top: 5px;
            display: none;
        }
        .form-input:invalid:not(:placeholder-shown) ~ .field-error {
            display: block;
        }
    </style>
</head>
<body>

    <main>
        <div class="login-card" role="main">

            <div class="login-header">
                <span class="login-logo">ANERS</span>
                <h1 class="login-title">Welcome back</h1>
                <p class="login-subtitle">Masuk ke ANERS Platform</p>
            </div>

            <form action="/api/auth/login" method="POST" novalidate>

                <div class="form-group">
                    <label for="email" class="form-label">
                        Email <span class="required" aria-hidden="true">*</span>
                    </label>
                    <input
                        type="email"
                        id="email"
                        name="email"
                        class="form-input"
                        placeholder="nama@email.com"
                        autocomplete="email"
                        required
                        aria-required="true"
                    >
                    <p class="field-error" role="alert">Format email tidak valid.</p>
                </div>

                <div class="form-group">
                    <label for="password" class="form-label">
                        Password <span class="required" aria-hidden="true">*</span>
                    </label>
                    <div class="input-wrapper">
                        <input
                            type="password"
                            id="password"
                            name="password"
                            class="form-input form-input--has-toggle"
                            placeholder="Minimal 8 karakter"
                            autocomplete="current-password"
                            minlength="8"
                            required
                            aria-required="true"
                        >
                        <button
                            type="button"
                            class="input-toggle"
                            id="toggle-pass"
                            aria-label="Toggle password visibility"
                        >
                            SHOW
                        </button>
                    </div>
                    <p class="field-error" role="alert">Password minimal 8 karakter.</p>
                </div>

                <div class="form-footer">
                    <label class="form-check">
                        <input type="checkbox" name="remember" value="1">
                        <span>Inget gue</span>
                    </label>
                    <a href="/lupa-password" class="form-link">Lupa password?</a>
                </div>

                <button type="submit" class="btn-submit">
                    Masuk ke Platform
                </button>

                <div class="divider">atau</div>

                <p class="signup-text">
                    Belum punya akun? <a href="/daftar">Daftar gratis</a>
                </p>

            </form>

        </div>
    </main>

    <script>
        // Toggle password visibility
        const toggleBtn = document.getElementById('toggle-pass');
        const passInput = document.getElementById('password');

        toggleBtn.addEventListener('click', () => {
            const isHidden = passInput.type === 'password';
            passInput.type = isHidden ? 'text' : 'password';
            toggleBtn.textContent = isHidden ? 'HIDE' : 'SHOW';
            toggleBtn.setAttribute('aria-label',
                isHidden ? 'Hide password' : 'Show password'
            );
        });
    </script>

</body>
</html>
```

---

## 🏁 Penutup

Lo udah selesai membaca buku ini — dan itu berarti lo serius dengan jalan ini. Ini bukan akhir, ini **fondasi yang lo butuhkan** untuk melangkah lebih jauh.

### Roadmap selanjutnya dari sini:

| Level | Yang Dipelajari | Estimasi |
|-------|----------------|----------|
| 🟡 **Next Level** | Sass/SCSS, CSS Modules, PostCSS | 2-4 minggu |
| 🟠 **CSS Framework** | Tailwind CSS (utility-first) | 1-2 minggu |
| 🔴 **JavaScript** | DOM manipulation, Event handling | 4-8 minggu |
| 🟣 **Framework** | React, Next.js | 2-3 bulan |
| ⬛ **Pro** | Performance, Core Web Vitals, a11y, SEO teknis | ongoing |

### Resources terbaik untuk melanjutkan:

- **MDN Web Docs** (`developer.mozilla.org`) — referensi resmi HTML & CSS, paling akurat
- **CSS-Tricks** (`css-tricks.com`) — panduan visual Flexbox, Grid, dan property modern
- **web.dev** (`web.dev`) — performance, aksesibilitas, dan modern web dari Google
- **caniuse.com** — cek dukungan fitur CSS di browser tertentu sebelum pakai
- **cssgradient.io** — visual generator gradient
- **coolors.co** — palette warna generator
- **fonts.google.com** — free fonts berkualitas untuk proyek web
- **cubic-bezier.com** — visual editor timing function animasi
- **roadmap.sh/frontend** — peta jalan frontend yang komprehensif

---

> *"Good design is as little design as possible — more purity,*  
> *simplicity, and back to basics."*
>
> **— Riz-dev × Claude Sonnet 4.6**

---

*Dokumen ini dibuat untuk komunitas belajar web development Indonesia.*  
*Branding: **Riz-dev × Claude Sonnet 4.6** — AI-Native Engineering & Research Systems*  
*Versi: 1.0.0 · Mei 2025*
