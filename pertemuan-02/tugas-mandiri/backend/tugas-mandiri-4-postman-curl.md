# Tugas Mandiri 4 — Pengujian API dengan Postman dan curl

**Nama:** Abyyy  
**NIM:** 004  
**Base URL:** http://localhost:4000

## A. Postman

### GET

~~~text
GET http://localhost:4000/get
~~~

Request GET digunakan untuk menguji endpoint echo melalui Postman.

### POST

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

Response POST menampilkan kembali body JSON yang diterima server.

## B. curl

### curl -i

~~~bash
curl -i http://localhost:4000/get
~~~

Opsi -i menampilkan HTTP response headers sekaligus response body.

Pengujian status:

~~~bash
curl -i http://localhost:4000/status/404
~~~

Perintah tersebut memperlihatkan status 404, header, dan body response.

### curl -s

~~~bash
curl -s http://localhost:4000/get
~~~

Opsi -s berarti silent mode. Output tambahan curl disembunyikan sehingga response lebih bersih.

## Perbandingan

curl -s cocok ketika hanya membutuhkan body response, misalnya untuk diproses script. curl -i cocok ketika ingin memeriksa status HTTP dan header sekaligus.

## Bukti Pengujian

Lampirkan screenshot:
1. GET melalui Postman
2. POST melalui Postman
3. curl -i
4. curl -s
