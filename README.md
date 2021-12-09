# Jarkom-Modul-5-A09-2021
Laporan Resmi Praktikum Jarkom Modul 5

# Anggota Kelompok
Anggota  | NRP
---------|-------
Arvel Gavrilla Raissananda | 05111940000040
Johnivan Aldo Sudiono | 05111940000051
Vincent Yonathan | 05111940000186

## Soal Jarkom-Modul-5 2021

### (A) Tugas pertama kalian yaitu membuat topologi jaringan sesuai dengan rancangan yang diberikan Luffy dibawah ini:
![image](https://user-images.githubusercontent.com/36225278/145450558-89f3512b-93e2-4559-9382-a26b1a5b8dcd.png)

### (B) Konfigurasi IP dengan VLSM (Variable Length Subnet Masking) :
![image](https://user-images.githubusercontent.com/36225278/145450611-e5eba9ff-86a6-4e07-92df-419c056d3e67.png)

### Tree :

### Pembagian IP :
### 1. Jumlah Alamat IP
Subnet serta jumlah IP untuk mendapatkan netmask dari tiap subnet ditunjukkan oleh tabel berikut :
| Subnet  | Jumlah IP | Netmask | subnetmask | nid |
| :---         |     :---:      |     :---:      |     :---:      |          ---: |
| ------------- | ------------- | ------------- | ------------- | ------------- |
| A1  | 2 | /30 | 255.255.255.252 | 192.173.0.0 |
| A2  | 2 | /30 | 255.255.255.252 | 192.173.0.4 |
| A3  | 201 | /24 | 255.255.255.0 | 192.173.1.0 |
| A4  | 301 | /23 | 255.255.254.0 | 192.173.2.0 |
| A5  | 101 | /25 | 255.255.255.128 | 192.173.0.128 |
| A6  | 701 | /22 | 255.255.252.0	 | 192.173.4.0 |
| A7  | 4 | /29 | 255.255.255.248 | 192.173.0.16 |
| A8  | 4 | /29 | 255.255.255.248 | 192.173.0.24 |
| Total  | 5841 | /21 | 255.255.248.0 | - |
