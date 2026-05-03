# MACHINE LEARNING DI ANDROID
## Dari Nol Sampai Pro — 100% Offline, Free, Termux + Python
### r¡z | assistant — 2026

---

> **Ini dokumen belajar ML paling lengkap yang bisa lo jalanin di HP doang.**
> Ga butuh laptop. Ga butuh internet (setelah setup awal). Ga butuh bayar apapun.
> Yang lo butuh: HP, Termux, otak, dan waktu.

---

## DAFTAR ISI

```
BAGIAN 0  — Mindset & Peta Jalan
BAGIAN 1  — Setup Termux (Environment ML di Android)
BAGIAN 2  — Matematika ML (Wajib Paham)
  2.1 — Aljabar Linear
  2.2 — Kalkulus & Turunan
  2.3 — Statistika & Probabilitas
BAGIAN 3  — NumPy (Tulang Punggung ML)
BAGIAN 4  — Pandas (Olah Data)
BAGIAN 5  — Matplotlib (Visualisasi — via file)
BAGIAN 6  — ML dari Scratch (Tanpa Library)
  6.1 — Linear Regression
  6.2 — Logistic Regression
  6.3 — K-Nearest Neighbors
  6.4 — Decision Tree
BAGIAN 7  — Scikit-learn (Library ML Utama)
BAGIAN 8  — Neural Network dari Scratch
BAGIAN 9  — Neural Network dengan Keras/TFLite
BAGIAN 10 — Proyek Nyata
BAGIAN 11 — Analisis & Debug Model ML
BONUS     — Cheatsheet & Referensi Offline
```

---

## BAGIAN 0 — MINDSET & PETA JALAN

### Apa itu Machine Learning?

Komputer biasanya bekerja dengan aturan yang lo tulis sendiri:

```
IF suhu > 37 THEN "demam"
IF suhu <= 37 THEN "normal"
```

Machine Learning itu kebalikannya. Lo kasih **data** ke komputer, biarkan dia **sendiri menemukan aturannya**.

```
DATA: [36.5→normal, 38.0→demam, 37.2→normal, 39.1→demam, ...]
KOMPUTER: "Oh jadi kalau > 37.5 itu demam ya? Gua pelajari sendiri."
```

### Tiga Jenis ML

```
SUPERVISED LEARNING
— Lo kasih data + jawaban yang benar
— Komputer belajar pola dari pasangan (input → output)
— Contoh: spam detection, prediksi harga rumah

UNSUPERVISED LEARNING
— Lo kasih data tanpa jawaban
— Komputer cari pola sendiri
— Contoh: clustering pelanggan, anomaly detection

REINFORCEMENT LEARNING
— Komputer belajar dari reward/punishment
— Seperti melatih anjing dengan hadiah
— Contoh: game AI, robot
```

### Peta Jalan Belajar

```
BULAN 1: Matematika + NumPy + Pandas
BULAN 2: Algoritma ML dari Scratch (pahami cara kerjanya)
BULAN 3: Scikit-learn + Proyek pertama
BULAN 4: Neural Network dari Scratch
BULAN 5: Keras + Proyek serius
BULAN 6+: Specialisasi (NLP / Computer Vision / RL)
```

---

## BAGIAN 1 — SETUP TERMUX

### 1.1 Install Termux

Download Termux dari **F-Droid** (bukan Play Store — versinya lebih update).

```bash
# Update package list
pkg update && pkg upgrade -y

# Install Python dan dependencies wajib
pkg install python python-pip git clang libffi openssl -y

# Install build tools (dibutuhkan beberapa library)
pkg install build-essential -y
```

### 1.2 Install Library ML

```bash
# Ini yang bakal sering lo pake. Install satu-satu kalau ada error.

# Core ML stack
pip install numpy
pip install pandas
pip install scikit-learn
pip install scipy
pip install joblib

# Visualisasi (output ke file PNG/SVG)
pip install matplotlib

# Utility
pip install tqdm         # progress bar
pip install tabulate     # tampilkan tabel di terminal
pip install colorama     # warna di terminal

# Kalau mau Neural Network ringan (pilih salah satu)
pip install tensorflow   # berat, mungkin berhasil di RAM 4GB+
pip install tflite-runtime  # lebih ringan
# ATAU — pakai keras pure python (paling ringan)
pip install keras
```

### 1.3 Cek Instalasi

```python
# Buat file: cek_env.py
# Jalanin: python3 cek_env.py

import sys
print(f"Python: {sys.version}")

libraries = [
    "numpy", "pandas", "sklearn",
    "scipy", "matplotlib", "joblib"
]

for lib in libraries:
    try:
        mod = __import__(lib)
        ver = getattr(mod, "__version__", "installed")
        print(f"[OK] {lib}: {ver}")
    except ImportError:
        print(f"[MISSING] {lib} — install dulu!")
```

### 1.4 Setup Neovim untuk Python ML

```bash
# Install Neovim
pkg install neovim -y

# Buat config folder
mkdir -p ~/.config/nvim

# Buat init.vim dasar
cat > ~/.config/nvim/init.vim << 'EOF'
set number          " nomor baris
set tabstop=4       " tab = 4 spasi
set shiftwidth=4
set expandtab       " tab jadi spasi
set autoindent
set smartindent
set syntax=on
set hlsearch        " highlight hasil search
set ignorecase      " search case-insensitive
set mouse=a         " mouse support
set clipboard=unnamed

" Jalanin Python dengan F5
autocmd FileType python nnoremap <F5> :w<CR>:!python3 %<CR>

" Jalanin Python dan simpan output ke file dengan F6
autocmd FileType python nnoremap <F6> :w<CR>:!python3 % > output.txt 2>&1<CR>
EOF

echo "Neovim siap!"
```

### 1.5 Struktur Folder Belajar ML

```bash
mkdir -p ~/ml-belajar/{data,models,notebooks,utils,proyek}
cd ~/ml-belajar
```

```
~/ml-belajar/
├── data/           — dataset yang lo pake
├── models/         — model yang udah dilatih (disimpan)
├── notebooks/      — eksperimen dan latihan
├── utils/          — fungsi helper yang sering dipakai
└── proyek/         — proyek nyata
```

---

## BAGIAN 2 — MATEMATIKA UNTUK ML

> Ini bagian yang banyak orang skip. Jangan lo skip.
> Tanpa ini lo cuma tau cara **pakai** ML, bukan cara **memahami** ML.
> Penjelasannya gua bikin sesimpel mungkin — kayak ngomong sama bocah SD tapi dengan konten SMA.

---

### 2.1 ALJABAR LINEAR

#### A. Skalar, Vektor, Matriks, Tensor

```
SKALAR = satu angka biasa
  x = 5

VEKTOR = barisan angka (satu dimensi)
  v = [1, 2, 3]     ← vektor baris
  v = [[1],          ← vektor kolom
       [2],
       [3]]

MATRIKS = tabel angka (dua dimensi)
  M = [[1, 2, 3],
       [4, 5, 6],
       [7, 8, 9]]

TENSOR = matriks banyak dimensi (3D, 4D, dst)
  T = [[[1,2],[3,4]], [[5,6],[7,8]]]   ← tensor 3D
```

**Kenapa ini penting?**
- Data lo = matriks (baris = sampel, kolom = fitur)
- Gambar = tensor 3D (tinggi × lebar × channel_warna)
- Bobot neural network = matriks

#### B. Operasi Vektor

```python
# Contoh manual tanpa library dulu — biar paham
a = [1, 2, 3]
b = [4, 5, 6]

# Penjumlahan vektor
c = [a[i] + b[i] for i in range(len(a))]
# c = [5, 7, 9]

# Pengurangan vektor
d = [a[i] - b[i] for i in range(len(a))]
# d = [-3, -3, -3]

# Skalar kali vektor
skalar = 2
e = [skalar * x for x in a]
# e = [2, 4, 6]
```

**Visualisasi vektor:**
```
a = [1, 2]  →  titik di koordinat (1,2)
              arahnya: dari (0,0) ke (1,2)

b = [3, 1]  →  titik di koordinat (3,1)

a + b = [4, 3]  →  titik (4,3)
              kayak jalan 1 ke kanan 2 ke atas,
              terus 3 ke kanan 1 ke atas.
              Hasilnya di (4,3)
```

#### C. Dot Product (Perkalian Titik)

Ini yang paling sering dipake di ML.

```
a · b = a[0]*b[0] + a[1]*b[1] + a[2]*b[2] + ...

Contoh:
a = [1, 2, 3]
b = [4, 5, 6]

a · b = (1×4) + (2×5) + (3×6)
      = 4 + 10 + 18
      = 32
```

```python
# Manual
def dot_product(a, b):
    return sum(a[i] * b[i] for i in range(len(a)))

a = [1, 2, 3]
b = [4, 5, 6]
print(dot_product(a, b))  # 32
```

**Kenapa dot product penting?**

```
Di ML: prediksi = dot(bobot, input) + bias

Contoh prediksi harga rumah:
bobot = [100000, 50000, -10000]
        (per m²,  per kamar, per tahun_tua)
input  = [50, 3, 5]
         (50m², 3 kamar, 5 tahun)

prediksi = (100000×50) + (50000×3) + (-10000×5)
         = 5000000 + 150000 - 50000
         = 5100000
```

#### D. Perkalian Matriks

```
A (m×n) × B (n×p) = C (m×p)

Syarat: kolom A harus sama dengan baris B

A = [[1, 2],    B = [[5, 6],
     [3, 4]]         [7, 8]]

C[0][0] = A[0] · B_kolom0 = [1,2]·[5,7] = 5+14 = 19
C[0][1] = A[0] · B_kolom1 = [1,2]·[6,8] = 6+16 = 22
C[1][0] = A[1] · B_kolom0 = [3,4]·[5,7] = 15+28 = 43
C[1][1] = A[1] · B_kolom1 = [3,4]·[6,8] = 18+32 = 50

C = [[19, 22],
     [43, 50]]
```

```python
def matmul(A, B):
    m, n = len(A), len(A[0])
    n2, p = len(B), len(B[0])
    assert n == n2, "Dimensi tidak cocok!"

    C = [[0] * p for _ in range(m)]
    for i in range(m):
        for j in range(p):
            for k in range(n):
                C[i][j] += A[i][k] * B[k][j]
    return C

A = [[1,2],[3,4]]
B = [[5,6],[7,8]]
print(matmul(A, B))  # [[19,22],[43,50]]
```

#### E. Transpose Matriks

```
A = [[1, 2, 3],     A.T = [[1, 4],
     [4, 5, 6]]            [2, 5],
                           [3, 6]]

Baris jadi kolom, kolom jadi baris.
```

```python
def transpose(A):
    return [[A[j][i] for j in range(len(A))]
            for i in range(len(A[0]))]
```

#### F. Magnitude (Panjang Vektor) & Normalisasi

```
|v| = sqrt(v[0]² + v[1]² + v[2]²)

v = [3, 4]
|v| = sqrt(9 + 16) = sqrt(25) = 5

Normalisasi: v_norm = v / |v|
v_norm = [3/5, 4/5] = [0.6, 0.8]

Vektor ternormalisasi: panjangnya selalu 1
```

```python
import math

def magnitude(v):
    return math.sqrt(sum(x**2 for x in v))

def normalize(v):
    mag = magnitude(v)
    return [x / mag for x in v]

v = [3, 4]
print(magnitude(v))   # 5.0
print(normalize(v))   # [0.6, 0.8]
```

---

### 2.2 KALKULUS & TURUNAN

> Ini bagian paling penting untuk training neural network.
> Konsep utama: **gradient descent** — cara komputer belajar dari kesalahan.

#### A. Fungsi & Grafik

```
Fungsi = mesin yang terima input, keluarkan output

f(x) = x²        → input 3, output 9
f(x) = 2x + 1    → input 3, output 7
f(x) = sin(x)    → input π, output 0
```

#### B. Turunan (Derivative)

Turunan = **seberapa cepat fungsi berubah** di suatu titik.
Alias: kemiringan (slope) grafik di titik itu.

```
f(x) = x²

Turunan f'(x) = 2x

Di x=3:   f'(3) = 6   → grafik naik cepat di sini
Di x=0:   f'(0) = 0   → grafik datar di sini (titik minimum)
Di x=-2:  f'(-2) = -4 → grafik turun di sini
```

**Rumus Turunan Dasar:**
```
f(x) = c         → f'(x) = 0          (konstanta)
f(x) = x         → f'(x) = 1
f(x) = xⁿ        → f'(x) = n·xⁿ⁻¹
f(x) = eˣ        → f'(x) = eˣ
f(x) = ln(x)     → f'(x) = 1/x
f(x) = sin(x)    → f'(x) = cos(x)
f(x) = cos(x)    → f'(x) = -sin(x)

CHAIN RULE (Aturan Rantai):
f(g(x))' = f'(g(x)) · g'(x)

Contoh:
f(x) = (2x + 1)³
g(x) = 2x + 1    → g'(x) = 2
f(u) = u³        → f'(u) = 3u²

f'(x) = 3(2x+1)² · 2 = 6(2x+1)²
```

**Cara intuisi turunan:**

```python
# Turunan numerik (pendekatan)
def turunan(f, x, h=0.0001):
    """
    Definisi turunan:
    f'(x) = lim(h→0) [f(x+h) - f(x)] / h
    """
    return (f(x + h) - f(x)) / h

# Test
f = lambda x: x**2        # f(x) = x²
print(turunan(f, 3))      # ~6.0 (harusnya persis 6)

g = lambda x: 3*x**2 + 2*x + 1
print(turunan(g, 2))      # ~14.0 (6x+2 di x=2 = 14)
```

#### C. Gradient Descent (Inti dari ML)

Ini inti dari cara ML belajar. Visualisasinya gini:

```
Bayangin lo berdiri di bukit yang berkabut.
Lo mau turun ke lembah (titik terendah).
Lo ga bisa liat jauh karena kabut.

Yang bisa lo lakukan:
1. Rasain kemiringan tanah di bawah kaki lo (hitung gradient)
2. Melangkah ke arah turun (update parameter)
3. Ulangi sampai ga ada lagi yang lebih rendah

Itulah Gradient Descent.
```

**Algoritma:**
```
1. Tentukan fungsi loss L(w) — ngukur seberapa salah model
2. Hitung turunan L terhadap w: dL/dw (arah naiknya)
3. Update: w = w - learning_rate × (dL/dw)
4. Ulangi sampai konvergen
```

```python
# Gradient Descent dari scratch
# Cari nilai minimum dari f(x) = x² - 4x + 5
# (minimum ada di x=2, f(2)=1)

def f(x):
    return x**2 - 4*x + 5

def df(x):  # turunan f: 2x - 4
    return 2*x - 4

# Hyperparameter
learning_rate = 0.1
x = 10.0        # mulai dari x=10 (jauh dari minimum)
iterasi = 50

print(f"Start: x={x:.4f}, f(x)={f(x):.4f}")

for i in range(iterasi):
    gradient = df(x)            # hitung kemiringan
    x = x - learning_rate * gradient  # langkah ke arah turun

    if i % 10 == 0:
        print(f"Iter {i:3d}: x={x:.6f}, f(x)={f(x:.6f}")

print(f"\nMinimum ditemukan: x={x:.6f}, f(x)={f(x):.6f}")
# Harusnya: x≈2.0, f(x)≈1.0
```

#### D. Partial Derivative (Turunan Parsial)

Kalau fungsinya punya banyak variabel (seperti bobot neural network):

```
f(w1, w2) = w1² + 3·w1·w2 + w2²

∂f/∂w1 = 2w1 + 3w2   (anggap w2 konstan)
∂f/∂w2 = 3w1 + 2w2   (anggap w1 konstan)

Gradient = [∂f/∂w1, ∂f/∂w2]
```

---

### 2.3 STATISTIKA & PROBABILITAS

#### A. Ukuran Pemusatan Data

```python
data = [2, 4, 4, 4, 5, 5, 7, 9]

# MEAN (Rata-rata)
mean = sum(data) / len(data)
# mean = 5.0

# MEDIAN (Nilai tengah)
sorted_data = sorted(data)
n = len(sorted_data)
if n % 2 == 0:
    median = (sorted_data[n//2 - 1] + sorted_data[n//2]) / 2
else:
    median = sorted_data[n//2]
# median = 4.5

# MODE (Nilai yang paling sering muncul)
from collections import Counter
mode = Counter(data).most_common(1)[0][0]
# mode = 4
```

#### B. Ukuran Penyebaran Data

```python
import math

data = [2, 4, 4, 4, 5, 5, 7, 9]
mean = sum(data) / len(data)

# VARIANCE (Varians) — rata-rata kuadrat jarak ke mean
variance = sum((x - mean)**2 for x in data) / len(data)
# variance = 3.5

# STANDARD DEVIATION (Simpangan Baku)
std = math.sqrt(variance)
# std ≈ 1.87

# RANGE
data_range = max(data) - min(data)
# range = 7
```

**Intuisi Varians & Std:**
```
Data A: [5, 5, 5, 5, 5]    → std = 0   (semua sama, ga ada spread)
Data B: [1, 3, 5, 7, 9]    → std = 2.8 (agak menyebar)
Data C: [1, 1, 5, 9, 9]    → std = 3.6 (lebih menyebar)

Std besar = data menyebar jauh dari mean
Std kecil = data berkumpul dekat mean
```

#### C. Korelasi

Ukur seberapa kuat hubungan antara dua variabel.

```
Korelasi = -1 sampai +1

+1 : sempurna positif (X naik → Y naik sempurna)
 0 : tidak ada hubungan
-1 : sempurna negatif (X naik → Y turun sempurna)
```

```python
def korelasi(x, y):
    n = len(x)
    mean_x = sum(x) / n
    mean_y = sum(y) / n

    # Kovarians
    cov = sum((x[i] - mean_x) * (y[i] - mean_y) for i in range(n)) / n

    # Std masing-masing
    std_x = math.sqrt(sum((xi - mean_x)**2 for xi in x) / n)
    std_y = math.sqrt(sum((yi - mean_y)**2 for yi in y) / n)

    return cov / (std_x * std_y)

# Tinggi vs berat badan (biasanya positif)
tinggi = [150, 160, 170, 175, 180]
berat  = [50,  60,  70,  75,  85]
print(f"Korelasi: {korelasi(tinggi, berat):.4f}")  # ~0.99
```

#### D. Probabilitas Dasar

```
P(A) = kemungkinan kejadian A terjadi
       = jumlah cara A terjadi / total kemungkinan

0 ≤ P(A) ≤ 1

P(dadu = 6) = 1/6 ≈ 0.167
P(koin = kepala) = 1/2 = 0.5

P(A dan B) = P(A) × P(B)   ← jika A dan B independen
P(A atau B) = P(A) + P(B) - P(A dan B)
P(bukan A) = 1 - P(A)
```

#### E. Distribusi Normal (Gaussian)

Ini yang paling sering muncul di ML.

```
Bentuknya lonceng (bell curve)
Ditentukan oleh: mean (μ) dan std (σ)

Aturan 68-95-99.7:
  68% data ada di μ ± 1σ
  95% data ada di μ ± 2σ
  99.7% data ada di μ ± 3σ
```

```python
import math

def pdf_normal(x, mean, std):
    """Probability Density Function distribusi normal"""
    koef = 1 / (std * math.sqrt(2 * math.pi))
    exp_term = math.exp(-0.5 * ((x - mean) / std)**2)
    return koef * exp_term

# Distribusi nilai ujian: mean=70, std=10
mean, std = 70, 10

print(f"P(nilai=70): {pdf_normal(70, mean, std):.4f}")  # puncak
print(f"P(nilai=80): {pdf_normal(80, mean, std):.4f}")
print(f"P(nilai=90): {pdf_normal(90, mean, std):.4f}")  # makin kecil
```

#### F. Bayes Theorem

```
P(A|B) = P(B|A) × P(A) / P(B)

Dibaca: "Probabilitas A terjadi, JIKA diketahui B terjadi"

P(A)   = Prior — keyakinan awal
P(B|A) = Likelihood — kemungkinan B kalau A terjadi
P(A|B) = Posterior — keyakinan setelah dapat info B
```

```python
# Contoh: deteksi spam
# P(spam) = 0.2             — 20% email adalah spam
# P(kata "menang"|spam) = 0.8   — 80% spam ada kata "menang"
# P(kata "menang"|normal) = 0.05 — 5% email normal ada kata "menang"

def bayes(p_A, p_B_given_A, p_B_given_not_A):
    """Hitung P(A|B) dengan Bayes Theorem"""
    p_not_A = 1 - p_A
    p_B = p_B_given_A * p_A + p_B_given_not_A * p_not_A
    return (p_B_given_A * p_A) / p_B

p_spam = 0.2
p_menang_spam = 0.8
p_menang_normal = 0.05

p_spam_given_menang = bayes(p_spam, p_menang_spam, p_menang_normal)
print(f"P(spam | ada kata 'menang'): {p_spam_given_menang:.4f}")
# ≈ 0.8 — 80% kemungkinan spam kalau ada kata "menang"
```

---

## BAGIAN 3 — NUMPY

> NumPy itu fondasi ML di Python. Semua library ML (scikit-learn, keras, dll)
> di bawahnya pake NumPy. Lo HARUS paham ini.

### 3.1 Array Dasar

```python
import numpy as np

# Buat array dari list
a = np.array([1, 2, 3, 4, 5])
print(a)           # [1 2 3 4 5]
print(a.shape)     # (5,) — 5 elemen, 1 dimensi
print(a.dtype)     # int64
print(a.ndim)      # 1

# Array 2D (matriks)
M = np.array([[1, 2, 3],
              [4, 5, 6]])
print(M.shape)     # (2, 3) — 2 baris, 3 kolom
print(M.ndim)      # 2

# Array 3D (tensor)
T = np.array([[[1,2],[3,4]],
              [[5,6],[7,8]]])
print(T.shape)     # (2, 2, 2)
```

### 3.2 Buat Array Khusus

```python
# Nol semua
zeros = np.zeros((3, 4))       # matriks 3x4 isi 0

# Satu semua
ones = np.ones((2, 3))         # matriks 2x3 isi 1

# Identity matrix
I = np.eye(3)                  # matriks identitas 3x3

# Random
rng = np.random.default_rng(42)  # seed untuk reproducibility
r1 = rng.random((3, 3))       # uniform 0-1
r2 = rng.normal(0, 1, (3, 3)) # normal dengan mean=0, std=1
r3 = rng.integers(0, 10, (3, 3)) # integer 0-9

# Range
a = np.arange(0, 10, 2)       # [0, 2, 4, 6, 8]
b = np.linspace(0, 1, 5)      # [0, 0.25, 0.5, 0.75, 1.0]
```

### 3.3 Operasi Array

```python
a = np.array([1, 2, 3, 4])
b = np.array([10, 20, 30, 40])

# ELEMENT-WISE (operasi per elemen)
print(a + b)    # [11, 22, 33, 44]
print(a * b)    # [10, 40, 90, 160]
print(a ** 2)   # [1, 4, 9, 16]
print(np.sqrt(a)) # [1, 1.41, 1.73, 2.0]

# BROADCASTING — operasi dengan skalar
print(a * 3)    # [3, 6, 9, 12]
print(a + 100)  # [101, 102, 103, 104]

# DOT PRODUCT
print(np.dot(a, b))   # 1*10 + 2*20 + 3*30 + 4*40 = 300

# MATRIX MULTIPLICATION
A = np.array([[1,2],[3,4]])
B = np.array([[5,6],[7,8]])
print(A @ B)      # [[19,22],[43,50]]  (operator @)
print(np.matmul(A, B))  # sama

# TRANSPOSE
print(A.T)        # [[1,3],[2,4]]
```

### 3.4 Indexing & Slicing

```python
a = np.array([10, 20, 30, 40, 50])

print(a[0])      # 10
print(a[-1])     # 50
print(a[1:4])    # [20, 30, 40]
print(a[::2])    # [10, 30, 50]

# 2D indexing
M = np.array([[1,2,3],[4,5,6],[7,8,9]])

print(M[1, 2])    # 6 — baris 1, kolom 2
print(M[0, :])    # [1, 2, 3] — baris 0, semua kolom
print(M[:, 1])    # [2, 5, 8] — semua baris, kolom 1
print(M[0:2, 1:]) # [[2,3],[5,6]] — submatriks

# BOOLEAN INDEXING — ini penting banget!
a = np.array([1, 5, 3, 8, 2, 9, 4])
mask = a > 4
print(mask)     # [F, T, F, T, F, T, F]
print(a[mask])  # [5, 8, 9] — hanya yang True
print(a[a > 4]) # lebih singkat, hasil sama
```

### 3.5 Operasi Agregasi

```python
data = np.array([[4, 7, 2],
                 [3, 8, 1],
                 [6, 5, 9]])

print(np.sum(data))          # 45 — jumlah semua
print(np.sum(data, axis=0))  # [13,20,12] — jumlah per kolom
print(np.sum(data, axis=1))  # [13,12,20] — jumlah per baris

print(np.mean(data))         # 5.0
print(np.mean(data, axis=0)) # mean per kolom

print(np.min(data))          # 1
print(np.max(data))          # 9
print(np.argmin(data))       # 8 (index flat dari minimum)
print(np.argmax(data))       # 8 (index flat dari maximum)

print(np.std(data))          # standard deviation
print(np.var(data))          # variance
```

### 3.6 Reshape & Flatten

```python
a = np.arange(12)     # [0,1,2,...,11]

b = a.reshape(3, 4)   # reshape jadi 3x4
c = a.reshape(2, 6)   # reshape jadi 2x6
d = a.reshape(2, 2, 3)  # reshape jadi 3D

flat = b.flatten()    # balik ke 1D
flat2 = b.ravel()     # sama tapi reference (lebih cepat)

# -1 berarti "hitung sendiri"
e = a.reshape(3, -1)  # 3 baris, kolom dihitung otomatis → (3,4)
f = a.reshape(-1, 4)  # kolom 4, baris dihitung otomatis → (3,4)
```

### 3.7 Stack & Concatenate

```python
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

# Concatenate — gabung dalam 1 dimensi
print(np.concatenate([a, b]))   # [1,2,3,4,5,6]

# Stack — buat dimensi baru
print(np.stack([a, b]))         # [[1,2,3],[4,5,6]] — (2,3)
print(np.vstack([a, b]))        # vertical stack (baris baru)
print(np.hstack([a, b]))        # horizontal stack (kolom baru)

# Contoh nyata: gabung fitur dengan label
X = np.array([[1,2],[3,4],[5,6]])  # 3 sampel, 2 fitur
y = np.array([0, 1, 0])            # label

data = np.column_stack([X, y])     # gabung jadi 1 matriks
print(data)
```

### 3.8 NumPy untuk Operasi ML Nyata

```python
# Normalisasi data (Min-Max Scaling)
data = np.array([10.0, 20.0, 30.0, 40.0, 50.0])

def min_max_scale(x):
    return (x - x.min()) / (x.max() - x.min())

scaled = min_max_scale(data)
print(scaled)  # [0.0, 0.25, 0.5, 0.75, 1.0]

# Standardisasi (Z-score normalization)
def standardize(x):
    return (x - x.mean()) / x.std()

std_data = standardize(data)
print(std_data.mean())  # ≈ 0
print(std_data.std())   # ≈ 1

# Fungsi aktivasi neural network
def sigmoid(x):
    return 1 / (1 + np.exp(-x))

def relu(x):
    return np.maximum(0, x)

def softmax(x):
    exp_x = np.exp(x - x.max())  # substract max untuk stabilitas
    return exp_x / exp_x.sum()

x = np.array([-2, -1, 0, 1, 2])
print(sigmoid(x))    # [0.12, 0.27, 0.5, 0.73, 0.88]
print(relu(x))       # [0, 0, 0, 1, 2]
print(softmax(x))    # [0.02, 0.06, 0.18, 0.47, 0.87] — jumlah = 1
```

---

## BAGIAN 4 — PANDAS

> Pandas itu alat olah data. Data dunia nyata = kotor, tidak lengkap, format aneh.
> Pandas bantu lo bersihkan, analisa, dan siapkan data untuk ML.

### 4.1 DataFrame & Series

```python
import pandas as pd
import numpy as np

# SERIES — kolom tunggal
s = pd.Series([10, 20, 30, 40], index=["a","b","c","d"])
print(s)
print(s["b"])    # 20
print(s[1])      # 20

# DATAFRAME — tabel 2D
data = {
    "nama": ["Ali", "Budi", "Cici", "Dedi"],
    "umur": [25, 30, 22, 35],
    "nilai": [85.5, 72.0, 90.0, 68.5],
    "lulus": [True, True, True, False]
}

df = pd.DataFrame(data)
print(df)
print(df.shape)       # (4, 4)
print(df.dtypes)      # tipe tiap kolom
print(df.info())      # ringkasan lengkap
print(df.describe())  # statistik dasar
```

### 4.2 Akses Data

```python
# Akses kolom
print(df["nama"])          # Series
print(df[["nama", "umur"]]) # DataFrame (double bracket)

# Akses baris dengan loc (label) dan iloc (index)
print(df.loc[0])           # baris index 0
print(df.iloc[0])          # baris posisi 0 (sama kalau index default)
print(df.loc[0:2])         # baris 0, 1, 2
print(df.iloc[0:2])        # baris 0, 1 (TIDAK include 2)

# Filter (boolean indexing)
muda = df[df["umur"] < 30]
nilai_tinggi = df[df["nilai"] >= 80]
filter_ganda = df[(df["umur"] < 30) & (df["lulus"] == True)]

# Akses sel spesifik
print(df.loc[1, "nama"])   # "Budi"
print(df.at[1, "nama"])    # sama, lebih cepat
```

### 4.3 Manipulasi Data

```python
# Tambah kolom baru
df["grade"] = df["nilai"].apply(lambda x: "A" if x >= 85 else "B")

# Ubah nilai
df.loc[df["nama"] == "Ali", "nilai"] = 88.0

# Hapus kolom
df = df.drop(columns=["lulus"])
df = df.drop("lulus", axis=1)   # sama

# Hapus baris
df = df.drop(index=2)

# Rename kolom
df = df.rename(columns={"nilai": "score", "nama": "name"})

# Sort
df = df.sort_values("score", ascending=False)
df = df.sort_values(["umur", "score"], ascending=[True, False])

# Reset index setelah sort/filter
df = df.reset_index(drop=True)
```

### 4.4 Handling Missing Data

```python
# Buat data dengan nilai kosong
data = {
    "A": [1, 2, None, 4, 5],
    "B": [10, None, None, 40, 50],
    "C": [100, 200, 300, None, 500]
}
df = pd.DataFrame(data)

# Cek missing values
print(df.isnull())          # True/False tiap sel
print(df.isnull().sum())    # jumlah missing per kolom
print(df.isnull().sum().sum())  # total missing

# Hapus baris yang punya missing value
df_clean = df.dropna()

# Hapus kolom yang lebih dari 50% missing
df_clean = df.dropna(thresh=len(df)*0.5, axis=1)

# Isi dengan nilai tertentu
df_filled = df.fillna(0)           # isi dengan 0
df_filled = df.fillna(df.mean())   # isi dengan mean kolom
df_filled = df.fillna(method="ffill")  # isi dari nilai sebelumnya
df_filled = df.fillna(method="bfill")  # isi dari nilai berikutnya

# Isi per kolom
df["A"] = df["A"].fillna(df["A"].median())
df["B"] = df["B"].fillna(df["B"].mean())
```

### 4.5 Groupby & Aggregasi

```python
data = {
    "kelas": ["A","A","B","B","C","C"],
    "nama": ["Ali","Budi","Cici","Dedi","Eka","Fani"],
    "nilai": [85, 90, 70, 75, 88, 82],
    "jam_belajar": [5, 6, 3, 4, 7, 6]
}
df = pd.DataFrame(data)

# Rata-rata per kelas
print(df.groupby("kelas")["nilai"].mean())

# Multiple agregasi
result = df.groupby("kelas").agg({
    "nilai": ["mean", "max", "min"],
    "jam_belajar": "sum"
})
print(result)

# Pivot table
pivot = df.pivot_table(
    values="nilai",
    index="kelas",
    aggfunc=["mean", "count"]
)
```

### 4.6 Baca & Tulis File

```python
# CSV
df.to_csv("data.csv", index=False)
df = pd.read_csv("data.csv")

# JSON
df.to_json("data.json", orient="records")
df = pd.read_json("data.json")

# Excel (butuh openpyxl: pip install openpyxl)
df.to_excel("data.xlsx", index=False)
df = pd.read_excel("data.xlsx")

# Baca CSV dari string (berguna untuk testing)
import io
csv_text = """nama,umur,nilai
Ali,25,85
Budi,30,72
"""
df = pd.read_csv(io.StringIO(csv_text))
```

### 4.7 Pipeline Data untuk ML

```python
import pandas as pd
import numpy as np

def siapkan_data_ml(filepath):
    """Pipeline lengkap dari CSV ke X, y siap ML"""

    # 1. Load data
    df = pd.read_csv(filepath)
    print(f"Shape awal: {df.shape}")

    # 2. Cek & tangani missing values
    print(f"Missing values:\n{df.isnull().sum()}")
    for col in df.select_dtypes(include=[np.number]).columns:
        df[col] = df[col].fillna(df[col].median())

    # 3. Tangani outlier dengan IQR
    for col in df.select_dtypes(include=[np.number]).columns:
        Q1 = df[col].quantile(0.25)
        Q3 = df[col].quantile(0.75)
        IQR = Q3 - Q1
        lower = Q1 - 1.5 * IQR
        upper = Q3 + 1.5 * IQR
        df[col] = df[col].clip(lower, upper)

    # 4. Encode categorical (label encoding sederhana)
    for col in df.select_dtypes(include=["object"]).columns:
        if col != "target":  # jangan encode target
            df[col] = pd.Categorical(df[col]).codes

    # 5. Pisah fitur dan label
    X = df.drop("target", axis=1).values
    y = df["target"].values

    return X, y
```

---

## BAGIAN 5 — MATPLOTLIB (VISUALISASI)

> Di Android, ga bisa tampil window grafik secara langsung.
> Tapi bisa disimpan ke file PNG dan dibuka di galeri/Acode.

### 5.1 Setup Matplotlib untuk Android

```python
import matplotlib
matplotlib.use("Agg")  # WAJIB di Android — mode non-interactive
import matplotlib.pyplot as plt
import numpy as np

# Fungsi helper simpan plot
def save_plot(filename, dpi=150):
    plt.savefig(filename, dpi=dpi, bbox_inches="tight",
                facecolor="white")
    plt.close()
    print(f"Plot disimpan: {filename}")
```

### 5.2 Plot Dasar

```python
matplotlib.use("Agg")
import matplotlib.pyplot as plt
import numpy as np

# LINE PLOT
x = np.linspace(0, 10, 100)
y1 = np.sin(x)
y2 = np.cos(x)

plt.figure(figsize=(10, 5))
plt.plot(x, y1, label="sin(x)", color="blue", linewidth=2)
plt.plot(x, y2, label="cos(x)", color="red", linestyle="--")
plt.title("Fungsi Trigonometri")
plt.xlabel("x")
plt.ylabel("y")
plt.legend()
plt.grid(True, alpha=0.3)
save_plot("plot_sin_cos.png")

# SCATTER PLOT
x = np.random.randn(100)
y = 2*x + np.random.randn(100) * 0.5

plt.figure(figsize=(8, 6))
plt.scatter(x, y, alpha=0.6, c="blue", edgecolors="navy")
plt.title("Scatter Plot")
plt.xlabel("X")
plt.ylabel("Y")
save_plot("scatter.png")

# HISTOGRAM
data = np.random.normal(70, 10, 1000)

plt.figure(figsize=(8, 5))
plt.hist(data, bins=30, edgecolor="black", color="steelblue")
plt.axvline(data.mean(), color="red", linestyle="--",
            label=f"Mean: {data.mean():.1f}")
plt.title("Distribusi Nilai")
plt.xlabel("Nilai")
plt.ylabel("Frekuensi")
plt.legend()
save_plot("histogram.png")
```

### 5.3 Visualisasi untuk ML

```python
matplotlib.use("Agg")
import matplotlib.pyplot as plt
import numpy as np

# LOSS CURVE — penting buat monitor training
def plot_loss(train_losses, val_losses=None, filename="loss.png"):
    plt.figure(figsize=(10, 5))
    epochs = range(1, len(train_losses) + 1)

    plt.plot(epochs, train_losses, "b-", label="Training Loss", linewidth=2)
    if val_losses:
        plt.plot(epochs, val_losses, "r--", label="Validation Loss", linewidth=2)

    plt.title("Training Loss per Epoch")
    plt.xlabel("Epoch")
    plt.ylabel("Loss")
    plt.legend()
    plt.grid(True, alpha=0.3)
    plt.tight_layout()
    save_plot(filename)

# CONFUSION MATRIX
def plot_confusion_matrix(cm, classes, filename="confusion_matrix.png"):
    plt.figure(figsize=(8, 6))
    plt.imshow(cm, interpolation="nearest", cmap=plt.cm.Blues)
    plt.title("Confusion Matrix")
    plt.colorbar()

    tick_marks = np.arange(len(classes))
    plt.xticks(tick_marks, classes, rotation=45)
    plt.yticks(tick_marks, classes)

    thresh = cm.max() / 2
    for i in range(cm.shape[0]):
        for j in range(cm.shape[1]):
            plt.text(j, i, cm[i, j], ha="center", va="center",
                     color="white" if cm[i, j] > thresh else "black")

    plt.ylabel("Aktual")
    plt.xlabel("Prediksi")
    plt.tight_layout()
    save_plot(filename)

# DECISION BOUNDARY (2D)
def plot_decision_boundary(model, X, y, filename="boundary.png"):
    h = 0.02
    x_min, x_max = X[:, 0].min() - 1, X[:, 0].max() + 1
    y_min, y_max = X[:, 1].min() - 1, X[:, 1].max() + 1

    xx, yy = np.meshgrid(np.arange(x_min, x_max, h),
                          np.arange(y_min, y_max, h))

    Z = model.predict(np.c_[xx.ravel(), yy.ravel()])
    Z = Z.reshape(xx.shape)

    plt.figure(figsize=(8, 6))
    plt.contourf(xx, yy, Z, alpha=0.4, cmap="RdYlBu")
    plt.scatter(X[:, 0], X[:, 1], c=y, cmap="RdYlBu", edgecolors="black")
    plt.title("Decision Boundary")
    save_plot(filename)
```
---

## BAGIAN 6 — ALGORITMA ML DARI SCRATCH

> Lo HARUS implementasi algoritma dari scratch dulu.
> Bukan karena lo bakal pake terus, tapi supaya lo PAHAM cara kerjanya.
> Orang yang cuma bisa pakai sklearn tapi ga tau dalemnya = pengguna, bukan engineer.

---

### 6.1 LINEAR REGRESSION

**Intuisi:** Cari garis lurus yang paling "pas" dengan data.

```
Data: pasangan (x, y)
Tujuan: cari w dan b sehingga ŷ = w·x + b ≈ y

Langkah:
1. Mulai dengan w dan b acak
2. Hitung prediksi ŷ untuk semua x
3. Hitung error (loss) = MSE = mean((ŷ - y)²)
4. Hitung gradient dL/dw dan dL/db
5. Update: w = w - lr × dL/dw
          b = b - lr × dL/db
6. Ulangi (1000x atau sampai konvergen)
```

```python
import numpy as np
import matplotlib
matplotlib.use("Agg")
import matplotlib.pyplot as plt

class LinearRegression:
    def __init__(self, learning_rate=0.01, n_iterasi=1000):
        self.lr = learning_rate
        self.n_iter = n_iterasi
        self.w = None  # bobot
        self.b = None  # bias
        self.losses = []

    def fit(self, X, y):
        n_samples = len(X)

        # Inisialisasi parameter dengan 0
        self.w = 0.0
        self.b = 0.0

        for epoch in range(self.n_iter):
            # FORWARD PASS — hitung prediksi
            y_pred = self.w * X + self.b

            # HITUNG LOSS (Mean Squared Error)
            loss = np.mean((y_pred - y) ** 2)
            self.losses.append(loss)

            # BACKWARD PASS — hitung gradient
            # dL/dw = (2/n) * sum((ŷ - y) * x)
            # dL/db = (2/n) * sum(ŷ - y)
            dw = (2 / n_samples) * np.sum((y_pred - y) * X)
            db = (2 / n_samples) * np.sum(y_pred - y)

            # UPDATE parameter
            self.w -= self.lr * dw
            self.b -= self.lr * db

            if epoch % 100 == 0:
                print(f"Epoch {epoch:4d} | Loss: {loss:.6f} | "
                      f"w={self.w:.4f}, b={self.b:.4f}")

    def predict(self, X):
        return self.w * X + self.b

    def score(self, X, y):
        """R² Score — seberapa baik model menjelaskan variance data"""
        y_pred = self.predict(X)
        ss_res = np.sum((y - y_pred) ** 2)
        ss_tot = np.sum((y - y.mean()) ** 2)
        return 1 - (ss_res / ss_tot)

# ============================================================
# DEMO
# ============================================================
rng = np.random.default_rng(42)

# Generate data: y = 2x + 1 + noise
X = rng.uniform(0, 10, 100)
y = 2 * X + 1 + rng.normal(0, 1, 100)

# Split train/test
split = int(0.8 * len(X))
X_train, X_test = X[:split], X[split:]
y_train, y_test = y[:split], y[split:]

# Train model
model = LinearRegression(learning_rate=0.01, n_iterasi=500)
model.fit(X_train, y_train)

print(f"\nParameter: w={model.w:.4f}, b={model.b:.4f}")
print(f"R² Score (train): {model.score(X_train, y_train):.4f}")
print(f"R² Score (test):  {model.score(X_test, y_test):.4f}")

# Plot
fig, axes = plt.subplots(1, 2, figsize=(14, 5))

axes[0].scatter(X_test, y_test, alpha=0.6, label="Data Aktual")
x_line = np.linspace(X.min(), X.max(), 100)
axes[0].plot(x_line, model.predict(x_line), "r-",
             linewidth=2, label=f"ŷ = {model.w:.2f}x + {model.b:.2f}")
axes[0].set_title("Linear Regression")
axes[0].legend()
axes[0].grid(True, alpha=0.3)

axes[1].plot(model.losses, "b-", linewidth=1.5)
axes[1].set_title("Loss per Epoch")
axes[1].set_xlabel("Epoch")
axes[1].set_ylabel("MSE Loss")
axes[1].grid(True, alpha=0.3)

plt.tight_layout()
plt.savefig("linear_regression.png", dpi=150)
plt.close()
print("Plot disimpan: linear_regression.png")
```

### 6.2 LOGISTIC REGRESSION

**Intuisi:** Klasifikasi biner (0 atau 1). Hampir sama dengan Linear Regression tapi outputnya dimasukin ke fungsi sigmoid supaya hasilnya 0-1 (probabilitas).

```
ŷ = sigmoid(w·x + b)
sigmoid(z) = 1 / (1 + e^(-z))

Loss: Binary Cross Entropy
L = -mean(y·log(ŷ) + (1-y)·log(1-ŷ))

Gradient:
dL/dw = (1/n) * X.T @ (ŷ - y)
dL/db = mean(ŷ - y)
```

```python
import numpy as np

class LogisticRegression:
    def __init__(self, learning_rate=0.01, n_iterasi=1000):
        self.lr = learning_rate
        self.n_iter = n_iterasi
        self.w = None
        self.b = None
        self.losses = []

    def sigmoid(self, z):
        # Clipping untuk cegah overflow
        z = np.clip(z, -500, 500)
        return 1 / (1 + np.exp(-z))

    def binary_cross_entropy(self, y, y_pred):
        eps = 1e-15  # cegah log(0)
        y_pred = np.clip(y_pred, eps, 1 - eps)
        return -np.mean(y * np.log(y_pred) + (1 - y) * np.log(1 - y_pred))

    def fit(self, X, y):
        n_samples, n_features = X.shape
        self.w = np.zeros(n_features)
        self.b = 0.0

        for epoch in range(self.n_iter):
            # Forward
            z = X @ self.w + self.b
            y_pred = self.sigmoid(z)

            # Loss
            loss = self.binary_cross_entropy(y, y_pred)
            self.losses.append(loss)

            # Backward (gradient)
            error = y_pred - y
            dw = (1 / n_samples) * X.T @ error
            db = np.mean(error)

            # Update
            self.w -= self.lr * dw
            self.b -= self.lr * db

            if epoch % 100 == 0:
                acc = self.accuracy(X, y)
                print(f"Epoch {epoch:4d} | Loss: {loss:.4f} | Acc: {acc:.4f}")

    def predict_proba(self, X):
        return self.sigmoid(X @ self.w + self.b)

    def predict(self, X, threshold=0.5):
        return (self.predict_proba(X) >= threshold).astype(int)

    def accuracy(self, X, y):
        return np.mean(self.predict(X) == y)

# ============================================================
# DEMO — Klasifikasi lulus/gagal berdasar jam belajar & nilai
# ============================================================
rng = np.random.default_rng(42)
n = 200

jam_belajar = rng.uniform(1, 10, n)
nilai_uts = rng.uniform(40, 100, n)

# Label: lulus jika jam belajar > 5 ATAU nilai_uts > 70
lulus = ((jam_belajar > 5) | (nilai_uts > 70)).astype(int)
lulus += rng.integers(-1, 2, n)  # tambah noise
lulus = np.clip(lulus, 0, 1)

X = np.column_stack([jam_belajar, nilai_uts])

# Normalisasi (PENTING untuk gradient descent)
X_norm = (X - X.mean(axis=0)) / X.std(axis=0)

# Split
split = int(0.8 * n)
X_train, X_test = X_norm[:split], X_norm[split:]
y_train, y_test = lulus[:split], lulus[split:]

model = LogisticRegression(learning_rate=0.1, n_iterasi=500)
model.fit(X_train, y_train)

print(f"\nAkurasi Train: {model.accuracy(X_train, y_train):.4f}")
print(f"Akurasi Test:  {model.accuracy(X_test, y_test):.4f}")
```

### 6.3 K-NEAREST NEIGHBORS (KNN)

**Intuisi:** "Katakan siapa temanmu, kukatakan siapa kamu."
Prediksi berdasar K tetangga terdekat.

```
Langkah prediksi:
1. Hitung jarak dari data baru ke semua data training
2. Ambil K data training yang paling dekat
3. Untuk klasifikasi: ambil kelas yang paling banyak (voting)
4. Untuk regresi: ambil rata-rata nilai
```

```python
import numpy as np
from collections import Counter

class KNN:
    def __init__(self, k=5):
        self.k = k

    def fit(self, X, y):
        # KNN tidak perlu training — cukup simpan data
        self.X_train = X
        self.y_train = y

    def jarak_euclidean(self, a, b):
        return np.sqrt(np.sum((a - b) ** 2))

    def predict_satu(self, x):
        # Hitung jarak ke semua training point
        jarak = [self.jarak_euclidean(x, xt) for xt in self.X_train]

        # Ambil index K terdekat
        k_indices = np.argsort(jarak)[:self.k]

        # Ambil label K tetangga
        k_labels = self.y_train[k_indices]

        # Voting mayoritas
        paling_umum = Counter(k_labels).most_common(1)[0][0]
        return paling_umum

    def predict(self, X):
        return np.array([self.predict_satu(x) for x in X])

    def score(self, X, y):
        return np.mean(self.predict(X) == y)

# ============================================================
# DEMO
# ============================================================
from sklearn.datasets import make_classification

X, y = make_classification(n_samples=200, n_features=2,
                            n_redundant=0, n_clusters_per_class=1,
                            random_state=42)

split = int(0.8 * len(X))
X_train, X_test = X[:split], X[split:]
y_train, y_test = y[:split], y[split:]

# Test berbagai nilai K
for k in [1, 3, 5, 7, 11]:
    model = KNN(k=k)
    model.fit(X_train, y_train)
    acc = model.score(X_test, y_test)
    print(f"K={k}: Akurasi={acc:.4f}")
```

### 6.4 DECISION TREE

**Intuisi:** Pohon keputusan. Di setiap node, kita tanya pertanyaan yang paling memisahkan data.

```
Dataset nilai ujian:
        [Jam Belajar > 5?]
       /                  \
      Ya                  Tidak
  [Nilai UTS > 70?]     [GAGAL]
  /              \
Lulus           Gagal
```

```python
import numpy as np
from collections import Counter

class Node:
    def __init__(self, fitur=None, threshold=None, kiri=None,
                 kanan=None, nilai=None):
        self.fitur = fitur        # fitur yang dipakai split
        self.threshold = threshold # nilai threshold split
        self.kiri = kiri          # subtree kiri
        self.kanan = kanan        # subtree kanan
        self.nilai = nilai         # nilai leaf (kalau leaf node)

    def is_leaf(self):
        return self.nilai is not None

class DecisionTree:
    def __init__(self, max_depth=5, min_samples_split=2):
        self.max_depth = max_depth
        self.min_samples = min_samples_split
        self.root = None

    def gini(self, y):
        """Gini Impurity — ukuran ketidakmurnian"""
        n = len(y)
        if n == 0:
            return 0
        classes, counts = np.unique(y, return_counts=True)
        probabilitas = counts / n
        return 1 - np.sum(probabilitas ** 2)

    def information_gain(self, y, y_kiri, y_kanan):
        """Seberapa besar penurunan impurity setelah split"""
        n = len(y)
        n_l, n_r = len(y_kiri), len(y_kanan)
        gain = self.gini(y) - (n_l/n * self.gini(y_kiri) +
                               n_r/n * self.gini(y_kanan))
        return gain

    def cari_split_terbaik(self, X, y):
        best_gain = -1
        best_fitur, best_thresh = None, None
        n_features = X.shape[1]

        for fitur in range(n_features):
            thresholds = np.unique(X[:, fitur])

            for thresh in thresholds:
                mask_kiri = X[:, fitur] <= thresh
                y_kiri = y[mask_kiri]
                y_kanan = y[~mask_kiri]

                if len(y_kiri) == 0 or len(y_kanan) == 0:
                    continue

                gain = self.information_gain(y, y_kiri, y_kanan)

                if gain > best_gain:
                    best_gain = gain
                    best_fitur = fitur
                    best_thresh = thresh

        return best_fitur, best_thresh

    def bangun_tree(self, X, y, depth=0):
        n_samples = len(y)
        n_kelas = len(np.unique(y))

        # Kondisi berhenti
        if (depth >= self.max_depth or
            n_samples < self.min_samples or
            n_kelas == 1):
            # Leaf node: ambil kelas mayoritas
            kelas_mayoritas = Counter(y).most_common(1)[0][0]
            return Node(nilai=kelas_mayoritas)

        # Cari split terbaik
        fitur, thresh = self.cari_split_terbaik(X, y)

        if fitur is None:
            kelas_mayoritas = Counter(y).most_common(1)[0][0]
            return Node(nilai=kelas_mayoritas)

        # Split data
        mask_kiri = X[:, fitur] <= thresh
        kiri = self.bangun_tree(X[mask_kiri], y[mask_kiri], depth + 1)
        kanan = self.bangun_tree(X[~mask_kiri], y[~mask_kiri], depth + 1)

        return Node(fitur=fitur, threshold=thresh, kiri=kiri, kanan=kanan)

    def fit(self, X, y):
        self.root = self.bangun_tree(X, y)

    def predict_satu(self, x, node):
        if node.is_leaf():
            return node.nilai
        if x[node.fitur] <= node.threshold:
            return self.predict_satu(x, node.kiri)
        return self.predict_satu(x, node.kanan)

    def predict(self, X):
        return np.array([self.predict_satu(x, self.root) for x in X])

    def score(self, X, y):
        return np.mean(self.predict(X) == y)

# DEMO
from sklearn.datasets import make_classification

X, y = make_classification(n_samples=300, n_features=4,
                            random_state=42)
split = int(0.8 * len(X))
X_train, X_test = X[:split], X[split:]
y_train, y_test = y[:split], y[split:]

model = DecisionTree(max_depth=5)
model.fit(X_train, y_train)
print(f"Akurasi: {model.score(X_test, y_test):.4f}")
```

---

## BAGIAN 7 — SCIKIT-LEARN

> Sekarang lo boleh pakai sklearn. Tapi karena udah tau cara kerjanya dari scratch,
> lo bakal tau kenapa setiap parameter itu penting.

### 7.1 Workflow Standar ML dengan Sklearn

```python
import numpy as np
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split, cross_val_score
from sklearn.preprocessing import StandardScaler
from sklearn.pipeline import Pipeline
from sklearn.metrics import (accuracy_score, classification_report,
                              confusion_matrix)

# ============================================================
# STEP 1 — LOAD DATA
# ============================================================
iris = load_iris()
X, y = iris.data, iris.target

print(f"Shape X: {X.shape}")  # (150, 4)
print(f"Shape y: {y.shape}")  # (150,)
print(f"Kelas: {iris.target_names}")

# ============================================================
# STEP 2 — SPLIT DATA
# ============================================================
X_train, X_test, y_train, y_test = train_test_split(
    X, y,
    test_size=0.2,      # 20% untuk test
    random_state=42,    # reproducible
    stratify=y          # proporsi kelas tetap seimbang
)
print(f"Train: {X_train.shape}, Test: {X_test.shape}")

# ============================================================
# STEP 3 — PREPROCESSING + MODEL (Pipeline)
# ============================================================
from sklearn.ensemble import RandomForestClassifier
from sklearn.svm import SVC
from sklearn.neighbors import KNeighborsClassifier

# Pipeline otomatis handle scaling + model
pipeline = Pipeline([
    ("scaler", StandardScaler()),
    ("model", RandomForestClassifier(n_estimators=100, random_state=42))
])

# ============================================================
# STEP 4 — TRAIN
# ============================================================
pipeline.fit(X_train, y_train)

# ============================================================
# STEP 5 — EVALUASI
# ============================================================
y_pred = pipeline.predict(X_test)

print(f"\nAkurasi: {accuracy_score(y_test, y_pred):.4f}")
print(f"\nClassification Report:")
print(classification_report(y_test, y_pred, target_names=iris.target_names))

# Confusion matrix
cm = confusion_matrix(y_test, y_pred)
print(f"\nConfusion Matrix:")
print(cm)
```

### 7.2 Perbandingan Banyak Model

```python
from sklearn.datasets import make_classification
from sklearn.model_selection import train_test_split, cross_val_score
from sklearn.preprocessing import StandardScaler
from sklearn.pipeline import Pipeline
from sklearn.linear_model import LogisticRegression
from sklearn.tree import DecisionTreeClassifier
from sklearn.ensemble import (RandomForestClassifier,
                               GradientBoostingClassifier)
from sklearn.svm import SVC
from sklearn.neighbors import KNeighborsClassifier
import numpy as np

# Data
X, y = make_classification(n_samples=500, n_features=10,
                            random_state=42)
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42)

# Daftar model yang mau dibandingkan
models = {
    "Logistic Regression": LogisticRegression(max_iter=1000),
    "Decision Tree": DecisionTreeClassifier(max_depth=5),
    "Random Forest": RandomForestClassifier(n_estimators=100, random_state=42),
    "Gradient Boosting": GradientBoostingClassifier(n_estimators=100),
    "SVM": SVC(kernel="rbf"),
    "KNN (k=5)": KNeighborsClassifier(n_neighbors=5),
}

print(f"{'Model':<25} {'CV Mean':>10} {'CV Std':>10} {'Test Acc':>10}")
print("-" * 60)

for nama, model in models.items():
    # Pipeline dengan scaling
    pipe = Pipeline([("scaler", StandardScaler()), ("model", model)])

    # Cross-validation 5-fold
    cv_scores = cross_val_score(pipe, X_train, y_train, cv=5, scoring="accuracy")

    # Test score
    pipe.fit(X_train, y_train)
    test_acc = pipe.score(X_test, y_test)

    print(f"{nama:<25} {cv_scores.mean():>10.4f} "
          f"{cv_scores.std():>10.4f} {test_acc:>10.4f}")
```

### 7.3 Hyperparameter Tuning

```python
from sklearn.model_selection import GridSearchCV, RandomizedSearchCV
from sklearn.ensemble import RandomForestClassifier
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler

pipe = Pipeline([
    ("scaler", StandardScaler()),
    ("model", RandomForestClassifier(random_state=42))
])

# Grid Search — coba semua kombinasi
param_grid = {
    "model__n_estimators": [50, 100, 200],
    "model__max_depth": [None, 5, 10],
    "model__min_samples_split": [2, 5, 10]
}

grid_search = GridSearchCV(
    pipe,
    param_grid,
    cv=5,
    scoring="accuracy",
    n_jobs=-1,  # pakai semua CPU
    verbose=1
)

grid_search.fit(X_train, y_train)

print(f"Best params: {grid_search.best_params_}")
print(f"Best CV score: {grid_search.best_score_:.4f}")
print(f"Test score: {grid_search.best_estimator_.score(X_test, y_test):.4f}")
```

### 7.4 Regresi dengan Sklearn

```python
from sklearn.linear_model import LinearRegression, Ridge, Lasso
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import mean_squared_error, r2_score
from sklearn.datasets import make_regression
import numpy as np

X, y = make_regression(n_samples=500, n_features=10,
                        noise=20, random_state=42)
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)

models = {
    "Linear Regression": LinearRegression(),
    "Ridge (L2)": Ridge(alpha=1.0),
    "Lasso (L1)": Lasso(alpha=1.0),
    "Random Forest": RandomForestRegressor(n_estimators=100, random_state=42)
}

print(f"{'Model':<25} {'MSE':>12} {'R²':>8}")
print("-" * 48)

for nama, model in models.items():
    model.fit(X_train, y_train)
    y_pred = model.predict(X_test)
    mse = mean_squared_error(y_test, y_pred)
    r2 = r2_score(y_test, y_pred)
    print(f"{nama:<25} {mse:>12.2f} {r2:>8.4f}")
```

### 7.5 Clustering (Unsupervised)

```python
from sklearn.cluster import KMeans, DBSCAN
from sklearn.datasets import make_blobs
from sklearn.metrics import silhouette_score
import numpy as np

# Generate data 4 cluster
X, y_true = make_blobs(n_samples=300, centers=4,
                        cluster_std=0.8, random_state=42)

# KMeans
kmeans = KMeans(n_clusters=4, random_state=42, n_init=10)
labels_km = kmeans.fit_predict(X)

sil_km = silhouette_score(X, labels_km)
print(f"KMeans - Silhouette Score: {sil_km:.4f}")
print(f"KMeans - Inertia: {kmeans.inertia_:.2f}")

# Cari K optimal dengan Elbow Method
inertias = []
k_range = range(2, 11)
for k in k_range:
    km = KMeans(n_clusters=k, random_state=42, n_init=10)
    km.fit(X)
    inertias.append(km.inertia_)

print("\nElbow Method:")
print(f"{'K':>3} | {'Inertia':>12}")
for k, inertia in zip(k_range, inertias):
    bar = "#" * int(inertia / 1000)
    print(f"{k:>3} | {inertia:>12.2f} {bar}")
```

### 7.6 Feature Engineering & Selection

```python
from sklearn.feature_selection import (SelectKBest, f_classif,
                                        RFE, SelectFromModel)
from sklearn.ensemble import RandomForestClassifier
from sklearn.datasets import load_breast_cancer
import numpy as np

data = load_breast_cancer()
X, y = data.data, data.target
feature_names = data.feature_names

# METHOD 1: SelectKBest (statistik)
selector = SelectKBest(f_classif, k=10)
X_selected = selector.fit_transform(X, y)
selected_features = feature_names[selector.get_support()]
print("Top 10 fitur (SelectKBest):")
print(selected_features)

# METHOD 2: Feature Importance dari Random Forest
rf = RandomForestClassifier(n_estimators=100, random_state=42)
rf.fit(X, y)

importances = rf.feature_importances_
sorted_idx = np.argsort(importances)[::-1]

print("\nTop 10 Fitur (Random Forest Importance):")
for i in range(10):
    idx = sorted_idx[i]
    print(f"{i+1:2d}. {feature_names[idx]:<35} {importances[idx]:.4f}")
```

---

## BAGIAN 8 — NEURAL NETWORK DARI SCRATCH

> Ini paling penting dan paling susah.
> Tapi kalau lo paham ini, lo bakal ngerti kenapa deep learning bisa sekuat itu.

### 8.1 Konsep Dasar

```
NEURON TUNGGAL:
  input: x1, x2, x3
  bobot: w1, w2, w3
  bias: b

  z = w1*x1 + w2*x2 + w3*x3 + b   (linear combination)
  a = activation(z)                  (aktivasi)

LAYER:
  Kumpulan banyak neuron
  Layer 1 → Layer 2 → ... → Output

FORWARD PASS:
  X → Layer1 → Layer2 → Output → Loss

BACKWARD PASS (Backpropagation):
  Hitung gradient dari loss ke setiap bobot
  Update semua bobot
```

### 8.2 Implementasi Neural Network 2-Layer

```python
import numpy as np

class NeuralNetwork:
    """
    Neural network 2 layer:
    Input → Hidden (ReLU) → Output (Sigmoid untuk binary)
    """

    def __init__(self, input_size, hidden_size, output_size,
                 learning_rate=0.01):
        self.lr = learning_rate

        # Inisialisasi bobot dengan He Initialization
        # (lebih baik dari random untuk layer dalam)
        self.W1 = np.random.randn(input_size, hidden_size) * np.sqrt(2/input_size)
        self.b1 = np.zeros((1, hidden_size))
        self.W2 = np.random.randn(hidden_size, output_size) * np.sqrt(2/hidden_size)
        self.b2 = np.zeros((1, output_size))

        self.losses = []

    # ========================
    # FUNGSI AKTIVASI
    # ========================

    def relu(self, z):
        return np.maximum(0, z)

    def relu_deriv(self, z):
        return (z > 0).astype(float)

    def sigmoid(self, z):
        z = np.clip(z, -500, 500)
        return 1 / (1 + np.exp(-z))

    # ========================
    # FORWARD PASS
    # ========================

    def forward(self, X):
        # Layer 1: Input → Hidden
        self.Z1 = X @ self.W1 + self.b1    # (n, hidden)
        self.A1 = self.relu(self.Z1)         # (n, hidden) — aktivasi ReLU

        # Layer 2: Hidden → Output
        self.Z2 = self.A1 @ self.W2 + self.b2  # (n, output)
        self.A2 = self.sigmoid(self.Z2)          # (n, output) — probabilitas

        return self.A2

    # ========================
    # LOSS
    # ========================

    def binary_cross_entropy(self, y, y_pred):
        eps = 1e-15
        y_pred = np.clip(y_pred, eps, 1 - eps)
        return -np.mean(y * np.log(y_pred) + (1 - y) * np.log(1 - y_pred))

    # ========================
    # BACKWARD PASS
    # ========================

    def backward(self, X, y):
        n = X.shape[0]

        # LAYER 2 GRADIENT
        # dL/dZ2 = A2 - y (turunan BCE + sigmoid bisa disederhanakan jadi ini)
        dZ2 = self.A2 - y.reshape(-1, 1)   # (n, output)
        dW2 = self.A1.T @ dZ2 / n           # (hidden, output)
        db2 = np.sum(dZ2, axis=0, keepdims=True) / n  # (1, output)

        # LAYER 1 GRADIENT
        # dL/dA1 = dZ2 @ W2.T
        dA1 = dZ2 @ self.W2.T              # (n, hidden)
        dZ1 = dA1 * self.relu_deriv(self.Z1)  # (n, hidden)
        dW1 = X.T @ dZ1 / n                # (input, hidden)
        db1 = np.sum(dZ1, axis=0, keepdims=True) / n  # (1, hidden)

        # UPDATE BOBOT
        self.W2 -= self.lr * dW2
        self.b2 -= self.lr * db2
        self.W1 -= self.lr * dW1
        self.b1 -= self.lr * db1

    # ========================
    # TRAINING
    # ========================

    def fit(self, X, y, epochs=500, batch_size=32, verbose=True):
        n = X.shape[0]

        for epoch in range(epochs):
            # Mini-batch gradient descent
            indices = np.random.permutation(n)
            X_shuffled = X[indices]
            y_shuffled = y[indices]

            for i in range(0, n, batch_size):
                X_batch = X_shuffled[i:i+batch_size]
                y_batch = y_shuffled[i:i+batch_size]

                self.forward(X_batch)
                self.backward(X_batch, y_batch)

            # Hitung loss seluruh data
            y_pred = self.forward(X)
            loss = self.binary_cross_entropy(y, y_pred.flatten())
            self.losses.append(loss)

            if verbose and epoch % 50 == 0:
                acc = self.accuracy(X, y)
                print(f"Epoch {epoch:4d} | Loss: {loss:.4f} | Acc: {acc:.4f}")

    def predict_proba(self, X):
        return self.forward(X).flatten()

    def predict(self, X, threshold=0.5):
        return (self.predict_proba(X) >= threshold).astype(int)

    def accuracy(self, X, y):
        return np.mean(self.predict(X) == y)

# ============================================================
# DEMO
# ============================================================
from sklearn.datasets import make_classification
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler

X, y = make_classification(n_samples=1000, n_features=10,
                            n_informative=8, random_state=42)

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)

# Normalisasi
scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)

# Buat & train network
nn = NeuralNetwork(input_size=10, hidden_size=64, output_size=1,
                   learning_rate=0.01)
nn.fit(X_train, y_train, epochs=300, batch_size=32)

print(f"\nAkurasi Test: {nn.accuracy(X_test, y_test):.4f}")
```

### 8.3 Neural Network Multi-Layer (Deep)

```python
import numpy as np

class DeepNN:
    """
    Neural network dengan arbitrary jumlah layer.
    Architecture: [input_size, h1, h2, ..., output_size]
    """

    def __init__(self, layer_sizes, learning_rate=0.01):
        self.lr = learning_rate
        self.n_layers = len(layer_sizes) - 1
        self.losses = []

        # Inisialisasi weights semua layer
        self.params = {}
        for i in range(self.n_layers):
            fan_in = layer_sizes[i]
            fan_out = layer_sizes[i+1]
            self.params[f"W{i+1}"] = np.random.randn(fan_in, fan_out) * np.sqrt(2/fan_in)
            self.params[f"b{i+1}"] = np.zeros((1, fan_out))

    def relu(self, z): return np.maximum(0, z)
    def relu_d(self, z): return (z > 0).astype(float)
    def sigmoid(self, z): return 1/(1+np.exp(-np.clip(z,-500,500)))
    def softmax(self, z):
        e = np.exp(z - z.max(axis=1, keepdims=True))
        return e / e.sum(axis=1, keepdims=True)

    def forward(self, X):
        self.cache = {"A0": X}

        for i in range(1, self.n_layers + 1):
            A_prev = self.cache[f"A{i-1}"]
            W = self.params[f"W{i}"]
            b = self.params[f"b{i}"]

            Z = A_prev @ W + b

            # Aktivasi: ReLU untuk hidden, Sigmoid/Softmax untuk output
            if i < self.n_layers:
                A = self.relu(Z)
            else:
                A = self.sigmoid(Z)  # atau softmax untuk multi-kelas

            self.cache[f"Z{i}"] = Z
            self.cache[f"A{i}"] = A

        return self.cache[f"A{self.n_layers}"]

    def backward(self, X, y):
        n = X.shape[0]
        grads = {}

        # Output layer gradient
        dA = self.cache[f"A{self.n_layers}"] - y.reshape(-1, 1)

        for i in range(self.n_layers, 0, -1):
            A_prev = self.cache[f"A{i-1}"]
            Z = self.cache[f"Z{i}"]

            if i < self.n_layers:
                dZ = dA * self.relu_d(Z)
            else:
                dZ = dA  # sigmoid output sudah digabung

            dW = A_prev.T @ dZ / n
            db = dZ.sum(axis=0, keepdims=True) / n
            dA = dZ @ self.params[f"W{i}"].T

            grads[f"W{i}"] = dW
            grads[f"b{i}"] = db

        # Update
        for key in self.params:
            self.params[key] -= self.lr * grads[key]

    def fit(self, X, y, epochs=500, batch_size=32, verbose=True):
        for epoch in range(epochs):
            idx = np.random.permutation(len(X))
            for i in range(0, len(X), batch_size):
                Xb = X[idx[i:i+batch_size]]
                yb = y[idx[i:i+batch_size]]
                self.forward(Xb)
                self.backward(Xb, yb)

            out = self.forward(X)
            eps = 1e-15
            out = np.clip(out.flatten(), eps, 1-eps)
            loss = -np.mean(y*np.log(out) + (1-y)*np.log(1-out))
            self.losses.append(loss)

            if verbose and epoch % 100 == 0:
                acc = np.mean((out >= 0.5) == y)
                print(f"Epoch {epoch:4d} | Loss: {loss:.4f} | Acc: {acc:.4f}")

    def predict(self, X):
        out = self.forward(X).flatten()
        return (out >= 0.5).astype(int)

    def score(self, X, y):
        return np.mean(self.predict(X) == y)

# DEMO dengan architecture dalam
model = DeepNN([10, 128, 64, 32, 1], learning_rate=0.005)
model.fit(X_train, y_train, epochs=300)
print(f"Test Acc: {model.score(X_test, y_test):.4f}")
```

---

## BAGIAN 9 — KERAS DI ANDROID

> Keras adalah wrapper high-level untuk neural network.
> Setelah paham cara bikin dari scratch, ini cepet banget.

### 9.1 Install & Test Keras

```bash
pip install tensorflow  # atau:
pip install keras       # standalone keras
```

```python
# Cek versi
import tensorflow as tf
print(f"TensorFlow: {tf.__version__}")

# Konfigurasi untuk Android (kurangi memory usage)
import os
os.environ["TF_CPP_MIN_LOG_LEVEL"] = "3"  # matiin log verbose
```

### 9.2 Model Sequential Dasar

```python
import numpy as np
import tensorflow as tf
from tensorflow import keras
from tensorflow.keras import layers
from sklearn.datasets import make_classification
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler

# Data
X, y = make_classification(n_samples=1000, n_features=20,
                            n_informative=15, random_state=42)
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)

scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)

# ============================================================
# BUAT MODEL
# ============================================================
model = keras.Sequential([
    layers.Input(shape=(20,)),          # input layer
    layers.Dense(128, activation="relu"),
    layers.Dropout(0.3),                 # regularisasi
    layers.Dense(64, activation="relu"),
    layers.Dropout(0.2),
    layers.Dense(32, activation="relu"),
    layers.Dense(1, activation="sigmoid")  # output binary
])

model.summary()  # tampilkan arsitektur

# ============================================================
# COMPILE
# ============================================================
model.compile(
    optimizer=keras.optimizers.Adam(learning_rate=0.001),
    loss="binary_crossentropy",
    metrics=["accuracy"]
)

# ============================================================
# TRAIN
# ============================================================
history = model.fit(
    X_train, y_train,
    epochs=50,
    batch_size=32,
    validation_split=0.2,  # 20% dari train untuk validasi
    verbose=1,
    callbacks=[
        # Hentikan training jika ga ada perbaikan 10 epoch
        keras.callbacks.EarlyStopping(
            patience=10,
            restore_best_weights=True
        ),
        # Kurangi learning rate jika stuck
        keras.callbacks.ReduceLROnPlateau(
            factor=0.5,
            patience=5,
            min_lr=1e-6
        )
    ]
)

# ============================================================
# EVALUASI
# ============================================================
loss, acc = model.evaluate(X_test, y_test, verbose=0)
print(f"\nTest Loss: {loss:.4f}")
print(f"Test Acc:  {acc:.4f}")

# ============================================================
# SIMPAN & LOAD MODEL
# ============================================================
model.save("model_klasifikasi.keras")
# Load: model = keras.models.load_model("model_klasifikasi.keras")
```

### 9.3 Multi-Class Classification

```python
from sklearn.datasets import load_iris
from tensorflow import keras
from tensorflow.keras import layers
import numpy as np

iris = load_iris()
X, y = iris.data, iris.target

# Untuk multi-class: one-hot encode label
y_onehot = keras.utils.to_categorical(y, num_classes=3)

X_train, X_test, y_train, y_test = train_test_split(
    X, y_onehot, test_size=0.2, random_state=42)

# Normalisasi
from sklearn.preprocessing import StandardScaler
sc = StandardScaler()
X_train = sc.fit_transform(X_train)
X_test = sc.transform(X_test)

model = keras.Sequential([
    layers.Input(shape=(4,)),
    layers.Dense(64, activation="relu"),
    layers.Dense(32, activation="relu"),
    layers.Dense(3, activation="softmax")  # 3 kelas
])

model.compile(
    optimizer="adam",
    loss="categorical_crossentropy",  # bukan binary
    metrics=["accuracy"]
)

model.fit(X_train, y_train, epochs=100, batch_size=16,
          validation_split=0.2, verbose=0)

loss, acc = model.evaluate(X_test, y_test, verbose=0)
print(f"Akurasi: {acc:.4f}")
```

---

## BAGIAN 10 — PROYEK NYATA

### PROYEK 1: Sistem Deteksi Spam SMS

```python
"""
PROYEK 1: Spam Detector
Dataset: UCI SMS Spam Collection (bisa download offline)
Target: klasifikasi pesan spam/bukan spam
"""

import numpy as np
import re
from collections import Counter

# ============================================================
# TANPA DOWNLOAD — Buat dataset mini sendiri dulu
# ============================================================
data = [
    ("Selamat! Anda menang hadiah 10 juta klik link ini sekarang", 1),
    ("Hai kamu, jadi ketemu besok jam 3 ga?", 0),
    ("GRATIS! Daftar sekarang dan dapatkan bonus senilai 500rb", 1),
    ("Laporan keuangan bulan ini sudah dikirim ke email kamu", 0),
    ("Kamu terpilih sebagai pemenang, hubungi kami SEKARANG", 1),
    ("Meeting besok dipindah ke jam 2 siang ya", 0),
    ("PROMO TERBATAS! Beli sekarang diskon 90%", 1),
    ("Selamat ulang tahun! Semoga sehat selalu", 0),
    ("Klik link ini untuk klaim hadiahmu senilai jutaan rupiah", 1),
    ("Tugas matematika dikumpul besok pagi", 0),
    ("ALERT: Akun Anda akan diblokir, verifikasi sekarang", 1),
    ("Nanti malam jadi nonton bareng ga?", 0),
    ("Investasi dijamin untung 300% dalam 7 hari", 1),
    ("Tolong beli mie instan di warung ya", 0),
    ("Selamat kamu mendapatkan smartphone gratis dari kami", 1),
    ("Besok ada ujian fisika chapter 3 dan 4", 0),
]

# ============================================================
# FEATURE EXTRACTION (Bag of Words sederhana)
# ============================================================
def preprocess(text):
    """Lowercase, hapus tanda baca, split kata"""
    text = text.lower()
    text = re.sub(r"[^\w\s]", "", text)
    return text.split()

def build_vocab(data):
    """Bangun kamus kata dari semua teks"""
    vocab = Counter()
    for text, _ in data:
        words = preprocess(text)
        vocab.update(words)
    # Ambil 100 kata paling umum
    return {word: i for i, (word, _) in enumerate(vocab.most_common(100))}

def text_to_vector(text, vocab):
    """Konversi teks ke vektor biner (ada/tidak ada kata)"""
    words = set(preprocess(text))
    return np.array([1 if w in words else 0 for w in vocab])

# Bangun vocab
vocab = build_vocab(data)
print(f"Ukuran vocab: {len(vocab)}")

# Buat fitur dan label
X = np.array([text_to_vector(text, vocab) for text, _ in data])
y = np.array([label for _, label in data])

print(f"Shape X: {X.shape}")
print(f"Label: {y}")

# ============================================================
# NAIVE BAYES CLASSIFIER (Cocok untuk text)
# ============================================================
class NaiveBayesClassifier:
    def fit(self, X, y):
        n_samples, n_features = X.shape
        self.classes = np.unique(y)
        n_classes = len(self.classes)

        # Hitung prior P(kelas)
        self.priors = {}
        for c in self.classes:
            self.priors[c] = np.sum(y == c) / n_samples

        # Hitung likelihood P(fitur | kelas) dengan Laplace smoothing
        self.likelihoods = {}
        for c in self.classes:
            X_c = X[y == c]
            # +1 untuk Laplace smoothing (cegah 0 probability)
            self.likelihoods[c] = (X_c.sum(axis=0) + 1) / (len(X_c) + 2)

    def predict(self, X):
        predictions = []
        for x in X:
            posteriors = {}
            for c in self.classes:
                log_prior = np.log(self.priors[c])
                # Log probabilitas (untuk cegah underflow)
                log_likelihood = np.sum(
                    x * np.log(self.likelihoods[c]) +
                    (1 - x) * np.log(1 - self.likelihoods[c])
                )
                posteriors[c] = log_prior + log_likelihood

            predictions.append(max(posteriors, key=posteriors.get))
        return np.array(predictions)

# Train & test
from sklearn.model_selection import cross_val_score

nb = NaiveBayesClassifier()

# Leave-one-out cross validation untuk dataset kecil
correct = 0
for i in range(len(X)):
    X_train = np.delete(X, i, axis=0)
    y_train = np.delete(y, i)
    X_test = X[i:i+1]
    y_test = y[i]

    nb.fit(X_train, y_train)
    pred = nb.predict(X_test)[0]
    correct += (pred == y_test)

print(f"\nLeave-One-Out Accuracy: {correct/len(X):.4f}")

# Test prediksi baru
nb.fit(X, y)
pesan_baru = [
    "Kamu memenangkan hadiah mobil klik link ini",
    "Jangan lupa bawa buku besok ya",
]
for pesan in pesan_baru:
    v = text_to_vector(pesan, vocab).reshape(1, -1)
    pred = nb.predict(v)[0]
    label = "SPAM" if pred == 1 else "BUKAN SPAM"
    print(f"[{label}] {pesan}")
```

### PROYEK 2: Prediksi Harga Rumah

```python
"""
PROYEK 2: Prediksi Harga Rumah
Latihan: Feature engineering + model regresi
"""

import numpy as np
import pandas as pd
from sklearn.ensemble import GradientBoostingRegressor
from sklearn.model_selection import cross_val_score
from sklearn.preprocessing import StandardScaler
from sklearn.pipeline import Pipeline
from sklearn.metrics import mean_absolute_error, r2_score

# Generate dataset sintetik
rng = np.random.default_rng(42)
n = 500

df = pd.DataFrame({
    "luas_m2": rng.integers(30, 300, n),
    "kamar_tidur": rng.integers(1, 6, n),
    "kamar_mandi": rng.integers(1, 4, n),
    "umur_rumah": rng.integers(0, 30, n),
    "jarak_pusat_km": rng.uniform(1, 50, n),
    "ada_garasi": rng.integers(0, 2, n),
    "lantai": rng.integers(1, 4, n),
    "kondisi": rng.choice(["bagus", "sedang", "butuh renovasi"], n)
})

# Harga berdasar formula realistis + noise
harga = (
    df["luas_m2"] * 8_000_000 +
    df["kamar_tidur"] * 15_000_000 +
    df["kamar_mandi"] * 10_000_000 -
    df["umur_rumah"] * 2_000_000 -
    df["jarak_pusat_km"] * 3_000_000 +
    df["ada_garasi"] * 25_000_000 +
    rng.normal(0, 20_000_000, n)
)
df["harga"] = np.maximum(harga, 100_000_000)  # minimal 100jt

print(df.head())
print(f"\nStatistik harga (juta):")
print((df["harga"] / 1e6).describe().round(2))

# ============================================================
# FEATURE ENGINEERING
# ============================================================
# Encode categorical
kondisi_map = {"bagus": 2, "sedang": 1, "butuh renovasi": 0}
df["kondisi_encoded"] = df["kondisi"].map(kondisi_map)

# Buat fitur turunan
df["luas_per_kamar"] = df["luas_m2"] / df["kamar_tidur"]
df["rasio_kamar_mandi"] = df["kamar_mandi"] / df["kamar_tidur"]
df["skor_lokasi"] = 1 / (1 + df["jarak_pusat_km"])

# Pilih fitur
fitur = ["luas_m2", "kamar_tidur", "kamar_mandi", "umur_rumah",
         "jarak_pusat_km", "ada_garasi", "lantai", "kondisi_encoded",
         "luas_per_kamar", "rasio_kamar_mandi", "skor_lokasi"]

X = df[fitur].values
y = df["harga"].values

# ============================================================
# TRAIN & EVALUASI
# ============================================================
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)

pipeline = Pipeline([
    ("scaler", StandardScaler()),
    ("model", GradientBoostingRegressor(
        n_estimators=200,
        max_depth=4,
        learning_rate=0.05,
        random_state=42
    ))
])

pipeline.fit(X_train, y_train)
y_pred = pipeline.predict(X_test)

mae = mean_absolute_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)

print(f"\nMAE: Rp {mae/1e6:.1f} juta")
print(f"R²: {r2:.4f}")

# Prediksi rumah baru
rumah_baru = pd.DataFrame([{
    "luas_m2": 120,
    "kamar_tidur": 3,
    "kamar_mandi": 2,
    "umur_rumah": 5,
    "jarak_pusat_km": 10,
    "ada_garasi": 1,
    "lantai": 2,
    "kondisi_encoded": 2,  # bagus
    "luas_per_kamar": 120/3,
    "rasio_kamar_mandi": 2/3,
    "skor_lokasi": 1/(1+10)
}])

prediksi = pipeline.predict(rumah_baru[fitur].values)
print(f"\nPrediksi harga rumah: Rp {prediksi[0]/1e6:.1f} juta")
```

---

## BAGIAN 11 — ANALISIS & DEBUG MODEL ML

### 11.1 Overfitting vs Underfitting

```
UNDERFITTING:
- Model terlalu sederhana
- Akurasi train DAN test sama-sama rendah
- Solusi: model lebih kompleks, tambah fitur

OVERFITTING:
- Model terlalu hafal data training
- Akurasi train tinggi, test rendah (gap besar)
- Solusi: regularisasi, dropout, lebih banyak data

GOOD FIT:
- Akurasi train dan test sama-sama tinggi
- Gap kecil
```

```python
import numpy as np
import matplotlib
matplotlib.use("Agg")
import matplotlib.pyplot as plt
from sklearn.preprocessing import PolynomialFeatures
from sklearn.linear_model import LinearRegression, Ridge
from sklearn.pipeline import Pipeline
from sklearn.model_selection import validation_curve

# Generate data
rng = np.random.default_rng(42)
X = rng.uniform(-3, 3, 100).reshape(-1, 1)
y = np.sin(X.flatten()) + rng.normal(0, 0.3, 100)

# Cek underfitting vs overfitting vs good fit
derajat_polynomial = [1, 3, 10]

fig, axes = plt.subplots(1, 3, figsize=(15, 5))

for ax, d in zip(axes, derajat_polynomial):
    pipe = Pipeline([
        ("poly", PolynomialFeatures(degree=d)),
        ("model", LinearRegression())
    ])
    pipe.fit(X, y)

    x_plot = np.linspace(-3, 3, 300).reshape(-1, 1)
    y_plot = pipe.predict(x_plot)

    train_score = pipe.score(X, y)

    ax.scatter(X, y, alpha=0.5, s=20)
    ax.plot(x_plot, y_plot, "r-", linewidth=2)
    ax.set_title(f"Derajat {d}\nTrain R²: {train_score:.4f}")
    ax.set_ylim(-2, 2)
    ax.grid(True, alpha=0.3)

plt.tight_layout()
plt.savefig("fitting_comparison.png", dpi=150)
plt.close()
print("Disimpan: fitting_comparison.png")
```

### 11.2 Learning Curve (Deteksi Overfitting)

```python
from sklearn.model_selection import learning_curve
import matplotlib
matplotlib.use("Agg")
import matplotlib.pyplot as plt
import numpy as np

def plot_learning_curve(model, X, y, filename="learning_curve.png"):
    train_sizes, train_scores, val_scores = learning_curve(
        model, X, y,
        train_sizes=np.linspace(0.1, 1.0, 10),
        cv=5,
        scoring="accuracy",
        n_jobs=-1
    )

    train_mean = train_scores.mean(axis=1)
    train_std = train_scores.std(axis=1)
    val_mean = val_scores.mean(axis=1)
    val_std = val_scores.std(axis=1)

    plt.figure(figsize=(10, 6))
    plt.plot(train_sizes, train_mean, "b-o", label="Training Score")
    plt.fill_between(train_sizes, train_mean-train_std,
                     train_mean+train_std, alpha=0.2, color="blue")
    plt.plot(train_sizes, val_mean, "r-o", label="Validation Score")
    plt.fill_between(train_sizes, val_mean-val_std,
                     val_mean+val_std, alpha=0.2, color="red")

    plt.title("Learning Curve")
    plt.xlabel("Jumlah Training Samples")
    plt.ylabel("Accuracy")
    plt.legend()
    plt.grid(True, alpha=0.3)
    plt.savefig(filename, dpi=150)
    plt.close()

    # Analisis otomatis
    gap = train_mean[-1] - val_mean[-1]
    print(f"Train Score Akhir: {train_mean[-1]:.4f}")
    print(f"Val Score Akhir:   {val_mean[-1]:.4f}")
    print(f"Gap: {gap:.4f}")

    if gap > 0.1:
        print("DIAGNOSIS: OVERFITTING — Coba regularisasi atau lebih banyak data")
    elif val_mean[-1] < 0.7:
        print("DIAGNOSIS: UNDERFITTING — Model terlalu sederhana")
    else:
        print("DIAGNOSIS: FIT BAGUS")
```

### 11.3 Metrik Evaluasi Lengkap

```python
from sklearn.metrics import (
    accuracy_score, precision_score, recall_score,
    f1_score, roc_auc_score, confusion_matrix,
    mean_squared_error, mean_absolute_error, r2_score
)
import numpy as np

def evaluasi_klasifikasi(y_true, y_pred, y_prob=None):
    """Evaluasi lengkap untuk klasifikasi biner"""
    print("=" * 50)
    print("EVALUASI KLASIFIKASI")
    print("=" * 50)

    # Confusion Matrix
    cm = confusion_matrix(y_true, y_pred)
    TN, FP, FN, TP = cm.ravel()

    print(f"\nConfusion Matrix:")
    print(f"         Pred Neg  Pred Pos")
    print(f"Actual Neg  {TN:6d}    {FP:6d}  (Total Neg: {TN+FP})")
    print(f"Actual Pos  {FN:6d}    {TP:6d}  (Total Pos: {FN+TP})")

    print(f"\nMetrik:")
    print(f"  Accuracy  = (TP+TN)/(Total)  = {accuracy_score(y_true, y_pred):.4f}")
    print(f"  Precision = TP/(TP+FP)       = {precision_score(y_true, y_pred):.4f}")
    print(f"  Recall    = TP/(TP+FN)       = {recall_score(y_true, y_pred):.4f}")
    print(f"  F1 Score  = harmonic(P,R)    = {f1_score(y_true, y_pred):.4f}")

    if y_prob is not None:
        print(f"  AUC-ROC                    = {roc_auc_score(y_true, y_prob):.4f}")

    print("\nPenjelasan Metrik:")
    print("  Precision: Dari semua yang diprediksi positif, berapa yang beneran positif?")
    print("  Recall:    Dari semua yang beneran positif, berapa yang ketangkep?")
    print("  F1:        Balance antara Precision dan Recall")
    print("  AUC-ROC:   Seberapa baik model membedakan kelas (0.5=random, 1.0=sempurna)")


def evaluasi_regresi(y_true, y_pred):
    """Evaluasi lengkap untuk regresi"""
    mae = mean_absolute_error(y_true, y_pred)
    mse = mean_squared_error(y_true, y_pred)
    rmse = np.sqrt(mse)
    r2 = r2_score(y_true, y_pred)
    mape = np.mean(np.abs((y_true - y_pred) / y_true)) * 100

    print("=" * 50)
    print("EVALUASI REGRESI")
    print("=" * 50)
    print(f"  MAE  (Mean Abs Error):    {mae:.4f}")
    print(f"  MSE  (Mean Sq Error):     {mse:.4f}")
    print(f"  RMSE (Root MSE):          {rmse:.4f}")
    print(f"  R²   (Explained Var):     {r2:.4f}")
    print(f"  MAPE (Mean Abs % Error):  {mape:.2f}%")
```

---

## BONUS — CHEATSHEET & REFERENSI OFFLINE

### Dataset Offline (Generate Sendiri)

```python
from sklearn.datasets import (
    make_classification,   # klasifikasi
    make_regression,       # regresi
    make_blobs,            # clustering
    make_moons,            # non-linear boundary
    make_circles,          # non-linear (lingkaran)
    load_iris,             # iris flower dataset
    load_wine,             # wine dataset
    load_breast_cancer,    # cancer detection
    load_digits,           # handwritten digits
    load_diabetes          # diabetes regression
)

# Semua ini 100% offline, bawaan sklearn
X, y = make_classification(n_samples=1000, n_features=20,
                            n_classes=2, random_state=42)
```

### Algoritma & Kapan Dipakainya

```
KLASIFIKASI:
  Logistic Regression  — simple, interpretable, baseline
  Decision Tree        — interpretable, non-linear
  Random Forest        — powerful, non-linear, robust
  Gradient Boosting    — most powerful tabular, tapi lambat
  SVM                  — bagus untuk data kecil
  KNN                  — sederhana, non-parametric
  Naive Bayes          — text classification, cepat

REGRESI:
  Linear Regression    — simple, interpretable
  Ridge/Lasso          — linear + regularisasi
  Random Forest        — non-linear tabular
  Gradient Boosting    — state of the art tabular
  SVR                  — SVM untuk regresi

CLUSTERING:
  K-Means              — simple, bulat cluster
  DBSCAN               — arbitrary shape, noise-aware
  Hierarchical         — tidak perlu tentukan K dulu

NEURAL NETWORK:
  Dense NN             — tabular data
  CNN                  — gambar
  RNN/LSTM             — sekuens/teks
  Transformer          — NLP modern
```

### Cheatsheet Sklearn

```python
# Template Universal ML
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.pipeline import Pipeline

# 1. Split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# 2. Pipeline
pipe = Pipeline([("scaler", StandardScaler()), ("model", MODEL_HERE)])

# 3. Train
pipe.fit(X_train, y_train)

# 4. Evaluate
score = pipe.score(X_test, y_test)
y_pred = pipe.predict(X_test)

# 5. Cross-validate
from sklearn.model_selection import cross_val_score
cv = cross_val_score(pipe, X, y, cv=5).mean()

# 6. Tune
from sklearn.model_selection import GridSearchCV
gs = GridSearchCV(pipe, param_grid, cv=5)
gs.fit(X_train, y_train)

# 7. Save
import joblib
joblib.dump(pipe, "model.pkl")
pipe = joblib.load("model.pkl")
```

### Cheatsheet NumPy

```python
import numpy as np

# Buat array
np.array([1,2,3])          np.zeros((m,n))
np.ones((m,n))             np.eye(n)
np.arange(start,stop,step) np.linspace(start,stop,n)
np.random.randn(m,n)       np.random.randint(low,high,(m,n))

# Info
a.shape  a.ndim  a.dtype  a.size  len(a)

# Operasi
a + b    a - b   a * b    a / b    a ** n
np.dot(a,b)  a @ b  a.T
np.sqrt()  np.exp()  np.log()  np.abs()

# Agregasi
np.sum(a, axis=0)  np.mean()  np.std()  np.var()
np.min()  np.max()  np.argmin()  np.argmax()

# Reshape
a.reshape(m,n)  a.flatten()  a.ravel()
np.concatenate()  np.stack()  np.vstack()  np.hstack()

# Indexing
a[i]  a[i:j]  a[i:j:k]  a[mask]  a[:, col]
```

### Roadmap Lanjutan

```
Setelah selesai dokumen ini:

INTERMEDIATE:
□ Natural Language Processing (NLP)
  - TF-IDF, Word2Vec
  - Sentiment Analysis
  - Text Classification

□ Computer Vision
  - CNN dari scratch
  - Image classification dengan Keras
  - Transfer Learning (MobileNet, EfficientNet)

□ Time Series
  - ARIMA, SARIMA
  - LSTM untuk time series
  - Forecasting

ADVANCED:
□ Reinforcement Learning
  - Q-Learning dari scratch
  - Deep Q-Network (DQN)

□ Generative Models
  - Autoencoder
  - VAE (Variational Autoencoder)
  - GAN (Generative Adversarial Network)

□ MLOps
  - Model versioning (MLflow)
  - Serving model (FastAPI)
  - Monitoring dan retraining

RESOURCES OFFLINE:
□ Buku (download PDF legal):
  - "Hands-On ML" — Aurélien Géron
  - "Deep Learning" — Goodfellow, Bengio, Courville
  - "Pattern Recognition and ML" — Bishop (free dari Microsoft)
  - "Mathematics for ML" — Deisenroth (free di mml-book.github.io)

□ Dataset offline bawaan sklearn:
  - load_iris, load_breast_cancer, load_digits
  - load_wine, load_diabetes, load_boston
```

---

```
Ini bukan akhir perjalanan.
Ini awal dari sesuatu yang lebih besar.

Satu hal yang bikin orang gagal belajar ML:
nunggu "siap" dulu baru mulai.
Mulai aja. Berantakan itu bagian dari prosesnya.

— r¡z | assistant, 2026
```

---
*Versi: 1.0.0 | Python 3.10+ | Scikit-learn 1.x | TensorFlow 2.x*
*100% Offline setelah pip install | Diuji di Android + Termux*
