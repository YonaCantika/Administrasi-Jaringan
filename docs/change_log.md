\# Change Log - Kelompok 10



\## \[2026-03-02] - Setup Keamanan SSH

\*\*Perubahan:\*\*

\* File: `/etc/ssh/sshd\_config`

\* Parameter: `PermitRootLogin` diubah dari `yes` menjadi `no`.

\* Parameter: `PasswordAuthentication` diubah dari `yes` menjadi `no`.



\*\*Alasan:\*\*

\* Menjalankan standar keamanan Modul 1 untuk mencegah akses root langsung dan mewajibkan penggunaan SSH Key dari `adm01`.



\*\*Hasil:\*\*

\* User `root` tidak bisa lagi login via SSH.

\* Akses ke `srv01` hanya bisa dilakukan oleh user `student` melalui `adm01` menggunakan kunci (Key-based auth).

\* Perintah diterapkan dengan: `sudo systemctl restart ssh`.



---



\## \[2026-03-02] - Konfigurasi IP Statik LAN

\*\*Perubahan:\*\*

\* File: `/etc/network/interfaces`

\* Konfigurasi: Menambahkan IP `10.10.10.11` pada interface `enp0s8`.



\*\*Alasan:\*\*

\* Agar alamat IP server tetap (statik) sehingga memudahkan komunikasi antar VM dalam jaringan lokal.



\*\*Hasil:\*\*

\* VM `srv01` bisa di-ping oleh `adm01` melalui jaringan internal.

