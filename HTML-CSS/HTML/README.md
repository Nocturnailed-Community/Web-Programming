# Materi HTML

## 1. HTML (Struktur HTML, Tag, Atribut, Value, Nested Tag)

**HTML (HyperText Markup Language)** adalah bahasa standar untuk membuat halaman web. Struktur dasar HTML terdiri dari elemen-elemen yang dibatasi oleh tag pembuka (<tag>) dan penutup (</tag>). Setiap elemen HTML dapat memiliki atribut yang berfungsi untuk menambahkan informasi atau fungsi tambahan pada elemen tersebut.

- Tag: Digunakan untuk mendefinisikan elemen HTML. Contoh tag: <html>, <head>, <body>, <p>, <div>.
- Atribut: Menyediakan informasi tambahan pada elemen, ditulis di dalam tag pembuka. Contoh atribut: id, class, style.
- Value: Nilai yang diberikan untuk atribut, misalnya class="container".
- Nested Tag: Tag yang ditempatkan di dalam tag lain.

**Struktur Dasar HTML**:

```html

<!DOCTYPE html>  
<html lang="en">  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport" content="width=device-width, initial-scale=1.0">  
    <title>Dokumen HTML</title>  
</head>  
<body>  
    <h1>Judul Halaman</h1>  
    <p>Ini adalah paragraf pertama di dalam dokumen HTML ini.</p>  
</body>  
</html>  
```
### Penjelasan:
- <!DOCTYPE html>: Deklarasi tipe dokumen.
- <html>: Elemen utama HTML.
- <head>: Berisi informasi meta dan judul.
- <body>: Berisi konten yang akan ditampilkan pada halaman.

## 2. HTML (Text Formatting, Heading Tag, List)

### Text Formatting (Pemformatan Teks)
HTML menyediakan tag untuk memformat teks:

- <b>: Teks tebal (bold).
- <i>: Teks miring (italic).
- <u>: Garis bawah (underline).
- <mark>: Sorot teks.

### Heading Tag
Heading digunakan untuk judul dengan tingkat penting yang berbeda. Terdapat enam tingkat heading, dari <h1> (paling penting) hingga <h6> (paling rendah).

```html

<h1>Judul Utama</h1>  
<h2>Subjudul 1</h2>  
<h3>Subjudul 2</h3>  
```
### List
Terdapat dua jenis list di HTML:

**Ordered List (List Berurut)**: Menggunakan angka atau huruf.
```html

<ol>  
    <li>Item Pertama</li>  
    <li>Item Kedua</li>  
    <li>Item Ketiga</li>  
</ol>  
```
**Unordered List (List Tidak Berurut)**: Menggunakan bullet (titik).
```html

<ul>  
    <li>Item Pertama</li>  
    <li>Item Kedua</li>  
    <li>Item Ketiga</li>  
</ul>  
```

## 3. HTML (Form Input, Button, Hyperlink)

### Form Input
Formulir digunakan untuk mengumpulkan data pengguna, dengan berbagai jenis input seperti teks, email, password, checkbox, dan radio.

```html

<form action="/submit" method="POST">  
    <label for="name">Nama:</label>  
    <input type="text" id="name" name="name" required><br>  
    <label for="email">Email:</label>  
    <input type="email" id="email" name="email" required><br>  

    <input type="checkbox" id="agree" name="agree" value="yes">  
    <label for="agree">Saya setuju dengan syarat dan ketentuan</label><br>  

    <input type="radio" id="male" name="gender" value="male">  
    <label for="male">Laki-laki</label>  
    <input type="radio" id="female" name="gender" value="female">  
    <label for="female">Perempuan</label><br>  
</form>  
```
### Button (Tombol)
HTML menyediakan berbagai cara untuk membuat tombol.

- Tombol di dalam form:

```html
<button type="submit">Kirim</button>
```

- Tombol standalone:

```html
<button type="button" onclick="alert('Hello!')">Klik Saya</button>
```

### Hyperlink (Tautan)
Hyperlink digunakan untuk menghubungkan halaman lain atau dokumen eksternal.

```html
<a href="https://www.google.com">Kunjungi Google</a>
```

## 4. HTML (Image dan Table)

### Image (Gambar)
Gambar di HTML menggunakan tag <img>, dengan atribut src untuk mengatur sumber gambar dan alt untuk teks alternatif.

```html
<img src="gambar.jpg" alt="Deskripsi Gambar" width="300" height="200">
```

### Table (Tabel)
Tabel digunakan untuk menampilkan data dalam bentuk baris dan kolom.

```html

<table border="1">  
    <tr>  
        <th>Nama</th>  
        <th>Umur</th>  
    </tr>  
    <tr>  
        <td>Andi</td>  
        <td>25</td>  
    </tr>  
    <tr>  
        <td>Budi</td>  
        <td>30</td>  
    </tr>  
</table>  
```
### Penjelasan:
- <table>: Mendefinisikan tabel.
- <tr>: Baris tabel.
- <th>: Header kolom.
- <td>: Sel data.