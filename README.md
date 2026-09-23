# 🕌 Lentera Hijaiyah

> **Platform Web Interaktif Pembelajaran Huruf Hijaiyah Berbasis AI-Rule & Al-Quran Digital**

[![Framework](https://img.shields.io/badge/Framework-Next.js%2016-black?style=flat&logo=next.js)](https://nextjs.org/)
[![Language](https://img.shields.io/badge/Language-TypeScript-blue?style=flat&logo=typescript)](https://www.typescriptlang.org/)
[![Database](https://img.shields.io/badge/Database-PostgreSQL-336791?style=flat&logo=postgresql)](https://www.postgresql.org/)
[![ORM](https://img.shields.io/badge/ORM-Prisma-2D3748?style=flat&logo=prisma)](https://www.prisma.io/)
[![Styling](https://img.shields.io/badge/Styling-Tailwind%20CSS%20v4-38B2AC?style=flat&logo=tailwind-css)](https://tailwindcss.com/)
[![Runtime](https://img.shields.io/badge/Runtime-Bun%20%7C%20Node.js-fbf0df?style=flat&logo=bun)](https://bun.sh/)
[![Documentation](https://img.shields.io/badge/API%20Docs-Swagger%20UI-85EA2D?style=flat&logo=swagger)](http://localhost:3000/api-docs)

---

## 📌 Deskripsi Proyek

**Lentera Hijaiyah** adalah sistem aplikasi web edukasi modern yang dirancang untuk memfasilitasi pembelajaran huruf Hijaiyah, literasi Al-Quran digital, dan pemahaman materi keislaman secara interaktif. Dibangun menggunakan arsitektur modern Next.js 16 App Router, aplikasi ini menggabungkan antarmuka pengguna yang responsif dengan backend REST API terpadu.

Salah satu inovasi utama dalam platform ini adalah modul **Interactive Hijaiyah Canvas** yang dilengkapi validasi kecerdasan buatan (*AI-Rule assisted stroke similarity scoring*). Modul ini mengevaluasi bentuk goresan tulisan tangan pengguna saat menulis huruf Hijaiyah di kanvas digital secara deterministik dan memberikan umpan balik langsung. Selain itu, sistem menyediakan **Pembaca Al-Quran Digital** yang komprehensif serta **Modul Pembelajaran** terstruktur yang melacak perkembangan belajar setiap pengguna.

---

## ✨ Fitur Utama

### 1. 🔐 Autentikasi & Keamanan Pengguna
* **Sistem Registrasi & Login:** Autentikasi menggunakan Custom JWT yang dipadukan dengan enkripsi kata sandi `bcryptjs` dan validasi skema `Zod`.
* **Edge Middleware Protection:** Perlindungan rute terpusat pada layer Next.js Middleware yang memverifikasi token sesi dan menginjeksi identitas pengguna (`x-user-id`, `x-user-role`) ke header request backend secara aman.
* **Integrasi Google OAuth:** Memungkinkan pengguna masuk dengan akun Google secara praktis melalui pola verifikasi token `google-auth-library`.
* **Pemulihan Akun (Forgot & Reset Password):** Penerbitan token reset aman yang dikirimkan langsung ke email pengguna melalui integrasi SMTP (Brevo).

### 2. ✍️ Interactive Hijaiyah Canvas (AI-Rule Stroke Validation)
* **Kanvas Menulis Digital:** Kanvas interaktif dengan kontrol penuh terhadap goresan, penghapus, pembersihan kanvas, dan pemilihan huruf Hijaiyah (Alif hingga Ya).
* **Evaluasi Bentuk Goresan (AI-Rule Scoring):** Algoritma penilaian deterministik yang menganalisis normalisasi titik koordinat dan vektor goresan pengguna terhadap referensi standar huruf Hijaiyah.
* **Umpan Balik Real-time:** Memberikan skor akurasi dan pesan keberhasilan/koreksi seketika kepada pembelajar.

### 3. 📖 Al-Quran Digital Terintegrasi
* **Navigasi Fleksibel:** Akses seluruh ayat Al-Quran berdasarkan daftar Surah maupun pembagian Juz.
* **Tampilan Teks Arab & Terjemahan:** Tipografi Arab yang jelas dilengkapi transliterasi dan terjemahan bahasa Indonesia.
* **Pelacakan Terakhir Dibaca (Quran Progress):** Penyimpanan otomatis posisi ayat dan surah terakhir yang dibaca pengguna ke basis data.

### 4. 📚 Modul Pembelajaran & Kuis
* **Kategori Materi Terstruktur:** Pembagian materi berdasarkan topik dan tingkat pemahaman.
* **Integrasi Dokumen (PDF Viewer):** Menampilkan modul teks dan buku panduan digital secara langsung di web menggunakan `pdfjs-dist`.
* **Pelacakan Kemajuan Belajar:** Pengguna dapat menandai modul yang telah selesai dibaca (*UserModuleProgress*).

### 5. 📊 Dashboard & Manajemen Profil
* **Ringkasan Aktivitas Belajar:** Statistik progres modul yang telah diselesaikan dan aktivitas bacaan Al-Quran.
* **Pengaturan Akun:** Pembaruan informasi profil dan perubahan kata sandi secara mandiri.

### 6. 🛠️ REST API & Dokumentasi Interaktif
* **Swagger UI:** Dokumentasi antarmuka pengujian API interaktif yang dapat diakses langsung melalui `/api-docs`.
* **Postman Collection:** Koleksi endpoint terstandarisasi untuk kebutuhan pengujian integrasi dan pengembang.

---

## 💻 Tech Stack

| Kategori | Teknologi | Keterangan |
|---|---|---|
| **Framework Utama** | Next.js 16 (App Router) | Full-stack framework dengan React 19 Server & Client Components |
| **Bahasa Pemrograman** | TypeScript 5 | Static typing untuk keandalan dan pemeliharaan kode |
| **Styling & UI** | Tailwind CSS v4 | Utility-first CSS framework dengan kustomisasi font Montserrat Alternates |
| **Database** | PostgreSQL 15 | Sistem basis data relasional untuk integritas data |
| **ORM** | Prisma ORM 7 (`@prisma/client`) | Data modeling, migration, dan query generator |
| **Autentikasi** | Custom JWT (`jose`) & `bcryptjs` | Stateless session management pada Edge Runtime |
| **Third-Party Auth** | `google-auth-library` | Verifikasi ID Token OAuth2 Google |
| **Layanan Email** | `nodemailer` (SMTP Brevo) | Pengiriman email transaksional untuk reset password |
| **Penyimpanan Objek** | AWS SDK S3 / MinIO | Manajemen berkas dan materi modul PDF |
| **Validasi Skema** | Zod | Runtime schema validation untuk payload request API |
| **Dokumentasi API** | `swagger-ui-react` | OpenAPI 3.0 visualization di `/api-docs` |
| **Containerization** | Docker & Docker Compose | Isolasi environment database lokal |

---

## 📂 Struktur Direktori Proyek

```txt
lenterahijaiyah/
├── app/                          # Next.js App Router (Rute & Halaman)
│   ├── (auth)/                   # Halaman terlindungi (memerlukan autentikasi)
│   │   ├── dashboard/            # Halaman utama pengguna terautentikasi
│   │   ├── hijaiyah/             # Halaman modul kanvas Hijaiyah interaktif
│   │   ├── modul/                # Halaman materi & modul pembelajaran
│   │   ├── profile/              # Halaman profil pengguna & ganti sandi
│   │   └── quran/                # Halaman pembaca Al-Quran digital
│   ├── (public)/                 # Halaman publik (dapat diakses siapa saja)
│   │   ├── about/                # Halaman tentang platform
│   │   ├── api-docs/             # Tampilan Swagger UI interaktif
│   │   ├── forgot-password/      # Formulir permohonan reset sandi
│   │   ├── reset-password/       # Formulir konfirmasi sandi baru
│   │   ├── sign-in/              # Formulir masuk pengguna
│   │   ├── sign-up/              # Formulir pendaftaran akun
│   │   └── page.tsx              # Landing page utama
│   └── api/                      # Backend REST API Endpoints
│       ├── v1/auth/              # Endpoint login, register, OAuth, password
│       ├── v1/learning/          # Endpoint modul, kategori, & progress
│       ├── v1/quran/             # Endpoint data surah & progress Al-Quran
│       └── ...                   # Route handlers lainnya
├── components/                   # Komponen React modular & reusable
│   ├── about/                    # Komponen tampilan halaman About
│   ├── dashboard/                # Komponen widget & statistik dashboard
│   ├── landing/                  # Komponen landing page (Hero, Features, CTA)
│   ├── layout/                   # Navbar, Footer, dan Sidebar
│   ├── modul/                    # Komponen modul pembelajaran & pembaca PDF
│   ├── quran/                    # Komponen pembaca Al-Quran & navigasi surah
│   └── ui/                       # Komponen antarmuka atomik (Button, Modal, Input)
├── data/                         # Sumber data statis & data referensi
├── database/                     # Konfigurasi data & skrip pendukung basis data
├── docs/                         # Dokumentasi teknis pengembang (Postman, Setup, Auth)
├── lib/                          # Utility & layer logika aplikasi
│   ├── auth/                     # Helper autentikasi & JWT token management
│   ├── config/                   # Validasi variabel lingkungan (env)
│   ├── db/                       # Prisma client singleton instance
│   ├── email/                    # Layanan SMTP Nodemailer
│   ├── storage/                  # Integrasi penyimpanan file S3 / MinIO
│   ├── utils/                    # Formatters & helper umum
│   └── validation/               # Zod schema definitions
├── prisma/                       # Konfigurasi Prisma
│   ├── schema.prisma             # Skema relasional basis data
│   └── seed.ts                   # Skrip seeder data awal
├── public/                       # File aset statis (gambar, font, ikon)
├── docker-compose.yml            # Konfigurasi container PostgreSQL lokal
├── middleware.ts                 # Next.js Edge Middleware untuk proteksi rute
├── package.json                  # Konfigurasi modul & dependensi
└── tsconfig.json                 # Konfigurasi TypeScript
```

---

## 🚀 Panduan Menjalankan Proyek (Getting Started)

### 1. Prasyarat Sistem
* [Node.js](https://nodejs.org/) versi 20+ atau [Bun](https://bun.sh/)
* [Docker Desktop](https://www.docker.com/) (untuk menjalankan PostgreSQL)
* [Git](https://git-scm.com/)

### 2. Kloning Repositori
```bash
git clone https://github.com/ZeckRyan/lentera-hijaiyah-haki.git
cd lentera-hijaiyah-haki
```

### 3. Instalasi Dependensi
Gunakan Bun (disarankan) atau npm:
```bash
bun install
# atau
npm install
```

### 4. Konfigurasi Environment Variables
Buat file `.env` pada root direktori proyek, sesuaikan dengan konfigurasi berikut:

```env
# URL Aplikasi
NEXT_PUBLIC_APP_URL="http://localhost:3000"

# Basis Data (PostgreSQL via Docker)
DATABASE_URL="postgresql://postgres:postgres@localhost:5432/lentera_hijaiyah?schema=public"

# Kunci Rahasia JWT (Minimal 32 karakter acak)
AUTH_SECRET="your-super-secret-jwt-key-replace-this-with-random-string"

# Konfigurasi Email SMTP (Brevo) - Opsional untuk Forgot Password
BREVO_SMTP_HOST="smtp-relay.brevo.com"
BREVO_SMTP_PORT="587"
BREVO_SMTP_USER="your-brevo-smtp-user"
BREVO_SMTP_PASSWORD="your-brevo-smtp-password"
BREVO_SENDER_EMAIL="no-reply@lenterahijaiyah.com"
BREVO_SENDER_NAME="Lentera Hijaiyah"

# Konfigurasi Object Storage S3 / MinIO (Opsional jika modul PDF disimpan lokal/cloud)
MINIO_ENDPOINT="http://localhost:9000"
MINIO_REGION="us-east-1"
MINIO_ACCESS_KEY="minioadmin"
MINIO_SECRET_KEY="minioadmin"
MINIO_BUCKET="lentera-modules"
MINIO_PUBLIC_URL="http://localhost:9000/lentera-modules"
MINIO_SSL_VERIFY="false"
```

### 5. Menjalankan Database PostgreSQL
Jalankan service database PostgreSQL menggunakan Docker Compose:
```bash
docker compose up -d db
```

### 6. Sinkronisasi Skema Prisma & Seeding
Lakukan sinkronisasi skema ke database dan generate client:
```bash
# Generate Prisma Client
npx prisma generate

# Sinkronkan skema ke database
npx prisma db push

# (Opsional) Jalankan data seeding awal
bun run seed
# atau
npm run seed
```

Untuk membuka GUI basis data (Prisma Studio):
```bash
npm run db
```

### 7. Menjalankan Server Development
```bash
bun run dev
# atau
npm run dev
```

Aplikasi dapat diakses melalui peramban web pada tautan:
👉 **[http://localhost:3000](http://localhost:3000)**

---

## 📑 Dokumentasi API

Sistem menyediakan antarmuka pengujian API berbasis OpenAPI / Swagger UI yang telah terintegrasi:

* **Swagger UI Web:** Buka [http://localhost:3000/api-docs](http://localhost:3000/api-docs) saat server berjalan.
* **Postman Collection:** File koleksi tersedia pada direktori `docs/postman_collection.json`. Anda dapat mengimpor file tersebut langsung ke aplikasi Postman.

---

## ⚖️ Hak Kekayaan Intelektual & Lisensi Penggunaan

> [!IMPORTANT]
> **Pernyataan Kepemilikan Hak Cipta & Hak Guna:**
> 
> 1. **Kepemilikan Hak Cipta (Copyright):**
>    Hak Cipta atas seluruh kode sumber, desain arsitektur, algoritma validasi, dan aset perangkat lunak **Lentera Hijaiyah** adalah milik **Developer / Tim Pengembang** yang dilindungi di bawah Undang-Undang Republik Indonesia No. 28 Tahun 2014 tentang Hak Cipta.
> 
> 2. **Lisensi Penggunaan Klien & Kebutuhan Akademisi:**
>    Pengguna, Klien, dan Institusi Akademik diberikan **Hak Pakai (Lisensi Non-Eksklusif)** untuk mengoperasikan, menguji, dan memanfaatkan platform ini sesuai kebutuhan operasional, edukasi, dan penelitian akademis.
> 
> 3. **Batasan Penggunaan:**
>    Pihak manapun dilarang keras menjual kembali (*resell*), melisensikan ulang (*sublicense*), mengklaim kepemilikan ciptaan, atau menyalin dan mendistribusikan kode sumber tanpa izin tertulis dari Pemegang Hak Cipta.
