# PYTHON : DARI NOL SAMPE PRO
### Dokumen Belajar Lengkap — r¡z | assistant

> **Cara baca dokumen ini:**
> Baca dari atas ke bawah. Jangan skip. Setiap bagian itu fondasi buat bagian berikutnya.
> Kalo ada yang bingung, baca lagi pelan-pelan. Kayak makan nasi — habisin dulu baru minta tambah.

---

## DAFTAR ISI

```
LEVEL 0  — Persiapan & Mindset
LEVEL 1  — Dasar Python (Syntax, Variable, Tipe Data)
LEVEL 2  — Operator & Ekspresi
LEVEL 3  — Kondisi (if / elif / else)
LEVEL 4  — Perulangan (for / while)
LEVEL 5  — Fungsi (def)
LEVEL 6  — List, Tuple, Set, Dictionary
LEVEL 7  — String Manipulation
LEVEL 8  — File Handling (Baca & Tulis File)
LEVEL 9  — Error Handling (try / except)
LEVEL 10 — OOP (Object Oriented Programming)
LEVEL 11 — Module & Library
LEVEL 12 — Regex (Regular Expression)
LEVEL 13 — API Request (requests library)
LEVEL 14 — Database (SQLite & SQLAlchemy)
LEVEL 15 — Concurrency (Threading & Asyncio)
LEVEL 16 — Analisis Kode & Debugging Pro
LEVEL 17 — Best Practice & Clean Code
BONUS    — Cheatsheet Cepat
```

---

## LEVEL 0 — PERSIAPAN & MINDSET

### Apa itu Python?

Python itu bahasa pemrograman. Ibaratnya, kalo komputer adalah robot, Python adalah bahasa yang lo pake buat ngasih perintah ke robot itu. Python terkenal karena:

- **Simpel** — sintaknya mirip bahasa manusia
- **Powerful** — dipake di AI, web, hacking, data science, automation
- **Populer** — komunitas gede, library bejibun

### Install Python

```bash
# Cek apakah Python udah ada
python3 --version

# Install di Alpine OS (Pterodactyl)
apk add python3 py3-pip

# Install di Termux (Android)
pkg install python
```

### Jalanin Python

```bash
# Mode interaktif (coba-coba langsung)
python3

# Jalanin file
python3 nama_file.py
```

### Mindset yang Harus Lo Punya

```
Error ≠ Gagal. Error = Info yang dikasih Python ke lo.
Baca error dari BAWAH ke ATAS, bukan atas ke bawah.
Google + Stack Overflow = teman terbaik programmer.
Ketik ulang kodenya, jangan copy paste dulu — biar otak lo nyerap.
```

---

## LEVEL 1 — DASAR PYTHON

### 1.1 Hello World

Tradisi pertama setiap belajar bahasa baru: nyapa dunia.

```python
print("Hello, World!")
print("Gua lagi belajar Python nih")
```

**Output:**
```
Hello, World!
Gua lagi belajar Python nih
```

`print()` itu perintah buat nampilin sesuatu ke layar. Simpel.

---

### 1.2 Komentar

Komentar adalah tulisan yang diabaikan Python. Fungsinya buat catatan buat lo atau orang lain yang baca kode.

```python
# Ini komentar satu baris — Python gak baca ini

"""
Ini komentar
banyak baris
bisa panjang
"""

print("Ini yang dijalanin")  # bisa juga di samping kode
```

---

### 1.3 Variable

Variable itu kayak kotak. Lo kasih nama kotak-nya, terus lo simpen sesuatu di dalamnya.

```python
nama = "Rixz"
umur = 17
tinggi = 170.5
aktif = True

print(nama)   # Rixz
print(umur)   # 17
print(tinggi) # 170.5
print(aktif)  # True
```

**Aturan nama variable:**
```python
# BOLEH
nama_user = "ok"
namaUser  = "ok"
_private  = "ok"
var123    = "ok"

# TIDAK BOLEH
123var    = "error"   # mulai dengan angka
nama-user = "error"   # pakai strip/minus
class     = "error"   # kata reserved Python
```

---

### 1.4 Tipe Data

Python punya beberapa tipe data dasar:

```python
# String — teks, diapit kutip
nama = "Rixz"
kota = 'Jakarta'

# Integer — bilangan bulat
umur = 17
tahun = 2026

# Float — bilangan desimal
berat = 60.5
pi = 3.14159

# Boolean — True atau False (kapital!)
online = True
banned = False

# None — kosong / tidak ada nilai
data = None
```

**Cek tipe data:**
```python
x = 42
print(type(x))        # <class 'int'>

y = "hello"
print(type(y))        # <class 'str'>

z = 3.14
print(type(z))        # <class 'float'>
```

**Konversi tipe data:**
```python
# int ke string
angka = 100
teks = str(angka)       # "100"

# string ke int
teks = "42"
angka = int(teks)       # 42

# string ke float
teks = "3.14"
desimal = float(teks)   # 3.14

# int ke float
x = int(9.9)            # 9 (dipotong, bukan dibulatkan)
```

---

## LEVEL 2 — OPERATOR & EKSPRESI

### 2.1 Operator Aritmatika

```python
a = 10
b = 3

print(a + b)   # 13  — penjumlahan
print(a - b)   # 7   — pengurangan
print(a * b)   # 30  — perkalian
print(a / b)   # 3.333... — pembagian (hasilnya float)
print(a // b)  # 3   — pembagian bulat (floor division)
print(a % b)   # 1   — sisa bagi (modulo)
print(a ** b)  # 1000 — pangkat (10^3)
```

### 2.2 Operator Perbandingan

Hasilnya selalu True atau False.

```python
x = 10
y = 20

print(x == y)   # False — sama dengan
print(x != y)   # True  — tidak sama dengan
print(x > y)    # False — lebih besar
print(x < y)    # True  — lebih kecil
print(x >= 10)  # True  — lebih besar atau sama
print(x <= 10)  # True  — lebih kecil atau sama
```

### 2.3 Operator Logika

```python
a = True
b = False

print(a and b)  # False — keduanya harus True
print(a or b)   # True  — salah satu cukup True
print(not a)    # False — kebalikannya
```

**Contoh nyata:**
```python
umur = 18
punya_ktp = True

bisa_masuk = (umur >= 17) and punya_ktp
print(bisa_masuk)  # True
```

### 2.4 Operator Assignment

```python
x = 10      # assign biasa

x += 5      # x = x + 5  → 15
x -= 3      # x = x - 3  → 12
x *= 2      # x = x * 2  → 24
x //= 5     # x = x // 5 → 4
x **= 2     # x = x ** 2 → 16
x %= 5      # x = x % 5  → 1
```

---

## LEVEL 3 — KONDISI (IF / ELIF / ELSE)

### 3.1 Dasar If

Kondisi itu kayak percabangan jalan. "Kalau ini terjadi, lakukan ini."

```python
nilai = 85

if nilai >= 90:
    print("Nilai A")
elif nilai >= 80:
    print("Nilai B")
elif nilai >= 70:
    print("Nilai C")
elif nilai >= 60:
    print("Nilai D")
else:
    print("Nilai E — belajar lagi bro")
```

**PENTING:** Python pakai **indentasi (spasi/tab)** bukan kurung kurawal `{}`. Ini aturan wajib!

```python
# BENAR
if True:
    print("ini di dalam if")   # ada indentasi

# SALAH — IndentationError
if True:
print("ini error")             # tidak ada indentasi
```

### 3.2 If di Dalam If (Nested)

```python
umur = 20
status_member = True

if umur >= 18:
    if status_member:
        print("Boleh masuk, member aktif")
    else:
        print("Boleh masuk, tapi bukan member")
else:
    print("Belum boleh masuk, masih di bawah umur")
```

### 3.3 Ternary (If Singkat)

```python
# Format: nilai_true if kondisi else nilai_false
umur = 20
status = "dewasa" if umur >= 18 else "anak-anak"
print(status)  # dewasa
```

### 3.4 Operator `in` dan `not in`

```python
buah = ["apel", "mangga", "jeruk"]

if "mangga" in buah:
    print("Ada mangga!")

if "durian" not in buah:
    print("Ga ada durian")
```

---

## LEVEL 4 — PERULANGAN (FOR / WHILE)

### 4.1 For Loop

`for` dipake waktu lo tau berapa kali mau ngulang, atau lo mau iterasi sesuatu.

```python
# Ngulang 5 kali
for i in range(5):
    print(i)
# Output: 0 1 2 3 4

# range(start, stop, step)
for i in range(1, 11, 2):
    print(i)
# Output: 1 3 5 7 9

# Iterasi list
buah = ["apel", "mangga", "jeruk"]
for b in buah:
    print(b)

# Iterasi string
for huruf in "Python":
    print(huruf)
```

### 4.2 While Loop

`while` dipake waktu lo mau ngulang SELAMA kondisi tertentu terpenuhi.

```python
hitung = 0

while hitung < 5:
    print(f"Hitung: {hitung}")
    hitung += 1  # WAJIB ada ini, kalau tidak → infinite loop
```

### 4.3 Break, Continue, Pass

```python
# BREAK — hentikan loop sekarang
for i in range(10):
    if i == 5:
        break          # berhenti di 5
    print(i)
# Output: 0 1 2 3 4

# CONTINUE — skip iterasi ini, lanjut ke berikutnya
for i in range(10):
    if i % 2 == 0:
        continue       # skip angka genap
    print(i)
# Output: 1 3 5 7 9

# PASS — tidak melakukan apa-apa (placeholder)
for i in range(5):
    pass               # kode kosong, ga error
```

### 4.4 Enumerate & Zip

```python
# enumerate — dapat index sekaligus nilai
buah = ["apel", "mangga", "jeruk"]
for index, nilai in enumerate(buah):
    print(f"{index}: {nilai}")
# 0: apel
# 1: mangga
# 2: jeruk

# zip — gabung dua list sekaligus
nama = ["Ali", "Budi", "Cici"]
nilai = [90, 85, 78]
for n, v in zip(nama, nilai):
    print(f"{n} dapat nilai {v}")
```

### 4.5 List Comprehension (Cara Elegan Loop)

```python
# Biasa
angka = []
for i in range(10):
    angka.append(i * 2)

# List Comprehension — lebih singkat
angka = [i * 2 for i in range(10)]
print(angka)  # [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]

# Dengan kondisi
genap = [i for i in range(20) if i % 2 == 0]
print(genap)  # [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
```

---

## LEVEL 5 — FUNGSI (DEF)

### 5.1 Buat Fungsi Dasar

Fungsi itu kayak resep. Lo bikin sekali, bisa dipake berkali-kali.

```python
def sapa():
    print("Halo! Selamat datang.")

# Panggil fungsi
sapa()   # Halo! Selamat datang.
sapa()   # Halo! Selamat datang.
```

### 5.2 Parameter & Argumen

```python
def sapa(nama):
    print(f"Halo, {nama}!")

sapa("Rixz")   # Halo, Rixz!
sapa("Budi")   # Halo, Budi!
```

### 5.3 Default Parameter

```python
def sapa(nama, bahasa="id"):
    if bahasa == "id":
        print(f"Halo, {nama}!")
    elif bahasa == "en":
        print(f"Hello, {nama}!")

sapa("Rixz")         # Halo, Rixz! (default id)
sapa("Rixz", "en")   # Hello, Rixz!
```

### 5.4 Return Value

```python
def tambah(a, b):
    return a + b

hasil = tambah(5, 3)
print(hasil)   # 8

# Return banyak nilai
def hitung(a, b):
    jumlah = a + b
    selisih = a - b
    return jumlah, selisih

j, s = hitung(10, 4)
print(j, s)   # 14  6
```

### 5.5 Args & Kwargs

```python
# *args — terima banyak argumen biasa
def total(*angka):
    return sum(angka)

print(total(1, 2, 3))       # 6
print(total(1, 2, 3, 4, 5)) # 15

# **kwargs — terima banyak argumen bernama
def profil(**data):
    for key, value in data.items():
        print(f"{key}: {value}")

profil(nama="Rixz", umur=17, kota="Jakarta")
```

### 5.6 Lambda (Fungsi Anonim)

```python
# Fungsi biasa
def kuadrat(x):
    return x ** 2

# Lambda — satu baris
kuadrat = lambda x: x ** 2
print(kuadrat(5))   # 25

# Lambda dengan 2 parameter
tambah = lambda a, b: a + b
print(tambah(3, 4)) # 7

# Sering dipakai di sorted(), filter(), map()
angka = [5, 2, 8, 1, 9, 3]
terurut = sorted(angka, key=lambda x: x)
print(terurut)  # [1, 2, 3, 5, 8, 9]
```

### 5.7 Fungsi Rekursif

Fungsi yang manggil dirinya sendiri. Kayak cermin di depan cermin.

```python
def faktorial(n):
    if n == 0 or n == 1:   # base case — harus ada ini!
        return 1
    return n * faktorial(n - 1)

print(faktorial(5))  # 120  (5*4*3*2*1)
print(faktorial(0))  # 1
```

---

## LEVEL 6 — STRUKTUR DATA

### 6.1 LIST

List itu wadah yang bisa nyimpen banyak data, urutannya tetap, dan bisa diubah.

```python
# Buat list
buah = ["apel", "mangga", "jeruk", "anggur"]

# Akses elemen (index mulai dari 0)
print(buah[0])    # apel
print(buah[-1])   # anggur (dari belakang)

# Slicing
print(buah[1:3])  # ['mangga', 'jeruk']
print(buah[:2])   # ['apel', 'mangga']
print(buah[2:])   # ['jeruk', 'anggur']

# Ubah nilai
buah[0] = "semangka"
print(buah)  # ['semangka', 'mangga', 'jeruk', 'anggur']

# Tambah elemen
buah.append("durian")        # tambah di akhir
buah.insert(1, "pepaya")     # tambah di index 1

# Hapus elemen
buah.remove("mangga")        # hapus by nilai
del buah[0]                  # hapus by index
item = buah.pop()            # hapus & ambil elemen terakhir

# Info list
print(len(buah))             # jumlah elemen
print(buah.count("jeruk"))   # hitung kemunculan
print(buah.index("jeruk"))   # cari index

# Sort & Reverse
angka = [5, 2, 8, 1, 9]
angka.sort()                 # sort ascending
angka.sort(reverse=True)     # sort descending
angka.reverse()              # balik urutan

# Copy list
a = [1, 2, 3]
b = a.copy()   # BENAR (deep copy sederhana)
c = a          # SALAH — c cuma referensi ke a
```

### 6.2 TUPLE

Tuple itu kayak list tapi **tidak bisa diubah** (immutable). Lebih cepat dari list.

```python
koordinat = (10.5, -6.2)
warna = ("merah", "hijau", "biru")

print(warna[0])     # merah
print(len(warna))   # 3

# Tuple unpacking
x, y = koordinat
print(x, y)   # 10.5 -6.2

# Tuple satu elemen (perlu koma!)
satu = (42,)   # ini tuple
bukan = (42)   # ini cuma int dengan kurung
```

### 6.3 SET

Set itu koleksi **unik** dan **tidak berurutan**. Cocok buat hapus duplikat.

```python
angka = {1, 2, 3, 2, 1, 4}
print(angka)   # {1, 2, 3, 4} — duplikat hilang

# Operasi set
a = {1, 2, 3, 4}
b = {3, 4, 5, 6}

print(a | b)   # Union     — {1, 2, 3, 4, 5, 6}
print(a & b)   # Intersect — {3, 4}
print(a - b)   # Difference— {1, 2}
print(a ^ b)   # Symmetric — {1, 2, 5, 6}

# Add & Remove
angka.add(10)
angka.discard(3)   # hapus, ga error kalau ga ada
angka.remove(3)    # hapus, error kalau ga ada
```

### 6.4 DICTIONARY

Dictionary itu pasangan key-value. Kayak kamus — lo cari kata (key), dapat arti (value).

```python
profil = {
    "nama": "Rixz",
    "umur": 17,
    "kota": "Jakarta",
    "hobi": ["coding", "gaming"]
}

# Akses value
print(profil["nama"])          # Rixz
print(profil.get("email"))     # None (ga error kalau ga ada)
print(profil.get("email", "-")) # - (default value)

# Ubah & Tambah
profil["umur"] = 18
profil["email"] = "rixz@mail.com"

# Hapus
del profil["kota"]
nilai = profil.pop("umur")   # hapus & ambil valuenya

# Iterasi
for key in profil:
    print(key, ":", profil[key])

for key, value in profil.items():
    print(f"{key} = {value}")

# Info
print(profil.keys())    # semua key
print(profil.values())  # semua value
print(profil.items())   # pasangan key-value

# Nested dictionary
database = {
    "user1": {"nama": "Ali", "level": "admin"},
    "user2": {"nama": "Budi", "level": "user"}
}
print(database["user1"]["nama"])   # Ali
```

---

## LEVEL 7 — STRING MANIPULATION

### 7.1 Operasi Dasar String

```python
s = "Hello, Python!"

# Panjang
print(len(s))          # 14

# Case
print(s.upper())       # HELLO, PYTHON!
print(s.lower())       # hello, python!
print(s.title())       # Hello, Python!
print(s.capitalize())  # Hello, python!

# Cari & Ganti
print(s.find("Python"))    # 7 (index kemunculan pertama)
print(s.replace("Hello", "Halo"))  # Halo, Python!

# Strip (hapus spasi/karakter)
teks = "   banyak spasi   "
print(teks.strip())    # "banyak spasi"
print(teks.lstrip())   # "banyak spasi   "
print(teks.rstrip())   # "   banyak spasi"

# Split & Join
kalimat = "apel,mangga,jeruk"
buah = kalimat.split(",")   # ['apel', 'mangga', 'jeruk']

buah = ["apel", "mangga", "jeruk"]
gabung = ", ".join(buah)     # "apel, mangga, jeruk"
```

### 7.2 String Formatting

```python
nama = "Rixz"
umur = 17

# f-string (CARA TERBAIK — Python 3.6+)
print(f"Nama: {nama}, Umur: {umur}")
print(f"Dua kali umur: {umur * 2}")
print(f"Pi: {3.14159:.2f}")    # format 2 desimal

# format()
print("Nama: {}, Umur: {}".format(nama, umur))
print("Nama: {nama}, Umur: {umur}".format(nama=nama, umur=umur))

# % (cara lama, masih ada di kode jadul)
print("Nama: %s, Umur: %d" % (nama, umur))
```

### 7.3 String Slicing

```python
s = "Hello, Python!"
#    0123456789...

print(s[0])      # H
print(s[-1])     # !
print(s[7:13])   # Python
print(s[:5])     # Hello
print(s[::2])    # Hlo yhn  (step 2)
print(s[::-1])   # !nohtyP ,olleH (balik)
```

### 7.4 Cek String

```python
s = "Hello123"

print(s.isalpha())    # False (ada angka)
print(s.isdigit())    # False (ada huruf)
print(s.isalnum())    # True (huruf + angka)
print(s.startswith("He"))  # True
print(s.endswith("23"))    # True
print("py" in "python")    # True
```

---

## LEVEL 8 — FILE HANDLING

### 8.1 Baca & Tulis File

```python
# TULIS file
with open("data.txt", "w") as f:
    f.write("Baris pertama\n")
    f.write("Baris kedua\n")

# Mode file:
# "r"  — read (default), error jika file ga ada
# "w"  — write (buat baru / timpa jika ada)
# "a"  — append (tambah di akhir)
# "x"  — exclusive (buat baru, error jika sudah ada)
# "rb" — read binary (gambar, video, dll)
```

```python
# BACA file
with open("data.txt", "r") as f:
    isi = f.read()       # baca semua sekaligus
    print(isi)

with open("data.txt", "r") as f:
    baris = f.readline()  # baca satu baris
    print(baris)

with open("data.txt", "r") as f:
    for baris in f:       # baca baris per baris
        print(baris.strip())

with open("data.txt", "r") as f:
    semua = f.readlines() # list semua baris
    print(semua)
```

### 8.2 File JSON

```python
import json

# Python dict ke JSON file
data = {
    "nama": "Rixz",
    "umur": 17,
    "skill": ["python", "security"]
}

with open("data.json", "w") as f:
    json.dump(data, f, indent=4)

# JSON file ke Python dict
with open("data.json", "r") as f:
    hasil = json.load(f)
    print(hasil["nama"])   # Rixz

# String JSON
json_str = json.dumps(data)     # dict → string
data_lagi = json.loads(json_str) # string → dict
```

### 8.3 Operasi File & Folder

```python
import os
import shutil

# Info
print(os.getcwd())           # direktori aktif
print(os.listdir("."))       # list isi folder
print(os.path.exists("file.txt"))  # cek ada ga
print(os.path.isfile("file.txt"))  # cek apakah file
print(os.path.isdir("folder"))     # cek apakah folder

# Buat & hapus
os.makedirs("folder/subfolder", exist_ok=True)  # buat folder
os.remove("file.txt")         # hapus file
os.rmdir("folder")            # hapus folder kosong
shutil.rmtree("folder")       # hapus folder + isinya

# Rename & copy
os.rename("lama.txt", "baru.txt")
shutil.copy("src.txt", "dst.txt")
shutil.move("src.txt", "folder/")
```

---

## LEVEL 9 — ERROR HANDLING

### 9.1 Try / Except Dasar

Error itu normal. Yang penting lo tau cara nanganinnya.

```python
try:
    angka = int(input("Masukkan angka: "))
    hasil = 10 / angka
    print(f"Hasil: {hasil}")
except ValueError:
    print("Itu bukan angka!")
except ZeroDivisionError:
    print("Ga bisa bagi dengan nol!")
except Exception as e:
    print(f"Error tak terduga: {e}")
finally:
    print("Ini selalu jalan, error atau tidak")
```

### 9.2 Jenis-Jenis Error Umum

```
TypeError        — operasi ke tipe yang salah
ValueError       — nilai tidak sesuai
KeyError         — key dict tidak ada
IndexError       — index list di luar range
AttributeError   — attribute/method tidak ada
FileNotFoundError— file tidak ditemukan
ZeroDivisionError— bagi dengan nol
ImportError      — modul tidak bisa di-import
NameError        — variable belum didefinisikan
RecursionError   — rekursi terlalu dalam
```

### 9.3 Raise Error Custom

```python
def bagi(a, b):
    if b == 0:
        raise ValueError("Pembagi tidak boleh nol!")
    return a / b

try:
    print(bagi(10, 0))
except ValueError as e:
    print(f"Error: {e}")
```

### 9.4 Custom Exception

```python
class AgeError(Exception):
    def __init__(self, umur):
        self.umur = umur
        super().__init__(f"Umur {umur} tidak valid")

def validasi_umur(umur):
    if umur < 0 or umur > 150:
        raise AgeError(umur)
    return True

try:
    validasi_umur(-5)
except AgeError as e:
    print(e)  # Umur -5 tidak valid
```

---

## LEVEL 10 — OOP (Object Oriented Programming)

### 10.1 Kenapa OOP?

Bayangin lo bikin game. Ada banyak karakter dengan property (nama, HP, level) dan aksi (serang, defend, lari). Tanpa OOP, lo nulis ulang terus. Dengan OOP, lo bikin "cetakan" karakter sekali, terus pake berkali-kali.

### 10.2 Class & Object Dasar

```python
class Karakter:
    # __init__ dipanggil otomatis waktu bikin object
    def __init__(self, nama, hp, level):
        self.nama = nama    # attribute instance
        self.hp = hp
        self.level = level

    def info(self):
        print(f"[{self.level}] {self.nama} — HP: {self.hp}")

    def serang(self, target):
        damage = self.level * 10
        target.hp -= damage
        print(f"{self.nama} menyerang {target.nama} dengan {damage} damage!")

# Bikin object
hero = Karakter("Rixz", 100, 5)
musuh = Karakter("Goblin", 50, 2)

hero.info()        # [5] Rixz — HP: 100
hero.serang(musuh) # Rixz menyerang Goblin dengan 50 damage!
musuh.info()       # [2] Goblin — HP: 0
```

### 10.3 Class Variable vs Instance Variable

```python
class Pemain:
    server = "Indonesia"   # class variable — sama untuk semua

    def __init__(self, nama):
        self.nama = nama   # instance variable — berbeda tiap object

p1 = Pemain("Ali")
p2 = Pemain("Budi")

print(p1.server)   # Indonesia
print(p2.server)   # Indonesia
print(p1.nama)     # Ali
print(p2.nama)     # Budi

# Ubah class variable
Pemain.server = "Singapore"
print(p1.server)   # Singapore (berubah semua)
```

### 10.4 Inheritance (Pewarisan)

```python
class Hewan:
    def __init__(self, nama):
        self.nama = nama

    def suara(self):
        print("...")

    def info(self):
        print(f"Saya adalah {self.nama}")

class Anjing(Hewan):    # Anjing mewarisi Hewan
    def suara(self):    # Override method parent
        print("Woof!")

    def main(self):     # Method baru khusus Anjing
        print(f"{self.nama} lagi main bola")

class Kucing(Hewan):
    def suara(self):
        print("Meow!")

a = Anjing("Rex")
k = Kucing("Whiskers")

a.info()    # Saya adalah Rex (dari parent)
a.suara()   # Woof! (override)
a.main()    # Rex lagi main bola

k.info()    # Saya adalah Whiskers
k.suara()   # Meow!
```

### 10.5 Encapsulation & Property

```python
class BankAccount:
    def __init__(self, saldo):
        self.__saldo = saldo   # private (double underscore)

    @property
    def saldo(self):           # getter
        return self.__saldo

    @saldo.setter
    def saldo(self, nilai):    # setter dengan validasi
        if nilai < 0:
            raise ValueError("Saldo tidak boleh negatif")
        self.__saldo = nilai

    def deposit(self, jumlah):
        if jumlah <= 0:
            raise ValueError("Jumlah deposit harus positif")
        self.__saldo += jumlah
        print(f"Deposit {jumlah}. Saldo: {self.__saldo}")

akun = BankAccount(100000)
print(akun.saldo)    # 100000
akun.deposit(50000)  # Deposit 50000. Saldo: 150000
# akun.__saldo      # ERROR — tidak bisa akses langsung
```

### 10.6 Magic Methods

```python
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __str__(self):        # print(v) → string
        return f"Vector({self.x}, {self.y})"

    def __repr__(self):       # representasi di console
        return f"Vector(x={self.x}, y={self.y})"

    def __add__(self, other): # v1 + v2
        return Vector(self.x + other.x, self.y + other.y)

    def __len__(self):        # len(v)
        return int((self.x**2 + self.y**2)**0.5)

    def __eq__(self, other):  # v1 == v2
        return self.x == other.x and self.y == other.y

v1 = Vector(3, 4)
v2 = Vector(1, 2)

print(v1)          # Vector(3, 4)
print(v1 + v2)     # Vector(4, 6)
print(len(v1))     # 5
print(v1 == v2)    # False
```

---

## LEVEL 11 — MODULE & LIBRARY

### 11.1 Import Dasar

```python
# Import seluruh modul
import math
print(math.sqrt(16))   # 4.0
print(math.pi)         # 3.14159...

# Import spesifik
from math import sqrt, pi
print(sqrt(25))        # 5.0

# Import dengan alias
import numpy as np      # kalau udah install
import pandas as pd

# Import semua (hindari ini di produksi)
from math import *
print(sqrt(9))
```

### 11.2 Modul Bawaan Python yang Wajib Tau

```python
import os           # operasi sistem & file
import sys          # info interpreter
import re           # regex
import json         # JSON
import time         # waktu & delay
import datetime     # tanggal & jam
import random       # angka random
import hashlib      # hashing (md5, sha)
import base64       # encode/decode base64
import subprocess   # jalanin command shell
import socket       # network
import threading    # multithreading
import logging      # logging profesional
import argparse     # argumen command line
import collections  # struktur data lanjut
import itertools    # iterasi lanjut
import functools    # fungsi lanjut
```

### 11.3 Install Library Eksternal

```bash
# Install library
pip install requests
pip install flask
pip install sqlalchemy
pip install beautifulsoup4
pip install paramiko
pip install cryptography

# Lihat yang terinstall
pip list
pip show requests

# requirements.txt
pip freeze > requirements.txt    # simpan semua dependency
pip install -r requirements.txt  # install dari file
```

### 11.4 Buat Modul Sendiri

```python
# File: utils.py
def sapa(nama):
    return f"Halo, {nama}!"

def hitung_luas_persegi(sisi):
    return sisi ** 2

VERSI = "1.0.0"
```

```python
# File: main.py
import utils
from utils import hitung_luas_persegi

print(utils.sapa("Rixz"))         # Halo, Rixz!
print(hitung_luas_persegi(5))     # 25
print(utils.VERSI)                 # 1.0.0
```

---

## LEVEL 12 — REGEX (Regular Expression)

### 12.1 Apa itu Regex?

Regex itu pola untuk mencocokkan teks. Kayak ctrl+f tapi 10x lebih powerful. Krusial buat security dan parsing data.

```python
import re

teks = "Email saya adalah rixz@example.com dan backup di rixz2@gmail.com"

# Cari pola email
pola = r"[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}"
hasil = re.findall(pola, teks)
print(hasil)  # ['rixz@example.com', 'rixz2@gmail.com']
```

### 12.2 Fungsi Regex

```python
import re

teks = "Python 3 lebih baik dari Python 2"

# search — cari pertama kali ditemukan
hasil = re.search(r"\d", teks)
if hasil:
    print(hasil.group())   # 3

# match — cocokkan dari AWAL string
hasil = re.match(r"Python", teks)
print(bool(hasil))   # True

# findall — semua kemunculan
semua = re.findall(r"Python \d", teks)
print(semua)   # ['Python 3', 'Python 2']

# sub — ganti
baru = re.sub(r"\d", "X", teks)
print(baru)    # Python X lebih baik dari Python X

# split — pecah berdasarkan pola
parts = re.split(r"\s+", "kata  terpisah   spasi")
print(parts)   # ['kata', 'terpisah', 'spasi']
```

### 12.3 Karakter Regex Penting

```
.      — karakter apa saja (kecuali newline)
\d     — digit (0-9)
\D     — bukan digit
\w     — word character (huruf, angka, _)
\W     — bukan word character
\s     — whitespace (spasi, tab, newline)
\S     — bukan whitespace
^      — awal string
$      — akhir string
*      — 0 atau lebih
+      — 1 atau lebih
?      — 0 atau 1 (opsional)
{n}    — tepat n kali
{n,m}  — n sampai m kali
[abc]  — a, b, atau c
[^abc] — bukan a, b, c
(x|y)  — x atau y
```

### 12.4 Contoh Regex Praktis

```python
import re

# Validasi nomor HP Indonesia
def validasi_hp(nomor):
    pola = r"^(\+62|62|0)8[1-9][0-9]{6,10}$"
    return bool(re.match(pola, nomor))

print(validasi_hp("081234567890"))  # True
print(validasi_hp("123456"))        # False

# Ekstrak URL dari teks
def ekstrak_url(teks):
    pola = r"https?://[^\s<>\"']+"
    return re.findall(pola, teks)

teks = "Kunjungi https://google.com atau http://github.com"
print(ekstrak_url(teks))

# Validasi password (min 8 char, huruf + angka)
def validasi_password(pwd):
    cukup_panjang = len(pwd) >= 8
    ada_huruf = bool(re.search(r"[a-zA-Z]", pwd))
    ada_angka = bool(re.search(r"\d", pwd))
    return cukup_panjang and ada_huruf and ada_angka

print(validasi_password("abc12345"))   # True
print(validasi_password("abcdefgh"))   # False (ga ada angka)
```

---

## LEVEL 13 — API REQUEST

### 13.1 Library Requests

```bash
pip install requests
```

```python
import requests

# GET request sederhana
response = requests.get("https://api.github.com/users/python")

print(response.status_code)    # 200
print(response.headers)        # header HTTP
data = response.json()          # parse JSON
print(data["name"])             # Python
```

### 13.2 GET dengan Parameter

```python
import requests

url = "https://api.github.com/search/repositories"
params = {
    "q": "python security",
    "sort": "stars",
    "per_page": 5
}

response = requests.get(url, params=params)

if response.status_code == 200:
    data = response.json()
    for repo in data["items"]:
        print(f"{repo['full_name']} — ⭐ {repo['stargazers_count']}")
else:
    print(f"Error: {response.status_code}")
```

### 13.3 POST Request

```python
import requests
import json

url = "https://httpbin.org/post"
payload = {
    "username": "rixz",
    "password": "secret123"
}
headers = {
    "Content-Type": "application/json",
    "Authorization": "Bearer TOKEN_SINI"
}

response = requests.post(url, json=payload, headers=headers)
print(response.json())
```

### 13.4 Error Handling & Session

```python
import requests
from requests.exceptions import (
    ConnectionError, Timeout, HTTPError
)

# Session — efisien untuk banyak request ke host yang sama
session = requests.Session()
session.headers.update({
    "User-Agent": "MyApp/1.0",
    "Accept": "application/json"
})

try:
    response = session.get(
        "https://api.example.com/data",
        timeout=10   # timeout 10 detik
    )
    response.raise_for_status()  # raise jika 4xx/5xx
    data = response.json()
    print(data)

except ConnectionError:
    print("Tidak bisa terhubung ke server")
except Timeout:
    print("Request timeout")
except HTTPError as e:
    print(f"HTTP Error: {e.response.status_code}")
except Exception as e:
    print(f"Error: {e}")
finally:
    session.close()
```

---

## LEVEL 14 — DATABASE

### 14.1 SQLite (Bawaan Python)

```python
import sqlite3

# Koneksi (auto-buat file jika belum ada)
conn = sqlite3.connect("database.db")
cursor = conn.cursor()

# Buat tabel
cursor.execute("""
    CREATE TABLE IF NOT EXISTS users (
        id INTEGER PRIMARY KEY AUTOINCREMENT,
        nama TEXT NOT NULL,
        email TEXT UNIQUE NOT NULL,
        umur INTEGER
    )
""")

# Insert data
cursor.execute(
    "INSERT INTO users (nama, email, umur) VALUES (?, ?, ?)",
    ("Rixz", "rixz@mail.com", 17)
)
conn.commit()

# Insert banyak sekaligus
users = [
    ("Ali", "ali@mail.com", 20),
    ("Budi", "budi@mail.com", 22),
    ("Cici", "cici@mail.com", 19),
]
cursor.executemany(
    "INSERT OR IGNORE INTO users (nama, email, umur) VALUES (?, ?, ?)",
    users
)
conn.commit()

# Select
cursor.execute("SELECT * FROM users")
semua = cursor.fetchall()
for row in semua:
    print(row)

# Select dengan filter
cursor.execute("SELECT * FROM users WHERE umur > ?", (18,))
hasil = cursor.fetchall()

# Update
cursor.execute("UPDATE users SET umur = ? WHERE nama = ?", (18, "Rixz"))
conn.commit()

# Delete
cursor.execute("DELETE FROM users WHERE nama = ?", ("Budi",))
conn.commit()

# Tutup koneksi
conn.close()
```

### 14.2 Context Manager untuk DB

```python
import sqlite3

def get_db():
    return sqlite3.connect("app.db")

# Pakai with — auto commit dan auto close
with get_db() as conn:
    conn.row_factory = sqlite3.Row  # row jadi dict-like
    cursor = conn.cursor()
    cursor.execute("SELECT * FROM users")
    for row in cursor.fetchall():
        print(dict(row))
```

---

## LEVEL 15 — CONCURRENCY

### 15.1 Threading

```python
import threading
import time

def download(nama, durasi):
    print(f"Mulai download {nama}")
    time.sleep(durasi)   # simulasi proses
    print(f"Selesai download {nama}")

# Tanpa threading — berurutan
# download("file1.zip", 3)  # 3 detik
# download("file2.zip", 2)  # 2 detik
# Total: 5 detik

# Dengan threading — paralel
t1 = threading.Thread(target=download, args=("file1.zip", 3))
t2 = threading.Thread(target=download, args=("file2.zip", 2))

t1.start()
t2.start()

t1.join()   # tunggu t1 selesai
t2.join()   # tunggu t2 selesai
# Total: ~3 detik (yang paling lama)
print("Semua selesai!")
```

### 15.2 Asyncio (Async/Await)

```python
import asyncio
import time

async def fetch_data(nama, durasi):
    print(f"Fetching {nama}...")
    await asyncio.sleep(durasi)   # non-blocking sleep
    print(f"Done: {nama}")
    return f"Data dari {nama}"

async def main():
    # Jalankan semua bersamaan
    hasil = await asyncio.gather(
        fetch_data("API-1", 2),
        fetch_data("API-2", 1),
        fetch_data("API-3", 3),
    )
    print(hasil)

asyncio.run(main())
```

### 15.3 Async dengan aiohttp

```bash
pip install aiohttp
```

```python
import asyncio
import aiohttp

async def fetch(session, url):
    async with session.get(url) as response:
        return await response.json()

async def main():
    urls = [
        "https://api.github.com/users/python",
        "https://api.github.com/users/linux",
        "https://api.github.com/users/torvalds",
    ]

    async with aiohttp.ClientSession() as session:
        tasks = [fetch(session, url) for url in urls]
        results = await asyncio.gather(*tasks)

        for r in results:
            print(r.get("name", "Unknown"))

asyncio.run(main())
```

---

## LEVEL 16 — ANALISIS KODE & DEBUGGING PRO

### 16.1 Cara Baca Error Python

Ini yang paling penting. Error Python itu punya format standar:

```
Traceback (most recent call last):
  File "main.py", line 12, in <module>       ← file & baris yang memanggil
    hasil = hitung(x, y)
  File "main.py", line 5, in hitung          ← fungsi bermasalah
    return a / b
ZeroDivisionError: division by zero          ← JENIS ERROR & PESAN
```

**Cara baca: dari BAWAH ke ATAS**

1. Baris paling bawah: jenis error dan pesannya
2. Naik ke atas: jejak pemanggilan fungsi (call stack)
3. Baris terakhir sebelum error = baris yang menyebabkan crash

---

### 16.2 Analisis Kode: Contoh Kasus

**Kode Bermasalah:**

```python
def proses_data(data):
    total = 0
    for item in data:
        total += item["nilai"]
    rata = total / len(data)
    return rata

hasil = proses_data([])
print(hasil)
```

**Error yang muncul:**
```
ZeroDivisionError: division by zero
```

**Analisis:**
- Baris `total / len(data)` — `len([])` adalah 0
- Bagi dengan 0 = error
- Input kosong tidak dihandle

**Perbaikan:**

```python
def proses_data(data):
    if not data:               # ← cek dulu apakah kosong
        return 0               # atau raise ValueError
    total = 0
    for item in data:
        if "nilai" not in item:    # ← cek key ada
            continue
        total += item["nilai"]
    rata = total / len(data)
    return rata

print(proses_data([]))                           # 0
print(proses_data([{"nilai": 80}, {"nilai": 90}]))  # 85.0
```

---

### 16.3 Teknik Debugging

**A. Print Debugging (Cara Paling Simpel)**

```python
def kalkulasi(x, y):
    print(f"[DEBUG] x={x}, y={y}")      # lihat nilai masuk
    hasil = x * y + 10
    print(f"[DEBUG] hasil={hasil}")      # lihat nilai tengah
    return hasil / 2

print(kalkulasi(5, 3))
```

**B. Menggunakan Modul `logging`**

```python
import logging

# Setup logging
logging.basicConfig(
    level=logging.DEBUG,
    format="%(asctime)s [%(levelname)s] %(message)s",
    handlers=[
        logging.FileHandler("app.log"),   # simpan ke file
        logging.StreamHandler()           # tampilkan di terminal
    ]
)

def proses(data):
    logging.debug(f"Data masuk: {data}")

    if not data:
        logging.warning("Data kosong!")
        return None

    try:
        hasil = sum(data) / len(data)
        logging.info(f"Berhasil: rata-rata = {hasil}")
        return hasil
    except Exception as e:
        logging.error(f"Error: {e}", exc_info=True)
        return None

proses([10, 20, 30])
proses([])
```

**C. Menggunakan `pdb` (Python Debugger)**

```python
import pdb

def fungsi_bermasalah(x):
    a = x * 2
    pdb.set_trace()    # breakpoint! — eksekusi berhenti di sini
    b = a / 0          # baris bermasalah
    return b

fungsi_bermasalah(5)
```

Di `pdb`, perintah yang sering dipakai:
```
n     — next (eksekusi baris berikutnya)
s     — step (masuk ke fungsi)
c     — continue (lanjut sampai breakpoint berikutnya)
p var — print nilai variabel
l     — list kode sekitar
q     — quit debugger
```

**D. Pakai `breakpoint()` (Python 3.7+)**

```python
def kalkulasi(a, b):
    breakpoint()   # lebih simpel dari pdb.set_trace()
    return a / b
```

---

### 16.4 Debug Kasus Nyata

**Kasus 1: KeyError saat parsing API**

```python
# Kode bermasalah
import requests

def ambil_email(username):
    r = requests.get(f"https://api.github.com/users/{username}")
    data = r.json()
    return data["email"]   # ← KeyError kalau "email" None / tidak ada

# Perbaikan
def ambil_email(username):
    r = requests.get(f"https://api.github.com/users/{username}")

    if r.status_code != 200:
        raise ConnectionError(f"Gagal ambil data: {r.status_code}")

    data = r.json()
    email = data.get("email")   # ← None kalau tidak ada, bukan error

    if email is None:
        return "Email tidak publik"
    return email
```

**Kasus 2: Infinite Loop**

```python
# BERBAHAYA — infinite loop
i = 0
while i < 10:
    print(i)
    # lupa i += 1!

# Perbaikan
i = 0
max_iterasi = 1000   # safety guard
while i < 10:
    print(i)
    i += 1
    if i > max_iterasi:   # double safety
        break
```

**Kasus 3: Mutasi List di Dalam Loop**

```python
# SALAH — jangan hapus dari list yang sedang di-iterasi
angka = [1, 2, 3, 4, 5, 6]
for n in angka:
    if n % 2 == 0:
        angka.remove(n)   # ← behavior tidak terduga!
print(angka)   # [1, 3, 5] — tapi cara ini rawan bug

# BENAR — buat list baru
angka = [1, 2, 3, 4, 5, 6]
angka = [n for n in angka if n % 2 != 0]
print(angka)   # [1, 3, 5] — bersih dan aman
```

**Kasus 4: Referensi vs Copy**

```python
# MASALAH
a = [1, 2, 3]
b = a            # b BUKAN copy! b = referensi ke a
b.append(4)
print(a)         # [1, 2, 3, 4] — a ikut berubah!

# SOLUSI
a = [1, 2, 3]
b = a.copy()           # shallow copy
# atau
b = list(a)
# atau (untuk nested list)
import copy
b = copy.deepcopy(a)   # deep copy — aman untuk nested

b.append(4)
print(a)         # [1, 2, 3] — a tidak berubah
```

---

### 16.5 Profiling (Ukur Performa Kode)

```python
import time

# Cara simpel
start = time.time()
# ... kode yang mau diukur ...
end = time.time()
print(f"Waktu: {end - start:.4f} detik")

# Cara lebih akurat
import timeit

def fungsi_a():
    return sum(range(10000))

def fungsi_b():
    total = 0
    for i in range(10000):
        total += i
    return total

# Jalankan 1000 kali dan ukur rata-rata
t_a = timeit.timeit(fungsi_a, number=1000)
t_b = timeit.timeit(fungsi_b, number=1000)

print(f"fungsi_a: {t_a:.4f}s")
print(f"fungsi_b: {t_b:.4f}s")
```

---

## LEVEL 17 — BEST PRACTICE & CLEAN CODE

### 17.1 PEP 8 — Standar Penulisan Python

```python
# Nama variable & fungsi — snake_case
nama_lengkap = "Rixz"
def hitung_total():
    pass

# Nama class — PascalCase
class BankAccount:
    pass

# Konstanta — UPPER_CASE
MAX_RETRY = 3
BASE_URL = "https://api.example.com"

# Spasi di sekitar operator
x = 1 + 2       # BENAR
x = 1+2          # SALAH

# Spasi setelah koma
def f(a, b, c):  # BENAR
def f(a,b,c):    # SALAH

# Baris maksimal 79 karakter (PEP 8) atau 120 (praktik modern)
```

### 17.2 Docstring

```python
def kalkulasi_bmi(berat, tinggi):
    """
    Hitung Body Mass Index (BMI).

    Args:
        berat (float): Berat badan dalam kilogram
        tinggi (float): Tinggi badan dalam meter

    Returns:
        float: Nilai BMI

    Raises:
        ValueError: Jika berat atau tinggi <= 0

    Example:
        >>> kalkulasi_bmi(60, 1.7)
        20.76
    """
    if berat <= 0 or tinggi <= 0:
        raise ValueError("Berat dan tinggi harus positif")
    return berat / (tinggi ** 2)
```

### 17.3 Type Hints

```python
from typing import List, Dict, Optional, Union, Tuple

def sapa(nama: str) -> str:
    return f"Halo, {nama}!"

def hitung_rata(data: List[float]) -> Optional[float]:
    if not data:
        return None
    return sum(data) / len(data)

def proses(
    input_data: Dict[str, int],
    verbose: bool = False
) -> Tuple[int, str]:
    total = sum(input_data.values())
    pesan = "sukses"
    return total, pesan
```

### 17.4 Context Manager Custom

```python
from contextlib import contextmanager

@contextmanager
def timer(label=""):
    import time
    start = time.time()
    try:
        yield
    finally:
        elapsed = time.time() - start
        print(f"{label}: {elapsed:.4f}s")

# Penggunaan
with timer("Operasi besar"):
    hasil = sum(range(1_000_000))
```

### 17.5 Decorator

```python
import functools
import time

# Decorator untuk ukur waktu eksekusi
def ukur_waktu(func):
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        start = time.time()
        hasil = func(*args, **kwargs)
        end = time.time()
        print(f"{func.__name__}: {end - start:.4f}s")
        return hasil
    return wrapper

# Decorator untuk retry otomatis
def retry(max_retries=3, delay=1):
    def decorator(func):
        @functools.wraps(func)
        def wrapper(*args, **kwargs):
            for attempt in range(max_retries):
                try:
                    return func(*args, **kwargs)
                except Exception as e:
                    if attempt == max_retries - 1:
                        raise
                    print(f"Attempt {attempt+1} gagal: {e}. Retry...")
                    time.sleep(delay)
        return wrapper
    return decorator

@ukur_waktu
def proses_besar():
    time.sleep(0.5)
    return "selesai"

@retry(max_retries=3, delay=2)
def request_tidak_stabil():
    import random
    if random.random() < 0.7:
        raise ConnectionError("Koneksi gagal")
    return "sukses"

proses_besar()
```

---

## BONUS — CHEATSHEET CEPAT

### Tipe Data

| Tipe | Contoh | Mutable |
|------|--------|---------|
| str | `"hello"` | No |
| int | `42` | No |
| float | `3.14` | No |
| bool | `True/False` | No |
| list | `[1,2,3]` | Yes |
| tuple | `(1,2,3)` | No |
| set | `{1,2,3}` | Yes |
| dict | `{"a":1}` | Yes |

### Built-in Functions Penting

```python
len(x)          # panjang
type(x)         # tipe data
range(n)        # angka 0..n-1
print(x)        # tampilkan
input(prompt)   # input user
int/float/str/bool(x)  # konversi tipe
list/tuple/set/dict(x) # konversi koleksi
sorted(x)       # list terurut (baru)
reversed(x)     # iterator terbalik
enumerate(x)    # index + nilai
zip(a, b)       # gabung dua iterable
map(f, x)       # apply fungsi ke semua
filter(f, x)    # filter berdasar fungsi
any(x)          # True jika ada satu True
all(x)          # True jika semua True
sum(x)          # jumlah
min/max(x)      # minimum/maksimum
abs(x)          # nilai absolut
round(x, n)     # pembulatan
hash(x)         # hash value
id(x)           # memory address
dir(x)          # list attribute/method
help(x)         # dokumentasi
vars(x)         # attribute sebagai dict
isinstance(x,T) # cek tipe
```

### String Methods

```python
s.upper()       s.lower()      s.title()
s.strip()       s.lstrip()     s.rstrip()
s.split(sep)    s.join(iter)   s.replace(a,b)
s.find(sub)     s.index(sub)   s.count(sub)
s.startswith()  s.endswith()   s.encode()
s.isdigit()     s.isalpha()    s.isalnum()
s.format()      s.center(n)    s.zfill(n)
```

### List Methods

```python
l.append(x)     l.extend(iter) l.insert(i,x)
l.remove(x)     l.pop(i)       l.clear()
l.index(x)      l.count(x)     l.copy()
l.sort()        l.reverse()
```

### Dict Methods

```python
d.get(k,default)  d.keys()      d.values()
d.items()         d.update(d2)  d.pop(k)
d.setdefault(k,v) d.copy()      d.clear()
```

---

## PENUTUP

```
Ini bukan akhir — ini baru awal.

Setelah dokumen ini habis, langkah berikutnya:
1. Pilih proyek nyata yang lo minatin
2. Buat sesuatu yang bisa lo pake sendiri
3. Baca source code orang lain (GitHub)
4. Contribute ke proyek open source
5. Explore: Flask/FastAPI, Scrapy, Scapy, Pwntools

Kalo lo bingung di mana pun, tanya r¡z | assistant.
Ga ada kata menyerah — ada kata "belum ketemu caranya".
```

---

*Dokumen ini dibuat oleh r¡z | assistant — 2026*
*Versi: 1.0.0 | Python 3.10+*
