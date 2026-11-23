# Tugas Mandiri 3 — Memahami Request dan Response

**Nama:** Abyyy  
**NIM:** 004  
**Base URL:** http://localhost:4000

## Pengujian

~~~text
GET http://localhost:4000/get?nama=Umar&kelas=TI
GET http://localhost:4000/headers
~~~

## 1. Apa itu request?

Request adalah permintaan yang dikirim client kepada server. Pada pengujian ini Postman atau browser bertindak sebagai client.

## 2. Apa itu response?

Response adalah jawaban yang dikirim server setelah menerima dan memproses request. Pada pengujian ini response dikirim oleh API lokal localhost:4000.

## 3. Fungsi query parameter

Query parameter mengirim informasi tambahan melalui URL. Pada contoh:

~~~text
/get?nama=Umar&kelas=TI
~~~

nama memiliki nilai Umar dan kelas memiliki nilai TI. API echo menampilkan kembali parameter tersebut.

## 4. Fungsi HTTP header

Header membawa metadata request atau response. Contohnya Content-Type: application/json yang menunjukkan bahwa body menggunakan format JSON. Endpoint /headers digunakan untuk melihat header yang diterima server.

## 5. Query parameter vs body

Query parameter berada di URL setelah tanda ?. Body berada di isi request dan umum digunakan untuk POST, PUT, dan PATCH.

Contoh query:

~~~text
/get?nama=Umar&kelas=TI
~~~

Contoh body:

~~~json
{
  "nama": "Umar",
  "kelas": "Informatika"
}
~~~

## Alur

~~~text
Client → Request → Server → Response → Client
~~~

## Bukti Pengujian

Lampirkan screenshot:
1. Response /get?nama=Umar&kelas=TI
2. Response /headers
