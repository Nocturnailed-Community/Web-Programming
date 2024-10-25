# Pengantar Git dan GitHub

## Apa Itu Git?

Git adalah sistem kontrol versi terdistribusi yang digunakan untuk melacak perubahan dalam kode sumber selama pengembangan perangkat lunak. Git memungkinkan banyak pengembang untuk bekerja bersama secara lebih efisien dan mengelola proyek mereka dengan lebih baik.

### Fitur Utama Git:
- **Version Control**: Melacak semua perubahan yang dilakukan pada file.
- **Branching and Merging**: Membuat dan menggabungkan cabang pengembangan untuk mengelola fitur baru atau perbaikan bug.
- **Distributed Development**: Setiap pengembang memiliki salinan lengkap dari seluruh sejarah proyek.

## Apa Itu GitHub?

GitHub adalah platform hosting untuk repositori Git yang menyediakan kontrol versi dan kolaborasi. GitHub memungkinkan Anda dan orang lain untuk bekerja bersama pada proyek dari mana saja.

### Fitur Utama GitHub:
- **Repositories**: Tempat penyimpanan kode proyek.
- **Pull Requests**: Fitur untuk mengajukan perubahan dan meminta peninjauan kode.
- **Issues**: Alat untuk melacak tugas, bug, dan fitur baru.
- **Actions**: Alat CI/CD untuk mengotomatiskan alur kerja.

## Instalasi Git

Untuk menggunakan Git, Anda harus menginstalnya terlebih dahulu di komputer Anda. Berikut adalah langkah-langkah instalasi:

### Windows
1. Unduh Git dari [git-scm.com](https://git-scm.com/).
2. Jalankan installer dan ikuti petunjuk instalasi.

### macOS
1. Instal Git menggunakan Homebrew:
    ```sh
    brew install git
    ```

### Linux
1. Instal Git menggunakan paket manajer:
    ```sh
    sudo apt-get install git
    ```

## Menggunakan Git

Berikut adalah beberapa perintah dasar Git untuk memulai:

### Konfigurasi Awal
Setelah menginstal Git, konfigurasikan informasi pengguna Anda:
```sh
git config --global user.name "Nama Anda"
git config --global user.email "email@anda.com"
```

### Membuat Repositori Baru
Untuk membuat repositori baru:
```sh
mkdir nama-proyek
cd nama-proyek
git init
```

### Menambahkan File ke Repositori
Untuk menambahkan file ke repositori dan melakukan commit:
```sh
echo "# Nama Proyek" > README.md
git add README.md
git commit -m "Menambahkan README.md"
```

### Menghubungkan ke Repositori GitHub
Untuk menghubungkan repositori lokal ke repositori GitHub:
1. Buat repositori baru di GitHub.
2. Jalankan perintah berikut di terminal:
```sh
git remote add origin https://github.com/username/nama-repositori.git
git push -u origin master
```

## Menggunakan GitHub
Berikut adalah beberapa fitur utama GitHub yang sering digunakan:

### Clone Repositori
Untuk mengkloning repositori GitHub ke komputer lokal Anda:

```sh
git clone https://github.com/username/nama-repositori.git
```

### Membuat Branch Baru
Untuk membuat branch baru:

```sh
git checkout -b nama-branch
```

### Menggabungkan Branch
Untuk menggabungkan branch ke branch utama:

1. Pindah ke branch utama:

```sh
git checkout master
```

2. Gabungkan branch:

```sh
git merge nama-branch
```

### Mengirim Perubahan ke GitHub
Untuk mengirim perubahan ke repositori GitHub:

```sh
git push origin nama-branch
```

### Membuat Pull Request
Untuk membuat pull request:

1. Push branch ke GitHub.
2. Buka repositori di GitHub.
3. Klik tombol "New Pull Request".
4. Pilih branch yang ingin digabungkan dan buat pull request.

### Mengelola Issues
Untuk melacak tugas, bug, atau fitur baru, gunakan tab "Issues" di repositori GitHub Anda. Anda dapat membuat issue baru dan menetapkannya kepada anggota tim Anda.

## Contoh Penggunaan Git dan GitHub
Berikut adalah langkah-langkah untuk memulai proyek baru dan mengelola perubahan dengan Git dan GitHub:

1. Membuat Repositori Baru di GitHub:
- Buka GitHub dan buat repositori baru.
- Salin URL repositori.

2. Mengkloning Repositori ke Lokal:

```sh
git clone https://github.com/username/nama-repositori.git
cd nama-repositori
```

3. Membuat Branch Baru untuk Fitur:

```sh
git checkout -b fitur-baru
```

4. Melakukan Perubahan dan Commit:

```sh
echo "console.log('Hello, World!')" > hello.js
git add hello.js
git commit -m "Menambahkan fitur baru: hello.js"
```

5. Push Perubahan ke GitHub:

```sh
git push origin fitur-baru
```

6. Membuat Pull Request di GitHub:
- Buka repositori di GitHub.
- Klik tombol "New Pull Request".
- Pilih branch fitur-baru dan buat pull request.