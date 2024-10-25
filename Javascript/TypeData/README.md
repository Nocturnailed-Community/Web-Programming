# Materi Tipe Data di JavaScript

## 1. Tipe Data, Variable, Operator Aritmatika

### Tipe Data dalam JavaScript
Tipe data di JavaScript digunakan untuk mendefinisikan jenis nilai yang disimpan dalam variabel. Ada beberapa tipe data dasar di JavaScript:

- String: Teks yang diapit oleh tanda kutip (', ", atau ` \).
- Number: Angka, baik bilangan bulat maupun pecahan (integer dan float).
- Boolean: Hanya memiliki dua nilai: true atau false.
- Undefined: Nilai variabel yang belum ditetapkan.
- Null: Nilai khusus yang menyatakan "kosong".

### Variabel di JavaScript
Variabel digunakan untuk menyimpan data. Ada beberapa cara untuk mendeklarasikan variabel di JavaScript:

- var: Variabel global atau lokal, namun lebih rentan terhadap masalah hoisting.
- let: Variabel yang bisa diubah, memiliki cakupan blok.
- const: Variabel yang nilainya tetap (konstanta), tidak dapat diubah setelah dideklarasikan.

```javascript
// Deklarasi variabel dengan let
let nama = "Ikhwan"; // String
let umur = 25; // Number
let statusAktif = true; // Boolean

// Variabel dengan const
const PI = 3.14159; // Konstanta
```

### Operator Aritmatika
Operator aritmatika digunakan untuk melakukan operasi matematika seperti penjumlahan, pengurangan, perkalian, dll.

- +: Penjumlahan
- -: Pengurangan
- *: Perkalian
- /: Pembagian
- %: Modulus (Sisa bagi)
- ++: Increment (menambah 1)
- --: Decrement (mengurangi 1)

```javascript
let a = 10;
let b = 5;

let hasilPenjumlahan = a + b; // 15
let hasilPengurangan = a - b; // 5
let hasilPerkalian = a * b; // 50
let hasilPembagian = a / b; // 2
let hasilModulus = a % b; // 0

a++; // a menjadi 11
b--; // b menjadi 4
```

## 2. Tipe Data Lanjutan: Array, Object, & JSON

### Array
Array adalah tipe data yang dapat menyimpan banyak nilai dalam satu variabel. Nilai dalam array diakses menggunakan indeks, di mana indeks pertama dimulai dari 0.

```javascript
let angka = [1, 2, 3, 4, 5];
let buah = ["Apel", "Jeruk", "Mangga"];

// Akses elemen array
console.log(buah[0]); // "Apel"
console.log(angka[2]); // 3

// Mengubah elemen array
buah[1] = "Pisang";
console.log(buah); // ["Apel", "Pisang", "Mangga"]

// Menambahkan elemen ke array
buah.push("Durian");
console.log(buah); // ["Apel", "Pisang", "Mangga", "Durian"]
```

### Object
Object adalah tipe data yang menyimpan properti dalam bentuk pasangan key-value. Setiap key atau properti memiliki nama dan nilai.

```javascript
let mahasiswa = {
nama: "Ikhwan",
umur: 25,
jurusan: "Teknik Informatika",
statusAktif: true
};

// Akses properti object
console.log(mahasiswa.nama); // "Ikhwan"
console.log(mahasiswa["umur"]); // 25

// Mengubah properti object
mahasiswa.umur = 26;
console.log(mahasiswa.umur); // 26

// Menambah properti baru
mahasiswa.alamat = "Bandung";
console.log(mahasiswa.alamat); // "Bandung"
```

### JSON (JavaScript Object Notation)
JSON adalah format data yang sering digunakan untuk bertukar data antara server dan klien. JSON sangat mirip dengan object di JavaScript.

- Stringify: Mengubah object JavaScript menjadi format JSON.
- Parse: Mengubah JSON menjadi object JavaScript.

```javascript
// Object JavaScript
let dataMahasiswa = {
nama: "Ikhwan",
umur: 25,
jurusan: "Teknik Informatika"
};

// Mengubah Object menjadi JSON
let jsonData = JSON.stringify(dataMahasiswa);
console.log(jsonData); // {"nama":"Ikhwan","umur":25,"jurusan":"Teknik Informatika"}

// Mengubah JSON kembali menjadi Object
let objectData = JSON.parse(jsonData);
console.log(objectData.nama); // "Ikhwan"
```