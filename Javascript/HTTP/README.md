# JavaScript HTTP Request

HTTP Request merupakan salah satu hal penting dalam pengembangan web untuk mengambil atau mengirim data dari dan ke server. Pada JavaScript, terdapat beberapa cara yang umum digunakan untuk melakukan HTTP Request, seperti menggunakan `fetch`, `XMLHttpRequest`, atau pustaka eksternal seperti **AXIOS**.

## 1. Perkenalan AXIOS

**AXIOS** adalah pustaka berbasis `Promise` yang memudahkan dalam melakukan HTTP request di browser atau Node.js. AXIOS banyak digunakan karena sintaksnya yang sederhana dan mendukung fitur-fitur seperti interceptors, transform request/response, dan dukungan penuh untuk `Promise`.

### Kelebihan AXIOS:
- Berbasis `Promise`, sehingga lebih mudah untuk diintegrasikan dengan `Async/Await`.
- Mendukung transformasi request dan response.
- Memiliki fitur interceptors untuk memodifikasi request/response sebelum diproses.
- Mendukung pembatalan request dan timeout.
- Mendukung secara otomatis pengaturan headers.

### Contoh Penggunaan AXIOS:
```javascript
// Import Axios (pada Node.js, jika menggunakan di browser tidak perlu import jika sudah diinclude)
const axios = require('axios');

// Contoh GET request
axios.get('https://jsonplaceholder.typicode.com/posts')
  .then(response => {
    console.log(response.data); // Menampilkan data response
  })
  .catch(error => {
    console.error('Error:', error);
  });

// Contoh POST request
axios.post('https://jsonplaceholder.typicode.com/posts', {
    title: 'foo',
    body: 'bar',
    userId: 1,
  })
  .then(response => {
    console.log(response.data);
  })
  .catch(error => {
    console.error('Error:', error);
  });
```

## 2. Perkenalan Async / Await

`Async/Await` adalah cara modern dalam mengelola operasi asynchronous di JavaScript, yang diperkenalkan pada ECMAScript 2017 (ES8). Dengan `Async/Await`, kode asynchronous terlihat seperti kode synchronous, sehingga lebih mudah dipahami dan ditulis.

- `async`: Digunakan untuk mendefinisikan fungsi asynchronous. Fungsi yang didefinisikan dengan `async` secara otomatis mengembalikan Promise.
- `await`: Digunakan untuk menunggu penyelesaian Promise. Keyword ini hanya bisa digunakan di dalam fungsi `async`.

```javascript
// Contoh Penggunaan Async/Await:
// Fungsi dengan async
async function fetchData() {
  try {
    // Menunggu hasil dari axios.get()
    const response = await axios.get('https://jsonplaceholder.typicode.com/posts');
    console.log(response.data); // Menampilkan data response
  } catch (error) {
    console.error('Error:', error);
  }
}

fetchData(); // Memanggil fungsi fetchData
```

Keunggulan `Async/Await` adalah cara penanganan error yang lebih sederhana menggunakan `try/catch`, serta membuat kode lebih mudah dibaca daripada menggunakan `.then()` pada `Promise`.

## 3. Perkenalan Callback

Callback adalah fungsi yang diteruskan sebagai argumen ke fungsi lain dan dipanggil setelah fungsi utama selesai menjalankan tugasnya. Callback sering digunakan untuk menangani operasi asynchronous seperti membaca file, membuat HTTP request, atau berinteraksi dengan database.

```javascript
// Contoh Penggunaan Callback:
// Fungsi sederhana yang menggunakan callback
function fetchData(callback) {
  setTimeout(() => {
    const data = { message: 'Data fetched' };
    callback(null, data); // Memanggil callback setelah data diperoleh
  }, 2000);
}

// Memanggil fungsi fetchData dengan callback
fetchData((error, result) => {
  if (error) {
    console.error('Error:', error);
  } else {
    console.log(result); // Menampilkan hasil data yang diambil
  }
});
```

Pada contoh di atas, `fetchData` menerima fungsi callback yang akan dipanggil setelah 2 detik (simulasi waktu pengambilan data). Callback digunakan untuk mengeksekusi logika setelah tugas asynchronous selesai.



