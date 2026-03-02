# PBL Administrasi Jaringan - Kelompok 10

Selamat datang di repositori manajemen konfigurasi Kelompok 10. Proyek ini merupakan bagian dari Modul 1: Kickoff Peran SysAdmin & Meta-Principles.

## 📋 Profil Proyek
* **Instansi:** Politeknik Elektronika Negeri Surabaya
* **Anggota Kelompok:**
    1. Yona Cantika Damai Sari - 3124522001
    2. Nur Fajriyah - 3124522024
    3. Rahmatillah Niken Kurniawan - 3124522019

## ✅ Status Implementasi (Modul 1)
| Kriteria Sukses | Status | Bukti (Evidence) |
| :--- | :---: | :--- |
| SSH adm01 -> srv01 (No Password) | Done | `evidence/ssh_srv_tests.txt` |
| SSH adm01 -> cli01 (No Password) | Done | `evidence/ssh_cli_tests.txt` |
| Ping Internal LAN (0% Loss) | Done | `evidence/ssh_srv_tests.txt && ssh_cli_tests.txt` |
| Inventory & Policy Blueprint | Done | Folder `docs/` |
| Change Log (Min. 3 Entry) | Done | `docs/change_log.md` |
---

## 🌐 Topologi Jaringan
Sistem ini terdiri dari 3 VM Debian 12 yang saling terhubung dalam jaringan internal yang aman.

```mermaid
graph LR
    Host[Laptop Host] -- SSH --> adm01
    subgraph LAN_Internal [10.10.10.0/24]
        adm01[adm01 <br/> 10.10.10.10]
        srv01[srv01 <br/> 10.10.10.11]
        cli01[cli01 <br/> 10.10.10.12]
    end
    adm01 -- Management --> srv01
    adm01 -- Management --> cli01
