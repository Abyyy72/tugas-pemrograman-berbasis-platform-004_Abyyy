# Tugas Pendahuluan Pertemuan 3
## CSS Framework & Authentication vs Authorization

### Soal 1 — Bootstrap vs Tailwind

**Bootstrap:** class utama untuk kartu adalah `card`, `card-body`, `card-title`, dan untuk tombol `btn` yang dapat dikombinasikan dengan `btn-primary`.

**Tailwind CSS:** tidak menggunakan class khusus seperti `card`, tetapi menyusun kartu dari utility seperti `max-w-sm`, `rounded-xl`, `bg-white`, `p-6`, dan `shadow-lg`; tombol juga dibuat dari gabungan utility.

Menurut saya, **Bootstrap lebih mudah untuk pemula** karena komponen seperti card dan button sudah tersedia sehingga cukup menghafal beberapa class utama.

---

### Soal 2 — Kartu Biodata dengan Dua Pendekatan

Kartu biodata berisi foto, nama, NIM, dan satu tombol.

#### Pendekatan component-based (Bootstrap)

```html
<div class="card" style="width: 18rem;">
  <img src="foto.jpg" class="card-img-top" alt="Foto">
  <div class="card-body">
    <h5 class="card-title">Habiburrahman</h5>
    <p class="card-text">NIM: 2026004</p>
    <button class="btn btn-primary">Lihat Profil</button>
  </div>
</div>
```

Aturan/class utama yang digunakan: `card`, `card-img-top`, `card-body`, `card-title`, `card-text`, `btn`, dan `btn-primary`. Jika dihitung sebagai aturan komponen yang perlu dipahami, terdapat **7 class utama** dan tidak perlu menulis aturan CSS manual untuk tampilan dasarnya.

#### Pendekatan utility-first (Tailwind)

```html
<div class="max-w-sm rounded-xl bg-white p-6 shadow-lg">
  <img src="foto.jpg" class="mx-auto size-24 rounded-full object-cover" alt="Foto">
  <h2 class="mt-4 text-xl font-bold text-gray-900">Habiburrahman</h2>
  <p class="mt-1 text-gray-500">NIM: 2026004</p>
  <button class="mt-4 rounded-lg bg-blue-600 px-4 py-2 font-medium text-white hover:bg-blue-700">
    Lihat Profil
  </button>
</div>
```

Pada contoh tersebut terdapat **20 utility class**. Versi utility lebih mudah diubah secara detail karena warna, ukuran, jarak, dan bentuk dapat diganti langsung pada class yang digunakan elemen.

---

### Soal 3 — Analisis JWT

Token JWT yang diberikan terdiri dari **3 bagian**, yaitu **header, payload, dan signature**, yang dipisahkan oleh tanda titik.

Data yang terlihat pada payload adalah `sub`, `name`, dan `iat`. Password tidak boleh disimpan dalam payload JWT karena payload dapat dibaca oleh pihak yang memiliki token, sehingga password atau data rahasia dapat terekspos.

---

### Soal 4 — Authentication vs Authorization

Pada gerbang UNIRA, pemeriksaan kartu identitas atau akun untuk memastikan bahwa seseorang benar-benar mahasiswa merupakan contoh **authentication**, karena sistem memeriksa identitas pengguna.

Saat seseorang sudah terbukti sebagai mahasiswa tetapi ingin masuk ke ruang server laboratorium, pemeriksaan apakah ia memiliki izin masuk merupakan **authorization**. Contohnya, mahasiswa berhasil login tetapi tidak memiliki role yang diizinkan masuk ke ruang server, sehingga akses ditolak.

---

### Soal 5 — Peran di Aplikasi Nyata

Saya memilih **e-library** sebagai contoh aplikasi. Tiga perannya adalah **Anggota**, **Pustakawan**, dan **Pimpinan**. Fitur menambah katalog buku hanya boleh digunakan oleh Pustakawan dan Pimpinan.

Jika pengguna belum login atau token tidak valid, server memberikan **401 Unauthorized** karena identitas pengguna belum terbukti. Jika pengguna sudah login tetapi rolenya tidak memiliki izin terhadap fitur tersebut, server memberikan **403 Forbidden** karena identitasnya sudah diketahui tetapi hak aksesnya tidak mencukupi.
