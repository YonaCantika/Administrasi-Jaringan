# System Inventory v0 - Kelompok 10

**Tanggal Update:** 03/03/2026

## 1. Daftar Virtual Machines

| Hostname | Role | IP LAN (enp0s8) | Debian Version | SSH Key-Only |
| :--- | :--- | :--- | :--- | :--- |
| **adm01** | Admin Gateway | 10.10.10.10 | 12 | Y |
| **srv01** | Main Server | 10.10.10.11 | 12 | Y |
| **cli01** | Client/User | 10.10.10.12 | 12 | Y |

## 2. Detail Konfigurasi Network
* **Network Type:** NAT & Internal Network / Host-Only
* **Subnet:** 10.10.10.0/24
* **Gateway:** -

## 3. Paket Utama Terpasang
* `git` (Version Control)
* `openssh-server` (Akses Remote)
* `vim` / `nano` (Editor)
* `dnsutils` / `iputils-ping` (Troubleshooting)
