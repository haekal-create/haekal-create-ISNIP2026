<p align="center">
  <img src="https://img.shields.io/badge/Laravel-12-FF2D20?style=for-the-badge&logo=laravel&logoColor=white" alt="Laravel 12">
  <img src="https://img.shields.io/badge/Tailwind_CSS-3-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white" alt="Tailwind CSS">
  <img src="https://img.shields.io/badge/Alpine.js-3-8BC0D0?style=for-the-badge&logo=alpinedotjs&logoColor=white" alt="Alpine.js">
  <img src="https://img.shields.io/badge/Vite-5-646CFF?style=for-the-badge&logo=vite&logoColor=white" alt="Vite">
  <img src="https://img.shields.io/badge/PHP-8.2+-777BB4?style=for-the-badge&logo=php&logoColor=white" alt="PHP 8.2+">
</p>

<h1 align="center">🧬 ISNIP — Integrated SNP Identification Pipeline</h1>

<p align="center">
  <strong>Platform Analisis Genomik Berbasis Web untuk Identifikasi <em>Single Nucleotide Polymorphism</em> (SNP)</strong>
</p>

<p align="center">
  <em>Capstone Project — Sekolah Sains Data, Matematika, dan Informatika, IPB University (2026)</em>
</p>

---

## 📖 Tentang Proyek

**ISNIP (Integrated SNP Identification Pipeline)** adalah platform berbasis web yang mengintegrasikan berbagai tahapan analisis bioinformatika — meliputi kontrol kualitas *reads*, pemetaan (*mapping*) ke genom referensi, dan pemanggilan varian (*variant calling*) — ke dalam satu alur kerja otomatis dan terpadu.

Proyek ini merupakan **redesign menyeluruh** pada antarmuka pengguna (UI/UX) aplikasi ISNIP, yang mentransformasi tampilan lama yang kaku dan non-responsif menjadi antarmuka modern, intuitif, dan sepenuhnya responsif menggunakan *tech stack* front-end terkini.

---

## 🚀 Fitur Utama

### 🏠 Dashboard Informatif
- Halaman utama dengan *hero section* bergradien modern
- Kartu-kartu fitur dengan desain konsisten dan *hover effects*
- Tombol CTA kontekstual berdasarkan status autentikasi

### 📤 Self-Service Upload
- Upload mandiri data referensi (*reference genome*) dan data *query* (*reads*)
- Zona *drag-and-drop* yang responsif
- Validasi format file (`.fa`, `.fasta`, `.fastq`, `.fq`, `.gz`, `.fastq.gz`, `.fq.gz`) dan ukuran file (maks. 5 GB) secara *client-side*
- Eliminasi ketergantungan pada administrator

### 📋 Submit Job Pipeline (Step-by-Step Modal)
- Komponen modal interaktif bertahap ditenagai Alpine.js
- Konfigurasi parameter Bowtie2 dan Samtools secara terstruktur
- Validasi per tahap dengan transisi animasi yang mulus
- Pemilihan sumber *reads* dan tipe *reads* secara kondisional

### 📊 Job Monitoring
- Panel metrik statistik (Total Analyses, Currently Running, Storage Used, Avg. Runtime)
- Tabel riwayat *job* dengan *badge* status berwarna:
  - 🔵 **Submitted** — Indigo badge
  - 🔷 **Running** — Sky badge dengan animasi pulse
  - 🟢 **Finished** — Emerald badge
  - 🔴 **Canceled** — Red badge
- **Live Refreshing** otomatis setiap 4 detik untuk *job* aktif

### 🔍 Search Analysis
- Pencarian dan *query* data SNP yang teridentifikasi
- Tampilan hasil dalam format tabel responsif (posisi genomik, tipe varian, kualitas varian)

### 🔐 Sistem Autentikasi
- Halaman *login* dan *register* dengan desain konsisten
- Validasi *client-side* dan *server-side*

---

## 🛠️ Tech Stack

| Teknologi | Versi | Peran |
|-----------|-------|-------|
| **Laravel** | 12 | Framework PHP (MVC), Blade Templating Engine |
| **Tailwind CSS** | 3.x | *Utility-first CSS framework*, sistem desain kustom |
| **Alpine.js** | 3.x | Interaktivitas komponen *client-side* (modal, dropdown, validasi) |
| **Vite** | 5.x | *Build tool* dengan HMR instan & *production bundling* |
| **PHP** | ≥ 8.2 | Bahasa pemrograman *backend* |
| **MySQL/SQLite** | - | Basis data |

---

## 📁 Struktur Proyek

```
ISNIP2026/
├── app/                        # Logika aplikasi (Models, Controllers, dll.)
├── bootstrap/                  # Bootstrap framework
├── config/                     # File konfigurasi
├── database/                   # Migrasi, seeder, factory
├── public/                     # Entry point & aset publik
├── resources/
│   └── views/
│       ├── layouts/
│       │   └── layout.blade.php        # Master layout (sidebar, header, footer)
│       ├── home.blade.php              # Dashboard / halaman utama
│       ├── jobs/
│       │   ├── index.blade.php         # Daftar job (My Job List)
│       │   ├── details.blade.php       # Detail job + Live Refreshing
│       │   └── submit_modal.blade.php  # Modal step-by-step Submit Job
│       ├── search.blade.php            # Search Analysis
│       ├── contact.blade.php           # Halaman kontak
│       ├── auth/                       # Login & Register
│       └── welcome.blade.php           # Landing page publik
├── routes/                     # Definisi rute
├── storage/                    # File storage
├── tests/                      # Unit & feature tests
├── tailwind.config.js          # Konfigurasi design system
├── vite.config.js              # Konfigurasi Vite
├── composer.json               # Dependensi PHP
├── package.json                # Dependensi Node.js
└── vercel.json                 # Konfigurasi deployment Vercel
```

---

## ⚙️ Instalasi & Penggunaan

### Prasyarat

- **PHP** ≥ 8.2
- **Composer** ≥ 2.x
- **Node.js** ≥ 18.x
- **NPM** ≥ 9.x
- **MySQL** / **SQLite**

### Langkah Instalasi

```bash
# 1. Clone repository
git clone https://github.com/laathiifaaz/ISNIP2026.git
cd ISNIP2026

# 2. Install dependensi PHP
composer install

# 3. Install dependensi Node.js
npm install

# 4. Salin file environment
cp .env.example .env

# 5. Generate application key
php artisan key:generate

# 6. Konfigurasi database di file .env
# Sesuaikan DB_CONNECTION, DB_HOST, DB_PORT, DB_DATABASE, DB_USERNAME, DB_PASSWORD

# 7. Jalankan migrasi database
php artisan migrate

# 8. Build asset front-end (development)
npm run dev

# 9. Jalankan server development
php artisan serve
```

Aplikasi akan berjalan di `http://localhost:8000`

### Build untuk Produksi

```bash
npm run build
```

---

## 🏗️ Arsitektur

```
┌─────────────────────────────────────────────────────┐
│                    Browser (Client)                  │
│  ┌───────────┐  ┌───────────┐  ┌─────────────────┐ │
│  │ Tailwind   │  │ Alpine.js │  │   Blade Views   │ │
│  │ CSS        │  │ (Reactivity)│ │  (Templating)  │ │
│  └───────────┘  └───────────┘  └─────────────────┘ │
│                        │                             │
│                   Vite (Build Tool)                  │
└────────────────────────┬────────────────────────────┘
                         │ HTTP
┌────────────────────────┴────────────────────────────┐
│                 Laravel 12 (Server)                   │
│  ┌──────────┐  ┌──────────────┐  ┌───────────────┐  │
│  │ Routes   │→ │ Controllers  │→ │    Models      │  │
│  │          │  │ (Auth, Job,  │  │ (User, Job,    │  │
│  │          │  │  Search, Home)│  │  Upload, etc.) │  │
│  └──────────┘  └──────────────┘  └───────┬───────┘  │
│                                          │           │
│                                   ┌──────┴──────┐   │
│                                   │  Database   │   │
│                                   │ (MySQL/SQLite)│  │
│                                   └─────────────┘   │
└─────────────────────────────────────────────────────┘
```

---

## 🧪 Pipeline Bioinformatika

ISNIP mengintegrasikan alat-alat bioinformatika berikut dalam *pipeline* analisis SNP:

| Tahap | Tool | Fungsi |
|-------|------|--------|
| 1. Quality Control | FastQC | Kontrol kualitas *reads* hasil sekuensing |
| 2. Alignment | **Bowtie2** | Pemetaan *reads* ke genom referensi |
| 3. SAM Processing | **Samtools** | Pemrosesan file *alignment* (*sorting*, *indexing*, *filtering*) |
| 4. Variant Calling | **BCFtools** | Pemanggilan dan identifikasi varian SNP |

> **Catatan:** Proyek ini berfokus pada *front-end* dan UI/UX. Integrasi *production-ready* dengan *core engine* bioinformatika berada di luar cakupan proyek ini.

---

## 👥 Tim Pengembang

| Nama | NIM | Peran |
|------|-----|-------|
| **Lathiifa Zahra Yahya** | G6401231154 | Project Lead |
| **Emi Purnawadi** | G6401231032 | Developer |
| **Khalisha Rana Putri** | G6401231141 | Developer |
| **Fikri Nurhaekal** | G6401231030 | Developer |

**Institusi:** Sekolah Sains Data, Matematika, dan Informatika — IPB University

**Periode:** Januari – Juni 2026

---

## 📄 Lisensi

Proyek ini dikembangkan sebagai bagian dari Capstone Project di IPB University. Framework Laravel yang digunakan adalah perangkat lunak *open-source* berlisensi [MIT license](https://opensource.org/licenses/MIT).

---

<p align="center">
  <sub>Built with ❤️ at IPB University © 2026</sub>
</p>
