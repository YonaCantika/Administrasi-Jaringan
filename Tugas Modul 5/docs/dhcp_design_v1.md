# DHCP Design v1

- **Target Network**: LAN-B (Subnet `10.20.1.0/24`)
- **Interface Server**: `enp0s8` (di srv01 yang mengarah ke cli01)
- **Range IP Dinamis**: `10.20.1.50` sampai `10.20.1.100`
- **Default Gateway**: `10.20.1.1`
- **DNS Server**: `10.20.1.1`
- **Fitur Advanced (DHCP Reservation)**: Diaktifkan khusus untuk `cli01`. Dengan mendaftarkan MAC Address milik antarmuka klien, `cli01` akan selalu mendapatkan *fixed-address* `10.20.1.10` secara otomatis tanpa takut berubah.