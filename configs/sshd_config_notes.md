# SSH Configuration Notes - Kelompok 10

Dokumen ini mencatat langkah-langkah pengerasan (\*hardening\*) layanan SSH pada `srv01` dan `cli01` sesuai dengan standar keamanan Modul 1.

## 1. Parameter Utama yang Diubah

Perubahan dilakukan pada file `/etc/ssh/sshd\_config` untuk memastikan akses hanya melalui jalur yang terotorisasi.

| Parameter | Nilai Baru | Fungsi / Alasan |

| :--- | :--- | :--- |

| `PermitRootLogin` | `no` | Melarang user `root` login langsung demi keamanan. |

| `PasswordAuthentication` | `no` | Mematikan login pakai password untuk mencegah \*brute force\*. |

| `PubkeyAuthentication` | `yes` | Mewajibkan penggunaan SSH Key (RSA/Ed25519). |

| `AuthorizedKeysFile` | `.ssh/authorized\_keys` | Menentukan lokasi penyimpanan kunci publik yang diizinkan. |



## 2. Prosedur Implementasi

Langkah-langkah yang dilakukan agar tidak terkunci (\*lockout\*):

1\. \*\*Generate Key:\*\* Membuat pasangan kunci di `adm01` menggunakan `ssh-keygen`.

2\. \*\*Distribusi Kunci:\*\* Mengirimkan kunci publik ke server target dengan `ssh-copy-id student@10.10.10.11`.

3\. \*\*Uji Coba:\*\* Memastikan bisa login dari `adm01` ke `srv01` tanpa dimintai password.

4\. \*\*Hardening:\*\* Setelah sukses, baru mengubah `PasswordAuthentication` menjadi `no`.

5\. \*\*Restart Service:\*\* Menjalankan `sudo systemctl restart ssh`.



## 3. Verifikasi Keamanan

Bukti bahwa konfigurasi berhasil:

* Mencoba login SSH langsung dari Laptop ke `srv01` -> \*\*Rejected\*\* (karena harus lewat `adm01`).

* Mencoba login sebagai `root` -> \*\*Permission Denied\*\*.

\* Login dari `adm01` ke `srv01` -> \*\*Langsung masuk (Success)\*\*.

