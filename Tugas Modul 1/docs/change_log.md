# Change Log - Kelompok 10

Dokumen ini mencatat riwayat perubahan konfigurasi pada infrastruktur lab Modul 1.

## [2026-03-03] - Inisialisasi Repositori & Struktur Folder
**Perubahan:**
- Membuat repositori Git lokal di `adm01`.
- Membuat struktur folder: `docs/`, `configs/`, dan `evidence/`.
- Menambahkan file `README.md` dan `.gitignore`.

**Alasan:**
- Menerapkan Meta-Principle **"Knowledge as Jigsaw"** dan **"Repeatability"**. Dokumentasi terpusat di Git memastikan seluruh anggota kelompok memiliki informasi yang sama dan konfigurasi dapat diulang jika terjadi kegagalan sistem.

**Hasil:**
- Struktur proyek siap digunakan untuk menyimpan artefak PBL lainnya.

---

## [2026-03-03] - Konfigurasi Addressing & Hostname (Identity)
**Perubahan:**
- Mengubah hostname di `/etc/hostname` menjadi `adm01`, `srv01`, dan `cli01`.
- Mengatur IP Statik pada interface LAN (enp0s8) di file `/etc/network/interfaces`:
  - adm01: 10.10.10.10
  - srv01: 10.10.10.11
  - cli01: 10.10.10.12

**Alasan:**
- Memenuhi standar **Identity Host** (Bab 3 Burgess). IP statik diperlukan agar layanan komunikasi antar VM tidak terputus akibat perubahan IP dinamis (DHCP) pada jaringan internal.

**Hasil:**
- Seluruh VM dapat saling terhubung (ping sukses 0% loss) menggunakan IP yang konsisten sesuai Policy Blueprint.

---

## [2026-03-03] - Hardening Akses SSH (Security Baseline)
**Perubahan:**
- File: `/etc/ssh/sshd_config`
- Aksi: 
  - `PermitRootLogin` diubah ke `no`.
  - `PasswordAuthentication` diubah ke `no`.
  - Mengaktifkan `PubkeyAuthentication yes`.

**Alasan:**
- **Risk Mitigation**: Mencegah serangan *brute force* pada akun root dan user biasa. Akses admin kini hanya diizinkan melalui SSH Key yang sudah terdaftar di `authorized_keys`.

**Hasil:**
- Akses ke `srv01` dan `cli01` hanya bisa dilakukan secara aman dari `adm01`. Login menggunakan password ditolak oleh sistem.

---

## [2026-03-03] - Pembuatan Bukti Uji (Evidence Generation)
**Perubahan:**
- Menjalankan perintah `script` untuk merekam hasil uji konektivitas dan login SSH.
- Menyimpan output ke `evidence/ssh_tests.txt`.

**Alasan:**
- Memenuhi syarat **Audit & Verification** pada Modul 1 halaman 9. Tanpa bukti uji, klaim keberhasilan sistem tidak dapat divalidasi oleh instruktur.

**Hasil:**
- File log tersedia di repositori sebagai bukti fisik bahwa sistem berjalan sesuai kebijakan (Policy-based).
