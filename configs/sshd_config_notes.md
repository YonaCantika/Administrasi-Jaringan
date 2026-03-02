# SSH Configuration Notes - Kelompok 10

Dokumen ini mencatat langkah-langkah pengerasan (**hardening**) layanan SSH pada `srv01` dan `cli01` sesuai dengan standar keamanan Modul 1.

---

## 1. Parameter Utama yang Diubah
Perubahan dilakukan pada file `/etc/ssh/sshd_config` untuk memastikan akses hanya melalui jalur yang terotorisasi.

| Parameter | Nilai Baru | Fungsi / Alasan |
| :--- | :--- | :--- |
| `PermitRootLogin` | `no` | Melarang user `root` login langsung demi keamanan. |
| `PasswordAuthentication` | `no` | Mematikan login pakai password untuk mencegah *brute force*. |
| `PubkeyAuthentication` | `yes` | Mewajibkan penggunaan SSH Key (RSA/Ed25519). |
| `AuthorizedKeysFile` | `.ssh/authorized_keys` | Menentukan lokasi penyimpanan kunci publik yang diizinkan. |

---

## 2. Prosedur Implementasi
Langkah-langkah yang dilakukan agar tidak terkunci (**lockout**):

1.  **Generate Key** Membuat pasangan kunci di `adm01` menggunakan `ssh-keygen`:
    ```bash
    ssh-keygen -t ed25519 -C "adm01@lab10"
    ```

2.  **Distribusi Kunci** Mengirimkan kunci publik ke server target:
    ```bash
    ssh-copy-id yona@10.10.10.11
    ```

3.  **Uji Coba** Memastikan bisa login dari `adm01` ke `srv01` tanpa dimintai password:
    ```bash
    ssh yona@10.10.10.11
    ```

4.  **Hardening** Setelah sukses, baru mengubah `PasswordAuthentication` menjadi `no` di `/etc/ssh/sshd_config`.

5.  **Restart Service** Menjalankan perintah untuk menerapkan konfigurasi:
    ```bash
    sudo systemctl restart ssh
    ```

---

## 3. Verifikasi Keamanan
Bukti bahwa konfigurasi berhasil (Post-Hardening):

* **Akses Luar:** Mencoba login SSH langsung dari Laptop ke `srv01` $\rightarrow$ **Rejected** (Wajib lewat `adm01`).
* **Akses Root:** Mencoba login sebagai `root` $\rightarrow$ **Permission Denied**.
* **Akses Terotorisasi:** Login dari `adm01` ke `srv01` $\rightarrow$ **Success** (Tanpa password).

---
*Terakhir diperbarui: 3 Maret 2026*
