# Web Server & Virtual Host Architecture v1

**Author:** Yona Cantika Damai Sari
**Institution:** Teknik Informatika, Politeknik Elektronika Negeri Surabaya (PENS)

## 1. Layanan Inti
Sistem menggunakan **NGINX** pada `srv01` sebagai Web Server utama sekaligus bertindak sebagai Reverse Proxy untuk aplikasi internal.

## 2. Topologi Virtual Host (Multi-Site)
Sistem melayani dua domain internal berbeda menggunakan teknik Server Blocks (Virtual Host):
- **`portal.lab1.local` (Port 80):** Berperan sebagai web server tradisional yang langsung merender file statis HTML dari direktori root `/srv/data/apps/portal`.
- **`app.lab1.local` (Port 80 & 443 TLS):** Berperan sebagai API/App Gateway (Reverse Proxy) yang mengamankan lalu lintas menuju backend service.

## 3. Keamanan Dasar (Hardening)
- Menghapus halaman *default site* bawaan NGINX (`/etc/nginx/sites-enabled/default`) untuk meminimalisasi celah keamanan (*attack surface*).
- Menambahkan HTTP Header `X-Content-Type-Options: nosniff` dan `X-Frame-Options: DENY` untuk mencegah serangan *MIME sniffing* dan *Clickjacking*.