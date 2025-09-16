## 🚀 Hasil Akhir yang Akan Dibuat

* Daftar posting dalam kartu (card) Bootstrap
* Pencarian (search), filter kategori, dan urutkan (sort) di sisi klien
* Modal detail posting
* Tombol **Tambah Dummy Post** (DOM manipulasi)
* Tombol **Export JSON** (unduh `posts.json` dari state saat ini)
* (Opsional) Memisahkan data ke `posts.json` menggunakan `fetch()`

---

## 🧰 Prasyarat

* Browser modern (Chrome/Edge/Firefox/Safari)
* **Tidak wajib** install apa pun. Namun untuk fitur `fetch('posts.json')`, jalankan melalui **server lokal** (pilih salah satu: Node, Python, PHP, atau VSCode Live Server)

---

## 🗂️ Struktur Proyek

```
jsonblog-demo/
├─ index.html        # Aplikasi satu-berkas (paling mudah)
└─ posts.json        # (Opsional) Data dipisah, dimuat via fetch
```

---

## 1) Buat Folder Proyek

Buat folder bernama `jsonblog-demo` (atau nama lain yang Anda suka).

---

## 2) Buat `index.html`

Salin kode lengkap berikut ke file `index.html`.

> Sudah termasuk Bootstrap 5 (CDN), Bootstrap Icons, komponen UI, logika filter/pencarian/sortir, modal detail, serta utilitas ekspor JSON.

```html
<!doctype html>
<html lang="id">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Demo Blog Dinamis · Bootstrap + JSON</title>
  <!-- Bootstrap 5 -->
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet" />
  <style>
    body { background: #f7f7fb; }
    .post-card{ transition: transform .15s ease; }
    .post-card:hover{ transform: translateY(-2px); }
    .cover { object-fit: cover; height: 180px; }
    .badge-tag { font-weight: 500; }
    .markdown p { margin-bottom: 1rem; }
    .sticky-top-controls { top: .75rem; z-index: 1020; }
  </style>
</head>
<body>
  <!-- Navbar -->
  <nav class="navbar navbar-expand-lg bg-body-tertiary border-bottom">
    <div class="container">
      <a class="navbar-brand fw-bold" href="#">JSONBlog<span class="text-primary">Demo</span></a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#nav" aria-controls="nav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div id="nav" class="collapse navbar-collapse">
        <ul class="navbar-nav ms-auto mb-2 mb-lg-0">
          <li class="nav-item"><a class="nav-link active" href="#">Beranda</a></li>
          <li class="nav-item"><a class="nav-link" href="#" id="btnAbout">Tentang</a></li>
          <li class="nav-item"><a class="nav-link" href="#" id="btnExport">Export JSON</a></li>
        </ul>
      </div>
    </div>
  </nav>

  <!-- Header -->
  <header class="py-5 bg-white border-bottom">
    <div class="container">
      <div class="row align-items-center g-3">
        <div class="col-md-8">
          <h1 class="display-6 mb-2">Blog Dinamis dengan <span class="text-primary">Bootstrap</span> & <span class="text-success">JavaScript DOM</span></h1>
          <p class="text-secondary mb-0">Contoh sederhana memuat konten dari <code>JSON</code>, menampilkan daftar posting, pencarian, filter kategori, dan modal detail.</p>
        </div>
        <div class="col-md-4 text-md-end">
          <button class="btn btn-primary" id="btnAddDummy"><i class="bi bi-plus-lg me-1"></i>Tambah Dummy Post</button>
        </div>
      </div>
    </div>
  </header>

  <!-- Controls -->
  <section class="py-3">
    <div class="container">
      <div class="row g-3 align-items-center sticky-top sticky-top-controls">
        <div class="col-12 col-lg-3">
          <div class="input-group">
            <span class="input-group-text"><i class="bi bi-search"></i></span>
            <input id="q" type="search" class="form-control" placeholder="Cari judul, ringkas, atau tag..." />
          </div>
        </div>
        <div class="col-6 col-lg-3">
          <select id="category" class="form-select">
            <option value="">Semua Kategori</option>
          </select>
        </div>
        <div class="col-6 col-lg-3">
          <select id="sort" class="form-select">
            <option value="newest">Terbaru</option>
            <option value="oldest">Terlama</option>
            <option value="title">Judul A→Z</option>
          </select>
        </div>
        <div class="col-12 col-lg-3 text-lg-end">
          <span class="text-muted small">Jumlah: <span id="count">0</span> post</span>
        </div>
      </div>
    </div>
  </section>

  <!-- List -->
  <main class="py-2">
    <div class="container">
      <div id="grid" class="row g-4"></div>
    </div>
  </main>

  <!-- Footer -->
  <footer class="py-5 mt-4 border-top bg-white">
    <div class="container text-center">
      <p class="mb-1">Contoh oleh <strong>JSONBlogDemo</strong>. Bebas dimodifikasi.</p>
      <small class="text-secondary">Bootstrap 5 · Vanilla JS · DOM · JSON</small>
    </div>
  </footer>

  <!-- Post Modal -->
  <div class="modal fade" id="postModal" tabindex="-1" aria-hidden="true">
    <div class="modal-dialog modal-lg modal-dialog-scrollable">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="postTitle">Judul</h5>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="modal-body">
          <img id="postCover" class="img-fluid rounded mb-3" alt="cover" />
          <div class="d-flex flex-wrap gap-2 mb-3">
            <span id="postMeta" class="badge text-bg-light"></span>
            <span id="postCategory" class="badge text-bg-primary"></span>
            <span id="postTags"></span>
          </div>
          <div id="postContent" class="markdown"></div>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-outline-secondary" data-bs-dismiss="modal">Tutup</button>
        </div>
      </div>
    </div>
  </div>

  <!-- Icons & Bootstrap JS -->
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.css" />
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>

  <script>
    // ==============================
    // 1) DATA: JSON contoh (bisa diganti fetch ke posts.json)
    // ==============================
    /** Struktur disarankan:
     * {
     *   posts: [
     *     { id, title, author, date, excerpt, content, category, tags[], cover }
     *   ]
     * }
     */
    const SAMPLE_DATA = {
      posts: [
        {
          id: 1,
          title: "Memulai Website Dinamis dengan JSON",
          author: "Tim UTB",
          date: "2025-09-10",
          excerpt: "Belajar memuat konten blog dari JSON dan memanipulasi DOM tanpa framework.",
          content: `
            <p>Pada materi ini kita menggunakan <strong>Bootstrap 5</strong> dan <em>Vanilla JavaScript</em> untuk merender konten dari sebuah objek <code>JSON</code>.</p>
            <p>Keunggulannya: sederhana, cepat, dan mudah dikembangkan menjadi headless blog.</p>
            <ul>
              <li>Struktur data ringkas</li>
              <li>DOM API untuk membuat elemen</li>
              <li>Filter & pencarian sederhana</li>
            </ul>
          `,
          category: "Dasar",
          tags: ["json", "dom", "bootstrap"],
          cover: "https://picsum.photos/seed/json1/800/400"
        },
        {
          id: 2,
          title: "Membuat Kartu Postingan dengan Bootstrap",
          author: "Nocturnailed",
          date: "2025-09-12",
          excerpt: "Gunakan komponen Card untuk menampilkan daftar posting yang rapi.",
          content: `
            <p>Bootstrap Card memudahkan penataan daftar posting. Kita tinggal mengisi gambar sampul, judul, ringkasan, dan tombol detail.</p>
            <p>Tip: gunakan <code>row row-cols-*</code> agar grid responsif.</p>
          `,
          category: "UI",
          tags: ["bootstrap", "card", "grid"],
          cover: "https://picsum.photos/seed/json2/800/400"
        },
        {
          id: 3,
          title: "Pencarian & Filter Kategori di Front-End",
          author: "Direktorat Data & Informasi",
          date: "2025-09-14",
          excerpt: "Implementasi filter client-side: input cari, kategori, dan urutkan.",
          content: `
            <p>Pencarian dilakukan dengan mencocokkan kata kunci terhadap judul, ringkas, dan tag.</p>
            <p>Filter kategori cukup bandingkan field <code>category</code>. Sorting dapat berdasarkan tanggal atau judul.</p>
          `,
          category: "Fitur",
          tags: ["filter", "search", "sort"],
          cover: "https://picsum.photos/seed/json3/800/400"
        },
        {
          id: 4,
          title: "Memisah Konten ke posts.json (Opsional)",
          author: "PUSDATIN",
          date: "2025-09-15",
          excerpt: "Untuk produksi, simpan data ke file JSON terpisah dan konsumsi via fetch.",
          content: `
            <p>Anda bisa membuat <code>posts.json</code> lalu muat dengan <code>fetch</code>. Pastikan Anda menjalankan via server lokal (bukan <code>file://</code>).</p>
            <pre><code>fetch('posts.json')\n  .then(r =&gt; r.json())\n  .then(json =&gt; init(json));</code></pre>
          `,
          category: "Deployment",
          tags: ["fetch", "json", "server"],
          cover: "https://picsum.photos/seed/json4/800/400"
        }
      ]
    };

    // ==============================
    // 2) STATE & ELEMENTS
    // ==============================
    let STATE = { posts: [], q: '', category: '', sort: 'newest' };
    const elGrid = document.getElementById('grid');
    const elCount = document.getElementById('count');
    const elQ = document.getElementById('q');
    const elCategory = document.getElementById('category');
    const elSort = document.getElementById('sort');

    // ==============================
    // 3) INIT: bisa pakai SAMPLE_DATA atau fetch posts.json
    // ==============================
    // Untuk demo ini kita pakai data lokal:
    init(SAMPLE_DATA);

    // Jika ingin dari file posts.json, aktifkan ini dan jalankan dengan server lokal:
    // fetch('posts.json').then(r => r.json()).then(json => init(json));

    function init(json){
      STATE.posts = json.posts || [];
      buildCategoryOptions(STATE.posts);
      render();
      bindEvents();
    }

    // ==============================
    // 4) RENDERING
    // ==============================
    function render(){
      const list = filterAndSort(STATE.posts, STATE);
      elCount.textContent = list.length;
      renderGrid(list);
    }

    function renderGrid(list){
      // Bersihkan grid
      elGrid.innerHTML = '';
      if(list.length === 0){
        elGrid.innerHTML = `<div class=\"col-12 text-center text-muted py-5\">Tidak ada posting yang cocok.</div>`;
        return;
      }

      // Buat fragment agar efisien
      const frag = document.createDocumentFragment();
      list.forEach(post => frag.appendChild(createPostCol(post)));
      elGrid.appendChild(frag);
    }

    function createPostCol(post){
      // elemen kolom
      const col = document.createElement('div');
      col.className = 'col-12 col-md-6 col-lg-4';

      // kartu
      const card = document.createElement('div');
      card.className = 'card h-100 shadow-sm post-card';
      card.innerHTML = `
        <img class=\"card-img-top cover\" src=\"${post.cover}\" alt=\"${escapeHtml(post.title)}\"/>
        <div class=\"card-body d-flex flex-column\">
          <div class=\"d-flex gap-2 align-items-center mb-2\">
            <span class=\"badge text-bg-primary\">${escapeHtml(post.category)}</span>
            <small class=\"text-muted\">${formatDate(post.date)}</small>
          </div>
          <h5 class=\"card-title\">${escapeHtml(post.title)}</h5>
          <p class=\"card-text text-secondary\">${escapeHtml(post.excerpt)}</p>
          <div class=\"mt-auto d-flex flex-wrap gap-1 mb-2\">${post.tags.map(t=>`<span class='badge rounded-pill text-bg-light badge-tag'>#${escapeHtml(t)}</span>`).join('')}</div>
          <button class=\"btn btn-outline-primary w-100\" data-post-id=\"${post.id}\">Baca Selengkapnya</button>
        </div>`;

      // tombol detail
      card.querySelector('button').addEventListener('click', () => openModal(post));
      col.appendChild(card);
      return col;
    }

    function openModal(post){
      document.getElementById('postTitle').textContent = post.title;
      document.getElementById('postCover').src = post.cover;
      document.getElementById('postMeta').textContent = `${post.author} · ${formatDate(post.date)}`;
      document.getElementById('postCategory').textContent = post.category;
      document.getElementById('postTags').innerHTML = post.tags.map(t=>`<span class='badge rounded-pill text-bg-secondary me-1'>#${escapeHtml(t)}</span>`).join('');
      document.getElementById('postContent').innerHTML = post.content;
      const modal = new bootstrap.Modal('#postModal');
      modal.show();
    }

    // ==============================
    // 5) FILTER, SORT, UTIL
    // ==============================
    function filterAndSort(posts, {q, category, sort}){
      const qx = q.trim().toLowerCase();
      let result = posts.filter(p => {
        const hay = [p.title, p.excerpt, ...(p.tags||[])].join(' ').toLowerCase();
        const matchQ = qx === '' || hay.includes(qx);
        const matchCat = !category || p.category === category;
        return matchQ && matchCat;
      });

      if(sort === 'newest') result.sort((a,b)=> new Date(b.date) - new Date(a.date));
      if(sort === 'oldest') result.sort((a,b)=> new Date(a.date) - new Date(b.date));
      if(sort === 'title')  result.sort((a,b)=> a.title.localeCompare(b.title, 'id'));
      return result;
    }

    function buildCategoryOptions(posts){
      const cats = Array.from(new Set(posts.map(p=>p.category))).sort((a,b)=>a.localeCompare(b,'id'));
      cats.forEach(c => {
        const opt = document.createElement('option');
        opt.value = c; opt.textContent = c;
        document.getElementById('category').appendChild(opt);
      });
    }

    function formatDate(iso){
      const d = new Date(iso);
      return d.toLocaleDateString('id-ID', { year:'numeric', month:'short', day:'numeric' });
    }

    function escapeHtml(str=''){
      return str.replace(/[&<>"']/g, s => ({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;','\'':'&#39;'}[s]));
    }

    // ==============================
    // 6) EVENTS & DEMO ACTIONS
    // ==============================
    function bindEvents(){
      document.getElementById('q').addEventListener('input', (e)=>{ STATE.q = e.target.value; render(); });
      document.getElementById('category').addEventListener('change', (e)=>{ STATE.category = e.target.value; render(); });
      document.getElementById('sort').addEventListener('change', (e)=>{ STATE.sort = e.target.value; render(); });

      document.getElementById('btnAddDummy').addEventListener('click', addDummyPost);
      document.getElementById('btnAbout').addEventListener('click', showAbout);
      document.getElementById('btnExport').addEventListener('click', exportJSON);
    }

    function addDummyPost(){
      const id = Math.max(...STATE.posts.map(p=>p.id)) + 1;
      const now = new Date();
      const post = {
        id,
        title: `Contoh Post #${id}`,
        author: "Admin",
        date: now.toISOString().slice(0,10),
        excerpt: "Ini adalah posting dummy yang ditambahkan lewat DOM.",
        content: `<p>Konten dibuat secara dinamis menggunakan <code>document.createElement</code> dan manipulasi array <code>STATE.posts</code>.</p>` ,
        category: "Demo",
        tags: ["demo","dom"],
        cover: `https://picsum.photos/seed/${id}/800/400`
      };
      STATE.posts.unshift(post);
      render();
    }

    function showAbout(){
      const about = {
        title: "Tentang Demo",
        cover: "https://picsum.photos/seed/about/800/400",
        author: "JSONBlogDemo",
        date: new Date().toISOString().slice(0,10),
        category: "Info",
        tags: ["tentang","demo"],
        content: `<p>Demo ini menunjukkan pola dasar <strong>headless blog</strong>—konten dipisah dari tampilan. Anda bebas mengganti <code>SAMPLE_DATA</code> dengan <code>fetch('posts.json')</code>.</p>`
      };
      openModal(about);
    }

    function exportJSON(){
      const blob = new Blob([JSON.stringify({posts: STATE.posts}, null, 2)], {type:'application/json'});
      const url = URL.createObjectURL(blob);
      const a = Object.assign(document.createElement('a'), { href: url, download: 'posts.json' });
      document.body.appendChild(a); a.click(); a.remove();
      URL.revokeObjectURL(url);
    }
  </script>
</body>
</html>
```

> **Catatan:** Gambar sampul memakai placeholder `https://picsum.photos/...`. Anda boleh ganti URL gambar sendiri.

---

## 3) (Opsional) Pisahkan Data ke `posts.json`

Jika ingin memisahkan konten dari tampilan, buat file `posts.json`:

```json
{
  "posts": [
    {
      "id": 1,
      "title": "Contoh Post di posts.json",
      "author": "Admin",
      "date": "2025-09-16",
      "excerpt": "Ringkasan singkat posting dari file JSON.",
      "content": "<p>Konten <strong>HTML</strong> di-load dari file JSON eksternal.</p>",
      "category": "Info",
      "tags": ["json", "external"],
      "cover": "https://picsum.photos/seed/ext1/800/400"
    }
  ]
}
```

Lalu ubah bagian inisialisasi di `index.html` (komentari baris `init(SAMPLE_DATA)` dan aktifkan `fetch`):

```js
// init(SAMPLE_DATA);
fetch('posts.json').then(r => r.json()).then(json => init(json));
```

> **Penting:** `fetch()` tidak berjalan di `file://`. Anda harus menjalankan via **server lokal** (lihat langkah berikut).

---

## 4) Jalankan Server Lokal (Pilih Salah Satu)

### Opsi A — Node.js

```bash
# dari dalam folder proyek
npx serve . -p 5173
# buka http://localhost:5173
```

### Opsi B — Python 3

```bash
python -m http.server 8000
# buka http://localhost:8000
```

### Opsi C — PHP

```bash
php -S localhost:8000
# buka http://localhost:8000
```

### Opsi D — VS Code Live Server

* Buka folder di VS Code → klik kanan `index.html` → **Open with Live Server**.

---

## 5) Uji Fitur

* Ketik di kolom **Cari** → daftar menyaring berdasarkan judul/ringkasan/tag.
* Pilih **Kategori** → tampilkan hanya kategori tertentu.
* Ubah **Urutkan** → Terbaru/Terlama/Judul A→Z.
* Klik **Baca Selengkapnya** → modal detail terbuka.
* Klik **Tambah Dummy Post** → item baru ditambahkan ke atas daftar (DOM update).
* Klik **Export JSON** → unduh data saat ini sebagai `posts.json`.

---

## 6) Skema Data & Tips Konten

### Skema `post` yang digunakan

```ts
interface Post {
  id: number;
  title: string;
  author: string;
  date: string;      // format ISO: YYYY-MM-DD
  excerpt: string;   // ringkasan singkat
  content: string;   // HTML yang aman untuk ditampilkan
  category: string;  // satu kategori per post (bisa diperluas)
  tags: string[];    // daftar tag
  cover: string;     // URL gambar sampul
}
```

**Tips:**

* Gunakan tanggal format `YYYY-MM-DD` agar sorting berjalan benar.
* `content` mendukung HTML sederhana. Hindari script/tag berbahaya.
* Pastikan `id` unik untuk setiap post.
* Kategori untuk filter diambil otomatis dari `posts[].category`.

---

## 7) Kustomisasi Cepat

* **Branding**: ubah teks brand di navbar `JSONBlogDemo`.
* **Tema**: ganti CSS di `<style>` atau tambahkan kelas Bootstrap (mis. `text-bg-dark`).
* **Layout**: ubah kolom grid `col-12 col-md-6 col-lg-4` (mis. jadi 3/4 kolom).
* **Sumber Data**: sambungkan ke API/headless CMS → ganti `fetch('posts.json')` dengan endpoint Anda.
* **Keamanan Konten**: jika `content` berasal dari user, lakukan sanitasi HTML di server.

---

## 8) Deploy (Mudah)

### GitHub Pages

1. Buat repo → commit `index.html` (+ `posts.json` bila ada)
2. Push ke GitHub
3. Settings → Pages → Source: `main`/`docs` → Save
4. Akses URL GitHub Pages yang diberikan

### Netlify / Vercel

* Drag-and-drop folder ke Netlify
* Atau klik **New Project** di Vercel → import repo → deploy

---

## 9) Troubleshooting

* **Blank saat pakai fetch**: Anda membuka via `file://`. Jalankan server lokal (Langkah 4).
* **CDN tidak ter-load**: Cek koneksi internet/akses CDN. Bisa unduh Bootstrap lokal jika perlu.
* **Gambar tidak tampil**: Ganti URL `cover` dengan gambar valid.
* **Tanggal tidak terurut**: Pastikan format `YYYY-MM-DD`.
