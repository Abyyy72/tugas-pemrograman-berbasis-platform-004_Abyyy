# Tugas Pendahuluan Pertemuan 02 — Routing, HTTP, dan API

**Nama:** Abyyy  
**NIM:** 004  
**Repository:** tugas-pemrograman-berbasis-platform-004_Abyyy  
**Jenis tugas:** Individu

## Tujuan

Menganalisis API placeholder lokal pada `http://localhost:4000` untuk memahami struktur data, relasi resource, routing, query parameter, HTTP method, dan HTTP status code.

> API yang digunakan merupakan API placeholder lokal dengan data fiktif. Endpoint `/posts` dan `/users` tidak menggunakan prefix `/api/v1`.

---

## 1. Perbandingan Struktur Data `/posts/1` dan `/users/1`

### `GET /posts/1`

Contoh struktur data:

```json
{
  "id": 1,
  "userId": 1,
  "title": "Mengenal HTTP",
  "body": "Catatan fiktif praktikum nomor 1."
}
```

Field yang terdapat pada resource **post**:

| Field | Fungsi |
|---|---|
| `id` | Identitas unik untuk setiap tulisan/post. |
| `userId` | Menunjukkan pengguna yang memiliki atau membuat post. |
| `title` | Menyimpan judul tulisan. |
| `body` | Menyimpan isi tulisan. |

### `GET /users/1`

Resource **user** digunakan untuk menyimpan identitas pengguna. Struktur user berfokus pada informasi pengguna seperti identitas `id`, nama, dan informasi kontak yang tersedia pada fixture.

Perbedaan utamanya adalah **post menyimpan isi konten**, sedangkan **user menyimpan informasi pemilik/pembuat konten**. Field `userId` pada post menjadi penghubung ke `id` pada user.

---

## 2. Analisis Struktur Tabel dan Relasi `posts` dengan `users`

Secara konsep, data API dapat dipandang sebagai dua tabel utama:

### Tabel `users`

| Field | Fungsi |
|---|---|
| `id` | Primary key/identitas unik pengguna. |
| Informasi pengguna | Menyimpan data identitas dan kontak pengguna sesuai fixture. |

### Tabel `posts`

| Field | Fungsi |
|---|---|
| `id` | Primary key/identitas unik post. |
| `userId` | Foreign key secara konseptual yang merujuk ke `users.id`. |
| `title` | Judul post. |
| `body` | Isi post. |

### Diagram relasi sederhana

```text
USERS
┌──────────────┐
│ id (PK)      │
│ name         │
│ email        │
└──────┬───────┘
       │
       │ 1 : N
       │
       ▼
POSTS
┌──────────────┐
│ id (PK)      │
│ userId (FK)  │
│ title        │
│ body         │
└──────────────┘
```

Hubungannya adalah **one-to-many (1:N)**: satu user dapat memiliki banyak post, sedangkan satu post hanya memiliki satu `userId`.

---

## 3. Hubungan URL, HTTP Method, dan Data pada `/posts`

URL menentukan **resource** yang ingin diakses, sedangkan HTTP method menentukan **operasi** yang dilakukan terhadap resource tersebut.

| Request | Fungsi | Hasil |
|---|---|---|
| `GET /posts` | Membaca seluruh post | Array berisi data post |
| `GET /posts/1` | Membaca satu post | Satu objek post dengan ID 1 |
| `POST /posts` | Membuat post baru | Post baru dengan status `201 Created` |
| `PUT /posts/1` | Mengganti data post | Data post diperbarui |
| `PATCH /posts/1` | Mengubah sebagian data post | Field tertentu diperbarui |
| `DELETE /posts/1` | Menghapus post | Status `204 No Content` |

Jadi, path `/posts` menunjukkan resource yang sama, tetapi method menentukan tindakan yang dilakukan. Parameter `:id` digunakan ketika operasi diarahkan ke satu resource tertentu.

---

## 4. Perbedaan `/posts/1` dan `?userId=1`

### `GET /posts/1`

Request ini menggunakan **path parameter** berupa ID resource. Hasilnya adalah **satu post** dengan ID `1`.

Contoh:

```text
GET http://localhost:4000/posts/1
```

### `GET /posts?userId=1`

Request ini menggunakan **query parameter** untuk melakukan filter berdasarkan pemilik post.

Contoh:

```text
GET http://localhost:4000/posts?userId=1
```

Hasilnya berupa **kumpulan post** yang memiliki `userId = 1`.

### Kesimpulan

- `/posts/1` → mengambil **satu resource berdasarkan ID post**.
- `/posts?userId=1` → mengambil **beberapa resource yang memenuhi filter userId**.

Keduanya sama-sama menggunakan method GET, tetapi tujuan pengambilan datanya berbeda.

---

## 5. Perbandingan GET, POST, PUT, PATCH, dan DELETE

| Method | Fungsi | Status umum pada API | Perubahan data |
|---|---|---|---|
| GET | Membaca data | `200 OK` | Tidak mengubah data |
| POST | Membuat data baru | `201 Created` | Menambah resource |
| PUT | Mengganti data resource | `200 OK` | Mengubah representasi resource secara menyeluruh |
| PATCH | Mengubah sebagian data | `200 OK` | Mengubah field tertentu |
| DELETE | Menghapus resource | `204 No Content` | Menghapus resource |

### GET

GET digunakan untuk membaca data. Contohnya:

```text
GET /posts/1
```

Request berhasil akan mengembalikan data post tanpa mengubah isi database.

### POST

POST digunakan untuk membuat post baru:

```text
POST /posts
```

Body yang digunakan dapat berupa:

```json
{
  "userId": 1,
  "title": "Latihan lokal",
  "body": "Isi tulisan fiktif"
}
```

API membuat ID baru dan menyimpan data. Respons berhasil menggunakan status **201 Created**.

### PUT

PUT digunakan untuk mengganti representasi resource. Pada API placeholder, `userId`, `title`, dan `body` wajib dikirim.

```text
PUT /posts/1
```

Respons berhasil menggunakan **200 OK**.

### PATCH

PATCH digunakan ketika hanya sebagian field yang ingin diubah.

```text
PATCH /posts/1
```

Contohnya hanya mengubah `title` tanpa harus mengirim seluruh field post. Respons berhasil menggunakan **200 OK**.

### DELETE

DELETE digunakan untuk menghapus resource:

```text
DELETE /posts/1
```

API mengembalikan **204 No Content** dan tidak memiliki body respons. Setelah penghapusan, GET terhadap ID tersebut tidak lagi menemukan resource sehingga dapat menghasilkan **404 Not Found**.

---

## Kesimpulan

API placeholder lokal menunjukkan bahwa routing tidak hanya ditentukan oleh URL, tetapi juga oleh HTTP method dan parameter yang digunakan. Resource `users` dan `posts` memiliki hubungan melalui `users.id` dan `posts.userId`. Selain itu, path parameter digunakan untuk menentukan resource tertentu, sedangkan query parameter dapat digunakan untuk melakukan filtering.

Perbedaan HTTP method juga menentukan bagaimana data diperlakukan: GET membaca data, POST membuat data, PUT mengganti data, PATCH memperbarui sebagian data, dan DELETE menghapus data. Pemahaman ini menjadi dasar untuk implementasi REST API pada tahap praktikum berikutnya.

## Referensi Praktikum

- Modul Pertemuan 2 — Routing, Library & ORM.
- API Placeholder Lokal untuk Praktikum.
- Base URL latihan: `http://localhost:4000`.
