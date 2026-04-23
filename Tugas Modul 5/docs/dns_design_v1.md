# DNS Design v1

- **Domain Utama**: `lab1.local`
- **Server DNS**: `srv01` (IP: 10.20.1.1)
- **Tipe**: Authoritative Internal DNS Server (Menggunakan BIND9).
- **Zona Forward**: Memetakan nama host menjadi IP Address.
  - `srv01.lab1.local` -> `10.20.1.1`
  - `cli01.lab1.local` -> `10.20.1.10`
  - `adm01.lab1.local` -> `10.10.1.10`
- **Zona Reverse**: Blok `10.20.1.in-addr.arpa` untuk memetakan kembali IP klien/server menjadi nama domain (PTR record) guna keperluan verifikasi dan *logging* keamanan.