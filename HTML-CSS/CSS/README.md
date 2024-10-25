## 5. HTML & CSS (Div, Span, Selector, Color, Background Color, Display Block dan Inline)

### Div dan Span
- <div> dan <span> adalah elemen HTML yang digunakan sebagai kontainer untuk mengelompokkan elemen lainnya.

- <div>: Elemen block-level yang akan menampilkan elemen secara vertikal (memulai baris baru).
- <span>: Elemen inline-level yang tidak memulai baris baru.

```html

<div class="container">  
    <h1>Judul di dalam Div</h1>  
    <p>Paragraf di dalam div</p>  
</div>  
<span class="highlight">Teks di dalam span</span>
```

### CSS Selector
Selector digunakan untuk memilih elemen mana yang akan diterapkan gaya (style) menggunakan CSS.

- Selector Berdasarkan Tag: Menerapkan gaya ke semua elemen dari tag tertentu.
- Selector Berdasarkan Class: Menerapkan gaya ke elemen dengan class tertentu.
- Selector Berdasarkan ID: Menerapkan gaya ke elemen dengan ID tertentu.

```css
/* Berdasarkan Tag */
p {
color: red;
}

/* Berdasarkan Class */
.container {
background-color: lightgray;
}

/* Berdasarkan ID */
#main-title {
font-size: 24px;
}
```

### Color (Warna Teks)
Mengatur warna teks pada elemen menggunakan properti color.

```css
p {
color: blue;
}
```

### Background Color (Warna Latar)
Mengatur warna latar belakang elemen menggunakan properti background-color.

```css
div {
background-color: lightyellow;
}
```

### Display Block dan Inline
- Display Block: Elemen dengan display block akan memulai baris baru (block-level).
- Display Inline: Elemen inline tidak memulai baris baru dan akan ditampilkan dalam satu baris (inline-level).

```css
div {
display: block;
}

span {
display: inline;
}
```

## 6. HTML & CSS (Text Formatting, Size, Pseudo Class atau Element)

### Text Formatting (Pemformatan Teks dengan CSS)
CSS menyediakan properti untuk memformat teks, seperti ukuran font, ketebalan, gaya, dan sebagainya.

```css
p {
font-size: 16px; /* Ukuran Teks /
font-weight: bold; / Ketebalan Teks /
font-style: italic; / Gaya Teks /
text-align: center; / Perataan Teks /
color: green; / Warna Teks */
}
```

### Font Size (Ukuran Teks)
Ukuran teks dapat diatur menggunakan properti font-size.

```css
h1 {
font-size: 32px;
}

p {
font-size: 14px;
}
```

### Pseudo Class
Pseudo class digunakan untuk menargetkan elemen HTML dalam kondisi tertentu, seperti saat hover atau ketika elemen aktif.

```css
a
{
color: red; /* Mengubah warna teks ketika link di-hover */
}

button
{
background-color: yellow; /* Mengubah warna tombol ketika ditekan */
}
```

### Pseudo Element
Pseudo element digunakan untuk menambahkan gaya pada bagian tertentu dari elemen, seperti teks pertama, atau konten yang tidak ada di HTML.

```css
p::first-letter {
font-size: 2em; /* Membesarkan huruf pertama pada paragraf */
color: purple;
}

div::after {
content: ' - Tambahan Konten'; /* Menambahkan konten setelah elemen */
color: gray;
}
```