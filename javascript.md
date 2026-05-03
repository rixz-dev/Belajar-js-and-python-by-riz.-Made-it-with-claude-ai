# 🟨 Belajar JavaScript — Dari 0 Sampai Pro
> **by r¡xz · The ANERs**  
> *Dijelasin kayak ngomong sama bocil SD, dipraktekin kayak hacker beneran.*

---

## 📋 Daftar Isi

1. [Apa itu JavaScript?](#1-apa-itu-javascript)
2. [Setup — Siap Tempur](#2-setup--siap-tempur)
3. [Variabel — Kotak Penyimpan](#3-variabel--kotak-penyimpan)
4. [Tipe Data — Jenis-jenis Isi Kotak](#4-tipe-data--jenis-jenis-isi-kotak)
5. [Operator — Alat Hitung & Bandingin](#5-operator--alat-hitung--bandingin)
6. [Kondisi — Pengambil Keputusan](#6-kondisi--pengambil-keputusan)
7. [Perulangan / Loop — Kerja Berulang](#7-perulangan--loop--kerja-berulang)
8. [Fungsi — Mesin yang Bisa Dipanggil](#8-fungsi--mesin-yang-bisa-dipanggil)
9. [Array — Daftar Panjang](#9-array--daftar-panjang)
10. [Object — Kartu Identitas](#10-object--kartu-identitas)
11. [DOM — Ngoprek Halaman Web](#11-dom--ngoprek-halaman-web)
12. [Event — Nangkep Aksi User](#12-event--nangkep-aksi-user)
13. [Asynchronous — Kerja Sambil Nunggu](#13-asynchronous--kerja-sambil-nunggu)
14. [Fetch API — Ambil Data dari Internet](#14-fetch-api--ambil-data-dari-internet)
15. [Error Handling — Tangkap Kesalahan](#15-error-handling--tangkap-kesalahan)
16. [ES6+ — Fitur Keren Modern](#16-es6--fitur-keren-modern)
17. [OOP — Bikin Objek Kayak Nyata](#17-oop--bikin-objek-kayak-nyata)
18. [Module — Pisah-pisah File](#18-module--pisah-pisah-file)
19. [Tips Pro & Best Practice](#19-tips-pro--best-practice)
20. [Project Mini — Latihan Nyata](#20-project-mini--latihan-nyata)

---

## 1. Apa itu JavaScript?

Bayangin lo bikin rumah. HTML itu **dindingnya** (struktur), CSS itu **catnya** (tampilan), nah JavaScript itu **listriknya** — yang bikin rumah itu **hidup**, bisa dinyalain lampunya, buka pintunya, dll.

JavaScript (disingkat **JS**) adalah bahasa pemrograman yang bikin website jadi **interaktif**. Klik tombol → sesuatu terjadi. Isi form → data kekirim. Scroll → animasi jalan. Semua itu JS.

### Fakta penting:
- JS bisa jalan di **browser** (Chrome, Firefox, dll) langsung tanpa install apapun
- JS juga bisa jalan di **server** pakai Node.js (nanti kita bahas)
- JS adalah bahasa **paling populer** di dunia (survey Stack Overflow 10+ tahun berturut-turut)
- Belajar JS = bisa bikin website, aplikasi, bot, game, bahkan AI

---

## 2. Setup — Siap Tempur

### Cara paling gampang (langsung di browser):
1. Buka Chrome/Firefox
2. Klik kanan di halaman mana aja → **Inspect** (atau tekan `F12`)
3. Klik tab **Console**
4. Ketik kode JS langsung di situ → Enter!

### Cara proper (pakai VS Code):
```bash
# 1. Install Node.js dulu (buat jalanin JS di luar browser)
# Download di: nodejs.org

# 2. Cek udah keinstall belum
node --version   # harusnya muncul angka versi
npm --version

# 3. Bikin file baru
touch belajar.js

# 4. Jalanin file
node belajar.js
```

### Halo Dunia pertama lo:
```javascript
// Ini komentar — tidak dijalankan, cuma catatan
console.log("Halo Dunia!"); // Cetak teks ke layar
console.log("Gue lagi belajar JS!");
```

> 💡 `console.log()` itu kayak **mulut** JavaScript — apapun yang lo taruh di dalam kurung, dia yang "ngomong" ke layar.

---

## 3. Variabel — Kotak Penyimpan

Variabel itu kayak **kotak bertuliskan nama**. Lo taruh sesuatu di dalamnya, terus nanti bisa lo ambil lagi pakai namanya.

### 3 cara bikin variabel:

```javascript
// var — cara lama, hindari pemakaiannya
var nama = "Rixz";

// let — bisa diubah isinya, PAKAI INI untuk nilai yang berubah
let umur = 17;
umur = 18; // boleh diubah

// const — TIDAK BISA diubah, PAKAI INI untuk nilai tetap
const kota = "Indonesia";
// kota = "Jepang"; // ERROR! const tidak bisa diganti
```

### Aturan nama variabel:
```javascript
// ✅ Boleh
let namaLengkap = "Rixz Dev";     // camelCase — standar JS
let umur2 = 18;                    // boleh ada angka (bukan di depan)
let _rahasia = "password123";      // boleh pakai underscore

// ❌ Tidak boleh
// let 2nama = "salah";            // tidak boleh mulai dengan angka
// let nama-lengkap = "salah";     // tidak boleh pakai tanda minus
// let let = "salah";              // tidak boleh pakai kata kunci JS
```

### Contoh praktek:
```javascript
const namaGue = "Rixz";
let nilaiUjian = 75;
let sudahLulus = false;

console.log("Nama:", namaGue);
console.log("Nilai:", nilaiUjian);
console.log("Lulus?", sudahLulus);

// Update nilai
nilaiUjian = 90;
sudahLulus = true;
console.log("Nilai baru:", nilaiUjian);
console.log("Sekarang lulus?", sudahLulus);
```

---

## 4. Tipe Data — Jenis-jenis Isi Kotak

Sama kayak kotak beneran — ada kotak buat baju, buat makanan, buat uang. Di JS juga ada jenis-jenis data:

### Tipe data dasar (primitif):

```javascript
// 1. String — teks, diapit tanda kutip
let nama = "Rixz";
let kota = 'Jakarta';
let sapaan = `Halo, ${nama}!`; // template literal — bisa sisipkan variabel

// 2. Number — angka (bulat maupun desimal)
let umur = 17;
let tinggi = 170.5;
let hutang = -50000;

// 3. Boolean — hanya true atau false (benar atau salah)
let sudahMakan = true;
let sudahBelajar = false;

// 4. Undefined — variabel ada tapi belum diisi
let belumDiisi;
console.log(belumDiisi); // undefined

// 5. Null — sengaja dikosongkan
let dataPengguna = null;

// 6. BigInt — angka super besar
let populasiDunia = 8000000000n;

// 7. Symbol — identitas unik (jarang dipakai pemula)
let id = Symbol("id");
```

### Cek tipe data pakai `typeof`:
```javascript
console.log(typeof "Rixz");      // "string"
console.log(typeof 17);          // "number"
console.log(typeof true);        // "boolean"
console.log(typeof undefined);   // "undefined"
console.log(typeof null);        // "object" ← ini bug JS sejak dulu, hafalin aja
```

### String — fitur penting:
```javascript
let nama = "rixz engineering";

// Panjang teks
console.log(nama.length); // 17

// Ubah huruf besar/kecil
console.log(nama.toUpperCase()); // "RIXZ ENGINEERING"
console.log(nama.toLowerCase()); // "rixz engineering"

// Potong teks
console.log(nama.slice(0, 4));   // "rixz"
console.log(nama.slice(5));      // "engineering"

// Cek apakah ada teks tertentu
console.log(nama.includes("rixz")); // true
console.log(nama.includes("aners")); // false

// Ganti teks
console.log(nama.replace("rixz", "aners")); // "aners engineering"

// Pisah jadi array
let kalimat = "satu dua tiga";
console.log(kalimat.split(" ")); // ["satu", "dua", "tiga"]

// Template literal — cara modern gabungkan teks
let user = "Rixz";
let level = "Pro";
console.log(`User: ${user} | Level: ${level}`); // "User: Rixz | Level: Pro"
```

### Number — fitur penting:
```javascript
let angka = 3.14159;

// Bulatkan desimal
console.log(angka.toFixed(2)); // "3.14"

// Cek apakah angka
console.log(isNaN("abc"));  // true — bukan angka
console.log(isNaN(42));     // false — ini angka

// Math — objek bawaan JS buat matematika
console.log(Math.round(4.6));  // 5
console.log(Math.floor(4.9));  // 4 — bulatkan ke bawah
console.log(Math.ceil(4.1));   // 5 — bulatkan ke atas
console.log(Math.max(1, 5, 3)); // 5
console.log(Math.min(1, 5, 3)); // 1
console.log(Math.random());     // angka acak antara 0-1
console.log(Math.sqrt(16));     // 4 — akar kuadrat
console.log(Math.abs(-10));     // 10 — nilai mutlak

// Angka acak dalam range tertentu
let min = 1, max = 100;
let acak = Math.floor(Math.random() * (max - min + 1)) + min;
console.log(acak); // angka acak 1-100
```

---

## 5. Operator — Alat Hitung & Bandingin

### Operator Aritmatika (hitung-hitungan):
```javascript
let a = 10;
let b = 3;

console.log(a + b);  // 13 — tambah
console.log(a - b);  // 7  — kurang
console.log(a * b);  // 30 — kali
console.log(a / b);  // 3.333... — bagi
console.log(a % b);  // 1  — sisa bagi (modulo — hasil sisa pembagian)
console.log(a ** b); // 1000 — pangkat (10³)

// Shortcut
let x = 5;
x += 3;  // sama dengan x = x + 3 → 8
x -= 2;  // sama dengan x = x - 2 → 6
x *= 4;  // sama dengan x = x * 4 → 24
x /= 2;  // sama dengan x = x / 2 → 12
x++;     // tambah 1 → 13
x--;     // kurang 1 → 12
```

### Operator Perbandingan (hasilnya selalu true/false):
```javascript
console.log(5 == "5");   // true  — sama nilainya (tidak cek tipe)
console.log(5 === "5");  // false — sama nilai DAN tipe (SELALU PAKAI INI!)
console.log(5 !== "5");  // true  — tidak sama (strict)
console.log(5 > 3);      // true
console.log(5 < 3);      // false
console.log(5 >= 5);     // true
console.log(5 <= 4);     // false
```

> ⚠️ **PENTING:** Selalu pakai `===` bukan `==`. Kenapa? Karena `==` bisa nyebabkan bug aneh:
> ```javascript
> 0 == false   // true  ← aneh kan?
> 0 === false  // false ← ini yang bener
> ```

### Operator Logika:
```javascript
let udahMakan = true;
let udahMandi = false;

// && (AND) — kedua-duanya harus true
console.log(udahMakan && udahMandi); // false

// || (OR) — salah satu true sudah cukup
console.log(udahMakan || udahMandi); // true

// ! (NOT) — balik nilainya
console.log(!udahMakan); // false
console.log(!udahMandi); // true

// Contoh nyata
let umur = 17;
let punyaKTP = false;
let bolehMasuk = umur >= 18 && punyaKTP;
console.log("Boleh masuk?", bolehMasuk); // false
```

---

## 6. Kondisi — Pengambil Keputusan

Kondisi itu kayak **persimpangan jalan** — kalau ke kiri, kalau ke kanan.

### if / else if / else:
```javascript
let nilai = 85;

if (nilai >= 90) {
  console.log("Grade A — Luar biasa!");
} else if (nilai >= 80) {
  console.log("Grade B — Bagus!");
} else if (nilai >= 70) {
  console.log("Grade C — Cukup");
} else if (nilai >= 60) {
  console.log("Grade D — Kurang");
} else {
  console.log("Grade E — Perlu belajar lebih giat");
}
```

### Switch — kalau banyak pilihan:
```javascript
let hari = "Senin";

switch (hari) {
  case "Senin":
    console.log("Awal pekan, semangat!");
    break;
  case "Jumat":
    console.log("Hampir weekend!");
    break;
  case "Sabtu":
  case "Minggu":
    console.log("Weekend, istirahat!");
    break;
  default:
    console.log("Hari biasa");
}
```

> ⚠️ Jangan lupa `break`! Kalau tidak ada break, JS lanjut ke case berikutnya (ini disebut **fall-through** — mengalir ke bawah tanpa berhenti).

### Ternary Operator — kondisi singkat:
```javascript
// Format: kondisi ? jalankan_kalau_true : jalankan_kalau_false
let umur = 18;
let status = umur >= 18 ? "Dewasa" : "Anak-anak";
console.log(status); // "Dewasa"

// Nested ternary (jangan terlalu dalam, susah dibaca)
let nilai = 75;
let grade = nilai >= 90 ? "A" : nilai >= 80 ? "B" : nilai >= 70 ? "C" : "D";
console.log(grade); // "C"
```

### Nullish Coalescing `??` — nilai default:
```javascript
let nama = null;
let tampilan = nama ?? "Pengguna Anonim";
console.log(tampilan); // "Pengguna Anonim"

let username = "rixz";
let tampilan2 = username ?? "Anonim";
console.log(tampilan2); // "rixz"
```

### Optional Chaining `?.` — akses aman:
```javascript
let user = {
  nama: "Rixz",
  // tidak ada properti alamat
};

// Tanpa optional chaining — ERROR kalau alamat tidak ada
// console.log(user.alamat.kota); // TypeError!

// Dengan optional chaining — aman
console.log(user?.alamat?.kota); // undefined (tidak error)
```

---

## 7. Perulangan / Loop — Kerja Berulang

Loop itu kayak **mesin fotokopi** — lo set berapa kali, dia kerjain terus sampai selesai.

### for loop — kalau tau berapa kali:
```javascript
// Hitung 1 sampai 10
for (let i = 1; i <= 10; i++) {
  console.log(i);
}

// Cetak tabel perkalian 3
for (let i = 1; i <= 10; i++) {
  console.log(`3 x ${i} = ${3 * i}`);
}
```

> 💡 Anatomi for loop:
> ```
> for (awal; kondisi; langkah) { ... }
>        ↑       ↑        ↑
>      i=1    i<=10      i++
>   mulai dari 1  berhenti kalau > 10  tambah 1 setiap putaran
> ```

### while loop — kalau tidak tau berapa kali:
```javascript
let uang = 100000;
let harga = 25000;
let beliKe = 0;

while (uang >= harga) {
  uang -= harga;
  beliKe++;
  console.log(`Beli ke-${beliKe}, sisa uang: Rp${uang}`);
}

console.log(`Total beli: ${beliKe} item`);
```

### do...while — jalankan dulu, cek kondisi belakangan:
```javascript
let angka;
let tebakan = 7;

do {
  angka = Math.floor(Math.random() * 10) + 1;
  console.log(`Keluar angka: ${angka}`);
} while (angka !== tebakan);

console.log(`Akhirnya keluar angka ${tebakan}!`);
```

### for...of — loop array (nanti lebih detail di bagian Array):
```javascript
let buah = ["apel", "mangga", "jeruk", "pisang"];

for (let item of buah) {
  console.log(item);
}
```

### for...in — loop properti object:
```javascript
let orang = { nama: "Rixz", umur: 17, kota: "Indonesia" };

for (let key in orang) {
  console.log(`${key}: ${orang[key]}`);
}
```

### break & continue — kendalikan loop:
```javascript
// break — hentikan loop sepenuhnya
for (let i = 1; i <= 10; i++) {
  if (i === 5) break; // berhenti di 5
  console.log(i); // cetak 1, 2, 3, 4
}

// continue — skip iterasi ini, lanjut ke berikutnya
for (let i = 1; i <= 10; i++) {
  if (i % 2 === 0) continue; // skip angka genap
  console.log(i); // cetak 1, 3, 5, 7, 9
}
```

---

## 8. Fungsi — Mesin yang Bisa Dipanggil

Fungsi itu kayak **resep masakan**. Lo tulis sekali, bisa dipakai berkali-kali. Masukkan bahan (parameter — nilai yang dikirim masuk ke fungsi), keluar makanan (return value — nilai yang dihasilkan fungsi).

### Deklarasi fungsi biasa:
```javascript
function sapa(nama) {
  return `Halo, ${nama}! Selamat datang di ANERs.`;
}

let pesan = sapa("Rixz");
console.log(pesan); // "Halo, Rixz! Selamat datang di ANERs."
console.log(sapa("Budi")); // "Halo, Budi! Selamat datang di ANERs."
```

### Fungsi dengan banyak parameter:
```javascript
function hitung(a, b, operasi) {
  if (operasi === "tambah") return a + b;
  if (operasi === "kurang") return a - b;
  if (operasi === "kali")   return a * b;
  if (operasi === "bagi")   return a / b;
  return "Operasi tidak dikenal";
}

console.log(hitung(10, 5, "tambah")); // 15
console.log(hitung(10, 5, "kali"));   // 50
console.log(hitung(10, 5, "bagi"));   // 2
```

### Default parameter — nilai kalau tidak dikirim:
```javascript
function buat_akun(nama, role = "user", level = 1) {
  return { nama, role, level };
}

console.log(buat_akun("Rixz", "admin", 99)); // { nama: 'Rixz', role: 'admin', level: 99 }
console.log(buat_akun("Budi"));              // { nama: 'Budi', role: 'user', level: 1 }
```

### Arrow Function — cara singkat modern:
```javascript
// Fungsi biasa
function kuadrat(x) {
  return x * x;
}

// Arrow function — lebih ringkas
const kuadrat = (x) => x * x;          // satu baris
const kuadrat = x => x * x;            // kalau satu parameter, kurung boleh hilang

// Kalau lebih dari satu baris
const proses = (a, b) => {
  let hasil = a * b;
  hasil += 10;
  return hasil;
};

console.log(kuadrat(5));    // 25
console.log(proses(3, 4));  // 22
```

### Fungsi memanggil fungsi lain:
```javascript
function celsius_ke_fahrenheit(c) {
  return (c * 9/5) + 32;
}

function tampilkan_suhu(celcius) {
  let fahrenheit = celsius_ke_fahrenheit(celcius);
  console.log(`${celcius}°C = ${fahrenheit}°F`);
}

tampilkan_suhu(100); // "100°C = 212°F"
tampilkan_suhu(37);  // "37°C = 98.6°F"
```

### Rest Parameter — terima banyak argumen:
```javascript
function jumlahkan(...angka) {
  let total = 0;
  for (let n of angka) {
    total += n;
  }
  return total;
}

console.log(jumlahkan(1, 2, 3));          // 6
console.log(jumlahkan(10, 20, 30, 40));   // 100
console.log(jumlahkan(5));                 // 5
```

---

## 9. Array — Daftar Panjang

Array itu kayak **lemari laci bernomor**. Laci nomor 0, 1, 2, 3... (dimulai dari 0, ingat ya!).

### Membuat dan mengakses array:
```javascript
let buah = ["apel", "mangga", "jeruk", "pisang"];

console.log(buah[0]); // "apel"   ← index 0 = pertama
console.log(buah[1]); // "mangga"
console.log(buah[3]); // "pisang" ← index 3 = keempat
console.log(buah.length); // 4 — jumlah item

// Ganti item
buah[1] = "durian";
console.log(buah); // ["apel", "durian", "jeruk", "pisang"]
```

### Method array penting:
```javascript
let arr = [3, 1, 4, 1, 5, 9, 2, 6];

// Tambah/hapus di ujung
arr.push(7);         // tambah di belakang → [..., 7]
arr.pop();           // hapus dari belakang → keluarkan 7

// Tambah/hapus di depan
arr.unshift(0);      // tambah di depan → [0, 3, 1, ...]
arr.shift();         // hapus dari depan → keluarkan 0

// Cari index
console.log(arr.indexOf(5));    // 4 — posisi angka 5
console.log(arr.includes(9));   // true — ada angka 9?

// Gabungkan jadi string
let kata = ["Halo", "dunia", "dari", "ANERs"];
console.log(kata.join(" ")); // "Halo dunia dari ANERs"
console.log(kata.join("-")); // "Halo-dunia-dari-ANERs"

// Balik urutan
let angka = [1, 2, 3, 4, 5];
angka.reverse();
console.log(angka); // [5, 4, 3, 2, 1]

// Sortir
let acak = [3, 1, 4, 1, 5, 9];
acak.sort((a, b) => a - b); // ascending
console.log(acak); // [1, 1, 3, 4, 5, 9]

acak.sort((a, b) => b - a); // descending
console.log(acak); // [9, 5, 4, 3, 1, 1]

// Potong array
let buah2 = ["apel", "manga", "jeruk", "pisang", "semangka"];
console.log(buah2.slice(1, 3)); // ["manga", "jeruk"] ← dari index 1 sampai sebelum 3
console.log(buah2.slice(2));    // ["jeruk", "pisang", "semangka"]

// Hapus/ganti bagian array
let angka2 = [1, 2, 3, 4, 5];
angka2.splice(2, 1);           // hapus 1 item dari index 2
console.log(angka2);           // [1, 2, 4, 5]

angka2.splice(1, 0, 99, 100);  // sisipkan di index 1, hapus 0 item
console.log(angka2);           // [1, 99, 100, 2, 4, 5]
```

### Array Methods Fungsional — WAJIB dikuasai:
```javascript
let angka = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

// forEach — lakukan sesuatu untuk setiap item (tidak return array baru)
angka.forEach(n => console.log(n * 2));

// map — ubah setiap item, hasilkan array baru
let dikalikaDua = angka.map(n => n * 2);
console.log(dikalikaDua); // [2, 4, 6, 8, 10, 12, 14, 16, 18, 20]

// filter — ambil item yang memenuhi syarat
let genap = angka.filter(n => n % 2 === 0);
console.log(genap); // [2, 4, 6, 8, 10]

// find — ambil item PERTAMA yang memenuhi syarat
let pertamaLebihDari5 = angka.find(n => n > 5);
console.log(pertamaLebihDari5); // 6

// some — apakah ADA item yang memenuhi syarat?
console.log(angka.some(n => n > 9));   // true
console.log(angka.some(n => n > 100)); // false

// every — apakah SEMUA item memenuhi syarat?
console.log(angka.every(n => n > 0));  // true
console.log(angka.every(n => n > 5));  // false

// reduce — gabungkan semua item jadi satu nilai
let total = angka.reduce((akumulator, n) => akumulator + n, 0);
console.log(total); // 55

// flat — ratakan array bersarang
let nested = [1, [2, 3], [4, [5, 6]]];
console.log(nested.flat());    // [1, 2, 3, 4, [5, 6]]
console.log(nested.flat(2));   // [1, 2, 3, 4, 5, 6]
```

### Contoh nyata — kombinasi methods:
```javascript
let mahasiswa = [
  { nama: "Rixz", nilai: 95 },
  { nama: "Budi", nilai: 60 },
  { nama: "Citra", nilai: 80 },
  { nama: "Dedi", nilai: 45 },
  { nama: "Eka", nilai: 88 },
];

// Ambil mahasiswa yang lulus (nilai >= 70)
let lulus = mahasiswa
  .filter(m => m.nilai >= 70)
  .map(m => m.nama);

console.log("Yang lulus:", lulus); // ["Rixz", "Citra", "Eka"]

// Hitung rata-rata nilai
let rata = mahasiswa.reduce((sum, m) => sum + m.nilai, 0) / mahasiswa.length;
console.log("Rata-rata:", rata.toFixed(2)); // "73.60"
```

---

## 10. Object — Kartu Identitas

Object itu kayak **kartu identitas** atau **formulir**. Ada kolom-kolomnya (property — atribut/kolom pada object), dan tiap kolom ada isinya (value — isi dari property).

### Membuat object:
```javascript
let orang = {
  nama: "Rixz",
  umur: 17,
  kota: "Indonesia",
  hobi: ["coding", "security research", "musik"],
  aktif: true
};

// Akses property
console.log(orang.nama);       // "Rixz" — dot notation
console.log(orang["umur"]);    // 17 — bracket notation
console.log(orang.hobi[0]);    // "coding"

// Ubah property
orang.umur = 18;
orang.kota = "Jakarta";

// Tambah property baru
orang.email = "rixz@example.com";
orang.level = "Pro";

// Hapus property
delete orang.aktif;

console.log(orang);
```

### Method dalam object (fungsi di dalam object):
```javascript
let kalkulator = {
  hasil: 0,

  tambah(angka) {
    this.hasil += angka; // 'this' merujuk ke object kalkulator itu sendiri
    return this;         // return this buat chaining
  },

  kurang(angka) {
    this.hasil -= angka;
    return this;
  },

  reset() {
    this.hasil = 0;
    return this;
  },

  tampilkan() {
    console.log("Hasil:", this.hasil);
    return this;
  }
};

// Method chaining — panggil beruntun
kalkulator
  .tambah(100)
  .tambah(50)
  .kurang(30)
  .tampilkan()    // Hasil: 120
  .reset()
  .tampilkan();   // Hasil: 0
```

### Destructuring — bongkar object/array:
```javascript
// Object destructuring
let { nama, umur, kota } = orang;
console.log(nama);  // "Rixz"
console.log(umur);  // 18

// Rename waktu destructure
let { nama: namaUser, kota: kotaUser } = orang;
console.log(namaUser);  // "Rixz"
console.log(kotaUser);  // "Jakarta"

// Default value
let { level = "Beginner" } = orang;
console.log(level); // "Pro" (karena sudah ada)

// Array destructuring
let [pertama, kedua, ...sisanya] = [1, 2, 3, 4, 5];
console.log(pertama);  // 1
console.log(kedua);    // 2
console.log(sisanya);  // [3, 4, 5]
```

### Spread Operator `...` — sebar isi:
```javascript
// Spread array
let arr1 = [1, 2, 3];
let arr2 = [4, 5, 6];
let gabung = [...arr1, ...arr2];
console.log(gabung); // [1, 2, 3, 4, 5, 6]

// Copy array (bukan reference)
let original = [1, 2, 3];
let copy = [...original];
copy.push(4);
console.log(original); // [1, 2, 3] — tidak berubah
console.log(copy);     // [1, 2, 3, 4]

// Spread object
let base = { nama: "Rixz", level: 1 };
let updated = { ...base, level: 99, role: "admin" };
console.log(updated); // { nama: "Rixz", level: 99, role: "admin" }
```

---

## 11. DOM — Ngoprek Halaman Web

DOM (Document Object Model — model dokumen yang bisa diakses JS) itu kayak **peta interaktif** halaman web lo. Pakai JS, lo bisa ubah, tambah, hapus elemen HTML secara langsung.

### Setup HTML dulu:
```html
<!DOCTYPE html>
<html>
<head>
  <title>Belajar DOM</title>
</head>
<body>
  <h1 id="judul">Halo!</h1>
  <p class="teks">Ini paragraf pertama.</p>
  <p class="teks">Ini paragraf kedua.</p>
  <button id="tombol">Klik Gue!</button>
  <ul id="daftar">
    <li>Item 1</li>
    <li>Item 2</li>
  </ul>
  <script src="app.js"></script>
</body>
</html>
```

### Pilih elemen (selector):
```javascript
// Pilih berdasarkan ID
let judul = document.getElementById("judul");

// Pilih berdasarkan class (semua yang punya class ini)
let semuaTeks = document.getElementsByClassName("teks"); // HTMLCollection

// Pilih berdasarkan tag
let semuaLi = document.getElementsByTagName("li");

// querySelector — lebih modern, pakai CSS selector
let judulQ = document.querySelector("#judul");        // ID
let paragraf = document.querySelector(".teks");        // class (ambil PERTAMA)
let semuaP = document.querySelectorAll(".teks");       // class (ambil SEMUA)
let tombol = document.querySelector("button");
```

### Ubah konten:
```javascript
let judul = document.querySelector("#judul");

// Ubah teks
judul.textContent = "Selamat Datang!";
judul.innerHTML = "<span style='color:blue'>Halo Dunia!</span>"; // bisa HTML

// Baca teks
console.log(judul.textContent);
```

### Ubah style:
```javascript
let judul = document.querySelector("#judul");

// Langsung lewat style
judul.style.color = "red";
judul.style.fontSize = "40px";
judul.style.backgroundColor = "black";
judul.style.fontFamily = "monospace";

// Lewat class (lebih proper)
judul.classList.add("aktif");      // tambah class
judul.classList.remove("aktif");   // hapus class
judul.classList.toggle("aktif");   // kalau ada hapus, kalau tidak ada tambahkan
console.log(judul.classList.contains("aktif")); // cek ada atau tidak
```

### Ubah/baca atribut:
```javascript
let tombol = document.querySelector("#tombol");

tombol.setAttribute("disabled", "true"); // nonaktifkan tombol
tombol.removeAttribute("disabled");      // aktifkan lagi
console.log(tombol.getAttribute("id"));  // "tombol"
```

### Buat dan tambah elemen baru:
```javascript
let daftar = document.querySelector("#daftar");

// Buat elemen baru
let liBaru = document.createElement("li");
liBaru.textContent = "Item 3 — Baru Ditambahkan!";
liBaru.style.color = "green";

// Tambahkan ke halaman
daftar.appendChild(liBaru);  // tambah di paling bawah

// Alternatif: insertAdjacentHTML
daftar.insertAdjacentHTML("beforeend", "<li>Item 4</li>");
```

### Hapus elemen:
```javascript
let daftar = document.querySelector("#daftar");
let item = daftar.querySelector("li"); // ambil li pertama
item.remove(); // hapus
```

---

## 12. Event — Nangkep Aksi User

Event itu kayak **alarm** yang bunyi kalau user melakukan sesuatu — klik, ketik, scroll, hover, dll.

### addEventListener — cara paling proper:
```javascript
let tombol = document.querySelector("#tombol");

tombol.addEventListener("click", function() {
  console.log("Tombol diklik!");
  alert("Halo dari ANERs!");
});

// Dengan arrow function
tombol.addEventListener("click", () => {
  tombol.textContent = "Sudah diklik!";
  tombol.style.backgroundColor = "green";
});
```

### Event yang sering dipakai:
```javascript
let input = document.querySelector("input");
let form = document.querySelector("form");
let kotak = document.querySelector(".kotak");

// Keyboard events
input.addEventListener("keydown", (e) => {
  console.log("Tombol ditekan:", e.key);  // e.key = tombol apa yang ditekan
});

input.addEventListener("input", (e) => {
  console.log("Isi input:", e.target.value); // nilai saat ini
});

// Form submit
form.addEventListener("submit", (e) => {
  e.preventDefault(); // cegah halaman reload
  console.log("Form dikirim!");
});

// Mouse events
kotak.addEventListener("mouseover", () => {
  kotak.style.backgroundColor = "blue"; // saat kursor masuk
});

kotak.addEventListener("mouseout", () => {
  kotak.style.backgroundColor = ""; // saat kursor keluar
});

// Window events
window.addEventListener("scroll", () => {
  console.log("Scroll position:", window.scrollY);
});

window.addEventListener("resize", () => {
  console.log("Lebar window:", window.innerWidth);
});

// DOMContentLoaded — jalankan setelah HTML selesai dimuat
document.addEventListener("DOMContentLoaded", () => {
  console.log("Halaman siap!");
});
```

### Event Object:
```javascript
document.addEventListener("click", (event) => {
  console.log("Diklik di:", event.clientX, event.clientY); // posisi kursor
  console.log("Target elemen:", event.target);              // elemen yang diklik
  console.log("Type event:", event.type);                   // "click"
});
```

---

## 13. Asynchronous — Kerja Sambil Nunggu

Bayangin lo pesan makanan online. Lo tidak nunggu berdiri di depan pintu — lo main HP dulu sambil nunggu. Itu namanya **asynchronous** (= tidak langsung, bekerja di latar belakang sambil lanjut hal lain).

### Callback — cara lama:
```javascript
// Simulasi ambil data (nunggu 2 detik)
function ambilData(callback) {
  setTimeout(() => {
    callback({ nama: "Rixz", level: "Pro" });
  }, 2000);
}

ambilData((data) => {
  console.log("Data diterima:", data);
});
console.log("Ini dijalankan SEBELUM data diterima!");
// Output urutan:
// "Ini dijalankan SEBELUM data diterima!"
// (2 detik kemudian)
// "Data diterima: { nama: 'Rixz', level: 'Pro' }"
```

### Promise — cara lebih modern:
```javascript
// Promise = janji, nanti hasilnya bisa .then() atau .catch()
function ambilDataPromise(userId) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      if (userId > 0) {
        resolve({ id: userId, nama: "Rixz", email: "rixz@example.com" });
      } else {
        reject(new Error("ID tidak valid!"));
      }
    }, 1000);
  });
}

// Pakai promise
ambilDataPromise(1)
  .then(data => {
    console.log("Sukses:", data);
    return data.nama; // bisa diteruskan ke .then berikutnya
  })
  .then(nama => {
    console.log("Nama:", nama);
  })
  .catch(error => {
    console.log("Error:", error.message);
  })
  .finally(() => {
    console.log("Selesai (sukses atau gagal)");
  });
```

### Async/Await — cara PALING modern dan mudah dibaca:
```javascript
// async/await = cara menulis promise yang keliatan kayak kode biasa
async function tampilkanPengguna(userId) {
  try {
    console.log("Mulai ambil data...");
    
    let data = await ambilDataPromise(userId); // tunggu sampai selesai
    console.log("Data diterima:", data);
    
    console.log("Selesai!");
    return data;
    
  } catch (error) {
    console.log("Terjadi error:", error.message);
  }
}

tampilkanPengguna(1);
tampilkanPengguna(-1); // akan masuk catch
```

### setTimeout & setInterval:
```javascript
// setTimeout — jalankan sekali setelah delay
let timer = setTimeout(() => {
  console.log("Ini jalan setelah 3 detik");
}, 3000);

// clearTimeout — batalkan sebelum jalan
clearTimeout(timer);

// setInterval — jalankan berulang setiap interval
let counter = 0;
let interval = setInterval(() => {
  counter++;
  console.log(`Tick ke-${counter}`);
  
  if (counter >= 5) {
    clearInterval(interval); // hentikan setelah 5 kali
    console.log("Interval dihentikan");
  }
}, 1000);
```

---

## 14. Fetch API — Ambil Data dari Internet

Fetch itu cara JS buat **minta data ke server** — kayak chatting sama API (Application Programming Interface — jembatan yang menghubungkan dua aplikasi).

### Fetch dasar:
```javascript
// GET request — ambil data
async function ambilJoke() {
  try {
    let response = await fetch("https://official-joke-api.appspot.com/random_joke");
    
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }
    
    let data = await response.json(); // parse JSON
    console.log("Setup:", data.setup);
    console.log("Punchline:", data.punchline);
    
  } catch (error) {
    console.log("Gagal ambil data:", error.message);
  }
}

ambilJoke();
```

### POST request — kirim data:
```javascript
async function buatPost(judulPost, isiPost) {
  try {
    let response = await fetch("https://jsonplaceholder.typicode.com/posts", {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify({
        title: judulPost,
        body: isiPost,
        userId: 1,
      }),
    });

    let data = await response.json();
    console.log("Post berhasil dibuat:", data);
    
  } catch (error) {
    console.log("Gagal:", error.message);
  }
}

buatPost("Judul Post Gue", "Ini isi post dari ANERs");
```

### Fetch multiple — ambil banyak sekaligus:
```javascript
async function ambilSemua() {
  try {
    // Promise.all — jalankan semua sekaligus, tunggu semuanya selesai
    let [users, posts, todos] = await Promise.all([
      fetch("https://jsonplaceholder.typicode.com/users").then(r => r.json()),
      fetch("https://jsonplaceholder.typicode.com/posts").then(r => r.json()),
      fetch("https://jsonplaceholder.typicode.com/todos").then(r => r.json()),
    ]);
    
    console.log("Total users:", users.length);
    console.log("Total posts:", posts.length);
    console.log("Total todos:", todos.length);
    
  } catch (error) {
    console.log("Error:", error.message);
  }
}

ambilSemua();
```

---

## 15. Error Handling — Tangkap Kesalahan

Error itu **normal** dalam coding. Yang penting tau cara tangkapnya biar program tidak crash.

### try / catch / finally:
```javascript
function bagi(a, b) {
  if (b === 0) {
    throw new Error("Tidak bisa bagi dengan nol!"); // lempar error custom
  }
  return a / b;
}

try {
  let hasil = bagi(10, 2);
  console.log("Hasil:", hasil); // 5

  let error = bagi(10, 0); // ini akan throw error
  console.log("Ini tidak akan dijalankan");
  
} catch (error) {
  console.log("Error tertangkap:", error.message);
  
} finally {
  console.log("Ini SELALU jalan, error atau tidak");
}
```

### Jenis-jenis Error bawaan JS:
```javascript
// TypeError — tipe data salah
try {
  null.toString();
} catch (e) {
  console.log(e instanceof TypeError); // true
  console.log(e.message);
}

// ReferenceError — variabel tidak ditemukan
try {
  console.log(variabelTidakAda);
} catch (e) {
  console.log(e instanceof ReferenceError); // true
}

// SyntaxError — biasanya muncul waktu parse kode
try {
  JSON.parse("{ini: bukan json valid}");
} catch (e) {
  console.log(e instanceof SyntaxError); // true
  console.log("JSON tidak valid:", e.message);
}

// RangeError — angka di luar jangkauan
try {
  new Array(-1);
} catch (e) {
  console.log(e instanceof RangeError); // true
}
```

### Custom Error class:
```javascript
class ValidationError extends Error {
  constructor(field, message) {
    super(message);
    this.name = "ValidationError";
    this.field = field;
  }
}

class NetworkError extends Error {
  constructor(statusCode, message) {
    super(message);
    this.name = "NetworkError";
    this.statusCode = statusCode;
  }
}

function validasiEmail(email) {
  if (!email.includes("@")) {
    throw new ValidationError("email", "Format email tidak valid!");
  }
  return true;
}

try {
  validasiEmail("rixz-tanpa-at.com");
} catch (e) {
  if (e instanceof ValidationError) {
    console.log(`Field "${e.field}": ${e.message}`);
  } else {
    throw e; // re-throw kalau bukan jenis yang kita handle
  }
}
```

---

## 16. ES6+ — Fitur Keren Modern

ES6 (ECMAScript 2015 ke atas) adalah versi JS yang bawa banyak fitur baru yang **wajib** lo kuasai.

### Shorthand properties:
```javascript
let nama = "Rixz";
let umur = 17;
let kota = "Indonesia";

// Cara lama
let orang1 = { nama: nama, umur: umur, kota: kota };

// Shorthand — kalau nama variabel sama dengan nama property
let orang2 = { nama, umur, kota };
console.log(orang2); // { nama: "Rixz", umur: 17, kota: "Indonesia" }
```

### Computed property names:
```javascript
let key = "nama";
let obj = {
  [key]: "Rixz",          // property key dinamis
  [`get_${key}`]: () => "Rixz", // method dengan nama dinamis
};

console.log(obj.nama);     // "Rixz"
console.log(obj.get_nama()); // "Rixz"
```

### Symbol & Iterator:
```javascript
// Symbol — nilai unik yang tidak pernah sama
let id1 = Symbol("id");
let id2 = Symbol("id");
console.log(id1 === id2); // false — selalu unik
```

### Generator Function:
```javascript
function* hitungNaik(mulai = 0) {
  let i = mulai;
  while (true) {
    yield i++; // pause dan return nilai, lanjut pas dipanggil lagi
  }
}

let gen = hitungNaik(1);
console.log(gen.next().value); // 1
console.log(gen.next().value); // 2
console.log(gen.next().value); // 3
```

### WeakMap & WeakSet:
```javascript
// WeakMap — seperti Map tapi key harus object, dan bisa di-garbage collect
let cache = new WeakMap();
let obj = {};
cache.set(obj, "data penting");
console.log(cache.get(obj)); // "data penting"
```

### Map dan Set:
```javascript
// Map — seperti object tapi key bisa apa saja
let map = new Map();
map.set("nama", "Rixz");
map.set(1, "angka satu");
map.set(true, "nilai boolean");

console.log(map.get("nama")); // "Rixz"
console.log(map.size);        // 3

for (let [key, value] of map) {
  console.log(`${key} → ${value}`);
}

// Set — array tapi tidak boleh duplikat
let set = new Set([1, 2, 3, 2, 1, 4]);
console.log(set); // Set(4) {1, 2, 3, 4} — duplikat hilang otomatis

set.add(5);
set.delete(1);
console.log(set.has(2)); // true
console.log(set.size);   // 4

// Trick: hilangkan duplikat dari array
let arrayDuplikat = [1, 1, 2, 3, 3, 4];
let unik = [...new Set(arrayDuplikat)];
console.log(unik); // [1, 2, 3, 4]
```

---

## 17. OOP — Bikin Objek Kayak Nyata

OOP (Object-Oriented Programming — paradigma pemrograman yang menggunakan konsep objek) itu cara mikir pemrograman yang ngeliat semuanya sebagai "benda".

### Class dasar:
```javascript
class Karakter {
  // constructor — dipanggil saat bikin object baru
  constructor(nama, kelas, level = 1) {
    this.nama = nama;
    this.kelas = kelas;
    this.level = level;
    this.hp = level * 100;
    this.exp = 0;
  }

  // Method
  info() {
    return `[${this.kelas}] ${this.nama} | Lv.${this.level} | HP: ${this.hp}`;
  }

  serang(target) {
    let damage = this.level * 10;
    target.hp -= damage;
    console.log(`${this.nama} menyerang ${target.nama}! Damage: ${damage}`);
    
    if (target.hp <= 0) {
      console.log(`${target.nama} kalah!`);
      this.tambahExp(50);
    }
  }

  tambahExp(jumlah) {
    this.exp += jumlah;
    if (this.exp >= 100) {
      this.levelUp();
    }
  }

  levelUp() {
    this.level++;
    this.hp = this.level * 100;
    this.exp = 0;
    console.log(`${this.nama} naik ke Level ${this.level}!`);
  }
}

let hero = new Karakter("Rixz", "Hacker", 5);
let musuh = new Karakter("Bot", "Enemy", 3);

console.log(hero.info());
hero.serang(musuh);
hero.serang(musuh);
hero.serang(musuh);
```

### Inheritance — pewarisan:
```javascript
// Class anak mewarisi semua dari class induk
class Hacker extends Karakter {
  constructor(nama, level) {
    super(nama, "Hacker", level); // panggil constructor parent
    this.tool = "0day exploit";
    this.stealth = true;
  }

  // Override method parent
  serang(target) {
    console.log(`[STEALTH] ${this.nama} menggunakan ${this.tool}`);
    let damage = this.level * 20; // damage lebih besar
    target.hp -= damage;
    console.log(`Critical hit! Damage: ${damage}`);
  }

  // Method eksklusif Hacker
  hackSistem(target) {
    console.log(`${this.nama} berhasil hack sistem ${target}!`);
    return `Access granted: ${target}`;
  }
}

class Warrior extends Karakter {
  constructor(nama, level) {
    super(nama, "Warrior", level);
    this.armor = 50;
  }

  // Override method
  info() {
    return `${super.info()} | Armor: ${this.armor}`; // super = panggil method parent
  }
}

let rxz = new Hacker("rixz", 99);
let bot = new Warrior("GuardBot", 10);

console.log(rxz.info());
console.log(bot.info());
rxz.serang(bot);
console.log(rxz.hackSistem("mainframe"));
```

### Static method & property:
```javascript
class MathHelper {
  static PI = 3.14159265358979;

  static luasLingkaran(r) {
    return MathHelper.PI * r * r;
  }

  static kelilingLingkaran(r) {
    return 2 * MathHelper.PI * r;
  }
}

// Static dipanggil langsung dari class, bukan dari instance
console.log(MathHelper.luasLingkaran(5));     // 78.539...
console.log(MathHelper.kelilingLingkaran(5)); // 31.415...
// TIDAK perlu: new MathHelper()
```

### Getter & Setter:
```javascript
class Suhu {
  #celsius; // private field (# = tidak bisa diakses dari luar)

  constructor(celsius) {
    this.#celsius = celsius;
  }

  get celsius() { return this.#celsius; }
  get fahrenheit() { return (this.#celsius * 9/5) + 32; }
  get kelvin() { return this.#celsius + 273.15; }

  set celsius(nilai) {
    if (nilai < -273.15) throw new Error("Di bawah nol absolut!");
    this.#celsius = nilai;
  }
}

let suhu = new Suhu(100);
console.log(suhu.celsius);    // 100
console.log(suhu.fahrenheit); // 212
console.log(suhu.kelvin);     // 373.15

suhu.celsius = 37;
console.log(`Suhu tubuh: ${suhu.celsius}°C = ${suhu.fahrenheit}°F`);
```

---

## 18. Module — Pisah-pisah File

Module itu cara **memisahkan kode ke banyak file** biar rapi dan bisa dipakai ulang.

### Export:
```javascript
// utils.js
export const PI = 3.14159;

export function tambah(a, b) { return a + b; }
export function kurang(a, b) { return a - b; }

// Default export — satu file satu default
export default function kali(a, b) { return a * b; }
```

### Import:
```javascript
// main.js
import kali, { PI, tambah, kurang } from "./utils.js"; // default + named

console.log(tambah(5, 3));  // 8
console.log(kurang(10, 4)); // 6
console.log(kali(6, 7));    // 42
console.log(PI);            // 3.14159

// Import semua dengan alias
import * as utils from "./utils.js";
console.log(utils.tambah(1, 2)); // 3
```

### Dynamic import — load saat dibutuhkan:
```javascript
async function loadFeature() {
  const { tambah } = await import("./utils.js");
  console.log(tambah(1, 2));
}
```

---

## 19. Tips Pro & Best Practice

### ✅ Hal yang HARUS dilakukan:

```javascript
// 1. Selalu pakai const dulu, ganti ke let kalau perlu diubah
const MAX_RETRY = 3;
let retryCount = 0;

// 2. Pakai === bukan ==
if (x === null) { ... }

// 3. Kasih nama yang deskriptif
// ❌ Buruk
let d = new Date();
let n = d.getDay();
// ✅ Bagus
let tanggalSekarang = new Date();
let hariIni = tanggalSekarang.getDay();

// 4. Fungsi hanya lakukan SATU hal
// ❌ Buruk — fungsi ini terlalu banyak tanggung jawab
function prosesUser(user) {
  validasiUser(user);
  simpanDatabase(user);
  kirimEmail(user);
  updateUI(user);
}
// ✅ Bagus — pisah jadi fungsi kecil
async function daftarkanUser(userData) {
  const userValid = validasiUser(userData);
  if (!userValid) return;
  const userId = await simpanDatabase(userData);
  await kirimEmailKonfirmasi(userData.email);
  tampilkanPesanSukses(userId);
}

// 5. Handle error selalu
async function fetchData(url) {
  try {
    const res = await fetch(url);
    if (!res.ok) throw new Error(`HTTP ${res.status}`);
    return await res.json();
  } catch (err) {
    console.error("Fetch gagal:", err.message);
    return null;
  }
}

// 6. Pakai optional chaining
const kota = user?.alamat?.kota ?? "Tidak diketahui";

// 7. Gunakan Array methods daripada loop manual
// ❌ Buruk
let hasil = [];
for (let i = 0; i < data.length; i++) {
  if (data[i].aktif) {
    hasil.push(data[i].nama);
  }
}
// ✅ Bagus
let hasil = data.filter(d => d.aktif).map(d => d.nama);
```

### ❌ Hal yang JANGAN dilakukan:
```javascript
// 1. Jangan pakai var
var x = 1; // ❌ gunakan let atau const

// 2. Jangan eval()
eval("kode berbahaya"); // ❌ SANGAT berbahaya, bisa injeksi kode

// 3. Jangan ubah prototype bawaan
Array.prototype.hitung = function() {}; // ❌ bisa rusak library lain

// 4. Jangan blocking dengan loop tak terbatas
while(true) { /* tanpa break */ } // ❌ browser/node crash

// 5. Jangan abaikan promise
fetch(url); // ❌ harus di-await atau .then()
await fetch(url); // ✅
```

### Konsep penting yang harus dipahami:
```javascript
// HOISTING — deklarasi fungsi & var diangkat ke atas
sayHello(); // bisa dipanggil sebelum deklarasi
function sayHello() { console.log("Halo!"); }

// CLOSURE — fungsi yang "ingat" variabel dari scope luar
function buat_counter() {
  let count = 0; // variabel ini "terjebak" di dalam
  return {
    tambah: () => ++count,
    kurang: () => --count,
    nilai: () => count,
  };
}
let counter = buat_counter();
counter.tambah(); counter.tambah(); counter.tambah();
console.log(counter.nilai()); // 3

// SCOPE — di mana variabel bisa diakses
let global = "global"; // bisa diakses di mana saja
function coba() {
  let lokal = "lokal"; // hanya bisa di dalam fungsi ini
  console.log(global); // bisa
}
// console.log(lokal); // ERROR — tidak bisa diakses di luar

// IMMUTABILITY — jangan mutasi data langsung, buat yang baru
const arr = [1, 2, 3];
// ❌ Mutasi langsung
arr.push(4);
// ✅ Buat array baru
const arrBaru = [...arr, 4];
```

---

## 20. Project Mini — Latihan Nyata

### 🎮 Project 1: Todo List (DOM + Event + Array)
```html
<!DOCTYPE html>
<html lang="id">
<head>
  <title>Todo List — ANERs</title>
  <style>
    body { font-family: monospace; max-width: 500px; margin: 50px auto; background: #0d1117; color: #cdd6f4; }
    h1 { color: #89b4fa; }
    input { background: #1e1e2e; border: 1px solid #313244; color: #cdd6f4; padding: 10px; width: 70%; border-radius: 4px; }
    button { background: #89b4fa; color: #1e1e2e; border: none; padding: 10px 15px; cursor: pointer; border-radius: 4px; font-weight: bold; }
    ul { list-style: none; padding: 0; }
    li { background: #1e1e2e; margin: 5px 0; padding: 10px; border-radius: 4px; display: flex; justify-content: space-between; }
    li.selesai span { text-decoration: line-through; color: #6c7086; }
    .hapus { background: #f38ba8; font-size: 12px; padding: 5px 8px; }
  </style>
</head>
<body>
  <h1>📋 Todo List</h1>
  <div>
    <input type="text" id="inputTodo" placeholder="Tugas baru...">
    <button id="tombolTambah">Tambah</button>
  </div>
  <ul id="daftarTodo"></ul>
  <p id="info"></p>
  <script>
    const input = document.getElementById("inputTodo");
    const tombol = document.getElementById("tombolTambah");
    const daftar = document.getElementById("daftarTodo");
    const info = document.getElementById("info");
    let todos = [];

    function render() {
      daftar.innerHTML = "";
      todos.forEach((todo, index) => {
        const li = document.createElement("li");
        if (todo.selesai) li.classList.add("selesai");
        li.innerHTML = `
          <span onclick="toggleSelesai(${index})" style="cursor:pointer">${todo.teks}</span>
          <button class="hapus" onclick="hapusTodo(${index})">Hapus</button>
        `;
        daftar.appendChild(li);
      });
      const selesai = todos.filter(t => t.selesai).length;
      info.textContent = `${selesai}/${todos.length} selesai`;
    }

    function tambahTodo() {
      const teks = input.value.trim();
      if (!teks) return;
      todos.push({ teks, selesai: false });
      input.value = "";
      render();
    }

    function toggleSelesai(index) {
      todos[index].selesai = !todos[index].selesai;
      render();
    }

    function hapusTodo(index) {
      todos.splice(index, 1);
      render();
    }

    tombol.addEventListener("click", tambahTodo);
    input.addEventListener("keydown", e => {
      if (e.key === "Enter") tambahTodo();
    });
  </script>
</body>
</html>
```

### 🔢 Project 2: Kalkulator (OOP + DOM)
```javascript
class Kalkulator {
  constructor() {
    this.layar = document.getElementById("layar");
    this.reset();
    this.bindEvents();
  }

  reset() {
    this.nilai1 = "";
    this.nilai2 = "";
    this.operator = "";
    this.hasilDitampilkan = false;
  }

  bindEvents() {
    document.querySelectorAll(".angka").forEach(btn => {
      btn.addEventListener("click", () => this.inputAngka(btn.textContent));
    });
    document.querySelectorAll(".op").forEach(btn => {
      btn.addEventListener("click", () => this.inputOperator(btn.textContent));
    });
    document.getElementById("sama").addEventListener("click", () => this.hitung());
    document.getElementById("clear").addEventListener("click", () => {
      this.reset();
      this.layar.textContent = "0";
    });
  }

  inputAngka(angka) {
    if (this.operator === "") {
      this.nilai1 += angka;
      this.layar.textContent = this.nilai1;
    } else {
      this.nilai2 += angka;
      this.layar.textContent = this.nilai2;
    }
  }

  inputOperator(op) {
    if (this.nilai1 === "") return;
    this.operator = op;
    this.layar.textContent = `${this.nilai1} ${op}`;
  }

  hitung() {
    if (!this.nilai1 || !this.nilai2 || !this.operator) return;
    const a = parseFloat(this.nilai1);
    const b = parseFloat(this.nilai2);
    let hasil;

    switch(this.operator) {
      case "+": hasil = a + b; break;
      case "-": hasil = a - b; break;
      case "×": hasil = a * b; break;
      case "÷": hasil = b !== 0 ? a / b : "Error"; break;
    }

    this.layar.textContent = hasil;
    this.reset();
    this.nilai1 = String(hasil);
  }
}

const kalk = new Kalkulator();
```

### 🌐 Project 3: Fetch Cuaca (Async/Await + Fetch)
```javascript
const API_KEY = "masukkan_api_key_openweathermap"; // daftar gratis di openweathermap.org

async function getCuaca(kota) {
  const loadingEl = document.getElementById("loading");
  const hasilEl = document.getElementById("hasil");
  
  loadingEl.textContent = "Memuat...";
  hasilEl.innerHTML = "";

  try {
    const res = await fetch(
      `https://api.openweathermap.org/data/2.5/weather?q=${kota}&appid=${API_KEY}&units=metric&lang=id`
    );

    if (!res.ok) throw new Error("Kota tidak ditemukan!");
    
    const data = await res.json();
    
    hasilEl.innerHTML = `
      <h2>${data.name}, ${data.sys.country}</h2>
      <p>🌡️ Suhu: ${data.main.temp}°C (terasa ${data.main.feels_like}°C)</p>
      <p>☁️ Kondisi: ${data.weather[0].description}</p>
      <p>💧 Kelembapan: ${data.main.humidity}%</p>
      <p>🌬️ Angin: ${data.wind.speed} m/s</p>
    `;

  } catch (err) {
    hasilEl.innerHTML = `<p style="color:red">❌ ${err.message}</p>`;
  } finally {
    loadingEl.textContent = "";
  }
}

document.getElementById("tombolCari").addEventListener("click", () => {
  const kota = document.getElementById("inputKota").value.trim();
  if (kota) getCuaca(kota);
});
```

---

## 🏁 Penutup

Lo udah sampai di sini — berarti lo serius bro. Ini bukan akhir, ini baru **awal**. Roadmap selanjutnya:

| Level | Yang Dipelajari |
|-------|----------------|
| 🟡 Intermediate | Node.js, Express, NPM, REST API |
| 🟠 Advanced | TypeScript, React/Vue/Svelte, Testing |
| 🔴 Pro | System Design, Performance, Security, WebSockets |
| 🟣 Expert | Compiler internals, V8 engine, Custom runtimes |

### Resources terbaik buat lanjut:
- **javascript.info** — dokumentasi terlengkap dan paling jelas
- **MDN Web Docs** — referensi resmi semua fitur JS
- **freeCodeCamp** — kurikulum gratis terstruktur
- **roadmap.sh/javascript** — peta jalan visual

---

> *"The best way to learn programming is to write code, break it, fix it, and repeat."*
> 
> **— r¡xz · The ANERs**

---
*Dokumen ini dibuat untuk komunitas ANERs — AI-Native Engineering & Research Systems*
