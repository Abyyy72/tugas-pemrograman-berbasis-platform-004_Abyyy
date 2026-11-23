# Tugas Mandiri 5 — Membandingkan SQL Mentah dan ORM

**Nama:** Abyyy  
**NIM:** 004

## Operasi yang Dipilih

Mengambil satu data jadwal berdasarkan ID 1001 pada tabel Jadwal.

## A. SQL Mentah

~~~sql
SELECT *
FROM Jadwal
WHERE id = ?;
~~~

Parameter query diisi dengan nilai 1001.

Contoh Node.js:

~~~javascript
const [rows] = await connection.execute(
  'SELECT * FROM Jadwal WHERE id = ?',
  [1001]
);
~~~

## B. Prisma ORM

~~~javascript
const jadwal = await prisma.jadwal.findUnique({
  where: {
    id: 1001
  }
});
~~~

## Perbandingan

| Aspek | SQL Mentah | Prisma ORM |
|---|---|---|
| Bentuk | Query SQL | Method/API JavaScript |
| Kontrol query | Langsung | Melalui abstraksi ORM |
| Operasi sederhana | Lebih verbose | Lebih ringkas |
| Relasi | Ditulis dalam SQL | Didefinisikan melalui schema/model |
| Keamanan | Perlu parameterized query | ORM membantu, tetapi validasi tetap diperlukan |

## 1. Perbedaan SQL dan ORM

SQL langsung menuliskan instruksi database secara eksplisit. ORM menyediakan abstraksi berupa model dan method dalam bahasa pemrograman.

## 2. Kelebihan SQL mentah

SQL memberikan kontrol langsung terhadap query, fleksibel untuk query kompleks, dan memungkinkan developer mengoptimalkan perintah sesuai kemampuan database.

## 3. Kelebihan ORM

ORM membuat operasi database lebih terstruktur, mengurangi SQL berulang, dan memudahkan pengelolaan model serta relasi.

## 4. SQL injection

SQL injection terjadi ketika input pengguna dimasukkan ke query secara tidak aman sehingga dapat memengaruhi struktur atau tujuan query. Dampaknya dapat berupa pembacaan, perubahan, atau penghapusan data yang tidak semestinya.

## 5. Parameter query

Parameterized query memisahkan struktur SQL dari nilai input sehingga nilai pengguna tidak diperlakukan sebagai bagian dari sintaks SQL.

Contoh:

~~~sql
SELECT * FROM Jadwal WHERE id = ?;
~~~

## 6. Peran ORM

Prisma menyediakan API seperti findUnique untuk mengambil data berdasarkan ID tanpa menulis query SELECT secara manual untuk setiap operasi sederhana. Developer tetap harus memperhatikan validasi, hak akses, dan keamanan input.

## Kesimpulan

SQL mentah memberikan kontrol langsung terhadap database, sedangkan ORM memberikan abstraksi yang lebih praktis dan terstruktur. Keduanya dapat digunakan dengan aman apabila parameter input dan validasi diperhatikan.

> Catatan: ID 1001 digunakan sesuai instruksi tugas. Eksekusi database sungguhan dilakukan pada database latihan yang disediakan pada modul.
