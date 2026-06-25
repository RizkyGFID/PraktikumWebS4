# Praktikum Web S4
🚀 Full-Stack Artikel CMS
Sistem manajemen artikel berbasis REST API dengan arsitektur modern
PHP CodeIgniter Vue.js Axios MySQL License


Proyek full-stack yang menggabungkan CodeIgniter 4 sebagai backend REST API dengan Vue.js 3 sebagai frontend Single Page Application (SPA).


👤 Identitas
Nama : Ahmad Rizky Pramudia Pratama
NIM : 312410351
Kelas	: I241D
Mata Kuliah :	Pemrograman Web 2

📌 Tentang Proyek
Proyek ini terdiri dari dua modul yang saling terhubung:

Modul	Teknologi	Deskripsi
Lab 11 — Backend	CodeIgniter 4 (PHP)	REST API, autentikasi, admin panel, AJAX pagination
Lab 8 — Frontend	Vue.js 3 + Vue Router	SPA untuk konsumsi REST API secara real-time
Keduanya membentuk sistem CMS Artikel yang lengkap — dari manajemen konten di sisi server hingga antarmuka pengguna yang responsif dan dinamis.

✨ Fitur Utama
Berikut adalah fitur utama yang disajikan dalam web ini:

🖥️ Backend — CodeIgniter 4 (lab11_ci)
🔐 Autentikasi — Login/logout berbasis sesi dengan filter Auth
📰 CRUD Artikel — Tambah, lihat, edit, dan hapus artikel
🗂️ Kategori — Pengelompokan artikel berdasarkan kategori
🔍 Search & Filter — Pencarian dan filter berdasarkan kategori di panel admin
📄 Pagination — Pagination otomatis menggunakan built-in CI4 Pager
⚡ AJAX Support — Admin panel mendukung request AJAX tanpa reload halaman
🌐 RESTful API — Endpoint lengkap CRUD via ResourceController
🐌 Slug URL — URL artikel yang SEO-friendly
🎨 Frontend — Vue.js 3 (lab8_vuejs)
⚡ Single Page Application — Navigasi tanpa reload halaman
🔀 Vue Router — Routing berbasis hash (createWebHashHistory)
📡 Axios HTTP Client — Komunikasi real-time dengan REST API
📝 Manajemen Artikel — CRUD lengkap lewat modal form interaktif
🎛️ Status Artikel — Toggle antara status Draft dan Publish
🏗️ Arsitektur Sistem
┌─────────────────────────────────────────────────────────────┐
│                     BROWSER / CLIENT                        │
│                                                             │
│   ┌─────────────────────────────────────────────────────┐  │
│   │              Vue.js 3 SPA (Lab 8)                   │  │
│   │                                                     │  │
│   │   ┌──────────┐   ┌──────────────────────────────┐  │  │
│   │   │  Home.js │   │        Artikel.js             │  │  │
│   │   │(Beranda) │   │ (CRUD: Tambah/Edit/Hapus)    │  │  │
│   │   └──────────┘   └──────────────────────────────┘  │  │
│   │                                                     │  │
│   │            Vue Router  |  Axios HTTP                │  │
│   └─────────────────────────────────────────────────────┘  │
│                           │                                 │
│                    REST API Calls                           │
│                   (GET/POST/PUT/DELETE)                     │
└───────────────────────────┼─────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────┐
│                  CodeIgniter 4 (Lab 11)                     │
│                                                             │
│   ┌────────────────────────────────────────────────────┐   │
│   │                   ROUTES                           │   │
│   │  / about contact  │  /admin/*  │  /post (REST)    │   │
│   └─────────┬──────────────┬──────────────┬───────────┘   │
│             │              │              │                 │
│   ┌─────────▼──┐  ┌────────▼──┐  ┌───────▼────────┐       │
│   │ Controllers│  │ Auth      │  │ Post           │       │
│   │ Artikel    │  │ Filter    │  │ ResourceCtrl   │       │
│   │ User       │  │           │  │ (REST API)     │       │
│   └─────────┬──┘  └───────────┘  └───────┬────────┘       │
│             │                            │                 │
│   ┌─────────▼────────────────────────────▼────────────┐   │
│   │              Models (ArtikelModel, UserModel)      │   │
│   └──────────────────────────┬─────────────────────────┘   │
│                              │                              │
└──────────────────────────────┼──────────────────────────────┘
                               │
                               ▼
                     ┌─────────────────┐
                     │   MySQL / MariaDB│
                     │  (artikel, user, │
                     │   kategori)      │
                     └─────────────────┘
📁 Struktur Proyek
📦 root/
├── 📂 lab11_ci/                    ← Backend CodeIgniter 4
│   └── 📂 ci4/
│       ├── 📂 app/
│       │   ├── 📂 Config/
│       │   │   ├── Routes.php      ← Definisi semua route
│       │   │   └── Database.php    ← Konfigurasi database
│       │   ├── 📂 Controllers/
│       │   │   ├── Artikel.php     ← CRUD artikel + admin panel
│       │   │   ├── Post.php        ← REST API controller
│       │   │   ├── User.php        ← Autentikasi user
│       │   │   ├── AjaxController.php ← Endpoint AJAX
│       │   │   └── Home.php        ← Halaman beranda
│       │   ├── 📂 Models/
│       │   │   ├── ArtikelModel.php
│       │   │   ├── UserModel.php
│       │   │   └── KategoriModel.php
│       │   ├── 📂 Views/
│       │   │   ├── artikel/        ← View CRUD artikel
│       │   │   ├── user/           ← View login
│       │   │   └── layout/         ← Layout utama
│       │   ├── 📂 Filters/
│       │   │   └── Auth.php        ← Middleware autentikasi
│       │   └── 📂 Database/Seeds/
│       │       └── UserSeeder.php  ← Seed data user
│       └── .env                    ← Konfigurasi environment
│
└── 📂 lab8_vuejs/                  ← Frontend Vue.js SPA
    ├── index.html                  ← Entry point aplikasi
    └── 📂 assets/
        ├── 📂 css/
        │   └── style.css           ← Styling global
        └── 📂 js/
            ├── app.js              ← Vue app + Vue Router init
            └── 📂 components/
                ├── Home.js         ← Komponen halaman beranda
                └── Artikel.js      ← Komponen CRUD artikel
                
🌐 REST API Endpoints
Base URL: http://localhost/lab11_ci/ci4/public

Method	Endpoint	Deskripsi
GET	/post	Ambil semua artikel
GET	/post/{id}	Ambil artikel berdasarkan ID
POST	/post	Tambah artikel baru
PUT	/post/{id}	Update artikel
DELETE	/post/{id}	Hapus artikel
Contoh Request & Response
GET /post

{
  "artikel": [
    {
      "id": 1,
      "judul": "Judul Artikel Pertama",
      "isi": "Isi artikel...",
      "status": 1,
      "slug": "judul-artikel-pertama",
      "gambar": null
    }
  ]
}
POST /post

// Request Body
{
  "judul": "Artikel Baru",
  "isi": "Konten artikel baru..."
}

// Response
{
  "status": 201,
  "error": null,
  "messages": {
    "success": "Data artikel berhasil ditambahkan."
  }
}

🔗 Route Aplikasi (CI4)
Route	Controller	Deskripsi	Auth
GET /	Home::index	Halaman beranda	❌
GET /artikel	Artikel::index	Daftar artikel publik	❌
GET /artikel/{slug}	Artikel::view	Detail artikel	❌
GET /user/login	User::login	Halaman login	❌
POST /user/login	User::login	Proses login	❌
GET /user/logout	User::logout	Logout user	✅
GET /admin/artikel	Artikel::admin_index	Admin panel	✅
GET /admin/artikel/add	Artikel::add	Form tambah	✅
POST /admin/artikel/add	Artikel::add	Simpan artikel	✅
GET /admin/artikel/edit/{id}	Artikel::edit	Form edit	✅
GET /admin/artikel/delete/{id}	Artikel::delete	Hapus artikel	✅

⚙️ Instalasi & Konfigurasi
Prasyarat:

PHP >= 8.1
Composer
MySQL / MariaDB
Web Server (Apache / XAMPP)
Browser modern
1️⃣ Setup Backend (Lab 11 — CodeIgniter 4)

# Clone atau letakkan folder lab11_ci di htdocs
cp -r lab11_ci /xampp/htdocs/

# Masuk ke direktori CI4
cd /xampp/htdocs/lab11_ci/ci4

# Install dependencies via Composer
composer install
Konfigurasi .env:

CI_ENVIRONMENT = development

database.default.hostname = localhost
database.default.database = nama_database_kamu
database.default.username = root
database.default.password = 
database.default.DBDriver = MySQLi
Buat database & jalankan migrasi:

# Buat database di MySQL
CREATE DATABASE nama_database_kamu;

# Buat tabel artikel
CREATE TABLE artikel (
    id          INT AUTO_INCREMENT PRIMARY KEY,
    judul       VARCHAR(255) NOT NULL,
    isi         TEXT,
    status      TINYINT(1) DEFAULT 0,
    slug        VARCHAR(255),
    gambar      VARCHAR(255),
    id_kategori INT
);

# Buat tabel kategori
CREATE TABLE kategori (
    id_kategori  INT AUTO_INCREMENT PRIMARY KEY,
    nama_kategori VARCHAR(100)
);

# Buat tabel user
CREATE TABLE user (
    id           INT AUTO_INCREMENT PRIMARY KEY,
    username     VARCHAR(100),
    useremail    VARCHAR(100),
    userpassword VARCHAR(255)
);

# Seed data user (opsional)
php spark db:seed UserSeeder
✅ Backend siap diakses di: http://localhost/lab11_ci/ci4/public

2️⃣ Setup Frontend (Lab 8 — Vue.js SPA)
# Salin folder ke htdocs
cp -r lab8_vuejs /xampp/htdocs/
Pastikan URL API di assets/js/app.js sudah sesuai:

// Sesuaikan dengan URL backend kamu
const apiUrl = 'http://localhost/lab11_ci/ci4/public';
✅ Frontend siap diakses di: http://localhost/lab8_vuejs

🛠️ Teknologi yang Digunakan
- Backend
- Teknologi	Versi	Fungsi
- PHP	8.1+	Bahasa pemrograman server
- CodeIgniter 4	4.x	Framework MVC backend
- MySQL	5.7+	Database relasional
- RESTful API	—	Arsitektur komunikasi data
- Frontend
- Teknologi	Versi	Fungsi
- Vue.js	3.x	Framework reaktif frontend
- Vue Router	4.x	Client-side routing SPA
- Axios	Latest	HTTP client untuk API calls
- CSS3	—	Styling antarmuka

🔒 Autentikasi
Sistem menggunakan session-based authentication dengan filter Auth yang diaplikasikan ke semua route /admin/*.

POST /user/login
  └─ Verifikasi email + password_verify()
       ├─ ✅ Berhasil → Set session → Redirect ke /admin/artikel
       └─ ❌ Gagal   → Flash message → Redirect ke /user/login

Filter Auth (setiap request ke /admin/*)
  └─ Cek session 'logged_in'
       ├─ ✅ Ada     → Lanjutkan request
       └─ ❌ Tidak ada → Redirect ke /user/login
       
🧩 Komponen Vue.js
Home.js
Komponen sederhana sebagai halaman sambutan yang menjelaskan fungsi aplikasi.

Artikel.js
Komponen utama yang menangani seluruh operasi CRUD:

Method	Fungsi :
loadData()	Fetch semua artikel dari API (GET /post)
tambah()	Tampilkan modal form untuk data baru
edit(data)	Isi form dengan data artikel yang dipilih
saveData()	Simpan data (auto-detect POST atau PUT)
hapus(index, id)	Konfirmasi lalu hapus artikel (DELETE /post/{id})
statusText(status)	Konversi nilai status ke label teks
Lab 8 (Vue.js SPA) & Lab 11 (CodeIgniter 4 REST API)
