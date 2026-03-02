# Change Log - Kelompok 10

## [2026-03-02] - Setup Keamanan SSH
**Perubahan:**
- File: `/etc/ssh/sshd_config`
- Parameter: `PermitRootLogin` diubah dari `yes` menjadi `no`
- Parameter: `PasswordAuthentication` diubah dari `yes` menjadi `no`

**Alasan:**
- Menjalankan standar keamanan Modul 1 untuk mencegah akses root langsung dan mewajibkan penggunaan SSH Key dari `adm01`.

**Hasil:**
- User `root` tidak bisa lagi login via SSH.
- Akses ke `srv01` hanya bisa dilakukan oleh user `student` melalui `adm01` menggunakan kunci (Key-based auth).
- Perintah diterapkan dengan: `sudo systemctl restart ssh`.

---

## [2026-03-02] - Konfigurasi IP Statik LAN
**Perubahan:**
- File: `/etc/network/interfaces` atau menggunakan `nmcli`.
- Konfigurasi: Menetapkan IP `10.10.10.11` pada interface LAN (enp0s8).

**Alasan:**
- Memastikan alamat IP server tetap (statik) sesuai standar lab agar bisa saling ping antar VM.

**Hasil:**
- VM `srv01` sukses melakukan ping ke `adm01` (10.10.10.10) dan `cli01` (10.10.10.12).

---

## [2026-03-02] - Inisialisasi Repositori Git Kelompok
**Perubahan:**
- Membuat repositori lokal dan menghubungkannya ke GitHub.
- Menyusun struktur folder `docs/`, `configs/`, dan `evidence/`.

**Alasan:**
- Memenuhi prasyarat artefak PBL Modul 1 untuk manajemen konfigurasi dan dokumentasi yang terpusat.

**Hasil:**
- Dokumentasi `inventory_v0` dan `policy_blueprint_v0` tersimpan dan bisa diakses oleh seluruh anggota kelompok.
