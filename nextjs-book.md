# ⚡ Belajar Next.js — Dari 0 Sampai Production-Grade Developer

> **by Riz-dev × Claude Sonnet 4.6**
> *Riset langsung dari docs resmi & release notes Next.js 16.2 (Mei 2026)*
> *Dipraktekin di Termux & Acode, dijelasin kenapa — bukan cuma gimana.*

---

## 📋 Daftar Isi

### 🟥 BAGIAN 1 — Fondasi
1. [Apa itu Next.js? — Dan Kenapa Lo Perlu Ini](#1-apa-itu-nextjs--dan-kenapa-lo-perlu-ini)
2. [Versi & Ekosistem 2026](#2-versi--ekosistem-2026)
3. [Setup — Termux, Acode, VPS](#3-setup--termux-acode-vps)
4. [Struktur Project — App Router](#4-struktur-project--app-router)
5. [File-file Spesial Next.js](#5-file-file-spesial-nextjs)

### 🟧 BAGIAN 2 — Routing & Navigasi
6. [Routing — Folder = URL](#6-routing--folder--url)
7. [Dynamic Routes & Params](#7-dynamic-routes--params)
8. [Layouts — Komponen yang Bertahan](#8-layouts--komponen-yang-bertahan)
9. [Navigation — Link & useRouter](#9-navigation--link--userouter)
10. [Route Groups & Parallel Routes](#10-route-groups--parallel-routes)

### 🟨 BAGIAN 3 — Rendering & Data
11. [Server vs Client Components](#11-server-vs-client-components)
12. [Data Fetching — Cara Modern](#12-data-fetching--cara-modern)
13. [Server Actions — Mutasi Data Tanpa API Route](#13-server-actions--mutasi-data-tanpa-api-route)
14. [Caching — use cache & API Baru](#14-caching--use-cache--api-baru)
15. [Streaming & Suspense](#15-streaming--suspense)

### 🟩 BAGIAN 4 — API & Backend
16. [Route Handlers — API Endpoints](#16-route-handlers--api-endpoints)
17. [proxy.ts — Pengganti middleware.ts](#17-proxyts--pengganti-middlewarets)
18. [Database Integration — Prisma & Drizzle](#18-database-integration--prisma--drizzle)
19. [Authentication — Auth.js & Clerk](#19-authentication--authjs--clerk)

### 🟦 BAGIAN 5 — Optimasi & Deployment
20. [Image, Font & Script Optimization](#20-image-font--script-optimization)
21. [Metadata & SEO](#21-metadata--seo)
22. [Environment Variables & Config](#22-environment-variables--config)
23. [Turbopack — Bundler Default 2026](#23-turbopack--bundler-default-2026)
24. [Deployment — Vercel, VPS, Docker](#24-deployment--vercel-vps-docker)

### 🟪 BAGIAN 6 — Debug & Best Practice
25. [Debugging — Cara Analisa Bug Next.js](#25-debugging--cara-analisa-bug-nextjs)
26. [Error Handling — Graceful & Informatif](#26-error-handling--graceful--informatif)
27. [Security — Hal yang Wajib Lo Tahu](#27-security--hal-yang-wajib-lo-tahu)
28. [Best Practice & Anti-pattern](#28-best-practice--anti-pattern)
29. [Mini Projects — Latihan Nyata](#29-mini-projects--latihan-nyata)

---

# 🟥 BAGIAN 1 — FONDASI

## 1. Apa itu Next.js? — Dan Kenapa Lo Perlu Ini

Lo udah tau HTML, CSS, JavaScript. Lo mungkin udah tau React. Tapi kenapa masih perlu Next.js?

**Masalah dengan React biasa:**
- React render di browser (client-side). User download semua JS dulu, baru tampil.
- Lambat di HP murah, koneksi jelek.
- Google susah index konten yang di-render JavaScript.
- Tidak ada routing bawaan — lo harus install dan setup React Router sendiri.
- Tidak ada backend — lo perlu setup Express/Fastify terpisah.
- Tidak ada optimasi gambar bawaan.

**Next.js menyelesaikan semua itu:**

```
Next.js = React + Server-Side Rendering + Routing + API + Caching + Optimasi
```

Dengan Next.js, lo bisa:
- Render halaman di server → user langsung lihat konten, bukan loading spinner
- Punya URL dan routing otomatis berdasarkan struktur folder
- Buat API endpoint di dalam project yang sama
- Optimasi gambar, font, dan script secara otomatis
- Deploy ke mana saja — Vercel, VPS, Docker

### Perbandingan konkret:

```
React SPA (biasa):
  User buka browser → download 500KB JS → parse JS → fetch data → render
  Time to Content: ~2-4 detik (HP murah + internet lemot)

Next.js:
  User buka browser → server render HTML + data langsung → tampil
  Time to Content: ~0.3-0.8 detik
```

### Next.js bukan cuma untuk website

Lo bisa pakai Next.js untuk:
- **Web app full-stack** (frontend + backend dalam satu project)
- **API server** (Route Handlers)
- **Dashboard & admin panel**
- **Landing page & blog** (dengan static generation)
- **E-commerce** (dengan server rendering + caching)
- **SaaS platform**

---

## 2. Versi & Ekosistem 2026

> *Data ini hasil riset langsung dari nextjs.org, GitHub releases, dan changelog — Mei 2026*

### Versi terkini:

| Versi | Status | Tanggal Rilis | Node.js Min |
|-------|--------|---------------|-------------|
| **16.2** | ✅ Latest Stable | Maret 2026 | 20.9.0+ |
| 16.1 | Stable | Desember 2025 | 20.9.0+ |
| 16.0 | Stable (LTS) | Oktober 2025 | 20.9.0+ |
| 15.x | Supported | 2024-2025 | 18.18.0+ |
| 14.x | End of Life | 2023-2024 | 18.17.0+ |

**Upgrade ke versi terbaru:**
```bash
# Cara otomatis (pakai codemod resmi — direkomendasikan)
npx @next/codemod@canary upgrade latest

# Cara manual
npm install next@latest react@latest react-dom@latest
```

### Fitur besar yang masuk di Next.js 16.x:

**Next.js 16.0 (Oktober 2025):**
- **Turbopack stable** — jadi default bundler, gantiin Webpack. Build 2-5x lebih cepat.
- **Cache Components** — model caching baru dengan directive `"use cache"`. Lebih eksplisit dan predictable dari sebelumnya.
- **proxy.ts** — gantiin `middleware.ts`. Lebih jelas batasnya.
- **React 19.2** — bundled langsung. Ada `useEffectEvent`, `<Activity>`, View Transitions.
- **DevTools MCP** — AI-assisted debugging via Model Context Protocol.
- **Breaking: Node.js 20.9+ wajib** — Node 18 tidak lagi didukung.
- **Breaking: async params/searchParams** — sekarang harus di-`await`.
- **Breaking: AMP dihapus** — tidak ada lagi dukungan AMP.
- **Breaking: `next lint` dihapus** — jalankan ESLint langsung.

**Next.js 16.1 (Desember 2025):**
- **Turbopack FS Cache stable** — compiler artifacts disimpan ke disk. Restart dev server jauh lebih cepat.
- **`next dev --inspect`** — attach Node.js debugger langsung, tanpa harus set `NODE_OPTIONS`.
- **Bundle Analyzer** (experimental) — visualisasi ukuran bundle.

**Next.js 16.2 (Maret 2026):**
- **`next start --inspect`** — extend `--inspect` ke production server.
- **87% faster dev startup** — startup `localhost:3000` hampir instan.
- **350% faster RSC payload deserialization** → 25-60% faster rendering.
- **Server Fast Refresh** — hot reload server-side secara fine-grained.
- **Browser Log Forwarding** — error browser di-forward ke terminal (berguna untuk AI agent debugging).
- **Error cause chains** — overlay error sekarang tampilkan chain `Error.cause` sampai 5 level.
- **Adapters API (stable)** — API buat platform/hosting custom.
- **View Transitions di `<Link>`** — animasi transisi navigasi via `transitionTypes` prop.
- **200+ Turbopack bug fixes**.

### Ekosistem yang sering dipakai bersama Next.js (2026):

| Kategori | Tools Populer |
|----------|--------------|
| **Styling** | Tailwind CSS v4, CSS Modules, shadcn/ui |
| **Database** | PostgreSQL, SQLite, MongoDB |
| **ORM** | Prisma, Drizzle ORM |
| **Auth** | Auth.js v5 (NextAuth), Clerk |
| **State** | Zustand, Jotai, TanStack Query |
| **Form** | React Hook Form + Zod |
| **Testing** | Vitest, Playwright, Jest |
| **Deployment** | Vercel, Docker, Railway, Fly.io |
| **Cache/Queue** | Upstash Redis, BullMQ |

---

## 3. Setup — Termux, Acode, VPS

### 🖥️ Setup di PC/Laptop (Tercepat)

```bash
# Buat project baru
npx create-next-app@latest nama-project

# Wizard akan tanya beberapa hal:
# ✅ TypeScript? → Yes (direkomendasikan)
# ✅ ESLint? → Yes
# ✅ Tailwind CSS? → Yes (opsional, tapi berguna)
# ✅ src/ directory? → No (App Router pakai app/)
# ✅ App Router? → Yes (ini yang kita pelajari)
# ✅ Customize import alias? → No (default @/ sudah bagus)

cd nama-project
npm run dev
# Buka browser: http://localhost:3000
```

### 📱 Setup di Termux (Android)

```bash
# Pastikan Node.js terinstall dan versinya >= 20.9
node --version   # harus v20.9.0 atau lebih baru

# Kalau belum atau versi lama:
pkg install nodejs -y
# Atau update:
pkg upgrade nodejs -y

# Cek npm:
npm --version

# Install project baru
cd ~/storage/downloads
npx create-next-app@latest aners-web
cd aners-web

# Jalankan dev server
npm run dev

# Buka browser Android → http://localhost:3000
```

> ⚠️ **Catatan Termux:** Next.js cukup berat untuk HP RAM rendah. Kalau RAM HP lo < 4GB, proses build bisa lambat. Gunakan `--turbopack` sudah aktif by default di Next.js 16.

**Tips hemat RAM di Termux:**
```bash
# Set NODE_OPTIONS untuk batasi memory
export NODE_OPTIONS="--max-old-space-size=512"

# Kalau masih OOM (Out of Memory), coba swap:
# (membutuhkan akses root atau Termux dengan swap setup)
```

### 💻 Setup di VPS Ubuntu (DigitalOcean, Linode, dll)

```bash
# SSH ke VPS lo
ssh root@ip-vps-lo

# Pastikan Node.js 20+ terinstall
node --version
# Kalau belum, install via nvm (lebih fleksibel):
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
source ~/.bashrc
nvm install 20
nvm use 20
nvm alias default 20

# Clone project dari GitHub (atau upload via scp/rsync)
git clone https://github.com/username/repo.git
cd repo

# Install dependencies
npm install

# Build untuk production
npm run build

# Jalankan production server
npm run start

# Jalankan dengan PM2 (auto-restart kalau crash)
npm install -g pm2
pm2 start npm --name "my-app" -- start
pm2 save
pm2 startup   # biar restart otomatis kalau VPS reboot
```

**Nginx reverse proxy setup (VPS):**
```nginx
# /etc/nginx/sites-available/myapp
server {
    listen 80;
    server_name domain-lo.com www.domain-lo.com;

    location / {
        proxy_pass http://localhost:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_cache_bypass $http_upgrade;
    }
}
```

```bash
# Aktifkan site
ln -s /etc/nginx/sites-available/myapp /etc/nginx/sites-enabled/
nginx -t && nginx -s reload

# SSL dengan Certbot (free HTTPS)
apt install certbot python3-certbot-nginx -y
certbot --nginx -d domain-lo.com
```

### 📝 Setup di Acode (Edit File di HP)

Acode bagus buat ngedit file di proyek yang jalan di Termux atau VPS. Setup SSH connection di Acode:

```
Acode → Settings → SFTP/SSH:
  Host: ip-vps-lo atau localhost
  Port: 22 (atau custom)
  Username: root atau user
  Password: atau private key

→ Bisa browse dan edit file langsung
→ Acode punya syntax highlighting TypeScript/JSX otomatis
```

---

## 4. Struktur Project — App Router

Ini struktur project Next.js 16 yang lo dapatkan setelah `create-next-app`:

```
nama-project/
├── app/                    ← Semua halaman dan route ada di sini
│   ├── layout.tsx          ← Layout root (wraps semua halaman)
│   ├── page.tsx            ← Halaman utama (/)
│   ├── globals.css         ← CSS global
│   └── favicon.ico
│
├── public/                 ← File statis: gambar, icon, robots.txt
│   └── images/
│
├── components/             ← Komponen React yang bisa di-reuse
│   ├── ui/                 ← Komponen UI dasar (button, card, dll)
│   └── features/           ← Komponen per fitur
│
├── lib/                    ← Utilities, helpers, konfigurasi
│   ├── db.ts               ← Koneksi database
│   └── utils.ts            ← Helper functions
│
├── hooks/                  ← Custom React hooks
│
├── types/                  ← TypeScript type definitions
│
├── next.config.ts          ← Konfigurasi Next.js (pakai .ts di v16!)
├── package.json
├── tsconfig.json
└── .env.local              ← Environment variables (JANGAN di-commit!)
```

### `next.config.ts` — Konfigurasi Modern

Di Next.js 16, config file bisa pakai `.ts` langsung (bukan `.js`):

```typescript
// next.config.ts
import type { NextConfig } from 'next'

const nextConfig: NextConfig = {
    // Aktifkan Cache Components (fitur baru Next.js 16)
    cacheComponents: true,

    // Konfigurasi gambar dari domain eksternal
    images: {
        remotePatterns: [
            {
                protocol: 'https',
                hostname: 'images.unsplash.com',
            },
            {
                protocol: 'https',
                hostname: '**.githubusercontent.com',
            },
        ],
    },

    // Environment variables yang boleh di-expose ke browser
    env: {
        APP_NAME: 'ANERS Platform',
    },

    // Redirect
    async redirects() {
        return [
            {
                source: '/blog',
                destination: '/artikel',
                permanent: true,  // 308 redirect
            },
        ]
    },

    // Rewrite (URL berbeda, content dari path lain)
    async rewrites() {
        return [
            {
                source: '/api/:path*',
                destination: 'https://backend.example.com/:path*',
            },
        ]
    },

    // Header kustom
    async headers() {
        return [
            {
                source: '/(.*)',
                headers: [
                    {
                        key: 'X-Frame-Options',
                        value: 'DENY',
                    },
                ],
            },
        ]
    },
}

export default nextConfig
```

---

## 5. File-file Spesial Next.js

Next.js punya konvensi penamaan file yang otomatis menentukan perilaku routing. Ini wajib dihafal:

```
app/
├── layout.tsx          ← Layout yang wraps halaman di direktori ini
├── page.tsx            ← Konten halaman utama (yang tampil ke user)
├── loading.tsx         ← UI loading (Suspense fallback otomatis)
├── error.tsx           ← UI ketika ada error di halaman ini
├── not-found.tsx       ← UI 404 untuk route ini
├── global-error.tsx    ← Error handler untuk root layout
├── template.tsx        ← Mirip layout, tapi di-mount ulang tiap navigasi
├── default.tsx         ← Fallback untuk parallel routes
└── route.ts            ← API endpoint (GET, POST, dll — bukan halaman!)
```

### `page.tsx` — Halaman

```typescript
// app/page.tsx
// Ini adalah halaman untuk URL: /

export default function HomePage() {
    return (
        <main>
            <h1>Selamat Datang di ANERS</h1>
        </main>
    )
}

// Export opsional — metadata untuk SEO
export const metadata = {
    title: 'ANERS — AI Platform',
    description: 'Platform AI buatan Rixz',
}
```

### `layout.tsx` — Layout

```typescript
// app/layout.tsx
// Ini adalah ROOT layout — wraps SEMUA halaman

import type { Metadata } from 'next'
import { DM_Sans } from 'next/font/google'
import './globals.css'

const dmSans = DM_Sans({ subsets: ['latin'] })

export const metadata: Metadata = {
    title: {
        default: 'ANERS Platform',
        template: '%s | ANERS',  // halaman lain: "Login | ANERS"
    },
    description: 'AI-Native Engineering & Research Systems',
}

export default function RootLayout({
    children,
}: {
    children: React.ReactNode
}) {
    return (
        <html lang="id">
            <body className={dmSans.className}>
                {children}
            </body>
        </html>
    )
}
```

### `loading.tsx` — Loading UI Otomatis

```typescript
// app/dashboard/loading.tsx
// Otomatis tampil saat app/dashboard/page.tsx loading

export default function DashboardLoading() {
    return (
        <div className="loading-container">
            {/* Skeleton UI */}
            <div className="skeleton" style={{ height: 200 }} />
            <div className="skeleton" style={{ height: 40, marginTop: 16 }} />
        </div>
    )
}
```

### `error.tsx` — Error UI

```typescript
// app/dashboard/error.tsx
// ⚠️ Ini HARUS 'use client' karena pakai hooks!

'use client'

import { useEffect } from 'react'

export default function DashboardError({
    error,
    reset,  // fungsi untuk coba render ulang
}: {
    error: Error & { digest?: string }
    reset: () => void
}) {
    useEffect(() => {
        // Log ke error monitoring service (Sentry, dll)
        console.error('Dashboard error:', error)
    }, [error])

    return (
        <div>
            <h2>Ada yang error di Dashboard</h2>
            <p>{error.message}</p>
            <button onClick={reset}>Coba Lagi</button>
        </div>
    )
}
```

### `not-found.tsx` — 404 Page

```typescript
// app/not-found.tsx  ← Root 404 (berlaku seluruh app)
// app/produk/not-found.tsx  ← 404 khusus untuk /produk/*

import Link from 'next/link'

export default function NotFound() {
    return (
        <div>
            <h1>404 — Halaman Tidak Ditemukan</h1>
            <p>Halaman yang lo cari tidak ada.</p>
            <Link href="/">Balik ke Home</Link>
        </div>
    )
}
```

---

# 🟧 BAGIAN 2 — ROUTING & NAVIGASI

## 6. Routing — Folder = URL

Di Next.js App Router, **struktur folder = struktur URL**. Tidak ada konfigurasi routing manual.

```
Folder                     URL
────────────────────────   ─────────────────
app/page.tsx               /
app/tentang/page.tsx       /tentang
app/artikel/page.tsx       /artikel
app/artikel/baru/page.tsx  /artikel/baru
app/dashboard/page.tsx     /dashboard
```

Praktiknya:
```
app/
├── page.tsx               → /
├── tentang/
│   └── page.tsx           → /tentang
├── artikel/
│   ├── page.tsx           → /artikel
│   └── baru/
│       └── page.tsx       → /artikel/baru
└── dashboard/
    ├── layout.tsx         → layout khusus /dashboard/*
    ├── page.tsx           → /dashboard
    ├── pengaturan/
    │   └── page.tsx       → /dashboard/pengaturan
    └── pengguna/
        └── page.tsx       → /dashboard/pengguna
```

### Contoh nyata:

```typescript
// app/artikel/page.tsx
export default function ArtikelListPage() {
    return <h1>Semua Artikel</h1>
}

// app/artikel/baru/page.tsx
export default function ArtikelBaruPage() {
    return <h1>Tulis Artikel Baru</h1>
}
```

Sesimple itu. Buat folder, buat `page.tsx` di dalamnya — URL otomatis ada.

---

## 7. Dynamic Routes & Params

Untuk URL yang variabel, gunakan folder dengan nama dalam kurung kotak `[nama]`.

```
app/
├── artikel/
│   ├── page.tsx                  → /artikel
│   └── [slug]/
│       └── page.tsx              → /artikel/belajar-html
│                                 → /artikel/nextjs-tutorial
│                                 → /artikel/apa-aja
└── user/
    └── [id]/
        ├── page.tsx              → /user/123
        └── pengaturan/
            └── page.tsx          → /user/123/pengaturan
```

### ⚠️ PENTING: `params` sekarang async di Next.js 16!

```typescript
// app/artikel/[slug]/page.tsx

// ❌ CARA LAMA (Next.js 15 ke bawah) — TIDAK LAGI VALID di Next.js 16!
export default function ArtikelPage({ params }) {
    const slug = params.slug  // ← ini akan error di Next.js 16!
    return <h1>{slug}</h1>
}

// ✅ CARA BARU Next.js 16 — params harus di-await
export default async function ArtikelPage({
    params,
}: {
    params: Promise<{ slug: string }>
}) {
    const { slug } = await params  // ← wajib await!

    return <h1>Artikel: {slug}</h1>
}
```

### Kenapa params jadi async?

Ini memungkinkan streaming — Next.js bisa mulai render halaman sebelum semua params tersedia. Hasilnya: Time to First Byte (TTFB) lebih cepat.

### searchParams juga async:

```typescript
// app/search/page.tsx
// URL: /search?q=nextjs&halaman=2

export default async function SearchPage({
    searchParams,
}: {
    searchParams: Promise<{ q?: string; halaman?: string }>
}) {
    const { q, halaman } = await searchParams

    return (
        <div>
            <h1>Hasil pencarian untuk: {q}</h1>
            <p>Halaman: {halaman ?? '1'}</p>
        </div>
    )
}
```

### Catch-all Routes

```
app/docs/[...slug]/page.tsx
→ /docs/intro
→ /docs/api/route-handlers
→ /docs/api/route-handlers/get-method

// Mengakses semua segmen
const { slug } = await params
// slug = ['api', 'route-handlers', 'get-method']
```

### Optional Catch-all Routes

```
app/docs/[[...slug]]/page.tsx
→ /docs              ← slug = undefined
→ /docs/intro        ← slug = ['intro']
→ /docs/api/auth     ← slug = ['api', 'auth']
```

### Contoh route dengan fetch data:

```typescript
// app/user/[id]/page.tsx
import { notFound } from 'next/navigation'

export default async function UserPage({
    params,
}: {
    params: Promise<{ id: string }>
}) {
    const { id } = await params

    // Fetch data user dari DB atau API
    const user = await fetch(`https://api.example.com/users/${id}`)
        .then(r => r.ok ? r.json() : null)

    // Kalau user tidak ada, tampilkan 404
    if (!user) notFound()

    return (
        <div>
            <h1>{user.nama}</h1>
            <p>{user.email}</p>
        </div>
    )
}

// Generate static params (untuk static generation)
export async function generateStaticParams() {
    const users = await fetch('https://api.example.com/users')
        .then(r => r.json())

    return users.map((user: { id: string }) => ({
        id: user.id,
    }))
}
```

---

## 8. Layouts — Komponen yang Bertahan

Layout adalah komponen yang **tidak di-render ulang** saat navigasi antar halaman dalam direktori yang sama. Ini yang bikin navigasi Next.js terasa instant.

```
app/
└── dashboard/
    ├── layout.tsx   ← Sidebar + navbar dashboard (tidak hilang saat pindah halaman)
    ├── page.tsx     ← Content /dashboard
    ├── users/
    │   └── page.tsx ← Content /dashboard/users (layout di atas tetap ada)
    └── settings/
        └── page.tsx ← Content /dashboard/settings (layout di atas tetap ada)
```

### Root Layout (wajib ada):

```typescript
// app/layout.tsx
import type { Metadata } from 'next'
import { DM_Sans, JetBrains_Mono } from 'next/font/google'
import Navbar from '@/components/Navbar'
import './globals.css'

const dmSans = DM_Sans({
    subsets: ['latin'],
    variable: '--font-body',
    display: 'swap',
})

const jetbrainsMono = JetBrains_Mono({
    subsets: ['latin'],
    variable: '--font-mono',
    display: 'swap',
})

export const metadata: Metadata = {
    title: {
        default: 'ANERS Platform',
        template: '%s | ANERS',
    },
    description: 'AI-Native Engineering & Research Systems',
    metadataBase: new URL('https://aners.dev'),
}

export default function RootLayout({
    children,
}: {
    children: React.ReactNode
}) {
    return (
        <html lang="id" className={`${dmSans.variable} ${jetbrainsMono.variable}`}>
            <body>
                <Navbar />
                {children}
            </body>
        </html>
    )
}
```

### Nested Layout (layout bersarang):

```typescript
// app/dashboard/layout.tsx
// Ini wraps semua halaman di bawah /dashboard

import Sidebar from '@/components/dashboard/Sidebar'

export default function DashboardLayout({
    children,
}: {
    children: React.ReactNode
}) {
    return (
        <div className="dashboard-container">
            <Sidebar />
            <main className="dashboard-main">
                {children}
            </main>
        </div>
    )
}
```

### Layout vs Template:

```typescript
// layout.tsx  — STATE DIPERTAHANKAN antar navigasi
// Cocok untuk: sidebar, navbar, persistent UI

// template.tsx — DI-MOUNT ULANG tiap navigasi
// Cocok untuk: animasi page transition, reset state per halaman

// app/dashboard/template.tsx
'use client'
import { motion } from 'framer-motion'

export default function DashboardTemplate({
    children,
}: {
    children: React.ReactNode
}) {
    return (
        <motion.div
            initial={{ opacity: 0, y: 20 }}
            animate={{ opacity: 1, y: 0 }}
            transition={{ duration: 0.3 }}
        >
            {children}
        </motion.div>
    )
}
```

---

## 9. Navigation — Link & useRouter

### `<Link>` — Navigasi Client-Side (Cepat)

```typescript
import Link from 'next/link'

// Basic link
<Link href="/tentang">Tentang Kami</Link>

// Link dengan replace (tidak tambah history)
<Link href="/login" replace>Login</Link>

// Prefetch manual (default sudah auto-prefetch saat hover)
<Link href="/artikel" prefetch={false}>Artikel</Link>

// Link external (otomatis buka baru)
<Link href="https://github.com" target="_blank" rel="noopener noreferrer">
    GitHub
</Link>

// Dynamic route
<Link href={`/artikel/${slug}`}>Baca Artikel</Link>

// View Transitions (BARU di Next.js 16.2!)
<Link href="/dashboard" transitionTypes={['slide-left']}>
    Masuk Dashboard
</Link>
```

### Active Link — Tampilkan Styling untuk Halaman Aktif

```typescript
// components/NavLink.tsx
'use client'

import Link from 'next/link'
import { usePathname } from 'next/navigation'
import { cn } from '@/lib/utils'

interface NavLinkProps {
    href: string
    children: React.ReactNode
}

export default function NavLink({ href, children }: NavLinkProps) {
    const pathname = usePathname()
    const isActive = pathname === href || pathname.startsWith(href + '/')

    return (
        <Link
            href={href}
            className={cn(
                'nav-link',
                isActive && 'nav-link--active'
            )}
            aria-current={isActive ? 'page' : undefined}
        >
            {children}
        </Link>
    )
}
```

### `useRouter` — Navigasi Programatik

```typescript
// Hanya bisa di Client Component ('use client')
'use client'

import { useRouter } from 'next/navigation'

export default function LoginForm() {
    const router = useRouter()

    async function handleSubmit(e: React.FormEvent) {
        e.preventDefault()
        // ... proses login ...

        // Navigasi setelah berhasil
        router.push('/dashboard')

        // Ganti halaman (tanpa history)
        router.replace('/dashboard')

        // Kembali
        router.back()

        // Maju (kalau ada history ke depan)
        router.forward()

        // Refresh data server-side tanpa full reload
        router.refresh()
    }

    return <form onSubmit={handleSubmit}>...</form>
}
```

### Hooks navigasi lain yang berguna:

```typescript
'use client'
import {
    usePathname,     // URL path saat ini: '/dashboard/users'
    useSearchParams, // Query params: ?q=hello&page=2
    useParams,       // Dynamic route params: { id: '123' }
} from 'next/navigation'

export default function NavInfo() {
    const pathname = usePathname()        // '/dashboard/users'
    const searchParams = useSearchParams()
    const params = useParams()

    const query = searchParams.get('q')   // 'hello'
    const page = searchParams.get('page') // '2'

    return <p>Di halaman: {pathname}</p>
}
```

---

## 10. Route Groups & Parallel Routes

### Route Groups — Organisasi tanpa Mempengaruhi URL

Folder dengan nama dalam tanda kurung `(nama)` tidak mempengaruhi URL. Berguna untuk mengelompokkan route atau punya layout berbeda:

```
app/
├── (marketing)/          ← Tidak jadi bagian URL
│   ├── layout.tsx        ← Layout khusus marketing pages
│   ├── page.tsx          → /
│   ├── tentang/
│   │   └── page.tsx      → /tentang
│   └── harga/
│       └── page.tsx      → /harga
│
└── (app)/                ← Tidak jadi bagian URL
    ├── layout.tsx         ← Layout khusus app (dengan sidebar, dll)
    ├── dashboard/
    │   └── page.tsx      → /dashboard
    └── profil/
        └── page.tsx      → /profil
```

Jadi lo bisa punya `/` dan `/dashboard` dengan layout yang sama sekali berbeda, tanpa ada prefix di URL.

### Contoh: Auth layout vs App layout

```
app/
├── (auth)/
│   ├── layout.tsx        ← Layout minimalis (logo centered)
│   ├── login/
│   │   └── page.tsx      → /login
│   └── daftar/
│       └── page.tsx      → /daftar
│
└── (main)/
    ├── layout.tsx         ← Layout dengan navbar + sidebar
    ├── page.tsx           → /
    └── dashboard/
        └── page.tsx      → /dashboard
```

### Parallel Routes — Render Beberapa Halaman Sekaligus

Folder dengan `@nama` adalah "slot" yang bisa diisi secara parallel:

```
app/
└── dashboard/
    ├── layout.tsx
    ├── page.tsx
    ├── @stats/
    │   └── page.tsx      ← Tampil bersamaan
    └── @recent/
        └── page.tsx      ← Tampil bersamaan
```

```typescript
// app/dashboard/layout.tsx
export default function DashboardLayout({
    children,
    stats,    // @stats
    recent,   // @recent
}: {
    children: React.ReactNode
    stats: React.ReactNode
    recent: React.ReactNode
}) {
    return (
        <div className="dashboard-grid">
            <main>{children}</main>
            <aside>
                {stats}
                {recent}
            </aside>
        </div>
    )
}
```

---

# 🟨 BAGIAN 3 — RENDERING & DATA

## 11. Server vs Client Components

Ini konsep **PALING PENTING** di Next.js modern. Salah paham ini = salah arsitektur.

### Server Components — Default di App Router

Semua komponen di App Router adalah **Server Component secara default**. Mereka di-render di server, tidak ada JavaScript yang dikirim ke browser.

```typescript
// app/artikel/page.tsx
// Ini Server Component (tidak perlu 'use server', sudah default)

async function getArtikel() {
    // Bisa langsung akses database, environment variable sensitif, dll
    const res = await fetch('https://api.example.com/artikel')
    return res.json()
}

export default async function ArtikelPage() {
    // Bisa pakai async/await langsung di komponen!
    const artikel = await getArtikel()

    return (
        <ul>
            {artikel.map((item: { id: string; judul: string }) => (
                <li key={item.id}>{item.judul}</li>
            ))}
        </ul>
    )
}
```

**Kemampuan Server Component:**
- ✅ `async/await` langsung di komponen
- ✅ Akses database, file system, environment variable sensitif
- ✅ Fetch data di server (lebih cepat, dekat dengan sumber data)
- ✅ Zero bundle size tambahan di browser
- ✅ Bisa pakai paket Node.js (fs, path, crypto, dll)

**Keterbatasan Server Component:**
- ❌ Tidak bisa pakai `useState`, `useEffect`, atau hooks lain
- ❌ Tidak bisa handle event browser (onClick, onChange, dll)
- ❌ Tidak punya akses ke browser APIs (localStorage, window, dll)

### Client Components — Opt-in dengan `'use client'`

Ketika butuh interaktivitas, tambahkan `'use client'` di atas file:

```typescript
// components/Counter.tsx
'use client'  // ← HARUS di baris pertama!

import { useState } from 'react'

export default function Counter() {
    const [count, setCount] = useState(0)

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={() => setCount(count + 1)}>+1</button>
            <button onClick={() => setCount(count - 1)}>-1</button>
        </div>
    )
}
```

**Kemampuan Client Component:**
- ✅ `useState`, `useEffect`, dan semua hooks
- ✅ Event listeners (onClick, onSubmit, dll)
- ✅ Browser APIs (localStorage, window, document)
- ✅ Real-time updates (WebSocket, EventSource)

**Keterbatasan Client Component:**
- ❌ Tidak bisa `async` di komponen langsung (tapi bisa fetch dalam useEffect)
- ❌ JavaScript dikirim ke browser → tambah bundle size
- ❌ Tidak bisa langsung akses database

### Pola yang benar — Server + Client berkolaborasi:

```typescript
// app/dashboard/page.tsx — Server Component
// Fetch data di server, pass ke client component yang perlu interaktivitas

import KartuInteraktif from '@/components/KartuInteraktif'  // Client Component

async function getData() {
    const res = await fetch('https://api.example.com/data')
    return res.json()
}

export default async function DashboardPage() {
    const data = await getData()  // ← dijalankan di server

    return (
        <div>
            <h1>Dashboard</h1>
            {/* Kirim data sebagai props ke client component */}
            <KartuInteraktif data={data} />
        </div>
    )
}
```

```typescript
// components/KartuInteraktif.tsx — Client Component
'use client'

import { useState } from 'react'

interface Props {
    data: Array<{ id: string; nama: string; nilai: number }>
}

export default function KartuInteraktif({ data }: Props) {
    const [filter, setFilter] = useState('')

    const filtered = data.filter(item =>
        item.nama.toLowerCase().includes(filter.toLowerCase())
    )

    return (
        <div>
            <input
                type="search"
                value={filter}
                onChange={e => setFilter(e.target.value)}
                placeholder="Cari..."
            />
            {filtered.map(item => (
                <div key={item.id}>
                    <p>{item.nama}: {item.nilai}</p>
                </div>
            ))}
        </div>
    )
}
```

### Aturan penting: Server di dalam Client tidak bisa!

```typescript
// ❌ TIDAK VALID — Server Component di dalam Client Component
'use client'
import ServerComponent from './ServerComponent'  // Error!

// ✅ VALID — Kirim Server Component sebagai children (props)
'use client'
import { useState } from 'react'

export default function ClientWrapper({
    children,  // ← ini bisa berisi Server Component!
}: {
    children: React.ReactNode
}) {
    const [open, setOpen] = useState(false)
    return (
        <div>
            <button onClick={() => setOpen(!open)}>Toggle</button>
            {open && children}
        </div>
    )
}

// Di Server Component parent:
// <ClientWrapper>
//     <ServerComponentDiDalam />  ← ini boleh!
// </ClientWrapper>
```

---

## 12. Data Fetching — Cara Modern

### Fetch di Server Component — Cara Paling Simpel

```typescript
// app/produk/page.tsx

interface Produk {
    id: number
    nama: string
    harga: number
}

async function getProduk(): Promise<Produk[]> {
    const res = await fetch('https://api.example.com/produk', {
        // Opsi caching (lebih detail di bab 14)
        cache: 'no-store',  // Selalu fresh, tidak pernah cache
        // atau:
        next: { revalidate: 3600 },  // Cache 1 jam, lalu revalidate
    })

    if (!res.ok) {
        throw new Error('Gagal mengambil data produk')
    }

    return res.json()
}

export default async function ProdukPage() {
    const produk = await getProduk()

    return (
        <div>
            <h1>Produk ({produk.length} item)</h1>
            <ul>
                {produk.map(p => (
                    <li key={p.id}>
                        {p.nama} — Rp {p.harga.toLocaleString('id-ID')}
                    </li>
                ))}
            </ul>
        </div>
    )
}
```

### Fetch Parallel — Ambil Data Bersamaan

```typescript
// ❌ SEQUENTIAL — lambat (menunggu satu-satu)
const user = await fetchUser(id)
const orders = await fetchOrders(id)    // tunggu user selesai dulu
const reviews = await fetchReviews(id)  // tunggu orders selesai dulu

// ✅ PARALLEL — lebih cepat (semua jalan bersamaan)
const [user, orders, reviews] = await Promise.all([
    fetchUser(id),
    fetchOrders(id),
    fetchReviews(id),
])
```

### Fetch dengan Error Handling yang Proper:

```typescript
// lib/api.ts
export class ApiError extends Error {
    constructor(
        message: string,
        public statusCode: number,
        public code?: string
    ) {
        super(message)
        this.name = 'ApiError'
    }
}

export async function apiFetch<T>(
    url: string,
    options?: RequestInit
): Promise<T> {
    const res = await fetch(url, options)

    if (!res.ok) {
        const error = await res.json().catch(() => ({}))
        throw new ApiError(
            error.message ?? `HTTP ${res.status}`,
            res.status,
            error.code
        )
    }

    return res.json()
}

// Penggunaan:
import { apiFetch, ApiError } from '@/lib/api'
import { notFound } from 'next/navigation'

export default async function ProdukDetailPage({
    params,
}: {
    params: Promise<{ id: string }>
}) {
    const { id } = await params

    try {
        const produk = await apiFetch<Produk>(`/api/produk/${id}`)
        return <div>{produk.nama}</div>
    } catch (error) {
        if (error instanceof ApiError && error.statusCode === 404) {
            notFound()  // Tampilkan not-found.tsx
        }
        throw error  // Lempar ke error.tsx
    }
}
```

### Fetch dari Database Langsung (tanpa API route):

```typescript
// lib/db.ts
import { PrismaClient } from '@prisma/client'

const globalForPrisma = globalThis as unknown as {
    prisma: PrismaClient | undefined
}

export const db =
    globalForPrisma.prisma ??
    new PrismaClient({
        log: process.env.NODE_ENV === 'development' ? ['query'] : [],
    })

if (process.env.NODE_ENV !== 'production') {
    globalForPrisma.prisma = db
}
```

```typescript
// app/users/page.tsx — Server Component langsung akses DB!
import { db } from '@/lib/db'

export default async function UsersPage() {
    // Langsung query database — tidak perlu API route!
    const users = await db.user.findMany({
        where: { active: true },
        select: { id: true, nama: true, email: true },
        orderBy: { createdAt: 'desc' },
        take: 20,
    })

    return (
        <ul>
            {users.map(user => (
                <li key={user.id}>{user.nama} — {user.email}</li>
            ))}
        </ul>
    )
}
```

---

## 13. Server Actions — Mutasi Data Tanpa API Route

Server Actions adalah fungsi yang **jalan di server** tapi bisa dipanggil dari Client Component. Ini cara modern untuk handle form submission dan mutasi data.

### Deklarasi Server Action

```typescript
// Cara 1: Inline di Server Component
export default function FormPage() {
    async function simpanData(formData: FormData) {
        'use server'  // ← harus ada di dalam fungsi

        const nama = formData.get('nama') as string
        const email = formData.get('email') as string

        // Validasi
        if (!nama || !email) {
            throw new Error('Nama dan email wajib diisi')
        }

        // Simpan ke database
        await db.user.create({ data: { nama, email } })

        // Revalidate halaman (refresh data)
        revalidatePath('/users')
    }

    return (
        <form action={simpanData}>  {/* ← bukan onSubmit! */}
            <input name="nama" type="text" required />
            <input name="email" type="email" required />
            <button type="submit">Simpan</button>
        </form>
    )
}
```

```typescript
// Cara 2: File terpisah (direkomendasikan untuk project besar)
// app/actions/user.ts — atau lib/actions.ts

'use server'  // ← di atas file, berlaku untuk semua fungsi di file ini

import { db } from '@/lib/db'
import { revalidatePath } from 'next/cache'
import { redirect } from 'next/navigation'
import { z } from 'zod'

const UserSchema = z.object({
    nama: z.string().min(2, 'Nama minimal 2 karakter'),
    email: z.string().email('Format email tidak valid'),
    password: z.string().min(8, 'Password minimal 8 karakter'),
})

export async function daftarUser(formData: FormData) {
    // Validasi input dengan Zod
    const validasi = UserSchema.safeParse({
        nama: formData.get('nama'),
        email: formData.get('email'),
        password: formData.get('password'),
    })

    if (!validasi.success) {
        return {
            error: validasi.error.flatten().fieldErrors,
        }
    }

    const { nama, email, password } = validasi.data

    // Cek email sudah ada
    const existing = await db.user.findUnique({ where: { email } })
    if (existing) {
        return { error: { email: ['Email sudah terdaftar'] } }
    }

    // Hash password
    const bcrypt = await import('bcrypt')
    const hashedPassword = await bcrypt.hash(password, 12)

    // Simpan
    await db.user.create({
        data: { nama, email, password: hashedPassword },
    })

    redirect('/login?registered=true')
}

export async function hapusUser(id: string) {
    await db.user.delete({ where: { id } })
    revalidatePath('/admin/users')
}

export async function updateProfil(userId: string, formData: FormData) {
    const nama = formData.get('nama') as string

    await db.user.update({
        where: { id: userId },
        data: { nama },
    })

    revalidatePath(`/profil/${userId}`)
    revalidateTag('user-data')
}
```

### Gunakan di Client Component:

```typescript
// components/FormDaftar.tsx
'use client'

import { useActionState } from 'react'
import { daftarUser } from '@/app/actions/user'

export default function FormDaftar() {
    const [state, action, isPending] = useActionState(daftarUser, undefined)

    return (
        <form action={action}>
            <div>
                <label htmlFor="nama">Nama</label>
                <input id="nama" name="nama" type="text" required />
                {state?.error?.nama && (
                    <p className="error">{state.error.nama[0]}</p>
                )}
            </div>

            <div>
                <label htmlFor="email">Email</label>
                <input id="email" name="email" type="email" required />
                {state?.error?.email && (
                    <p className="error">{state.error.email[0]}</p>
                )}
            </div>

            <div>
                <label htmlFor="password">Password</label>
                <input id="password" name="password" type="password" required />
                {state?.error?.password && (
                    <p className="error">{state.error.password[0]}</p>
                )}
            </div>

            <button type="submit" disabled={isPending}>
                {isPending ? 'Mendaftar...' : 'Daftar'}
            </button>
        </form>
    )
}
```

### Server Action vs API Route — kapan pakai yang mana:

| Situasi | Gunakan |
|---------|---------|
| Form submission | **Server Action** |
| Mutasi data dari UI | **Server Action** |
| API yang dipakai aplikasi lain | **Route Handler** |
| Webhook dari layanan eksternal | **Route Handler** |
| Public REST API | **Route Handler** |
| File upload streaming | **Route Handler** |

---

## 14. Caching — `use cache` & API Baru

Di Next.js 16, sistem caching berubah total. Sebelumnya caching "magic" dan sering confusing. Sekarang **explicit dan opt-in**.

### Prinsip baru: Semua dinamis by default

```typescript
// Di Next.js 15: fetch di-cache secara default (sering bikin data stale)
// Di Next.js 16: semua dynamic by default, cache harus explicitly diminta
```

### Aktifkan Cache Components di config:

```typescript
// next.config.ts
const nextConfig = {
    cacheComponents: true,  // ← aktifkan fitur ini
}
export default nextConfig
```

### `"use cache"` — Directive Caching Eksplisit

```typescript
// Cache seluruh halaman
'use cache'

export default async function BlogPage() {
    const posts = await fetchPosts()
    return <PostList posts={posts} />
}

// Cache sebuah komponen
async function SidebarWidget() {
    'use cache'  // bisa juga di dalam komponen

    const stats = await fetchStats()
    return <StatsDisplay stats={stats} />
}

// Cache sebuah fungsi
'use cache'
export async function getCachedUser(id: string) {
    return db.user.findUnique({ where: { id } })
}
```

### `cacheLife` — Berapa Lama di-Cache

```typescript
import { unstable_cacheLife as cacheLife } from 'next/cache'

// Built-in profiles:
// 'seconds' — beberapa detik
// 'minutes' — beberapa menit
// 'hours'   — beberapa jam
// 'days'    — beberapa hari
// 'weeks'   — beberapa minggu
// 'max'     — cache selama mungkin

async function getArtikelFeatured() {
    'use cache'
    cacheLife('hours')  // cache selama berjam-jam

    return db.artikel.findMany({
        where: { featured: true },
        take: 5,
    })
}

// Custom cache life
async function getDataSensitif() {
    'use cache'
    cacheLife({
        stale: 60,       // data "stale" setelah 60 detik
        revalidate: 300, // revalidate setelah 5 menit
        expire: 3600,    // hapus dari cache setelah 1 jam
    })

    return fetchDataSensitif()
}
```

### `cacheTag` — Tandai Cache untuk Invalidasi

```typescript
import {
    unstable_cacheTag as cacheTag,
    revalidateTag,
} from 'next/cache'

// Tag cache agar bisa di-invalidasi nanti
async function getUserProfile(userId: string) {
    'use cache'
    cacheTag(`user-${userId}`, 'all-users')

    return db.user.findUnique({ where: { id: userId } })
}

// Di Server Action — invalidasi cache saat data berubah
'use server'
export async function updateUserProfile(userId: string, data: UserData) {
    await db.user.update({ where: { id: userId }, data })

    // Invalidasi cache user ini saja
    revalidateTag(`user-${userId}`)
}
```

### API Cache Baru di Next.js 16:

```typescript
import { revalidateTag, revalidatePath } from 'next/cache'
// Dua hal baru di Next.js 16:
import { updateTag, refresh } from 'next/cache'

// revalidateTag — invalidasi + eventual consistency (background refresh)
// Cocok untuk: blog posts, produk, data yang boleh delay sedikit
export async function publishArtikel(id: string) {
    'use server'
    await db.artikel.update({ where: { id }, data: { published: true } })
    revalidateTag('artikel-list')  // refresh dalam background, user lihat lama dulu sebentar
}

// updateTag — invalidasi + immediate (user langsung lihat data baru)
// Cocok untuk: profil user, settings, data yang harus langsung update
export async function updateNamaUser(userId: string, nama: string) {
    'use server'
    await db.user.update({ where: { id: userId }, data: { nama } })
    updateTag(`user-${userId}`)  // user langsung lihat perubahan!
}

// refresh — refresh client router
// Cocok untuk: ketika data berubah tapi tidak pakai cacheTag
export async function tandaiNotifDibaca(notifId: string) {
    'use server'
    await db.notifikasi.update({ where: { id: notifId }, data: { dibaca: true } })
    refresh()  // refresh router di client
}
```

---

## 15. Streaming & Suspense

Streaming memungkinkan halaman dikirim ke browser secara **bertahap** — bagian yang cepat dikirim duluan, bagian yang perlu fetch data dikirim belakangan.

### Tanpa Streaming (blocking):

```
Browser request halaman
    → Server fetch semua data (misal 2 detik)
    → Server render HTML
    → Browser tampilkan halaman
Total: 2 detik blank screen
```

### Dengan Streaming + Suspense:

```
Browser request halaman
    → Server langsung kirim shell HTML (navbar, judul, skeleton)
    → Browser tampilkan shell (instant!)
    → Sambil data di-fetch, stream potongan-potongan content
    → Browser update secara progressive
Total: ~0.1 detik pertama tampil, konten masuk bertahap
```

### Implementasi Suspense:

```typescript
// app/dashboard/page.tsx
import { Suspense } from 'react'
import StatsSkeleton from '@/components/StatsSkeleton'
import RecentActivitySkeleton from '@/components/RecentActivitySkeleton'

// Import komponen yang fetch data lambat
import StatsWidget from '@/components/StatsWidget'
import RecentActivity from '@/components/RecentActivity'
import QuickInfo from '@/components/QuickInfo'  // komponen cepat

export default function DashboardPage() {
    return (
        <div className="dashboard">
            {/* QuickInfo tidak perlu Suspense — tidak fetch data */}
            <QuickInfo />

            {/* StatsWidget fetch data — wrap dengan Suspense */}
            <Suspense fallback={<StatsSkeleton />}>
                <StatsWidget />
            </Suspense>

            {/* RecentActivity juga fetch data — wrapper terpisah */}
            <Suspense fallback={<RecentActivitySkeleton />}>
                <RecentActivity />
            </Suspense>
        </div>
    )
}
```

```typescript
// components/StatsWidget.tsx — Server Component yang fetch data
async function fetchStats() {
    // Simulasi fetch lambat
    await new Promise(r => setTimeout(r, 2000))
    return { total: 1234, growth: 12.5 }
}

export default async function StatsWidget() {
    const stats = await fetchStats()

    return (
        <div className="stats-widget">
            <p>Total: {stats.total}</p>
            <p>Growth: {stats.growth}%</p>
        </div>
    )
}
```

```typescript
// components/StatsSkeleton.tsx — Loading placeholder
export default function StatsSkeleton() {
    return (
        <div className="stats-widget stats-widget--skeleton" aria-busy="true">
            <div className="skeleton" style={{ height: 40, width: '60%' }} />
            <div className="skeleton" style={{ height: 24, width: '40%' }} />
        </div>
    )
}
```

### `loading.tsx` — Suspense Boundary Otomatis untuk Halaman

```typescript
// app/dashboard/loading.tsx
// Ini otomatis jadi fallback untuk app/dashboard/page.tsx
// TIDAK perlu wrap manual dengan <Suspense>!

export default function DashboardLoading() {
    return (
        <div className="page-skeleton">
            <div className="skeleton skeleton--title" />
            <div className="skeleton-grid">
                {Array.from({ length: 6 }).map((_, i) => (
                    <div key={i} className="skeleton skeleton--card" />
                ))}
            </div>
        </div>
    )
}
```

---

# 🟩 BAGIAN 4 — API & BACKEND

## 16. Route Handlers — API Endpoints

Route Handlers adalah cara buat API endpoint di Next.js. File `route.ts` di dalam folder `app/api/` (atau di mana saja).

```
app/
└── api/
    ├── users/
    │   ├── route.ts          → GET /api/users, POST /api/users
    │   └── [id]/
    │       └── route.ts      → GET /api/users/123, PUT /api/users/123
    ├── auth/
    │   └── [...nextauth]/
    │       └── route.ts      → Auth.js catch-all
    └── webhook/
        └── route.ts          → POST /api/webhook
```

### Route Handler lengkap dengan semua HTTP method:

```typescript
// app/api/users/route.ts
import { NextRequest, NextResponse } from 'next/server'
import { db } from '@/lib/db'
import { z } from 'zod'

// GET /api/users
export async function GET(request: NextRequest) {
    const { searchParams } = new URL(request.url)
    const page = parseInt(searchParams.get('page') ?? '1')
    const limit = parseInt(searchParams.get('limit') ?? '20')
    const search = searchParams.get('q') ?? ''

    const users = await db.user.findMany({
        where: {
            OR: [
                { nama: { contains: search, mode: 'insensitive' } },
                { email: { contains: search, mode: 'insensitive' } },
            ],
        },
        skip: (page - 1) * limit,
        take: limit,
        select: { id: true, nama: true, email: true, createdAt: true },
        orderBy: { createdAt: 'desc' },
    })

    const total = await db.user.count()

    return NextResponse.json({
        success: true,
        data: users,
        meta: {
            page,
            limit,
            total,
            totalPages: Math.ceil(total / limit),
        },
    })
}

// POST /api/users
const CreateUserSchema = z.object({
    nama: z.string().min(2).max(100),
    email: z.string().email(),
    password: z.string().min(8),
})

export async function POST(request: NextRequest) {
    try {
        const body = await request.json()
        const parsed = CreateUserSchema.safeParse(body)

        if (!parsed.success) {
            return NextResponse.json(
                {
                    success: false,
                    error: 'Validasi gagal',
                    details: parsed.error.flatten(),
                },
                { status: 422 }
            )
        }

        const { nama, email, password } = parsed.data

        // Cek email duplikat
        const existing = await db.user.findUnique({ where: { email } })
        if (existing) {
            return NextResponse.json(
                { success: false, error: 'Email sudah terdaftar' },
                { status: 409 }
            )
        }

        const bcrypt = await import('bcrypt')
        const hashedPassword = await bcrypt.hash(password, 12)

        const user = await db.user.create({
            data: { nama, email, password: hashedPassword },
            select: { id: true, nama: true, email: true, createdAt: true },
        })

        return NextResponse.json(
            { success: true, data: user },
            { status: 201 }
        )
    } catch (error) {
        console.error('POST /api/users error:', error)
        return NextResponse.json(
            { success: false, error: 'Internal server error' },
            { status: 500 }
        )
    }
}
```

```typescript
// app/api/users/[id]/route.ts
import { NextRequest, NextResponse } from 'next/server'
import { db } from '@/lib/db'

// GET /api/users/:id
export async function GET(
    request: NextRequest,
    { params }: { params: Promise<{ id: string }> }
) {
    const { id } = await params

    const user = await db.user.findUnique({
        where: { id },
        select: { id: true, nama: true, email: true },
    })

    if (!user) {
        return NextResponse.json(
            { success: false, error: 'User tidak ditemukan' },
            { status: 404 }
        )
    }

    return NextResponse.json({ success: true, data: user })
}

// PATCH /api/users/:id
export async function PATCH(
    request: NextRequest,
    { params }: { params: Promise<{ id: string }> }
) {
    const { id } = await params
    const body = await request.json()

    const user = await db.user.update({
        where: { id },
        data: { nama: body.nama },
        select: { id: true, nama: true, email: true },
    })

    return NextResponse.json({ success: true, data: user })
}

// DELETE /api/users/:id
export async function DELETE(
    request: NextRequest,
    { params }: { params: Promise<{ id: string }> }
) {
    const { id } = await params

    await db.user.delete({ where: { id } })

    return new NextResponse(null, { status: 204 })
}
```

### Response dengan headers kustom:

```typescript
return NextResponse.json(
    { data: result },
    {
        status: 200,
        headers: {
            'Cache-Control': 'public, s-maxage=3600, stale-while-revalidate=86400',
            'X-Request-Id': crypto.randomUUID(),
        },
    }
)
```

### Webhook handler:

```typescript
// app/api/webhook/stripe/route.ts
import { NextRequest, NextResponse } from 'next/server'
import Stripe from 'stripe'

const stripe = new Stripe(process.env.STRIPE_SECRET_KEY!)

export async function POST(request: NextRequest) {
    const body = await request.text()  // raw text untuk verifikasi
    const signature = request.headers.get('stripe-signature')!

    let event: Stripe.Event

    try {
        event = stripe.webhooks.constructEvent(
            body,
            signature,
            process.env.STRIPE_WEBHOOK_SECRET!
        )
    } catch (err) {
        console.error('Webhook signature verification failed:', err)
        return NextResponse.json(
            { error: 'Invalid signature' },
            { status: 400 }
        )
    }

    switch (event.type) {
        case 'checkout.session.completed':
            const session = event.data.object as Stripe.Checkout.Session
            await handlePaymentSuccess(session)
            break

        case 'invoice.payment_failed':
            await handlePaymentFailed(event.data.object as Stripe.Invoice)
            break
    }

    return NextResponse.json({ received: true })
}
```

---

## 17. proxy.ts — Pengganti middleware.ts

Di Next.js 16, `middleware.ts` digantikan oleh `proxy.ts`. Middleware lama deprecated.

**Perbedaan utama:**
- `proxy.ts` jalan di **Node.js runtime** (bukan Edge Runtime)
- `proxy.ts` tidak bisa mengembalikan response body (hanya redirect, rewrite, header)
- Untuk response body → gunakan Route Handler

```typescript
// proxy.ts (di root project, bukan di dalam app/)
import { NextRequest, NextResponse } from 'next/server'

export default function proxy(request: NextRequest) {
    const { pathname } = new URL(request.url)

    // ── Auth check — redirect ke login kalau belum auth ──
    const token = request.cookies.get('session-token')?.value
    const isAuthPage = pathname.startsWith('/login') ||
                       pathname.startsWith('/daftar')
    const isProtectedPage = pathname.startsWith('/dashboard') ||
                            pathname.startsWith('/profil') ||
                            pathname.startsWith('/admin')

    if (isProtectedPage && !token) {
        const loginUrl = new URL('/login', request.url)
        loginUrl.searchParams.set('callbackUrl', pathname)
        return NextResponse.redirect(loginUrl)
    }

    if (isAuthPage && token) {
        return NextResponse.redirect(new URL('/dashboard', request.url))
    }

    // ── Locale detection ──
    const acceptLanguage = request.headers.get('accept-language') ?? ''
    if (pathname === '/' && acceptLanguage.includes('en')) {
        return NextResponse.redirect(new URL('/en', request.url))
    }

    // ── Rate limiting header (actual logic di Route Handler) ──
    const response = NextResponse.next()
    response.headers.set('X-Request-Id', crypto.randomUUID())
    return response
}

// Tentukan path mana yang melewati proxy ini
export const config = {
    matcher: [
        '/((?!_next/static|_next/image|favicon.ico|public/).*)',
    ],
}
```

**Migrasi dari middleware.ts:**
```bash
# Gunakan codemod otomatis
npx @next/codemod@canary upgrade latest

# Atau manual:
# 1. Rename middleware.ts → proxy.ts
# 2. Rename fungsi dari 'middleware' menjadi 'proxy' (atau default export)
# 3. Cek penggunaan Edge Runtime — tidak lagi support di proxy.ts
```

---

## 18. Database Integration — Prisma & Drizzle

### Prisma — ORM dengan Type Safety

**Setup:**
```bash
npm install prisma @prisma/client
npx prisma init
```

**Schema:**
```prisma
// prisma/schema.prisma
datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

generator client {
  provider = "prisma-client-js"
}

model User {
  id        String   @id @default(cuid())
  nama      String
  email     String   @unique
  password  String
  avatar    String?
  role      Role     @default(USER)
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt

  posts     Post[]
  sessions  Session[]

  @@map("users")
}

model Post {
  id          String   @id @default(cuid())
  judul       String
  slug        String   @unique
  konten      String
  diterbitkan Boolean  @default(false)
  authorId    String
  author      User     @relation(fields: [authorId], references: [id], onDelete: Cascade)
  createdAt   DateTime @default(now())
  updatedAt   DateTime @updatedAt

  @@map("posts")
}

enum Role {
  USER
  ADMIN
  MODERATOR
}
```

```bash
# Jalankan migration
npx prisma migrate dev --name init

# Generate Prisma Client
npx prisma generate

# Lihat data di browser (Prisma Studio)
npx prisma studio
```

### Drizzle ORM — Lebih Ringan, SQL-like

```bash
npm install drizzle-orm postgres
npm install -D drizzle-kit
```

```typescript
// lib/schema.ts
import {
    pgTable, text, timestamp, boolean, pgEnum
} from 'drizzle-orm/pg-core'

export const roleEnum = pgEnum('role', ['user', 'admin', 'moderator'])

export const users = pgTable('users', {
    id: text('id').primaryKey().$defaultFn(() => crypto.randomUUID()),
    nama: text('nama').notNull(),
    email: text('email').notNull().unique(),
    password: text('password').notNull(),
    role: roleEnum('role').default('user').notNull(),
    createdAt: timestamp('created_at').defaultNow().notNull(),
})

export const posts = pgTable('posts', {
    id: text('id').primaryKey().$defaultFn(() => crypto.randomUUID()),
    judul: text('judul').notNull(),
    slug: text('slug').notNull().unique(),
    konten: text('konten').notNull(),
    diterbitkan: boolean('diterbitkan').default(false).notNull(),
    authorId: text('author_id').notNull().references(() => users.id, {
        onDelete: 'cascade',
    }),
    createdAt: timestamp('created_at').defaultNow().notNull(),
})

// lib/db.ts
import { drizzle } from 'drizzle-orm/postgres-js'
import postgres from 'postgres'
import * as schema from './schema'

const client = postgres(process.env.DATABASE_URL!)
export const db = drizzle(client, { schema })

// Query example
const userPosts = await db.query.posts.findMany({
    where: eq(posts.authorId, userId),
    with: { author: true },
    orderBy: [desc(posts.createdAt)],
})
```

---

## 19. Authentication — Auth.js & Clerk

### Auth.js v5 (NextAuth) — Open Source

```bash
npm install next-auth@beta
```

```typescript
// auth.ts (di root project)
import NextAuth from 'next-auth'
import Google from 'next-auth/providers/google'
import Credentials from 'next-auth/providers/credentials'
import { PrismaAdapter } from '@auth/prisma-adapter'
import { db } from '@/lib/db'
import bcrypt from 'bcrypt'
import { z } from 'zod'

export const { handlers, auth, signIn, signOut } = NextAuth({
    adapter: PrismaAdapter(db),
    session: { strategy: 'jwt' },

    providers: [
        Google({
            clientId: process.env.GOOGLE_CLIENT_ID!,
            clientSecret: process.env.GOOGLE_CLIENT_SECRET!,
        }),

        Credentials({
            credentials: {
                email: { label: 'Email', type: 'email' },
                password: { label: 'Password', type: 'password' },
            },
            async authorize(credentials) {
                const parsed = z.object({
                    email: z.string().email(),
                    password: z.string().min(8),
                }).safeParse(credentials)

                if (!parsed.success) return null

                const user = await db.user.findUnique({
                    where: { email: parsed.data.email },
                })

                if (!user || !user.password) return null

                const passwordMatch = await bcrypt.compare(
                    parsed.data.password,
                    user.password
                )

                if (!passwordMatch) return null

                return {
                    id: user.id,
                    nama: user.nama,
                    email: user.email,
                    role: user.role,
                }
            },
        }),
    ],

    callbacks: {
        jwt({ token, user }) {
            if (user) {
                token.id = user.id
                token.role = (user as any).role
            }
            return token
        },
        session({ session, token }) {
            session.user.id = token.id as string
            session.user.role = token.role as string
            return session
        },
    },

    pages: {
        signIn: '/login',
        error: '/login',
    },
})
```

```typescript
// app/api/auth/[...nextauth]/route.ts
import { handlers } from '@/auth'
export const { GET, POST } = handlers
```

```typescript
// Cek session di Server Component
import { auth } from '@/auth'
import { redirect } from 'next/navigation'

export default async function DashboardPage() {
    const session = await auth()

    if (!session) redirect('/login')

    return <h1>Halo, {session.user?.name}</h1>
}

// Cek session di Client Component
'use client'
import { useSession } from 'next-auth/react'

export default function UserMenu() {
    const { data: session, status } = useSession()

    if (status === 'loading') return <p>Loading...</p>
    if (!session) return <a href="/login">Login</a>

    return <p>Halo, {session.user?.name}</p>
}
```

---

# 🟦 BAGIAN 5 — OPTIMASI & DEPLOYMENT

## 20. Image, Font & Script Optimization

### `next/image` — Optimasi Gambar Otomatis

```typescript
import Image from 'next/image'

// Local image — ukuran otomatis dari file
import profilePic from '@/public/images/profile.jpg'
<Image src={profilePic} alt="Foto profil" />

// External image — ukuran harus manual
<Image
    src="https://images.unsplash.com/photo-123"
    alt="Foto dari Unsplash"
    width={800}
    height={600}
/>

// Fill mode — gambar mengisi container (seperti background-size: cover)
<div style={{ position: 'relative', height: '400px' }}>
    <Image
        src="/hero.jpg"
        alt="Hero image"
        fill
        style={{ objectFit: 'cover' }}
        priority  // ← preload gambar penting (LCP)
    />
</div>

// Responsive
<Image
    src="/foto.jpg"
    alt="Foto"
    width={1200}
    height={800}
    sizes="(max-width: 768px) 100vw, (max-width: 1200px) 50vw, 33vw"
/>

// Lazy load dengan blur placeholder
<Image
    src="/foto-besar.jpg"
    alt="Foto"
    width={800}
    height={600}
    loading="lazy"        // default
    placeholder="blur"    // tampilkan blur dulu
    blurDataURL="data:image/jpeg;base64,..." // atau otomatis dari local image
/>
```

### `next/font` — Load Font Tanpa Layout Shift

```typescript
// app/layout.tsx
import { DM_Sans, JetBrains_Mono, Bebas_Neue } from 'next/font/google'

const dmSans = DM_Sans({
    subsets: ['latin'],
    weight: ['300', '400', '600', '700'],
    variable: '--font-body',
    display: 'swap',
})

const jetbrainsMono = JetBrains_Mono({
    subsets: ['latin'],
    weight: ['400', '600'],
    variable: '--font-mono',
    display: 'swap',
})

const bebasNeue = Bebas_Neue({
    subsets: ['latin'],
    weight: '400',
    variable: '--font-display',
    display: 'swap',
})

// Gunakan variabel CSS di body
<body className={`
    ${dmSans.variable}
    ${jetbrainsMono.variable}
    ${bebasNeue.variable}
`}>
```

```css
/* globals.css */
body {
    font-family: var(--font-body), Helvetica, sans-serif;
}

h1, h2, h3 {
    font-family: var(--font-display), sans-serif;
}

code, pre {
    font-family: var(--font-mono), 'Courier New', monospace;
}
```

### `next/script` — Load Script Eksternal dengan Benar

```typescript
import Script from 'next/script'

// strategy="afterInteractive" — load setelah halaman interaktif
// Cocok untuk: analytics, chat widget
<Script
    src="https://www.googletagmanager.com/gtag/js?id=GA_ID"
    strategy="afterInteractive"
/>

// strategy="lazyOnload" — load saat browser idle
// Cocok untuk: non-critical scripts
<Script
    src="https://widget.chat.com/embed.js"
    strategy="lazyOnload"
/>

// strategy="beforeInteractive" — load sebelum halaman interaktif
// Hanya untuk script yang SANGAT critical (jarang dipakai)
<Script
    src="/critical-init.js"
    strategy="beforeInteractive"
/>

// Inline script
<Script id="gtag-init" strategy="afterInteractive">
    {`
        window.dataLayer = window.dataLayer || [];
        function gtag(){dataLayer.push(arguments);}
        gtag('js', new Date());
        gtag('config', 'GA_ID');
    `}
</Script>
```

---

## 21. Metadata & SEO

### Static Metadata

```typescript
// app/page.tsx
import type { Metadata } from 'next'

export const metadata: Metadata = {
    title: 'ANERS — AI Platform',
    description: 'Platform AI buatan Rixz untuk developer Indonesia',
    keywords: ['AI', 'developer tools', 'Indonesia'],
    authors: [{ name: 'Rixz', url: 'https://rixz.dev' }],
    creator: 'Rixz',

    // Open Graph (untuk share di sosmed)
    openGraph: {
        type: 'website',
        url: 'https://aners.dev',
        title: 'ANERS Platform',
        description: 'Platform AI untuk developer Indonesia',
        siteName: 'ANERS',
        images: [{
            url: '/og-image.jpg',
            width: 1200,
            height: 630,
            alt: 'ANERS Platform',
        }],
    },

    // Twitter Card
    twitter: {
        card: 'summary_large_image',
        title: 'ANERS Platform',
        description: 'Platform AI untuk developer Indonesia',
        images: ['/og-image.jpg'],
        creator: '@rixz_dev',
    },

    // Robots
    robots: {
        index: true,
        follow: true,
        googleBot: {
            index: true,
            follow: true,
            'max-video-preview': -1,
            'max-image-preview': 'large',
            'max-snippet': -1,
        },
    },

    // Canonical URL
    alternates: {
        canonical: 'https://aners.dev',
    },
}
```

### Dynamic Metadata — Berdasarkan Data

```typescript
// app/artikel/[slug]/page.tsx
import type { Metadata } from 'next'

export async function generateMetadata({
    params,
}: {
    params: Promise<{ slug: string }>
}): Promise<Metadata> {
    const { slug } = await params

    // Fetch data artikel
    const artikel = await db.artikel.findUnique({ where: { slug } })

    if (!artikel) {
        return { title: 'Artikel Tidak Ditemukan' }
    }

    return {
        title: artikel.judul,
        description: artikel.ringkasan,
        openGraph: {
            title: artikel.judul,
            description: artikel.ringkasan,
            images: artikel.gambarUtama ? [artikel.gambarUtama] : [],
            type: 'article',
            publishedTime: artikel.publishedAt.toISOString(),
            authors: [artikel.penulis.nama],
        },
    }
}
```

### Sitemap Otomatis

```typescript
// app/sitemap.ts
import { MetadataRoute } from 'next'
import { db } from '@/lib/db'

export default async function sitemap(): Promise<MetadataRoute.Sitemap> {
    const artikel = await db.artikel.findMany({
        where: { diterbitkan: true },
        select: { slug: true, updatedAt: true },
    })

    const artikelSitemap = artikel.map(a => ({
        url: `https://aners.dev/artikel/${a.slug}`,
        lastModified: a.updatedAt,
        changeFrequency: 'weekly' as const,
        priority: 0.8,
    }))

    return [
        {
            url: 'https://aners.dev',
            lastModified: new Date(),
            changeFrequency: 'daily',
            priority: 1,
        },
        {
            url: 'https://aners.dev/artikel',
            lastModified: new Date(),
            changeFrequency: 'daily',
            priority: 0.9,
        },
        ...artikelSitemap,
    ]
}
```

### robots.txt Otomatis

```typescript
// app/robots.ts
import { MetadataRoute } from 'next'

export default function robots(): MetadataRoute.Robots {
    return {
        rules: [
            {
                userAgent: '*',
                allow: '/',
                disallow: ['/api/', '/admin/', '/dashboard/'],
            },
        ],
        sitemap: 'https://aners.dev/sitemap.xml',
    }
}
```

---

## 22. Environment Variables & Config

### `.env` files — Hierarki dan Prioritas

```bash
# Urutan prioritas (yang paling atas paling tinggi):
.env.local          ← Override lokal (JANGAN commit ke Git!)
.env.development    ← Hanya untuk npm run dev
.env.production     ← Hanya untuk npm run build + start
.env                ← Base, semua environment
```

```bash
# .env.local
DATABASE_URL="postgresql://user:pass@localhost:5432/mydb"
NEXTAUTH_SECRET="rahasia-super-panjang-acak-minimal-32-karakter"
NEXTAUTH_URL="http://localhost:3000"

# API Keys — JANGAN pernah dengan prefix NEXT_PUBLIC_!
STRIPE_SECRET_KEY="sk_test_..."
OPENAI_API_KEY="sk-..."
RESEND_API_KEY="re_..."

# Environment variables yang AMAN di expose ke browser (prefix NEXT_PUBLIC_)
NEXT_PUBLIC_APP_URL="http://localhost:3000"
NEXT_PUBLIC_GA_ID="G-XXXXXXXX"
NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY="pk_test_..."
```

```typescript
// lib/env.ts — Validasi env dengan Zod (sangat direkomendasikan)
import { z } from 'zod'

const ServerEnvSchema = z.object({
    DATABASE_URL: z.string().url(),
    NEXTAUTH_SECRET: z.string().min(32),
    NEXTAUTH_URL: z.string().url(),
    STRIPE_SECRET_KEY: z.string().startsWith('sk_'),
})

const ClientEnvSchema = z.object({
    NEXT_PUBLIC_APP_URL: z.string().url(),
    NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY: z.string().startsWith('pk_'),
})

// Parse dan validasi saat startup
export const serverEnv = ServerEnvSchema.parse(process.env)
export const clientEnv = ClientEnvSchema.parse({
    NEXT_PUBLIC_APP_URL: process.env.NEXT_PUBLIC_APP_URL,
    NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY: process.env.NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY,
})

// Penggunaan (type-safe!)
import { serverEnv } from '@/lib/env'
const db = new Client(serverEnv.DATABASE_URL)
```

---

## 23. Turbopack — Bundler Default 2026

Sejak Next.js 16, **Turbopack** adalah bundler default — bukan Webpack lagi. Ditulis dalam Rust, jauh lebih cepat.

### Angka performa (dari benchmark resmi Vercel):

| Metrik | Webpack | Turbopack | Peningkatan |
|--------|---------|-----------|-------------|
| Fast Refresh | baseline | 5-10x lebih cepat | 500-1000% |
| Build time | baseline | 2-5x lebih cepat | 200-500% |
| Dev startup | baseline | 87% lebih cepat (v16.2) | — |
| Cold start | baseline | Jauh lebih cepat dengan FS cache | — |

### Turbopack File System Caching (stable di 16.1):

```bash
# Aktif by default di Next.js 16.1+
# Artifact compiler disimpan ke disk: .next/cache/turbopack/

# Kalau ada masalah dengan cache, clear:
rm -rf .next/cache/turbopack

# Atau full clear:
rm -rf .next
```

### Konfigurasi Turbopack:

```typescript
// next.config.ts
const nextConfig = {
    turbopack: {
        // Resolve alias
        resolveAlias: {
            // Contoh: mock modul Node.js untuk browser
            'node:fs': './empty.ts',
        },

        // Extend default file extensions
        resolveExtensions: ['.ts', '.tsx', '.js', '.jsx', '.json'],

        // Rules untuk file loader
        rules: {
            '*.svg': {
                loaders: ['@svgr/webpack'],
                as: '*.tsx',
            },
        },
    },
}
```

### Kalau ada masalah dengan Turbopack:

```bash
# Temporarily pakai Webpack (fallback)
next dev --webpack
next build --webpack

# Ini untuk kasus di mana plugin/loaders Webpack tertentu belum
# diport ke Turbopack. Laporkan ke github.com/vercel/next.js
```

---

## 24. Deployment — Vercel, VPS, Docker

### Option 1: Vercel (Termudah)

```bash
# Install Vercel CLI
npm install -g vercel

# Deploy (pertama kali akan tanya setup)
vercel

# Deploy production
vercel --prod

# Tambahkan env variable
vercel env add DATABASE_URL production
```

Atau push ke GitHub → connect di vercel.com → deploy otomatis setiap push.

### Option 2: VPS Ubuntu dengan PM2

```bash
# Di VPS
git clone https://github.com/username/project.git
cd project
npm install --production
npm run build

# Jalankan dengan PM2
npm install -g pm2
pm2 start npm --name "aners-web" -- start
pm2 save
pm2 startup systemd  # biar auto-start setelah reboot
```

### Option 3: Docker

```dockerfile
# Dockerfile
FROM node:20-alpine AS base

# Dependencies stage
FROM base AS deps
RUN apk add --no-cache libc6-compat
WORKDIR /app
COPY package.json package-lock.json ./
RUN npm ci

# Builder stage
FROM base AS builder
WORKDIR /app
COPY --from=deps /app/node_modules ./node_modules
COPY . .

ENV NEXT_TELEMETRY_DISABLED 1
RUN npm run build

# Runner stage (production)
FROM base AS runner
WORKDIR /app

ENV NODE_ENV production
ENV NEXT_TELEMETRY_DISABLED 1

RUN addgroup --system --gid 1001 nodejs
RUN adduser --system --uid 1001 nextjs

COPY --from=builder /app/public ./public

# Copy standalone output
COPY --from=builder --chown=nextjs:nodejs /app/.next/standalone ./
COPY --from=builder --chown=nextjs:nodejs /app/.next/static ./.next/static

USER nextjs
EXPOSE 3000
ENV PORT 3000
ENV HOSTNAME "0.0.0.0"

CMD ["node", "server.js"]
```

```typescript
// next.config.ts — aktifkan standalone output untuk Docker
const nextConfig = {
    output: 'standalone',
}
```

```yaml
# docker-compose.yml
version: '3.8'
services:
    web:
        build: .
        ports:
            - "3000:3000"
        environment:
            - DATABASE_URL=postgresql://postgres:password@db:5432/mydb
            - NEXTAUTH_SECRET=rahasia-super-panjang
            - NEXTAUTH_URL=https://domain.com
        depends_on:
            - db
        restart: unless-stopped

    db:
        image: postgres:16-alpine
        environment:
            POSTGRES_DB: mydb
            POSTGRES_USER: postgres
            POSTGRES_PASSWORD: password
        volumes:
            - postgres_data:/var/lib/postgresql/data
        restart: unless-stopped

volumes:
    postgres_data:
```

```bash
# Build dan jalankan
docker compose up -d

# Lihat log
docker compose logs -f web

# Rebuild setelah perubahan
docker compose up -d --build
```

---

# 🟪 BAGIAN 6 — DEBUG & BEST PRACTICE

## 25. Debugging — Cara Analisa Bug Next.js

Ini bagian yang paling sering dilewati orang — padahal ini yang paling menentukan seberapa cepat lo bisa solve masalah.

### Level 1: Error Message & Stack Trace

```
Saat ada error, langkah pertama: BACA error message-nya dengan teliti.

Next.js 16.2 sekarang tampilkan Error.cause chain sampai 5 level.
Artinya lo bisa lihat "root cause" dari error yang wrapped.

Contoh error chain:
  Error: Gagal load user profile
    caused by: ApiError: 401 Unauthorized
      caused by: FetchError: network timeout
```

**Tipe error umum di Next.js dan artinya:**

```
"Hydration failed because the server rendered HTML didn't match the client"
→ Server render konten berbeda dari client
→ Cek: conditional rendering berdasarkan waktu/random/window object
→ Solusi: pakai suppressHydrationWarning, atau pindahkan ke client component

"Cannot access X before initialization"
→ Circular import atau variabel belum diinit
→ Cek: urutan import di file lo

"Error: async/await is not yet supported in Client Components"
→ Lo bikin Client Component tapi pakai async function di komponen
→ Solusi: pindahkan async ke fungsi terpisah, pakai useEffect

"NEXT_REDIRECT" / "NEXT_NOT_FOUND"
→ Ini bukan error! Ini mekanisme Next.js untuk redirect() dan notFound()
→ Jangan tangkap dengan try/catch di luar

"TypeError: Cannot read properties of undefined (reading 'map')"
→ Data belum ada ketika komponen render
→ Solusi: null check, optional chaining, atau loading state
```

### Level 2: `next dev --inspect` (Node.js Debugger)

Fitur baru di Next.js 16.1 — attach debugger langsung:

```bash
# Development
next dev --inspect

# Atau tambahkan ke package.json:
"scripts": {
    "dev:debug": "next dev --inspect",
    "start:debug": "next start --inspect"  // next 16.2+
}
```

Setelah `next dev --inspect`:
1. Buka Chrome → `chrome://inspect`
2. Klik "Open dedicated DevTools for Node"
3. Set breakpoint di kode server-side lo
4. Buka halaman yang mau didebug
5. Debugger pause di breakpoint!

```typescript
// Tambahkan debugger statement kalau perlu
export default async function MyPage() {
    const data = await fetchData()
    debugger  // ← pause di sini saat debugger aktif
    return <div>{data.nama}</div>
}
```

### Level 3: Console Logging yang Strategis

```typescript
// Di Server Component — log tampil di TERMINAL, bukan browser console
export default async function DataPage() {
    console.log('[DataPage] Mulai fetch...')

    const data = await fetchData()
    console.log('[DataPage] Data berhasil:', {
        count: data.length,
        firstItem: data[0],
    })

    return <div>...</div>
}

// Di Client Component — log tampil di BROWSER console
'use client'
export default function ClientComp({ data }: { data: any }) {
    console.log('[ClientComp] Props diterima:', data)
    // ...
}
```

**Browser Log Forwarding (Next.js 16.2):**
```bash
# Error browser sekarang di-forward ke terminal!
# Berguna untuk AI agent debugging dan saat remote debugging
npm run dev
# Error yang terjadi di browser akan tampil di terminal lo
```

### Level 4: Next.js DevTools MCP

Fitur debugging dengan AI. Setup di `.cursor/mcp.json` atau config MCP editor lo:

```json
{
    "mcpServers": {
        "next-devtools": {
            "command": "npx",
            "args": ["-y", "next-devtools-mcp@latest"]
        }
    }
}
```

Setelah dev server jalan (`npm run dev`), AI bisa jawab pertanyaan seperti:
- "Kenapa halaman /dashboard lambat?"
- "Route mana yang paling sering error?"
- "Komponen mana yang hydration mismatch?"

### Level 5: Analisis Bundle Size

```bash
# Bundle analyzer (experimental di Next.js 16.1)
ANALYZE=true npm run build
# Buka .next/analyze/client.html dan server.html

# Atau install terpisah:
npm install @next/bundle-analyzer
```

```typescript
// next.config.ts
const withBundleAnalyzer = require('@next/bundle-analyzer')({
    enabled: process.env.ANALYZE === 'true',
})

module.exports = withBundleAnalyzer({
    // config lain
})
```

### Level 6: Performance Debugging

```typescript
// Ukur waktu fetch data
export default async function SlowPage() {
    console.time('[SlowPage] fetchData')
    const data = await fetchData()
    console.timeEnd('[SlowPage] fetchData')  // "[SlowPage] fetchData: 523ms"

    return <div>...</div>
}

// Cek apakah fetch di-cache atau tidak
const res = await fetch('https://api.example.com/data')
// Di terminal akan tampil:
// GET /api/data 200 in 523ms     ← miss cache, fetch dari network
// GET /api/data 200 in 2ms       ← hit cache
```

### Checklist Debugging — Langkah-Langkah

```
1. BACA error message-nya lengkap (jangan skip!)
2. Cek apakah error di Server atau Client
   - Di terminal → Server Component
   - Di browser console → Client Component
3. Cek stack trace — cari baris di kode lo (bukan di node_modules)
4. Isolasi masalah — reduce ke contoh terkecil yang reproduksi error
5. Cek apakah terjadi hanya di dev atau juga di production
   (next dev vs next build && next start)
6. Cek environment variables sudah benar
7. Cek apakah bisa direproduksi setelah hapus .next/cache
8. Google exact error message lo — biasanya sudah ada solusi di GitHub Issues
9. Buka next.js GitHub Issues/Discussions untuk bug yang tidak umum
```

### Error umum dan solusinya:

```typescript
// ─── ERROR 1: Hydration Mismatch ───
// Error: Hydration failed because server rendered HTML didn't match client

// Penyebab: random/Date/window dipakai saat render server
const id = Math.random()  // ← berbeda di server dan client!

// Solusi 1: pindah ke Client Component dengan useEffect
'use client'
import { useEffect, useState } from 'react'
function MyComp() {
    const [id, setId] = useState<string | null>(null)
    useEffect(() => setId(Math.random().toString()), [])
    if (!id) return null
    return <div>{id}</div>
}

// Solusi 2: suppressHydrationWarning (untuk konten yang memang berbeda)
<div suppressHydrationWarning>
    {new Date().toLocaleString()}
</div>


// ─── ERROR 2: redirect() tertangkap try/catch ───
// NEXT_REDIRECT tidak dianggap error, tapi jadi exception internal

// ❌ SALAH
try {
    const user = await getUser()
    if (!user) redirect('/login')  // ← ini throw exception internal!
} catch (error) {
    console.error(error)  // ← menangkap NEXT_REDIRECT! Jangan!
}

// ✅ BENAR — cek kondisi dulu, redirect di luar try/catch
const user = await getUser()
if (!user) redirect('/login')

try {
    // logika lain yang bisa error
} catch (error) {
    console.error(error)
}


// ─── ERROR 3: "use server" di Client Component ───
'use client'

// ❌ SALAH
async function handleSubmit() {
    'use server'  // ← tidak bisa di dalam client component function!
    await saveData()
}

// ✅ BENAR — definisikan di file terpisah
// actions/data.ts
'use server'
export async function saveData() { ... }

// Di client component:
import { saveData } from '@/actions/data'
async function handleSubmit() {
    await saveData()
}


// ─── ERROR 4: Data stale / tidak update ───
// Lupa revalidate setelah mutasi data

// ❌ SALAH — data tidak update setelah simpan
async function simpanArtikel(data: ArtikelData) {
    'use server'
    await db.artikel.create({ data })
    // ← tidak ada revalidate!
}

// ✅ BENAR
import { revalidatePath, revalidateTag } from 'next/cache'
async function simpanArtikel(data: ArtikelData) {
    'use server'
    await db.artikel.create({ data })
    revalidatePath('/artikel')           // revalidate halaman /artikel
    revalidateTag('artikel-list')        // revalidate semua yang pakai tag ini
}
```

---

## 26. Error Handling — Graceful & Informatif

### Hierarki error handling di Next.js:

```
global-error.tsx      ← menangkap error di root layout
    ↑ fallback untuk
error.tsx di app/     ← menangkap error di app/page.tsx
    ↑ fallback untuk
error.tsx di subfolder ← menangkap error di halaman tersebut
    ↑ fallback untuk
try/catch di komponen ← handling lokal
```

### `error.tsx` yang informatif:

```typescript
// app/dashboard/error.tsx
'use client'

import { useEffect } from 'react'
import Link from 'next/link'

interface ErrorProps {
    error: Error & { digest?: string }
    reset: () => void
}

export default function DashboardError({ error, reset }: ErrorProps) {
    useEffect(() => {
        // Log ke Sentry atau error monitoring
        if (typeof window !== 'undefined') {
            console.error('Dashboard error:', {
                message: error.message,
                digest: error.digest,
                stack: error.stack,
            })
            // Sentry.captureException(error)
        }
    }, [error])

    return (
        <div className="error-container">
            <h2>Ada yang tidak beres</h2>

            {process.env.NODE_ENV === 'development' && (
                <details>
                    <summary>Detail error (development only)</summary>
                    <pre>{error.message}</pre>
                    <pre>{error.stack}</pre>
                </details>
            )}

            {error.digest && (
                <p className="error-id">
                    Error ID: <code>{error.digest}</code>
                    <br />
                    <small>Sertakan ID ini jika menghubungi support.</small>
                </p>
            )}

            <div className="error-actions">
                <button onClick={reset}>Coba Lagi</button>
                <Link href="/dashboard">Kembali ke Dashboard</Link>
            </div>
        </div>
    )
}
```

### `global-error.tsx` — Safety net terakhir:

```typescript
// app/global-error.tsx
// Ini menangkap error di root layout — sangat jarang terjadi
// Harus render html dan body sendiri!

'use client'

export default function GlobalError({
    error,
    reset,
}: {
    error: Error & { digest?: string }
    reset: () => void
}) {
    return (
        <html lang="id">
            <body>
                <div className="critical-error">
                    <h1>Terjadi Kesalahan Kritis</h1>
                    <p>Aplikasi mengalami error yang tidak terduga.</p>
                    <button onClick={reset}>Reload</button>
                </div>
            </body>
        </html>
    )
}
```

### Custom error classes:

```typescript
// lib/errors.ts
export class AppError extends Error {
    constructor(
        message: string,
        public code: string,
        public statusCode: number = 500,
        public details?: unknown
    ) {
        super(message)
        this.name = 'AppError'
    }
}

export class ValidationError extends AppError {
    constructor(message: string, details?: unknown) {
        super(message, 'VALIDATION_ERROR', 422, details)
        this.name = 'ValidationError'
    }
}

export class NotFoundError extends AppError {
    constructor(resource: string) {
        super(`${resource} tidak ditemukan`, 'NOT_FOUND', 404)
        this.name = 'NotFoundError'
    }
}

export class UnauthorizedError extends AppError {
    constructor(message = 'Tidak terautentikasi') {
        super(message, 'UNAUTHORIZED', 401)
        this.name = 'UnauthorizedError'
    }
}

export class ForbiddenError extends AppError {
    constructor(message = 'Tidak punya akses') {
        super(message, 'FORBIDDEN', 403)
        this.name = 'ForbiddenError'
    }
}
```

```typescript
// Gunakan di Route Handler
import { AppError, NotFoundError, ValidationError } from '@/lib/errors'
import { notFound } from 'next/navigation'

export async function GET(
    req: NextRequest,
    { params }: { params: Promise<{ id: string }> }
) {
    try {
        const { id } = await params
        const data = await getData(id)

        if (!data) throw new NotFoundError('Item')

        return NextResponse.json({ success: true, data })

    } catch (error) {
        if (error instanceof AppError) {
            return NextResponse.json(
                {
                    success: false,
                    error: error.message,
                    code: error.code,
                    details: error.details,
                },
                { status: error.statusCode }
            )
        }

        // Unknown error
        console.error('Unhandled error:', error)
        return NextResponse.json(
            { success: false, error: 'Internal server error' },
            { status: 500 }
        )
    }
}
```

---

## 27. Security — Hal yang Wajib Lo Tahu

### Input Validation — Jangan Percaya Input User

```typescript
// SELALU validasi input di server — walaupun ada validasi di client
'use server'

import { z } from 'zod'

const Schema = z.object({
    nama: z.string()
        .min(2, 'Minimal 2 karakter')
        .max(100, 'Maksimal 100 karakter')
        .regex(/^[a-zA-Z\s]+$/, 'Hanya huruf dan spasi'),

    email: z.string()
        .email('Format email tidak valid')
        .toLowerCase(),

    pesan: z.string()
        .min(10, 'Pesan minimal 10 karakter')
        .max(2000, 'Pesan maksimal 2000 karakter'),
})

export async function kirimPesan(formData: FormData) {
    const result = Schema.safeParse({
        nama: formData.get('nama'),
        email: formData.get('email'),
        pesan: formData.get('pesan'),
    })

    if (!result.success) {
        return { error: result.error.flatten().fieldErrors }
    }

    // Aman untuk diproses
    const { nama, email, pesan } = result.data
    await db.pesan.create({ data: { nama, email, pesan } })
}
```

### Server-Only Code — Jangan Expose ke Browser

```typescript
// lib/db.ts
import 'server-only'  // ← akan error jika diimport di Client Component!

import { PrismaClient } from '@prisma/client'
export const db = new PrismaClient()

// Penggunaan: kalau ada yang tidak sengaja import db.ts di client component,
// Next.js akan throw error saat build time — bukan runtime
```

### Environment Variables — Jaga Secret

```typescript
// ❌ JANGAN expose secret ke browser
const secret = process.env.DATABASE_URL  // OK di server
// tapi JANGAN pakai dengan prefix NEXT_PUBLIC_!

// ❌ JANGAN ini:
const secret = process.env.NEXT_PUBLIC_DATABASE_URL  // BAHAYA! Exposed ke browser!

// ✅ Aman: prefix NEXT_PUBLIC_ hanya untuk yang memang public
const publicUrl = process.env.NEXT_PUBLIC_APP_URL  // OK, memang public
```

### SQL Injection — Pakai Parameterized Query

```typescript
// ❌ SANGAT BERBAHAYA — SQL injection!
const userId = req.query.id  // bisa dimanipulasi user
const user = await db.$queryRaw`
    SELECT * FROM users WHERE id = ${userId}
`  // ← ini aman karena Prisma auto-parameterize

// Tapi kalau pakai raw query tanpa parameterize:
const users = await db.$queryRawUnsafe(
    `SELECT * FROM users WHERE id = '${userId}'`  // ❌ VULNERABLE!
)

// ✅ Selalu pakai ORM atau parameterized query
const user = await db.user.findUnique({ where: { id: userId } })  // ✅ aman
const user = await db.$queryRaw`SELECT * FROM users WHERE id = ${userId}`  // ✅ aman
```

### CSRF Protection

```typescript
// Server Actions sudah punya CSRF protection bawaan Next.js.
// Tapi untuk Route Handlers yang menerima mutasi, tambahkan check:

import { headers } from 'next/headers'

export async function POST(request: NextRequest) {
    const headersList = await headers()
    const origin = headersList.get('origin')
    const host = headersList.get('host')

    // Verifikasi origin
    if (origin && !origin.includes(host ?? '')) {
        return NextResponse.json(
            { error: 'CSRF check failed' },
            { status: 403 }
        )
    }

    // Lanjutkan proses...
}
```

### Rate Limiting

```typescript
// lib/rateLimit.ts
// Gunakan Upstash Redis untuk rate limiting di production

import { Ratelimit } from '@upstash/ratelimit'
import { Redis } from '@upstash/redis'

const ratelimit = new Ratelimit({
    redis: Redis.fromEnv(),
    limiter: Ratelimit.slidingWindow(10, '10 s'),  // 10 request per 10 detik
})

// Di Route Handler:
export async function POST(request: NextRequest) {
    const ip = request.headers.get('x-forwarded-for') ?? 'anonymous'
    const { success, limit, remaining } = await ratelimit.limit(ip)

    if (!success) {
        return NextResponse.json(
            { error: 'Too many requests' },
            {
                status: 429,
                headers: {
                    'X-RateLimit-Limit': limit.toString(),
                    'X-RateLimit-Remaining': remaining.toString(),
                    'Retry-After': '10',
                },
            }
        )
    }

    // Lanjutkan...
}
```

---

## 28. Best Practice & Anti-Pattern

### ✅ Yang Harus Dilakukan:

```typescript
// 1. Maksimalkan Server Components
// Kalau komponen tidak butuh state/event/browser API → Server Component!
// Rule of thumb: 'use client' hanya kalau benar-benar butuh

// 2. Fetch data sedekat mungkin dengan yang butuh
// ❌ Fetch di root, pass down via props (prop drilling)
async function RootPage() {
    const data = await fetchAllData()  // ambil semua di root
    return <ChildComponent data={data} />  // drilling props
}

// ✅ Fetch di komponen yang butuh
async function ChildComponent() {
    const data = await fetchData()  // fetch langsung di sini
    return <div>{data.nama}</div>
}

// 3. Pakai TypeScript secara ketat
// tsconfig.json
{
    "compilerOptions": {
        "strict": true,           // aktifkan semua strict checks
        "noUncheckedIndexedAccess": true,  // array access bisa undefined
        "noImplicitAny": true,
    }
}

// 4. Pakai Zod untuk validasi semua boundary
// Form input, API response, env variables — semua harus divalidasi

// 5. Optimasi gambar selalu pakai next/image
import Image from 'next/image'
// JANGAN pakai <img> langsung untuk user-generated content

// 6. Lazy load komponen yang berat
import dynamic from 'next/dynamic'
const BeratComponent = dynamic(() => import('@/components/BeratComponent'), {
    loading: () => <p>Loading...</p>,
    ssr: false,  // kalau tidak butuh SSR
})

// 7. Pakai generateStaticParams untuk halaman yang data-nya jarang berubah
export async function generateStaticParams() {
    const posts = await db.post.findMany({ where: { published: true } })
    return posts.map(p => ({ slug: p.slug }))
}
// Halaman di-generate saat build → super cepat, tidak ada DB call saat request
```

### ❌ Anti-Pattern yang Harus Dihindari:

```typescript
// ──────────────────────────────────────────
// ❌ Anti-pattern 1: 'use client' terlalu banyak
// ──────────────────────────────────────────
// JANGAN jadikan semua komponen client component hanya karena
// satu bagian kecil butuh interaktivitas

// ❌ SALAH — seluruh halaman jadi client karena satu tombol
'use client'
export default function ProductPage({ product }) {
    const [liked, setLiked] = useState(false)
    return (
        <div>
            <h1>{product.nama}</h1>       {/* ← tidak butuh client! */}
            <p>{product.deskripsi}</p>    {/* ← tidak butuh client! */}
            <button onClick={() => setLiked(!liked)}>
                {liked ? '❤️' : '🤍'}
            </button>
        </div>
    )
}

// ✅ BENAR — pisahkan bagian interaktif ke komponen kecil
// app/produk/[id]/page.tsx — Server Component
export default async function ProductPage({ params }) {
    const { id } = await params
    const product = await db.produk.findUnique({ where: { id } })
    return (
        <div>
            <h1>{product.nama}</h1>
            <p>{product.deskripsi}</p>
            <LikeButton productId={id} />  {/* ← hanya ini yang client */}
        </div>
    )
}

// components/LikeButton.tsx — Client Component kecil
'use client'
export default function LikeButton({ productId }: { productId: string }) {
    const [liked, setLiked] = useState(false)
    return (
        <button onClick={() => setLiked(!liked)}>
            {liked ? '❤️' : '🤍'}
        </button>
    )
}


// ──────────────────────────────────────────
// ❌ Anti-pattern 2: Fetch berulang untuk data yang sama
// ──────────────────────────────────────────
// Next.js auto-deduplicate fetch yang sama dalam satu request,
// tapi kalau pakai ORM langsung — tidak ada dedup otomatis

// ❌ BURUK — query user dua kali dalam satu request
async function getUser(id: string) {
    return db.user.findUnique({ where: { id } })  // query 1
}
async function checkUserAdmin(id: string) {
    const user = await db.user.findUnique({ where: { id } })  // query 2 (sama!)
    return user?.role === 'ADMIN'
}

// ✅ BAIK — pakai React.cache untuk memoize per request
import { cache } from 'react'

const getUser = cache(async (id: string) => {
    return db.user.findUnique({ where: { id } })
})

// Panggil berkali-kali → hanya DB query sekali per request
const user1 = await getUser('123')
const user2 = await getUser('123')  // ← dari cache, tidak DB lagi


// ──────────────────────────────────────────
// ❌ Anti-pattern 3: Tidak pakai loading state
// ──────────────────────────────────────────
// ❌ User stare ke layar kosong saat data loading

// ✅ Selalu ada loading state — bisa via loading.tsx atau Suspense


// ──────────────────────────────────────────
// ❌ Anti-pattern 4: Simpan secret di client
// ──────────────────────────────────────────
// ❌ FATAL — API key exposed ke browser!
const NEXT_PUBLIC_OPENAI_KEY = process.env.NEXT_PUBLIC_OPENAI_KEY

// ✅ Panggil AI dari Server Action atau Route Handler
// Kunci tetap aman di server


// ──────────────────────────────────────────
// ❌ Anti-pattern 5: Tidak handle error
// ──────────────────────────────────────────
// ❌ Kalau fetch gagal → app crash tanpa pesan jelas
const data = await fetch('/api/data').then(r => r.json())

// ✅ Selalu handle kemungkinan error
const res = await fetch('/api/data')
if (!res.ok) throw new Error(`Fetch gagal: ${res.status}`)
const data = await res.json()
```

### TypeScript Tips untuk Next.js:

```typescript
// types/next.d.ts — extend tipe Next.js
import 'next'
import 'next-auth'

declare module 'next-auth' {
    interface Session {
        user: {
            id: string
            role: 'user' | 'admin' | 'moderator'
        } & DefaultSession['user']
    }
}

// Tipe yang berguna
type PageProps<T extends Record<string, string> = {}> = {
    params: Promise<T>
    searchParams: Promise<Record<string, string | string[] | undefined>>
}

// Penggunaan:
export default async function BlogPost({
    params,
    searchParams,
}: PageProps<{ slug: string }>) {
    const { slug } = await params
    // ...
}
```

---

## 29. Mini Projects — Latihan Nyata

### 🎯 Project 1: Blog dengan Next.js 16

Project lengkap — landing page, list artikel, detail artikel, dan API sederhana.

**Struktur:**
```
app/
├── layout.tsx
├── page.tsx                  → Homepage
├── artikel/
│   ├── page.tsx              → List artikel
│   └── [slug]/
│       ├── page.tsx          → Detail artikel
│       └── loading.tsx
├── api/
│   └── artikel/
│       └── route.ts          → GET /api/artikel
└── globals.css
```

```typescript
// app/layout.tsx
import type { Metadata } from 'next'
import { DM_Sans, Bebas_Neue, JetBrains_Mono } from 'next/font/google'
import Link from 'next/link'
import './globals.css'

const dmSans = DM_Sans({
    subsets: ['latin'],
    weight: ['300', '400', '600'],
    variable: '--font-body',
    display: 'swap',
})
const bebasNeue = Bebas_Neue({
    subsets: ['latin'],
    weight: '400',
    variable: '--font-display',
    display: 'swap',
})
const jetbrainsMono = JetBrains_Mono({
    subsets: ['latin'],
    weight: '400',
    variable: '--font-mono',
    display: 'swap',
})

export const metadata: Metadata = {
    title: { default: 'ANERS Blog', template: '%s | ANERS Blog' },
    description: 'Artikel tentang web dev, AI, dan security',
    metadataBase: new URL('https://blog.aners.dev'),
}

export default function RootLayout({ children }: { children: React.ReactNode }) {
    return (
        <html lang="id" className={`${dmSans.variable} ${bebasNeue.variable} ${jetbrainsMono.variable}`}>
            <body>
                <header className="navbar">
                    <Link href="/" className="navbar__logo">ANERS BLOG</Link>
                    <nav>
                        <Link href="/artikel">Artikel</Link>
                        <Link href="https://github.com/rixz-dev"
                              target="_blank"
                              rel="noopener noreferrer">
                            GitHub
                        </Link>
                    </nav>
                </header>
                {children}
                <footer className="footer">
                    <p>© 2026 ANERS — Riz-dev × Claude Sonnet 4.6</p>
                </footer>
            </body>
        </html>
    )
}
```

```typescript
// lib/artikel.ts
// Data mock — ganti dengan Prisma/database di production

export interface Artikel {
    id: string
    slug: string
    judul: string
    ringkasan: string
    konten: string
    penulis: string
    tanggal: string
    tags: string[]
    bacaanMenit: number
}

export const artikelData: Artikel[] = [
    {
        id: '1',
        slug: 'belajar-nextjs-16',
        judul: 'Belajar Next.js 16 — Panduan Lengkap 2026',
        ringkasan: 'Next.js 16 bawa perubahan besar: Turbopack default, caching eksplisit, dan proxy.ts. Ini panduan lengkapnya.',
        konten: `# Belajar Next.js 16

Next.js 16 dirilis Oktober 2025 dan bawa banyak perubahan...

## Turbopack Sekarang Default

Build 2-5x lebih cepat dari Webpack...

## Cache Components

Model caching baru yang lebih eksplisit...`,
        penulis: 'Rixz',
        tanggal: '2026-03-15',
        tags: ['Next.js', 'Web Dev', 'JavaScript'],
        bacaanMenit: 12,
    },
    {
        id: '2',
        slug: 'server-actions-nextjs',
        judul: 'Server Actions — Mutasi Data Tanpa API Route',
        ringkasan: 'Server Actions bikin form submission jadi jauh lebih simpel. Tidak perlu buat API route terpisah lagi.',
        konten: `# Server Actions

Server Actions adalah fungsi server yang dipanggil dari client...`,
        penulis: 'Rixz',
        tanggal: '2026-02-28',
        tags: ['Next.js', 'Server Actions', 'React'],
        bacaanMenit: 8,
    },
    {
        id: '3',
        slug: 'debugging-nextjs-tips',
        judul: 'Tips Debugging Next.js yang Jarang Diketahui',
        ringkasan: 'Dari --inspect flag sampai DevTools MCP, ini cara debug Next.js yang lebih efektif.',
        konten: `# Tips Debugging Next.js

Debugging Next.js bisa tricky karena ada dua lingkungan: server dan client...`,
        penulis: 'Rixz',
        tanggal: '2026-01-10',
        tags: ['Debugging', 'Next.js', 'DX'],
        bacaanMenit: 6,
    },
]

export function getAllArtikel(): Artikel[] {
    return artikelData.sort(
        (a, b) => new Date(b.tanggal).getTime() - new Date(a.tanggal).getTime()
    )
}

export function getArtikelBySlug(slug: string): Artikel | undefined {
    return artikelData.find(a => a.slug === slug)
}
```

```typescript
// app/page.tsx
import Link from 'next/link'
import { getAllArtikel } from '@/lib/artikel'

export default function HomePage() {
    const artikelTerbaru = getAllArtikel().slice(0, 3)

    return (
        <main>
            {/* Hero */}
            <section className="hero">
                <div className="hero__content">
                    <p className="hero__label">// Riz-dev × Claude Sonnet 4.6</p>
                    <h1 className="hero__title">
                        ANERS
                        <span className="hero__title-accent">BLOG</span>
                    </h1>
                    <p className="hero__desc">
                        Artikel tentang web development, AI, dan security
                        dari developer Indonesia.
                    </p>
                    <Link href="/artikel" className="btn btn--primary">
                        Baca Semua Artikel
                    </Link>
                </div>
            </section>

            {/* Artikel Terbaru */}
            <section className="section">
                <div className="container">
                    <p className="section-label">// terbaru</p>
                    <h2 className="section-title">Artikel Terbaru</h2>
                    <div className="artikel-grid">
                        {artikelTerbaru.map(artikel => (
                            <article key={artikel.id} className="artikel-card">
                                <div className="artikel-card__tags">
                                    {artikel.tags.slice(0, 2).map(tag => (
                                        <span key={tag} className="tag">{tag}</span>
                                    ))}
                                </div>
                                <h3 className="artikel-card__judul">
                                    <Link href={`/artikel/${artikel.slug}`}>
                                        {artikel.judul}
                                    </Link>
                                </h3>
                                <p className="artikel-card__ringkasan">
                                    {artikel.ringkasan}
                                </p>
                                <div className="artikel-card__meta">
                                    <span>{artikel.penulis}</span>
                                    <span>·</span>
                                    <time dateTime={artikel.tanggal}>
                                        {new Date(artikel.tanggal).toLocaleDateString('id-ID', {
                                            day: 'numeric',
                                            month: 'long',
                                            year: 'numeric',
                                        })}
                                    </time>
                                    <span>·</span>
                                    <span>{artikel.bacaanMenit} menit</span>
                                </div>
                            </article>
                        ))}
                    </div>
                </div>
            </section>
        </main>
    )
}
```

```typescript
// app/artikel/page.tsx
import Link from 'next/link'
import { getAllArtikel } from '@/lib/artikel'
import type { Metadata } from 'next'

export const metadata: Metadata = {
    title: 'Semua Artikel',
    description: 'Semua artikel tentang web dev, AI, dan security',
}

export default function ArtikelListPage() {
    const artikel = getAllArtikel()

    return (
        <main className="container">
            <header className="page-header">
                <h1>Semua Artikel</h1>
                <p>{artikel.length} artikel tersedia</p>
            </header>

            <div className="artikel-list">
                {artikel.map(a => (
                    <article key={a.id} className="artikel-list-item">
                        <div className="artikel-list-item__tags">
                            {a.tags.map(tag => (
                                <span key={tag} className="tag">{tag}</span>
                            ))}
                        </div>
                        <h2 className="artikel-list-item__judul">
                            <Link href={`/artikel/${a.slug}`}>{a.judul}</Link>
                        </h2>
                        <p className="artikel-list-item__ringkasan">{a.ringkasan}</p>
                        <div className="artikel-list-item__meta">
                            <span>{a.penulis}</span>
                            <span>·</span>
                            <time dateTime={a.tanggal}>
                                {new Date(a.tanggal).toLocaleDateString('id-ID', {
                                    day: 'numeric', month: 'long', year: 'numeric',
                                })}
                            </time>
                            <span>·</span>
                            <span>{a.bacaanMenit} menit baca</span>
                        </div>
                    </article>
                ))}
            </div>
        </main>
    )
}
```

```typescript
// app/artikel/[slug]/page.tsx
import { getArtikelBySlug, getAllArtikel } from '@/lib/artikel'
import { notFound } from 'next/navigation'
import type { Metadata } from 'next'
import Link from 'next/link'

// Pre-generate semua slug (Static Generation)
export async function generateStaticParams() {
    const artikel = getAllArtikel()
    return artikel.map(a => ({ slug: a.slug }))
}

// Dynamic metadata
export async function generateMetadata({
    params,
}: {
    params: Promise<{ slug: string }>
}): Promise<Metadata> {
    const { slug } = await params
    const artikel = getArtikelBySlug(slug)

    if (!artikel) return { title: 'Artikel Tidak Ditemukan' }

    return {
        title: artikel.judul,
        description: artikel.ringkasan,
        openGraph: {
            title: artikel.judul,
            description: artikel.ringkasan,
            type: 'article',
            publishedTime: artikel.tanggal,
            authors: [artikel.penulis],
        },
    }
}

export default async function ArtikelDetailPage({
    params,
}: {
    params: Promise<{ slug: string }>
}) {
    const { slug } = await params
    const artikel = getArtikelBySlug(slug)

    if (!artikel) notFound()

    return (
        <main className="container artikel-detail">
            <div className="artikel-detail__tags">
                {artikel.tags.map(tag => (
                    <span key={tag} className="tag">{tag}</span>
                ))}
            </div>

            <h1 className="artikel-detail__judul">{artikel.judul}</h1>

            <div className="artikel-detail__meta">
                <span>Oleh {artikel.penulis}</span>
                <span>·</span>
                <time dateTime={artikel.tanggal}>
                    {new Date(artikel.tanggal).toLocaleDateString('id-ID', {
                        day: 'numeric', month: 'long', year: 'numeric',
                    })}
                </time>
                <span>·</span>
                <span>{artikel.bacaanMenit} menit baca</span>
            </div>

            <div className="artikel-detail__konten">
                {/* Di production, render markdown dengan remark/rehype */}
                <pre style={{ whiteSpace: 'pre-wrap' }}>{artikel.konten}</pre>
            </div>

            <div className="artikel-detail__footer">
                <Link href="/artikel" className="btn btn--ghost">
                    ← Kembali ke Artikel
                </Link>
            </div>
        </main>
    )
}
```

```typescript
// app/artikel/[slug]/loading.tsx
export default function ArtikelLoading() {
    return (
        <div className="container artikel-detail">
            <div className="skeleton" style={{ height: 24, width: '30%', marginBottom: 24 }} />
            <div className="skeleton" style={{ height: 56, width: '80%', marginBottom: 16 }} />
            <div className="skeleton" style={{ height: 20, width: '40%', marginBottom: 48 }} />
            {Array.from({ length: 8 }).map((_, i) => (
                <div key={i} className="skeleton"
                     style={{ height: 20, width: `${70 + Math.random() * 30}%`, marginBottom: 12 }} />
            ))}
        </div>
    )
}
```

```typescript
// app/api/artikel/route.ts
import { NextRequest, NextResponse } from 'next/server'
import { getAllArtikel } from '@/lib/artikel'

export async function GET(request: NextRequest) {
    const { searchParams } = new URL(request.url)
    const tag = searchParams.get('tag')
    const limit = parseInt(searchParams.get('limit') ?? '10')

    let artikel = getAllArtikel()

    if (tag) {
        artikel = artikel.filter(a =>
            a.tags.some(t => t.toLowerCase() === tag.toLowerCase())
        )
    }

    return NextResponse.json({
        success: true,
        data: artikel.slice(0, limit),
        total: artikel.length,
    }, {
        headers: {
            'Cache-Control': 'public, s-maxage=3600',
        },
    })
}
```

```css
/* app/globals.css */
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
ul { list-style: none; }
a { color: inherit; text-decoration: none; }
img { display: block; max-width: 100%; }

:root {
    --bg: #070b14;
    --surface: #0f172a;
    --surface-2: #1e293b;
    --border: rgba(148,163,184,0.08);
    --text: #e2e8f0;
    --muted: #64748b;
    --accent: #f59e0b;
    --accent-dim: rgba(245,158,11,0.1);
    --font-body: 'DM Sans', sans-serif;
    --font-display: 'Bebas Neue', sans-serif;
    --font-mono: 'JetBrains Mono', monospace;
}

html { font-size: 16px; scroll-behavior: smooth; }
body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--font-body, sans-serif);
    line-height: 1.6;
    -webkit-font-smoothing: antialiased;
}

/* ── Navbar ── */
.navbar {
    position: sticky; top: 0; z-index: 100;
    display: flex; justify-content: space-between; align-items: center;
    padding: 0 clamp(16px,5vw,64px); height: 60px;
    background: rgba(7,11,20,0.8); backdrop-filter: blur(16px);
    border-bottom: 1px solid var(--border);
}
.navbar__logo {
    font-family: var(--font-display, sans-serif);
    font-size: 1.2rem; letter-spacing: 0.08em; color: var(--accent);
}
.navbar nav { display: flex; gap: 24px; }
.navbar nav a {
    font-family: var(--font-mono, monospace); font-size: 0.78rem;
    color: var(--muted); transition: color 0.15s;
}
.navbar nav a:hover { color: var(--accent); }

/* ── Container & Section ── */
.container { max-width: 860px; margin: 0 auto; padding: 0 clamp(16px,5vw,48px); }
.section { padding: clamp(64px,10vw,120px) clamp(16px,5vw,64px); }
.section-label {
    font-family: var(--font-mono, monospace); font-size: 0.72rem;
    color: var(--accent); letter-spacing: 0.12em; text-transform: uppercase;
    margin-bottom: 12px;
}
.section-title {
    font-family: var(--font-display, sans-serif);
    font-size: clamp(2rem,5vw,3.5rem); margin-bottom: 40px;
}

/* ── Hero ── */
.hero {
    min-height: 90vh; display: flex; align-items: center;
    padding: 0 clamp(16px,5vw,64px);
}
.hero__label {
    font-family: var(--font-mono, monospace); font-size: 0.75rem;
    color: var(--muted); margin-bottom: 20px;
}
.hero__title {
    font-family: var(--font-display, sans-serif);
    font-size: clamp(4rem,12vw,9rem); line-height: 0.88;
    margin-bottom: 20px;
}
.hero__title-accent { display: block; color: var(--accent); }
.hero__desc { color: var(--muted); max-width: 500px; margin-bottom: 32px; font-size: 1.05rem; }

/* ── Buttons ── */
.btn {
    display: inline-flex; align-items: center; gap: 8px;
    padding: 11px 22px; border-radius: 6px;
    font-weight: 600; font-size: 0.875rem; border: none;
    cursor: pointer; transition: all 0.15s ease;
}
.btn--primary { background: var(--accent); color: #000; }
.btn--primary:hover { background: #d97706; transform: translateY(-1px); }
.btn--ghost { background: transparent; color: var(--text); border: 1px solid var(--border); }
.btn--ghost:hover { border-color: rgba(255,255,255,0.2); }

/* ── Tags ── */
.tag {
    display: inline-block; padding: 3px 10px;
    background: var(--accent-dim); color: var(--accent);
    border-radius: 4px; font-family: var(--font-mono, monospace);
    font-size: 0.7rem;
}

/* ── Artikel Grid (Home) ── */
.artikel-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px,1fr));
    gap: 20px;
}
.artikel-card {
    background: var(--surface); border: 1px solid var(--border);
    border-radius: 12px; padding: 24px;
    transition: all 0.2s ease;
}
.artikel-card:hover { border-color: rgba(245,158,11,0.2); transform: translateY(-3px); }
.artikel-card__tags { display: flex; gap: 6px; margin-bottom: 12px; }
.artikel-card__judul { font-size: 1.05rem; font-weight: 700; margin-bottom: 8px; line-height: 1.4; }
.artikel-card__judul a:hover { color: var(--accent); }
.artikel-card__ringkasan { color: var(--muted); font-size: 0.875rem; margin-bottom: 16px; line-height: 1.6; }
.artikel-card__meta { display: flex; gap: 8px; font-size: 0.78rem; color: var(--muted); flex-wrap: wrap; }

/* ── Artikel List ── */
.page-header { padding: 48px 0 32px; border-bottom: 1px solid var(--border); margin-bottom: 40px; }
.page-header h1 { font-family: var(--font-display,sans-serif); font-size: clamp(2rem,5vw,3rem); }
.page-header p { color: var(--muted); margin-top: 8px; }
.artikel-list { display: flex; flex-direction: column; gap: 0; }
.artikel-list-item { padding: 28px 0; border-bottom: 1px solid var(--border); }
.artikel-list-item__tags { display: flex; gap: 6px; margin-bottom: 10px; }
.artikel-list-item__judul { font-size: 1.2rem; font-weight: 700; margin-bottom: 8px; }
.artikel-list-item__judul a:hover { color: var(--accent); }
.artikel-list-item__ringkasan { color: var(--muted); font-size: 0.9rem; margin-bottom: 12px; }
.artikel-list-item__meta { display: flex; gap: 8px; font-size: 0.78rem; color: var(--muted); }

/* ── Artikel Detail ── */
.artikel-detail { padding-block: 48px; }
.artikel-detail__tags { display: flex; gap: 8px; margin-bottom: 20px; }
.artikel-detail__judul {
    font-family: var(--font-display,sans-serif);
    font-size: clamp(2rem,5vw,3.5rem); line-height: 1; margin-bottom: 16px;
}
.artikel-detail__meta { display: flex; gap: 8px; color: var(--muted); font-size: 0.875rem; margin-bottom: 48px; flex-wrap: wrap; }
.artikel-detail__konten {
    line-height: 1.8; color: #cbd5e1; font-size: 1.05rem;
    border-top: 1px solid var(--border); padding-top: 32px;
}
.artikel-detail__konten pre {
    font-family: var(--font-mono,monospace); font-size: 0.9rem; line-height: 1.7;
}
.artikel-detail__footer { margin-top: 48px; padding-top: 32px; border-top: 1px solid var(--border); }

/* ── Skeleton ── */
@keyframes skeleton { 0%{background-position:-200% center} 100%{background-position:200% center} }
.skeleton {
    background: linear-gradient(90deg,#1e293b 25%,#334155 50%,#1e293b 75%);
    background-size: 200% 100%;
    animation: skeleton 1.5s ease-in-out infinite;
    border-radius: 4px;
}

/* ── Footer ── */
.footer {
    text-align: center; padding: 32px;
    border-top: 1px solid var(--border);
    color: var(--muted); font-family: var(--font-mono,monospace); font-size: 0.78rem;
}

/* ── Responsive ── */
@media (max-width: 640px) {
    .navbar nav a:not(:last-child) { display: none; }
    .artikel-grid { grid-template-columns: 1fr; }
}
```

**Cara jalankan:**
```bash
npx create-next-app@latest aners-blog --typescript --app --no-tailwind --no-src-dir
cd aners-blog
# Salin semua file di atas ke lokasi yang sesuai
npm run dev
# Buka: http://localhost:3000
```

---

### 🔌 Project 2: API REST dengan Route Handlers

```typescript
// app/api/v1/produk/route.ts — API publik untuk produk

import { NextRequest, NextResponse } from 'next/server'
import { z } from 'zod'

// Data mock (ganti dengan database di production)
const produkDb = [
    { id: '1', nama: 'Hosting Basic', harga: 25000, stok: 100, kategori: 'hosting' },
    { id: '2', nama: 'Hosting Pro', harga: 75000, stok: 50, kategori: 'hosting' },
    { id: '3', nama: 'Bot Custom', harga: 500000, stok: 10, kategori: 'jasa' },
    { id: '4', nama: 'VPS 1 Core', harga: 50000, stok: 25, kategori: 'vps' },
]

// GET /api/v1/produk?kategori=hosting&sort=harga&limit=10
export async function GET(request: NextRequest) {
    const { searchParams } = new URL(request.url)
    const kategori = searchParams.get('kategori')
    const sort = searchParams.get('sort') as 'harga' | 'nama' | null
    const limit = Math.min(parseInt(searchParams.get('limit') ?? '20'), 100)
    const page = parseInt(searchParams.get('page') ?? '1')

    let hasil = [...produkDb]

    // Filter
    if (kategori) {
        hasil = hasil.filter(p => p.kategori === kategori)
    }

    // Sort
    if (sort === 'harga') {
        hasil.sort((a, b) => a.harga - b.harga)
    } else if (sort === 'nama') {
        hasil.sort((a, b) => a.nama.localeCompare(b.nama))
    }

    // Pagination
    const total = hasil.length
    const totalPages = Math.ceil(total / limit)
    const offset = (page - 1) * limit
    hasil = hasil.slice(offset, offset + limit)

    return NextResponse.json({
        success: true,
        data: hasil,
        meta: { page, limit, total, totalPages },
    }, {
        headers: { 'Cache-Control': 'public, s-maxage=60' },
    })
}

// POST /api/v1/produk (butuh auth di production)
const CreateProdukSchema = z.object({
    nama: z.string().min(3).max(100),
    harga: z.number().int().min(1000),
    stok: z.number().int().min(0),
    kategori: z.enum(['hosting', 'vps', 'jasa', 'domain']),
})

export async function POST(request: NextRequest) {
    // Cek auth token (simplified)
    const authHeader = request.headers.get('authorization')
    if (!authHeader?.startsWith('Bearer ')) {
        return NextResponse.json(
            { success: false, error: 'Unauthorized' },
            { status: 401 }
        )
    }

    try {
        const body = await request.json()
        const parsed = CreateProdukSchema.safeParse(body)

        if (!parsed.success) {
            return NextResponse.json(
                {
                    success: false,
                    error: 'Validasi gagal',
                    details: parsed.error.flatten(),
                },
                { status: 422 }
            )
        }

        // Simpan ke database di production
        const produkBaru = {
            id: crypto.randomUUID(),
            ...parsed.data,
        }
        produkDb.push(produkBaru as any)

        return NextResponse.json(
            { success: true, data: produkBaru },
            { status: 201 }
        )

    } catch {
        return NextResponse.json(
            { success: false, error: 'Internal server error' },
            { status: 500 }
        )
    }
}
```

**Test API dari Termux:**
```bash
# GET semua produk
curl http://localhost:3000/api/v1/produk | python -m json.tool

# GET dengan filter
curl "http://localhost:3000/api/v1/produk?kategori=hosting&sort=harga"

# POST buat produk baru
curl -X POST http://localhost:3000/api/v1/produk \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer token-test" \
  -d '{"nama":"VPS 2 Core","harga":100000,"stok":20,"kategori":"vps"}' \
  | python -m json.tool
```

---

## 🏁 Penutup

Lo udah capai akhir buku ini. Itu bukan hal kecil.

Next.js adalah framework yang luas — tapi lo sekarang punya peta yang jelas: dari routing sampai deployment, dari debugging sampai security.

### Roadmap setelah Next.js:

| Level | Yang Dipelajari | Timeline |
|-------|----------------|----------|
| 🟡 **Dalami** | Prisma/Drizzle lebih dalam, Zod, TanStack Query | 2-3 minggu |
| 🟠 **UI** | Tailwind CSS v4, shadcn/ui, Radix UI | 1-2 minggu |
| 🔴 **Auth** | Auth.js v5 atau Clerk — deploy ke production | 1 minggu |
| 🟣 **Full Project** | Bangun SaaS kecil dari scratch | 1-2 bulan |
| ⬛ **Pro** | Core Web Vitals, OpenTelemetry, load testing | Ongoing |

### Resources penting:

- **nextjs.org/docs** — Dokumentasi resmi, selalu update
- **nextjs.org/blog** — Release notes dan artikel mendalam
- **github.com/vercel/next.js** — Source code, Issues, Discussions
- **github.com/vercel/next.js/discussions** — Tanya jawab komunitas
- **vercel.com/templates** — Project starter templates
- **shadcn.com/docs** — UI components yang populer untuk Next.js
- **orm.drizzle.team** — Drizzle ORM documentation
- **authjs.dev** — Auth.js v5 documentation

### Cara terbaik belajar sekarang:

```
1. Ikutin Project 1 (Blog) dari awal sampai jalan
2. Tambahkan database (Prisma + SQLite buat development)
3. Tambahkan auth dengan Auth.js
4. Deploy ke Vercel (gratis untuk hobby projects)
5. Bangun project kedua yang lo sendiri yang tentukan
```

---

> *"First, solve the problem. Then, write the code."*
>
> **— Riz-dev × Claude Sonnet 4.6**

---

*Riset dari: nextjs.org/blog, github.com/vercel/next.js, endoflife.date/nextjs, Wikipedia Next.js*
*Data versi akurat per Mei 2026 — Next.js 16.2 adalah versi stable terbaru*
*Branding: **Riz-dev × Claude Sonnet 4.6** — AI-Native Engineering & Research Systems*
*Versi: 1.0.0 · Mei 2026*
