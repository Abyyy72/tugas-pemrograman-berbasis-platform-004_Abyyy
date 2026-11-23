# Tugas Mandiri 2 — Memahami HTTP Status Code

**Nama:** Abyyy  
**NIM:** 004  
**Base URL:** http://localhost:4000

## Hasil Pengujian

| Status | Arti | Penggunaan |
|---|---|---|
| 200 | OK | Request berhasil. |
| 201 | Created | Resource berhasil dibuat. |
| 400 | Bad Request | Request tidak valid. |
| 401 | Unauthorized | Client belum terautentikasi atau kredensial tidak valid. |
| 403 | Forbidden | Client tidak memiliki hak akses. |
| 404 | Not Found | Resource atau endpoint tidak ditemukan. |
| 500 | Internal Server Error | Terjadi kegagalan internal server. |

Pengujian:

~~~text
GET http://localhost:4000/status/200
GET http://localhost:4000/status/201
GET http://localhost:4000/status/400
GET http://localhost:4000/status/401
GET http://localhost:4000/status/403
GET http://localhost:4000/status/404
GET http://localhost:4000/status/500
~~~

Endpoint status memang dirancang untuk mensimulasikan kode HTTP.

## Jawaban

### 1. Perbedaan 400 dan 404

400 menunjukkan masalah pada request, misalnya format atau data yang dikirim tidak sesuai. 404 menunjukkan resource atau endpoint yang diminta tidak ditemukan.

### 2. Perbedaan 401 dan 403

401 berkaitan dengan autentikasi: identitas client belum valid atau belum diberikan. 403 berarti client sudah dikenali tetapi tidak memiliki izin melakukan operasi tertentu.

### 3. Mengapa 500 menunjukkan masalah server?

500 termasuk kategori 5xx dan menunjukkan server mengalami kegagalan internal ketika memproses request.

### 4. Apakah setiap error HTTP berarti server rusak?

Tidak. Kode 4xx sering terjadi karena request atau kondisi client, misalnya 400 karena input salah dan 404 karena resource tidak tersedia. Kode 500 menunjukkan kegagalan internal pada server.

## Bukti Pengujian

Tambahkan minimal tiga screenshot:
1. /status/200
2. /status/404
3. /status/500
