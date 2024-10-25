# Materi DOM di JavaScript

## 1. Perkenalan Apa Itu DOM
DOM (Document Object Model) adalah representasi struktur dokumen HTML atau XML dalam bentuk pohon yang memungkinkan Anda untuk memanipulasi dan mengubah konten, struktur, dan gaya halaman web menggunakan JavaScript. DOM menyediakan antarmuka untuk berinteraksi dengan elemen-elemen di dalam halaman web.

---

## 2. Menggunakan Method `getElementById()`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Contoh getElementById</title>
</head>
<body>
    <p id="contoh">Teks awal</p>
    <script>
        // Mengambil elemen dengan ID "contoh"
        let elemen = document.getElementById("contoh");

        // Mengubah teks dari elemen
        elemen.innerText = "Teks baru";
    </script>
</body>
</html>
```

## 3. Perkenalan dengan `innerHTML` dan `innerText` (Set and Return)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Contoh innerHTML dan innerText</title>
</head>
<body>
    <div id="contoh">Teks HTML awal</div>
    <script>
        // Mengambil elemen dengan ID "contoh"
        let elemen = document.getElementById("contoh");

        // Mengatur HTML konten
        elemen.innerHTML = "<strong>Teks HTML Baru</strong>";

        // Mengatur teks tanpa HTML
        elemen.innerText = "Teks Plain Baru";

        // Mendapatkan HTML konten
        console.log(elemen.innerHTML); // Output: <strong>Teks HTML Baru</strong>

        // Mendapatkan teks tanpa HTML
        console.log(elemen.innerText); // Output: Teks Plain Baru
    </script>
</body>
</html>
```

## 4. Memperkenalkan `getElementsByTagName` dan `getElementsByClassName`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Contoh getElementsByTagName dan getElementsByClassName</title>
</head>
<body>
    <p class="contoh">Paragraf 1</p>
    <p class="contoh">Paragraf 2</p>
    <p>Paragraf 3</p>
    <script>
        // Mengambil semua elemen <p>
        let paragraf = document.getElementsByTagName("p");
        console.log(paragraf);

        // Mengambil semua elemen dengan kelas "contoh"
        let contohClass = document.getElementsByClassName("contoh");
        console.log(contohClass);
    </script>
</body>
</html>
```

## 5. Mengenal Method `setAttribute`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Contoh setAttribute</title>
</head>
<body>
    <div id="contoh">Elemen Contoh</div>
    <script>
        // Mengambil elemen dengan ID "contoh"
        let elemen = document.getElementById("contoh");

        // Mengatur atribut "data-info"
        elemen.setAttribute("data-info", "Informasi tambahan");

        // Menampilkan nilai atribut "data-info"
        console.log(elemen.getAttribute("data-info")); // Output: Informasi tambahan
    </script>
</body>
</html>
```

## 6. Mengenal Method `remove()`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Contoh remove()</title>
</head>
<body>
    <div id="contoh">Elemen yang akan dihapus</div>
    <script>
        // Mengambil elemen dengan ID "contoh"
        let elemen = document.getElementById("contoh");

        // Menghapus elemen
        elemen.remove();
    </script>
</body>
</html>
```

## 7. Mengenal `onClick` Attribute pada Element

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Contoh onClick</title>
</head>
<body>
    <button id="klikSaya">Klik Saya!</button>
    <script>
        // Fungsi yang akan dijalankan saat elemen diklik
        function klikSaya() {
            alert("Elemen diklik!");
        }

        // Mengambil elemen dengan ID "klikSaya"
        let tombol = document.getElementById("klikSaya");

        // Menetapkan event handler onClick
        tombol.onclick = klikSaya;
    </script>
</body>
</html>
```

## 8. JSON

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Contoh JSON</title>
</head>
<body>
    <script>
        // Object JavaScript
        let data = {
            nama: "Ikhwan",
            umur: 25,
            jurusan: "Teknik Informatika"
        };

        // Mengubah object menjadi string JSON
        let jsonData = JSON.stringify(data);
        console.log(jsonData); // Output: {"nama":"Ikhwan","umur":25,"jurusan":"Teknik Informatika"}

        // Mengubah string JSON kembali menjadi object
        let objekData = JSON.parse(jsonData);
        console.log(objekData.nama); // Output: "Ikhwan"
    </script>
</body>
</html>
```