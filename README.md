# PBL Administrasi Jaringan - Kelompok 10

Selamat datang di repositori manajemen konfigurasi Kelompok 10. Proyek ini merupakan bagian dari Modul 1: Kickoff Peran SysAdmin & Meta-Principles.

## 📋 Profil Proyek
* **Instansi:** Politeknik Elektronika Negeri Surabaya
* **Anggota Kelompok:**
    1. [Nama Kamu] - [NRP]
    2. [Nama Teman] - [NRP]
    3. [Nama Teman] - [NRP]
* **Skenario:** [Opsi A: WSN/IoT Lab Kampus / Opsi B: Smart PKL]

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