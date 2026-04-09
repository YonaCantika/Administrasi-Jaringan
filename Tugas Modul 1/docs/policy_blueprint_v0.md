# Policy Blueprint v0 - Kelompok 10

## 1. Tujuan Sistem & Definisi Sukses
* **Tujuan:** Membangun infrastruktur dasar yang aman untuk [Pilih Opsi A atau B] dengan akses admin terpusat dari `adm01`.
* **Definisi Sukses:**
    1. Seluruh VM dapat saling terhubung via IP Statik LAN.
    2. Akses SSH antar VM wajib menggunakan SSH Key.
    3. Root login via SSH dinonaktifkan di semua server.

## 2. Analisis Risiko Awal
* **Risiko:** Akses ilegal melalui *brute force* password SSH.
* **Mitigasi:** Mematikan `PasswordAuthentication` dan hanya mengizinkan login via Public Key yang sudah terdaftar.

## 3. Standar Konfigurasi (Meta-Principles)
* **Naming Convention:** Hostname menggunakan format `[role][nomor]` (contoh: srv01, adm01).
* **IP Planning:**
    * .10 - .19: Management/Admin
    * .20 - .50: Servers
    * .100+: Clients
* **Security Baseline:**
    * User utama: `student` (atau sesuai user yang dibuat di VM).
    * Sudo access: Hanya diberikan kepada user administratif.

## 4. Prosedur Perubahan (Change Management)
Setiap perubahan pada file konfigurasi sistem (`/etc/`) wajib dicatat dalam `change_log.md` dengan menyertakan:
1. Apa yang diubah.
2. Alasan perubahan.
3. Hasil setelah perubahan.
