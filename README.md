# 🚀 Praktikum Pemrograman Web S4

## Full-Stack CMS Artikel (CodeIgniter 4 + Vue.js 3)

![PHP](https://img.shields.io/badge/PHP-8.1+-777BB4?logo=php\&logoColor=white)
![CodeIgniter](https://img.shields.io/badge/CodeIgniter-4-EF4223?logo=codeigniter\&logoColor=white)
![Vue.js](https://img.shields.io/badge/Vue.js-3-42B883?logo=vue.js\&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-Database-4479A1?logo=mysql\&logoColor=white)
![REST API](https://img.shields.io/badge/REST-API-000000?logo=api\&logoColor=white)
![License](https://img.shields.io/badge/Status-Project%20Akademik-blue)

---

## 👤 Identitas

| Komponen    | Keterangan                   |
| ----------- | ---------------------------- |
| Nama        | Ahmad Rizky Pramudia Pratama |
| NIM         | 312410351                    |
| Kelas       | I241D                        |
| Mata Kuliah | Pemrograman Web 2            |

---

## 📌 Deskripsi Proyek

Proyek ini merupakan aplikasi **CMS (Content Management System) Artikel** berbasis web yang mengimplementasikan arsitektur **Full-Stack Development**.

Sistem ini terdiri dari:

* Backend menggunakan **CodeIgniter 4 (REST API)**
* Frontend menggunakan **Vue.js 3 (Single Page Application)**

Kedua sistem saling terhubung melalui komunikasi API berbasis JSON.

---

## 🧩 Struktur Modul

| Modul            | Teknologi             | Fungsi                             |
| ---------------- | --------------------- | ---------------------------------- |
| Lab 11 (Backend) | CodeIgniter 4         | REST API, autentikasi, admin panel |
| Lab 8 (Frontend) | Vue.js 3 + Vue Router | SPA untuk konsumsi API             |

---

## ✨ Fitur Utama

### 🖥️ Backend (CodeIgniter 4)

* 🔐 Login & logout (session-based authentication)
* 📰 CRUD artikel (create, read, update, delete)
* 🗂️ Manajemen kategori artikel
* 🔍 Pencarian & filter artikel
* 📄 Pagination otomatis
* ⚡ AJAX (tanpa reload halaman)
* 🌐 RESTful API (Resource Controller)
* 🐌 URL SEO-friendly (slug)

---

### 🌐 Frontend (Vue.js 3)

* ⚡ Single Page Application (SPA)
* 🔀 Vue Router (navigasi tanpa reload)
* 📡 Axios untuk komunikasi API
* 📝 CRUD artikel interaktif (modal form)
* 🎛️ Status artikel (Draft / Publish)

---

## 🏗️ Arsitektur Sistem

```text
Browser (Client)
│
├── Vue.js 3 SPA
│   ├── Home Component
│   └── Artikel Component (CRUD)
│
├── Vue Router + Axios
│
└── REST API Request
        ↓
Backend (CodeIgniter 4)
│
├── Controller (Artikel, User, API Post)
├── Model (Database Layer)
├── Filter (Auth Middleware)
│
└── MySQL Database
    ├── artikel
    ├── user
    └── kategori
```

---

## 📁 Struktur Proyek

```text
root/
├── lab11_ci/              # Backend CodeIgniter 4
│   └── ci4/
│       ├── app/
│       │   ├── Controllers/
│       │   ├── Models/
│       │   ├── Views/
│       │   ├── Filters/
│       │   └── Config/
│       └── .env
│
└── lab8_vuejs/            # Frontend Vue.js SPA
    ├── index.html
    └── assets/
        ├── css/
        └── js/
            └── components/
```

---

## 🌐 REST API

**Base URL:**

```text
http://localhost/lab11_ci/ci4/public
```

### Endpoint API

| Method | Endpoint   | Deskripsi                    |
| ------ | ---------- | ---------------------------- |
| GET    | /post      | Ambil semua artikel          |
| GET    | /post/{id} | Ambil artikel berdasarkan ID |
| POST   | /post      | Tambah artikel               |
| PUT    | /post/{id} | Update artikel               |
| DELETE | /post/{id} | Hapus artikel                |

---

## 📌 Contoh Response API

```json
{
  "artikel": [
    {
      "id": 1,
      "judul": "Contoh Artikel",
      "isi": "Isi artikel...",
      "status": 1,
      "slug": "contoh-artikel",
      "gambar": null
    }
  ]
}
```

---

## 🔐 Sistem Autentikasi

Sistem menggunakan **session-based authentication** dengan middleware filter.

Alur login:

```text
Login → Validasi → Session dibuat → Akses Admin
Logout → Session dihapus
```

Proteksi diterapkan pada seluruh route `/admin/*`.

---

## 🔗 Route Aplikasi (CI4)

| Route                      | Controller           | Akses  |
| -------------------------- | -------------------- | ------ |
| /                          | Home::index          | Publik |
| /artikel                   | Artikel::index       | Publik |
| /artikel/{slug}            | Artikel::view        | Publik |
| /user/login                | User::login          | Publik |
| /user/logout               | User::logout         | Login  |
| /admin/artikel             | Artikel::admin_index | Login  |
| /admin/artikel/add         | Artikel::add         | Login  |
| /admin/artikel/edit/{id}   | Artikel::edit        | Login  |
| /admin/artikel/delete/{id} | Artikel::delete      | Login  |

---

## ⚙️ Instalasi & Konfigurasi

### 🔧 Persyaratan Sistem

* PHP >= 8.1
* Composer
* MySQL / MariaDB
* XAMPP / Apache

---

### 1️⃣ Backend (CodeIgniter 4)

```bash
cp -r lab11_ci /xampp/htdocs/
cd /xampp/htdocs/lab11_ci/ci4
composer install
```

#### Konfigurasi `.env`

```env
CI_ENVIRONMENT = development

database.default.hostname = localhost
database.default.database = nama_database
database.default.username = root
database.default.password =
database.default.DBDriver = MySQLi
```

---

#### Database

```sql
CREATE DATABASE nama_database;

CREATE TABLE artikel (
  id INT AUTO_INCREMENT PRIMARY KEY,
  judul VARCHAR(255),
  isi TEXT,
  status TINYINT(1),
  slug VARCHAR(255),
  gambar VARCHAR(255),
  id_kategori INT
);

CREATE TABLE kategori (
  id_kategori INT AUTO_INCREMENT PRIMARY KEY,
  nama_kategori VARCHAR(100)
);

CREATE TABLE user (
  id INT AUTO_INCREMENT PRIMARY KEY,
  username VARCHAR(100),
  useremail VARCHAR(100),
  userpassword VARCHAR(255)
);
```

---

### 2️⃣ Frontend (Vue.js)

```bash
cp -r lab8_vuejs /xampp/htdocs/
```

Update API:

```javascript
const apiUrl = "http://localhost/lab11_ci/ci4/public";
```

---

## 🛠️ Teknologi yang Digunakan

### Backend

* PHP 8.1+
* CodeIgniter 4
* MySQL
* REST API

### Frontend

* Vue.js 3
* Vue Router 4
* Axios
* CSS3

---

## 📌 Kesimpulan

Proyek ini menunjukkan implementasi:

* Arsitektur Full-Stack modern
* Komunikasi REST API
* SPA berbasis Vue.js
* Sistem CRUD terintegrasi
* Authentication berbasis session
