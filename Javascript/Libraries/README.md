# Materi Standard Library di JavaScript

## 1. Standard Library
JavaScript menyediakan berbagai metode dan fungsi bawaan (built-in) yang membantu memudahkan manipulasi data, seperti string, array, dan penyimpanan lokal.

---

## 2. Find
Metode `find()` digunakan untuk menemukan elemen pertama dalam array yang memenuhi kondisi yang ditentukan. Jika tidak ada yang cocok, hasilnya adalah `undefined`.

```javascript
let angka = [1, 2, 3, 4, 5];
let hasil = angka.find(element => element > 3);
console.log(hasil); // Output: 4
```

## 3. Split
Metode `split()` digunakan untuk memecah string menjadi array berdasarkan karakter atau string separator yang ditentukan.

```javascript
let kalimat = "Halo dunia";
let kataArray = kalimat.split(" ");
console.log(kataArray); // Output: ["Halo", "dunia"]
```

## 4. Filter
Metode `filter()` mengembalikan array baru berisi elemen-elemen yang memenuhi kondisi tertentu. Elemen-elemen yang tidak sesuai kondisi akan diabaikan.

```javascript
let angka = [1, 2, 3, 4, 5];
let angkaGenap = angka.filter(element => element % 2 === 0);
console.log(angkaGenap); // Output: [2, 4]
```

## 5. Join
Metode `join()` digunakan untuk menggabungkan elemen-elemen array menjadi satu string, dengan separator yang bisa ditentukan.

```javascript
let buah = ["Apel", "Jeruk", "Mangga"];
let buahString = buah.join(", ");
console.log(buahString); // Output: "Apel, Jeruk, Mangga"
```

## 6. Concat
Metode `concat()` digunakan untuk menggabungkan dua atau lebih array menjadi satu array baru.

```javascript
let buah1 = ["Apel", "Jeruk"];
let buah2 = ["Mangga", "Pisang"];
let gabunganBuah = buah1.concat(buah2);
console.log(gabunganBuah); // Output: ["Apel", "Jeruk", "Mangga", "Pisang"]
```

## 7. Parse (JSON to Object)
Metode `JSON.parse()` digunakan untuk mengonversi string JSON menjadi object JavaScript.

```javascript
let jsonString = '{"nama": "Ikhwan", "umur": 25}';
let objek = JSON.parse(jsonString);
console.log(objek.nama); // Output: "Ikhwan"
```

## 8. Assign
Metode `Object.assign()` digunakan untuk menyalin nilai dari satu atau lebih objek sumber ke objek target. Metode ini mengembalikan objek target.

```javascript
let objek1 = { nama: "Ikhwan" };
let objek2 = { umur: 25 };
let gabunganObjek = Object.assign({}, objek1, objek2);
console.log(gabunganObjek); // Output: { nama: "Ikhwan", umur: 25 }
```

## 9. Slice
Metode `slice()` mengembalikan salinan sebagian dari array, mulai dari indeks awal hingga indeks akhir (indeks akhir tidak termasuk).

```javascript
let angka = [1, 2, 3, 4, 5];
let subArray = angka.slice(1, 4);
console.log(subArray); // Output: [2, 3, 4]
```

## 10. Local Storage
`localStorage` digunakan untuk menyimpan data secara lokal dalam browser yang dapat bertahan setelah halaman di-refresh atau browser ditutup.

```javascript
// Menyimpan Data
localStorage.setItem("nama", "Ikhwan");

// Mengambil Data
let nama = localStorage.getItem("nama");
console.log(nama); // Output: "Ikhwan"

// Menghapus Data
localStorage.removeItem("nama");

// Menghapus Semua Data
localStorage.clear();
```

