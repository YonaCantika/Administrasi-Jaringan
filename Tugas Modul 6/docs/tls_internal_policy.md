# TLS Internal Policy & Analisis

**Author:** Yona Cantika Damai Sari

## 1. Kebijakan TLS Internal (Self-Signed CA)
Untuk mengamankan lalu lintas *East-West* antar node di dalam jaringan lokal (LAN), sistem mengimplementasikan enkripsi TLS. Karena otoritas global tidak mengenali domain `.local`, kami membuat otoritas sertifikat (Certificate Authority) internal bernama **LabCA** untuk menandatangani sertifikat khusus domain `app.lab1.local`.

## 2. Jawaban Pertanyaan Analitis
1. **Perbedaan Web Server dan Reverse Proxy:** Web server bertugas langsung membaca file statis (HTML/CSS) dari penyimpanannya dan mengirimkannya ke klien. Reverse proxy bertindak sebagai perantara; ia menerima permintaan, meneruskannya ke aplikasi/server lain (backend) di belakang layar, lalu mengembalikan responsnya seolah-olah proxy itulah yang menghasilkan jawabannya.
2. **Kenapa TLS wajib meskipun internal?** Untuk mencegah *Insider Threat* dan *Packet Sniffing*. Tanpa TLS, seluruh komunikasi di dalam LAN berbentuk teks polos (*plaintext*), sehingga rentan disadap menggunakan *tools* seperti Wireshark jika ada perangkat di jaringan lokal yang terkompromi.
3. **Risiko jika private key bocor:** Peretas dapat mendekripsi lalu lintas data historis dan melakukan serangan *Man-in-the-Middle* (MITM) dengan membuat server palsu (*spoofing*) yang akan dipercaya sepenuhnya oleh klien karena gembok sertifikatnya valid.
4. **Kenapa tidak semua service expose port langsung?** Sebagai bentuk perlindungan *Defense in Depth*. Menyembunyikan port backend (misal port 9000) dan memaksanya lewat Reverse Proxy (port 80/443) memungkinkan kita memusatkan filter keamanan, WAF, log, dan sertifikat di satu titik tanpa perlu mengubah kode pada aplikasi backend.