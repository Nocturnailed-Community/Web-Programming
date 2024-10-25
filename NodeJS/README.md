# Node.js

## 1. Apa itu Node.js?

**Node.js** adalah runtime environment berbasis JavaScript yang memungkinkan Anda menjalankan JavaScript di sisi server (server-side) di luar browser. Node.js dibangun di atas **V8 JavaScript Engine** yang digunakan oleh Chrome untuk menjalankan JavaScript secara cepat dan efisien. Dengan Node.js, JavaScript bisa digunakan untuk membangun aplikasi backend, API, server, dan banyak lagi.

### Keunggulan Node.js:
- **Non-blocking I/O**: Menggunakan event-driven architecture dan non-blocking I/O untuk menangani banyak koneksi secara bersamaan tanpa menunggu proses lain selesai.
- **Cross-platform**: Bisa berjalan di berbagai sistem operasi seperti Windows, macOS, dan Linux.
- **Ekosistem Paket yang Luas**: Node.js memiliki **npm (Node Package Manager)** yang menyediakan lebih dari jutaan paket untuk berbagai kebutuhan pengembangan.

## 2. Cara Instalasi Node.js

Untuk menggunakan Node.js, pertama-tama Anda harus menginstalnya di komputer. Ikuti langkah berikut:

1. Unduh Node.js dari [nodejs.org](https://nodejs.org/).
2. Ikuti instruksi instalasi sesuai dengan sistem operasi Anda.
3. Setelah instalasi selesai, cek apakah Node.js sudah terpasang dengan benar menggunakan perintah berikut di terminal atau command prompt:

```bash
node -v
```

Ini akan menampilkan versi Node.js yang terpasang.
Anda juga bisa mengecek versi npm yang terinstal dengan perintah:

```bash
npm -v
```

### 3. Menjalankan JavaScript dengan Node.js

Anda bisa menulis file JavaScript dan menjalankannya dengan Node.js di terminal. Contoh sederhana:

1. Buat file app.js dengan isi berikut:
```javascript
console.log('Hello, Node.js!');
```

2. Jalankan file tersebut menggunakan Node.js dengan perintah:
```bash
node app.js
```

Hasilnya akan menampilkan: Hello, Node.js!

### 4. Modul dalam Node.js

Node.js memiliki sistem modul yang memungkinkan Anda membagi kode ke dalam file atau modul yang terpisah untuk pengorganisasian yang lebih baik. Modul dapat berupa modul bawaan Node.js atau modul eksternal dari npm.

#### a. Modul Bawaan

Node.js dilengkapi dengan beberapa modul bawaan seperti `fs` (file system), `http`, `path`, dan lainnya. Contoh penggunaan modul bawaan:

```javascript
// Menggunakan modul 'fs' untuk membaca file
const fs = require('fs');

// Membaca file secara synchronous
const data = fs.readFileSync('file.txt', 'utf8');
console.log(data);
```

#### b. Modul Eksternal (npm)

npm (Node Package Manager) adalah tool untuk mengelola paket-paket eksternal yang bisa Anda gunakan dalam proyek Node.js. Untuk menginstal paket, Anda bisa menggunakan perintah `npm install`.

Contoh, instal paket express untuk membuat server web sederhana:

```bash
npm install express
```

Setelah diinstal, Anda bisa menggunakan Express dalam proyek Anda:

```javascript
const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('Hello, Express!');
});

app.listen(3000, () => {
  console.log('Server running on port 3000');
});
```

Jalankan kode di atas, dan server akan berjalan di `localhost:3000`.

### 5. Membuat Server HTTP Sederhana

Node.js menyediakan modul `http` untuk membuat server HTTP. Berikut adalah contoh sederhana membuat server HTTP menggunakan modul `http` bawaan Node.js:

```javascript
const http = require('http');

// Membuat server
const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello, World!\n');
});

// Menjalankan server pada port 3000
server.listen(3000, '127.0.0.1', () => {
  console.log('Server running at http://127.0.0.1:3000/');
});
```

Setelah menjalankan kode di atas, buka browser dan arahkan ke `http://127.0.0.1:3000/`. Anda akan melihat pesan "Hello, World!".

### 6. Asynchronous Programming dengan Callback, Promises, dan Async/Await

Node.js sangat mendukung pemrograman asynchronous yang efisien melalui callback, promises, dan `async/await`.

#### a. Callback

`Callback` adalah fungsi yang dipanggil setelah operasi asynchronous selesai. Misalnya:

```javascript
const fs = require('fs');

// Membaca file secara asynchronous
fs.readFile('file.txt', 'utf8', (err, data) => {
  if (err) throw err;
  console.log(data);
});
```

#### b. Promises

`Promise` memungkinkan Anda menangani operasi asynchronous secara lebih mudah dibandingkan dengan callback:

```javascript
const fs = require('fs').promises;

// Membaca file menggunakan Promise
fs.readFile('file.txt', 'utf8')
  .then(data => {
    console.log(data);
  })
  .catch(err => {
    console.error(err);
  });
```

#### c. Async/Await

Dengan `async/awai`t, kode asynchronous menjadi lebih mudah dibaca dan ditulis:

```javascript
const fs = require('fs').promises;

async function readFile() {
  try {
    const data = await fs.readFile('file.txt', 'utf8');
    console.log(data);
  } catch (err) {
    console.error(err);
  }
}

readFile();
```

### 7. Manajemen Paket dengan npm

npm adalah package manager untuk Node.js yang memungkinkan Anda menginstal, mengelola, dan berbagi modul/paket.

#### a. Inisialisasi Proyek npm

Untuk memulai proyek Node.js dengan npm, pertama-tama inisialisasi proyek dengan perintah:

```bash
npm init
```

Ini akan membuat file package.json yang menyimpan informasi tentang proyek dan dependensinya.

#### b. Instalasi Paket

Untuk menginstal paket menggunakan npm, gunakan perintah npm install. Contoh, instal paket `lodash`:

```bash
npm install lodash
```

#### c. Mengelola Skrip dengan npm

Anda bisa menambahkan skrip di file package.json untuk menjalankan perintah-perintah tertentu. Contoh:

```json
{
  "scripts": {
    "start": "node app.js"
  }
}
```

Sekarang Anda bisa menjalankan perintah npm start untuk menjalankan app.js.

### Kesimpulan

Node.js adalah runtime JavaScript yang powerful untuk pengembangan server-side. Dengan arsitektur event-driven dan non-blocking I/O, Node.js sangat cocok untuk membangun aplikasi yang scalable dan cepat. Ekosistemnya yang besar melalui npm memungkinkan Anda membangun aplikasi dengan berbagai macam kebutuhan mulai dari API, server web, hingga aplikasi real-time.