# Materi Fungsi di JavaScript

## 1. Arrow Function
Arrow function adalah sintaks baru untuk mendefinisikan fungsi yang lebih ringkas dibandingkan dengan fungsi biasa. Arrow function tidak memiliki `this` sendiri dan `arguments`.

```javascript
// Fungsi biasa
function tambah(a, b) {
    return a + b;
}

// Arrow function
const tambah = (a, b) => a + b;

console.log(tambah(2, 3)); // Output: 5
```

## 2. Anonymous Function
Anonymous function adalah fungsi yang tidak memiliki nama dan sering digunakan sebagai argumen dalam metode atau untuk fungsi satu kali pakai.

```javascript
// Fungsi biasa
// Anonymous function sebagai argumen
setTimeout(function() {
    console.log("Ini adalah anonymous function");
}, 1000);

// Arrow function sebagai anonymous function
setTimeout(() => {
    console.log("Ini adalah anonymous arrow function");
}, 1000);
```

## 3. Return
`return` digunakan untuk mengembalikan nilai dari fungsi. Setelah `return` dijalankan, fungsi akan berhenti eksekusi.

```javascript
function kali(a, b) {
    return a * b;
}

let hasil = kali(4, 5);
console.log(hasil); // Output: 20
```

## 4. Parameter
Parameter adalah variabel yang didefinisikan dalam deklarasi fungsi. Parameter berfungsi untuk menerima nilai saat fungsi dipanggil.

```javascript
// Fungsi dengan parameter default
function greet(nama = "Pengguna") {
    console.log(`Halo, ${nama}!`);
}

greet("Ikhwan"); // Output: Halo, Ikhwan!
greet(); // Output: Halo, Pengguna!
```