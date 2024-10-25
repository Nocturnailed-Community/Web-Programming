# Database

## 1. Perkenalan Database

**Database** adalah kumpulan data yang terstruktur, disimpan, dan dikelola secara elektronik dalam sebuah sistem komputer. Database digunakan untuk menyimpan informasi yang dapat diakses, diubah, dan dihapus dengan mudah. 

Beberapa contoh sistem manajemen basis data (DBMS) yang umum digunakan:
- MySQL
- PostgreSQL
- MongoDB
- SQLite
- Microsoft SQL Server

### Kegunaan Database:
- Menyimpan data pengguna, transaksi, dan informasi lain yang dibutuhkan aplikasi.
- Memudahkan dalam pencarian, pengelolaan, dan pengubahan data.
- Memungkinkan penggunaan data yang konsisten dan aman dalam berbagai aplikasi.

## 2. Tipe Data dalam Database

Tipe data dalam database menentukan jenis nilai yang dapat disimpan dalam kolom. Beberapa tipe data umum dalam sistem database relasional:

### Tipe Data Umum:
- **INT**: Menyimpan angka bulat (integer).
- **VARCHAR(n)**: Menyimpan string dengan panjang maksimum `n` karakter.
- **TEXT**: Menyimpan teks dengan panjang besar.
- **DATE**: Menyimpan tanggal (YYYY-MM-DD).
- **DATETIME**: Menyimpan tanggal dan waktu (YYYY-MM-DD HH:MM:SS).
- **BOOLEAN**: Menyimpan nilai `TRUE` atau `FALSE`.
- **FLOAT**: Menyimpan angka desimal.

### Contoh Penggunaan Tipe Data:
```sql
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(255),
    created_at DATETIME
);
```

## 3. Pembuatan Database

Pembuatan database melibatkan perancangan tabel, kolom, tipe data, serta penentuan primary key dan foreign key.

### Contoh Pembuatan Database:
```sql
-- Membuat database baru
CREATE DATABASE nama_database;

-- Menggunakan database yang baru dibuat
USE nama_database;

-- Membuat tabel 'users'
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(255) UNIQUE,
    password VARCHAR(255),
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP
);

-- Membuat tabel 'posts'
CREATE TABLE posts (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT,
    title VARCHAR(255),
    body TEXT,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id)
);
```

## 4. Query CRUD

CRUD adalah singkatan dari Create, Read, Update, dan Delete, yang merupakan empat operasi dasar untuk mengelola data dalam database.

### Create (Menambah Data):
```sql
-- Menambah data ke dalam tabel users
INSERT INTO users (name, email, password)
VALUES ('John Doe', 'johndoe@example.com', 'password123');
```

### Read (Membaca Data):
```sql
-- Membaca semua data dari tabel users
SELECT * FROM users;

-- Membaca data spesifik dengan kondisi
SELECT * FROM users WHERE email = 'johndoe@example.com';
```

### Update (Memperbarui Data):
```sql
-- Memperbarui data user
UPDATE users
SET name = 'John Updated', email = 'johnupdated@example.com'
WHERE id = 1;
```

### Delete (Menghapus Data):
```sql
-- Menghapus data user berdasarkan id
DELETE FROM users WHERE id = 1;
```

## 5. Relasi dalam Database

Relasi adalah hubungan antara dua tabel dalam database. Ada beberapa jenis relasi:

- One-to-One: Satu baris di tabel pertama berhubungan dengan satu baris di tabel kedua.
- One-to-Many: Satu baris di tabel pertama berhubungan dengan banyak baris di tabel kedua.
- Many-to-Many: Banyak baris di tabel pertama berhubungan dengan banyak baris di tabel kedua.

### One-to-One Relationship:

Misalnya, seorang pengguna hanya memiliki satu profil, dan profil hanya dimiliki oleh satu pengguna.

```sql
CREATE TABLE profiles (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT UNIQUE,
    bio TEXT,
    FOREIGN KEY (user_id) REFERENCES users(id)
);
```

### One-to-Many Relationship:

Contoh, satu pengguna dapat memiliki banyak postingan, tetapi setiap postingan hanya dimiliki oleh satu pengguna.

```sql
CREATE TABLE posts (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT,
    title VARCHAR(255),
    body TEXT,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id)
);
```

### Many-to-Many Relationship:

Contoh, satu pengguna bisa mengikuti banyak kategori, dan satu kategori bisa diikuti oleh banyak pengguna. Untuk mengimplementasikan ini, kita membutuhkan tabel pivot.

```sql
CREATE TABLE categories (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255)
);

CREATE TABLE user_categories (
    user_id INT,
    category_id INT,
    FOREIGN KEY (user_id) REFERENCES users(id),
    FOREIGN KEY (category_id) REFERENCES categories(id),
    PRIMARY KEY (user_id, category_id)
);
```

## Kesimpulan

Database adalah inti dari penyimpanan data dalam aplikasi modern. Dalam database, kita dapat membuat dan mengelola data menggunakan query CRUD (Create, Read, Update, Delete) serta memanfaatkan relasi antar tabel untuk menyusun data yang lebih terstruktur dan terorganisir. Menguasai konsep dasar ini akan membantu Anda dalam merancang sistem yang efisien dan scalable.