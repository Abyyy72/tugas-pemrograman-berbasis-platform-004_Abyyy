# Tugas Mandiri 1 — Mengenal HTTP Method dan Endpoint

**Nama:** Abyyy  
**NIM:** 004  
**Base URL:** http://localhost:4000

## Hasil Pengujian

| No | Method | Endpoint | Data | Status | Hasil |
|---|---|---|---|---|---|
| 1 | GET | /get?nama=Umar&kelas=Informatika | Query parameter | 200 OK | Server memantulkan informasi request dan query. |
| 2 | POST | /post | JSON nama dan kelas | 200 OK | Server memantulkan body JSON. |
| 3 | PUT | /put | JSON nama dan kelas | 200 OK | Server memantulkan body JSON. |
| 4 | PATCH | /patch | JSON kelas | 200 OK | Server memantulkan body JSON. |
| 5 | DELETE | /delete | Tidak ada body | 200 OK | Server memantulkan informasi request DELETE. |

Endpoint echo hanya memantulkan informasi request sehingga tidak mengubah database.

## GET

~~~text
GET http://localhost:4000/get?nama=Umar&kelas=Informatika
~~~

GET digunakan untuk meminta data. Query parameter nama dan kelas dikirim melalui URL dan ditampilkan kembali oleh server.

## POST

~~~text
POST http://localhost:4000/post
Content-Type: application/json
~~~

Body:

~~~json
{
  "nama": "Umar",
  "kelas": "Informatika"
}
~~~

POST digunakan untuk mengirim data melalui request body.

## PUT

~~~text
PUT http://localhost:4000/put
~~~

Body:

~~~json
{
  "nama": "Umar",
  "kelas": "Informatika"
}
~~~

PUT digunakan untuk operasi penggantian resource. Pada endpoint echo, tidak ada resource yang benar-benar diubah.

## PATCH

~~~text
PATCH http://localhost:4000/patch
~~~

Body:

~~~json
{
  "kelas": "Informatika"
}
~~~

PATCH digunakan untuk perubahan sebagian data. Endpoint echo hanya memantulkan request.

## DELETE

~~~text
DELETE http://localhost:4000/delete
~~~

DELETE digunakan untuk menghapus resource pada API yang memiliki resource. Endpoint echo hanya memantulkan request sehingga tidak menghapus data.

## Kesimpulan

HTTP method menentukan jenis operasi yang diminta client. GET membaca, POST membuat/mengirim, PUT mengganti, PATCH memperbarui sebagian, dan DELETE menghapus. API echo pada tugas ini digunakan untuk mengamati request tanpa mengubah database.

## Bukti Pengujian

Tambahkan minimal dua screenshot Postman:
1. GET /get
2. POST /post
