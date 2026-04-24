# Reverse Proxy Design v1

**Author:** Yona Cantika Damai Sari

## 1. Arsitektur Proxy
- **Frontend Server:** NGINX di `srv01` mendengarkan koneksi dari LAN pada domain `app.lab1.local` (Port 80 HTTP dan 443 HTTPS).
- **Backend Service:** Aplikasi *dummy* berbasis Python berjalan secara terisolasi pada antarmuka *loopback* lokal di alamat `127.0.0.1` port `9000`. Backend ini tidak terpapar langsung ke jaringan publik/LAN.

## 2. Mekanisme Penerusan (Forwarding)
NGINX dikonfigurasi untuk menangkap *request* yang masuk ke *location /* dan meneruskannya ke backend menggunakan direktif `proxy_pass http://127.0.0.1:9000;`. 

Agar aplikasi backend tetap dapat mengidentifikasi pengguna aslinya, NGINX menyematkan header tambahan:
- `proxy_set_header Host $host;`
- `proxy_set_header X-Real-IP $remote_addr;` (Meneruskan IP asli dari `cli01` ke backend).