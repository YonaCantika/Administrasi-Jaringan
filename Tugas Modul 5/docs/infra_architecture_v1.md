# Infrastructure Architecture v1

Topologi jaringan ini terdiri dari 3 node utama yang terisolasi dalam *Internal Network*:
1. **srv01 (Router & Core Services)**:
   - Memiliki dua antarmuka (`10.10.1.1` untuk LAN-A, `10.20.1.1` untuk LAN-B).
   - Menjalankan layanan inti BIND9 (DNS) dan ISC-DHCP-Server.
   - Bertindak sebagai jembatan *routing* (*IP Forwarding*).
2. **adm01 (Administrator)**:
   - Berada di LAN-A dengan IP Statik `10.10.1.10`.
   - Diatur secara manual untuk menggunakan DNS `10.10.1.1`.
3. **cli01 (Client Testing)**:
   - Berada di LAN-B.
   - Menggunakan mode antarmuka DHCP untuk menerima IP, Gateway, dan DNS secara otomatis dari `srv01`.