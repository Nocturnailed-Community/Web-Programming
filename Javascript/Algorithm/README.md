# Materi Algoritma di JavaScript

## 1. Algoritma Kondisi

### If
Menjalankan blok kode jika kondisi tertentu benar.

```javascript
    if (kondisi) {
        // kode yang dijalankan jika kondisi benar
    }
```

### If Else
Menambahkan `else` untuk mengeksekusi blok kode jika kondisi `if` tidak benar.

```javascript
    if (kondisi) {
        // kode yang dijalankan jika kondisi benar
    } else {
        // kode yang dijalankan jika kondisi tidak benar
    }
```

### If Else If
Menambahkan beberapa kondisi dengan `else if`.

```javascript
    if (kondisi1) {
        // kode yang dijalankan jika kondisi1 benar
    } else if (kondisi2) {
        // kode yang dijalankan jika kondisi2 benar
    } else {
        // kode yang dijalankan jika semua kondisi di atas tidak benar
    }
```

### Nested If Else
Menggunakan `if` di dalam `if` untuk kondisi yang lebih kompleks.

```javascript
    if (kondisi1) {
        if (kondisi2) {
            // kode yang dijalankan jika kondisi1 dan kondisi2 benar
        } else {
            // kode yang dijalankan jika kondisi1 benar tapi kondisi2 tidak benar
        }
    } else {
        // kode yang dijalankan jika kondisi1 tidak benar
    }
```

### Ternary
Menggunakan operator ternary untuk kondisi sederhana.

```javascript
    var hasil = (kondisi) ? nilaiJikaBenar : nilaiJikaSalah;
```

### Switch Case
Menangani beberapa nilai dari satu variabel.

```javascript
    switch (ekspresi) {
        case nilai1:
            // kode yang dijalankan jika ekspresi == nilai1
            break;
        case nilai2:
            // kode yang dijalankan jika ekspresi == nilai2
            break;
        default:
            // kode yang dijalankan jika tidak ada nilai yang cocok
    }
```

## 2. Algoritma Pengulangan

### For
Looping untuk iterasi berdasarkan indeks.

```javascript
    for (var i = 0; i < 5; i++) {
        // kode yang dijalankan selama i < 5
    }
```

### Foreach
Looping khusus untuk array.

```javascript
    array.forEach(function(item) {
        // kode yang dijalankan untuk setiap item dalam array
    });
```

### While
Looping selama kondisi benar.

```javascript
    while (kondisi) {
        // kode yang dijalankan selama kondisi benar
    }
```

### Do While
Looping yang dijalankan setidaknya sekali sebelum memeriksa kondisi.

```javascript
    do {
        // kode yang dijalankan setidaknya sekali
    } while (kondisi);
```

### Nested Loop
Loop di dalam loop untuk iterasi kompleks.

```javascript
    for (var i = 0; i < 3; i++) {
        for (var j = 0; j < 3; j++) {
            // kode yang dijalankan untuk setiap kombinasi i dan j
        }
    }
```