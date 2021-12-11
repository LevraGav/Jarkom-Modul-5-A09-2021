# Jarkom-Modul-5-A09-2021
Laporan Resmi Praktikum Jarkom Modul 5

# Anggota Kelompok
Anggota  | NRP
---------|-------
Arvel Gavrilla Raissananda | 05111940000040
Johnivan Aldo Sudiono | 05111940000051
Vincent Yonathan | 05111940000186

## Soal Jarkom-Modul-5 2021
- [Soal](https://docs.google.com/document/d/1Sc2jTlqmyM149yi4QzOGijyjPmSeEoy14Ajg9MnmkuY/edit)

### (A) Tugas pertama kalian yaitu membuat topologi jaringan sesuai dengan rancangan yang diberikan Luffy dibawah ini:
![image](https://user-images.githubusercontent.com/36225278/145450558-89f3512b-93e2-4559-9382-a26b1a5b8dcd.png)

### (B) Konfigurasi IP dengan VLSM (Variable Length Subnet Masking) :
![image](https://user-images.githubusercontent.com/36225278/145450611-e5eba9ff-86a6-4e07-92df-419c056d3e67.png)

### Tree :
![modul5 drawio](https://user-images.githubusercontent.com/36225278/145531452-3c5e149a-1517-4688-803e-751bac83f606.png)

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
| Total  | 1361 | /21 | 255.255.248.0 | - |

SETTING INTERFACE PADA GNS3

- Foosha

```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
        address 192.173.0.1
        netmask 255.255.255.252

auto eth2
iface eth2 inet static
         address 192.173.0.5
         netmask 255.255.255.252
```

- Water7

```
auto eth0
iface eth0 inet static
        address 192.173.0.2
        netmask 255.255.255.252
        gateway 192.173.0.1

auto eth1
iface eth1 inet static
        address 192.173.0.17
        netmask 255.255.255.248

auto eth2
iface eth2 inet static
         address 192.173.0.129
         netmask 255.255.255.128

auto eth3
iface eth3 inet static
         address 192.173.4.1
         netmask 255.255.252.0
```

- Guanhao

```
auto eth0
iface eth0 inet static
          address 192.173.0.6
          netmask 255.255.255.252
          gateway 192.173.0.5

auto eth1
iface eth1 inet static
          address 192.173.0.25
          netmask 255.255.255.248

auto eth2
iface eth2 inet static
          address 192.173.1.1
          netmask 255.255.255.0

auto eth3
iface eth3 inet static
           address 192.173.2.1
          netmask 255.255.254.0
```

- Blueno

```
auto eth0
iface eth0 inet static
      address 192.173.0.130
      netmask 255.255.255.128
      gateway 192.173.0.129
```

- Chiper

```
auto eth0
iface eth0 inet static
       address 192.173.4.2
      netmask 255.255.252.0
       gateway 192.173.4.1
```

- Elena

```
auto eth0
iface eth0 inet static
       address 192.173.2.2
       netmask 255.255.254.0
       gateway 192.173.2.1
```

- Fukurou

```
auto eth0
iface eth0 inet static
       address 192.173.1.2
       netmask 255.255.255.0
       gateway 192.173.1.1
```

- Maingate

```
auto eth0
iface eth0 inet static
       address 192.173.0.27
       netmask 255.255.255.248
       gateway 192.173.0.25
```

- Jorge

```
auto eth0
iface eth0 inet static
       address 192.173.0.26
       netmask 255.255.255.248
       gateway 192.173.0.25
```

- Doriki

```
auto eth0
iface eth0 inet static
       address 192.173.0.18
       netmask 255.255.255.248
       gateway 192.173.0.17
```

- Jipangu

```
auto eth0
iface eth0 inet static
       address 192.173.0.19
       netmask 255.255.255.248
       gateway 192.173.0.17
```

### (C) Routing

```
route add -net 192.173.1.0 netmask 255.255.255.0 gw 192.173.0.6                                     
route add -net 192.173.2.0 netmask 255.255.254.0 gw 192.173.0.6                                   
route add -net 192.173.0.24 netmask 255.255.255.248 gw 192.173.0.6                                    
route add -net 192.173.4.0 netmask 255.255.252.0 gw 192.173.0.2                                         
route add -net 192.173.0.128 netmask 255.255.255.128 gw 192.173.0.2                                 
route add -net 192.173.0.16 netmask 255.255.255.248 gw 192.173.0.2 
```

### (D) Tugas berikutnya adalah memberikan ip pada subnet Blueno, Cipher, Fukurou, dan Elena secara dinamis menggunakan bantuan DHCP server. Kemudian kalian ingat bahwa kalian harus setting DHCP Relay pada router yang menghubungkannya.

1. Install `apt-get install isc-dhcp-relay -y` pada foosha, water7, dan guanhao, `apt-get install isc-dhcp-server` pada Jipangu
2. Pada Router (foosha, water7 dan guanhao) Edit file `/etc/sysctl.conf` deengan command
    ```
    net.ipv4.ip_forward=1
    net.ipv4.conf.all.accept_source_route = 1
    ```
3. Lakukan sysctl -p
4. Buka `file /etc/default/isc-dhcp-relay` dan edit server dengan mengarahkan dchp-relay menuju Jipangu `192.173.0.19` lalu `service isc-dhcp-relay restart` pada foosha, water7, dan guanhao
```
echo '# What servers should the DHCP relay forward requests to?
SERVERS="192.173.0.19"

# On what interfaces should the DHCP relay (dhrelay) serve DHCP requests?
INTERFACES=""

# Additional options that are passed to the DHCP relay daemon?
OPTIONS="" '> /etc/default/isc-dhcp-relay
```
5. Pada Jipangu edit file `/etc/default/isc-dhcp-server` dengan menambahkan:
`INTERFACES="eth0"`
6. Pada dhcp-server isikan data pada `/etc/dhcp/dhcpd.conf` di Jipangu, lalu lakukan `service isc-dhcp-server restart`
```
subnet 192.173.1.0 netmask 255.255.255.0 {
    range 192.173.1.2 192.173.1.254;
    option routers 192.173.1.1;
    option broadcast-address 192.173.1.255;
    option domain-name-servers 192.173.0.18;
    default-lease-time 600;
    max-lease-time 7200;
}
subnet 192.173.0.128 netmask 255.255.255.128 {
    range 192.173.0.130 192.173.0.254;
    option routers 192.173.0.129;
    option broadcast-address 192.173.0.255;
    option domain-name-servers 192.173.0.18;
    default-lease-time 600;
    max-lease-time 7200;
}
subnet 192.173.4.0 netmask 255.255.252.0 {
    range 192.173.4.2 192.173.4.254;
    option routers 192.173.4.1;
    option broadcast-address 192.173.4.255;
    option domain-name-servers 192.173.0.18;
    default-lease-time 600;
    max-lease-time 7200;
}
subnet 192.173.2.0 netmask 255.255.254.0 {
    range 192.173.2.2 192.173.2.254;
    option routers 192.173.2.1;
    option broadcast-address 192.173.2.255;
    option domain-name-servers 192.173.0.18;
    default-lease-time 600;
    max-lease-time 7200;
}
subnet 192.173.0.16 netmask 255.255.255.248{
}
```
7. Buka file `/etc/network/interfaces`. Command konfigurasi lama (static) dan ubah ip Blueno, Cipher, Fukurou, dan Elena dengan command
8. Lakukan restart di node yang dijadikan ip dhcp

## (1) Agar topologi yang kalian buat dapat mengakses keluar, kalian diminta untuk mengkonfigurasi Foosha menggunakan iptables, tetapi Luffy tidak ingin menggunakan MASQUERADE.

#### Foosha 

Command yang digunakan `iptables -t nat -A POSTROUTING -s 192.173.0.0/16 -o eth0 -j SNAT --to-s` (ip eth0) yang menyesuaikan dari eth0 tersebut

Lalu, pada semua node yang terkait dilakukan echo nameserver `192.168.122.1 > /etc/resolv.conf`

Keterangan:

-> ip eth0 akan selalu berganti ketika restart node pada foosha atau restart GNS3 dengan rentang IP yang sudah dijelaskan
-> Cara mengetahui eth0, masukan command ip a pada foosha

## (2) Kalian diminta untuk mendrop semua akses HTTP dari luar Topologi kalian pada server yang memiliki ip DHCP dan DNS Server demi menjaga keamanan.
#### Foosha

Command yang digunakan yaitu `iptables -A FORWARD -p tcp --dport 80 -d 192.173.0.16/29 -i eth0 -j DROP`

Keterangan:
- `A FORWARD:` Menggunakan chain FORWARD
- `p tcp:` Mendefinisikan protokol yang digunakan, yaitu tcp
- `dport 80:` Mendefinisikan port yang digunakan, yaitu 80 (HTTP)
- `d 192.173.0.16/29:` Mendefinisikan alamat tujuan dari paket (DHCP dan DNS SERVER ) berada pada subnet 192.173.0.16/29
- `i eth0:` Paket masuk dari eth0 Foosha
- `j DROP:` Paket di-drop

#### Testing

1. Install netcat di server Jipangu dan Doriki: `apt-get install netcat`
2. Pada Jipangu dan Doriki ketikkan: `nc -l -p 80`
3. Pada foosha ketikkan: `nmap -p 80 192.173.0.19` atau `nmap -p 80 192.173.0.18`

#### Foosha
![messageImage_1638870785918](https://user-images.githubusercontent.com/36225278/145457234-60fba7a4-1356-40eb-a32d-3ecc7e16ae2c.jpg)
![image](https://user-images.githubusercontent.com/36225278/145457134-3c68dcd0-8aeb-47c0-9929-7764e5f8b122.png)

#### Doriki
![messageImage_1638870718188](https://user-images.githubusercontent.com/36225278/145457706-c64452ac-463f-40f5-95e0-00dfa6cf0235.jpg)

#### Jipangu
![messageImage_1638870734466](https://user-images.githubusercontent.com/36225278/145457665-ed2a9e32-b39d-4720-993a-b76fb1173d4d.jpg)


## (3) Karena kelompok kalian maksimal terdiri dari 3 orang. Luffy meminta kalian untuk membatasi DHCP dan DNS Server hanya boleh menerima maksimal 3 koneksi ICMP secara bersamaan menggunakan iptables, selebihnya didrop.

#### Jipangu dan Doriki
Diberikan komen:
```
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -p icmp -m connlimit --connlimit-above 3 --connlimit-mask 0 -j DROP
```

Keterangan:
- `A INPUT:` Menggunakan chain INPUT
- `p icmp:` Mendefinisikan protokol yang digunakan, yaitu ICMP (ping)
- `m connlimit:` Menggunakan rule connection limit
- `connlimit-above 3:` Limit yang ditangkap paket adalah di atas 3
- `connlimit-mask 0 :` Hanya memperbolehkan 3 koneksi setiap subnet dalam satu waktu
- `j DROP:` Paket di-drop

Lalu untuk mengecek bisa dilakukan dengan masuk ke 4 node berbeda
Lalu, ping ke arah Jipangu secara bersamaan.

### Testing
Kita ping ke Jipangu secara bersamaan,

#### Foosha
![messageImage_1639067277163](https://user-images.githubusercontent.com/36225278/145457931-6bf1e091-1289-4c70-9aaf-b8ff0afd3ad9.jpg)

#### Fukurou
![messageImage_1639067269426](https://user-images.githubusercontent.com/36225278/145457991-3888f300-a6f9-4269-8d3e-042a2e2bda36.jpg)

#### Maingate
![messageImage_1639067260886](https://user-images.githubusercontent.com/36225278/145458046-527e03e9-38db-46f8-8bde-3ce72c92f43f.jpg)

#### Elena
Pada saat yang ke-4 mengakses node yang sama, maka ditolak
![messageImage_1639067251507](https://user-images.githubusercontent.com/36225278/145460468-d2eef565-ba96-4c46-bab7-596b08ed6f20.jpg)

## (4) Kemudian kalian diminta untuk membatasi akses ke Doriki yang berasal dari subnet Blueno, Cipher, Elena dan Fukuro dengan beraturan sebagai berikut :Akses dari subnet Blueno dan Cipher hanya diperbolehkan pada pukul 07.00 - 15.00 pada hari Senin sampai Kamis.

#### Doriki
```
iptables -A INPUT -s 192.173.0.128/25 -m time --timestart 07:00 --timestop 15:00 --weekdays Mon,Tue,Wed,Thu -j ACCEPT
iptables -A INPUT -s 192.173.0.128/25 -j REJECT
```

#### Chiper
```
iptables -A INPUT -s 192.173.4.0/22 -m time --timestart 07:00 --timestop 15:00 --weekdays Mon,Tue,Wed,Thu -j ACCEPT
iptables -A INPUT -s 192.173.4.0/22 -j REJECT
```

Keterangan:

- `A INPUT :` Menggunakan chain INPUT
- `s 192.173.0.128/25 :` Mendifinisikan alamat asal dari paket yaitu IP dari subnet Blueno
- `s 192.173.4.0/22 :` Mendifinisikan alamat asal dari paket yaitu IP dari subnet Chiper
- `m time :` Menggunakan rule time
- `timestart 07:00 :` Mendefinisikan waktu mulai yaitu 07:00
- `timestop 15:00:` Mendefinisikan waktu berhenti yaitu 15:00
- `weekdays Mon,Tue,Wed,Thu :` Mendefinisikan hari yaitu Senin hingga Kamis
- `j ACCEPT :` Paket di-accept
- `j REJECT :` Paket ditolak

### Testing

Saat Hari Senin - Kamis antara jam 07.00 - 15.00
![image](https://user-images.githubusercontent.com/36225278/145458400-03be2876-9647-46f6-87bd-c6b633e8e613.png)

Saat Hari Senin - Kamis selain jam 07.00 - 15.00
![image](https://user-images.githubusercontent.com/36225278/145458662-d1c9658d-eb8a-4ac0-a60a-ede0820beef4.png)

## (5) Akses dari subnet Elena dan Fukuro hanya diperbolehkan pada pukul 15.01 hingga pukul 06.59 setiap harinya.Selain itu di reject

#### Doriki 
Untuk paket yang berasal dari ELENA menggunakan perintah:
`iptables -A INPUT -s 192.173.2.0/23 -m time --timestart 07:00 --timestop 15:00 -j REJECT`
Untuk paket yang berasal dari FUKUROU menggunakan perintah:
`iptables -A INPUT -s 192.173.1.0/24 -m time --timestart 07:00 --timestop 15:00 -j REJECT`

Keterangan:

- `A INPUT :` Menggunakan chain INPUT
- `s 192.173.2.0/23 :` Mendifinisikan alamat asal dari paket yaitu IP dari subnet Elena
- `s 192.173.1.0/24 :` Mendifinisikan alamat asal dari paket yaitu IP dari subnet Fukurou
- `m time :` Menggunakan rule time
- `timestart 07:00 :` Mendefinisikan waktu mulai yaitu 07:00
- `timestop 15:00 :` Mendefinisikan waktu berhenti yaitu 15:00
- `j REJECT :` Paket ditolak

### Testing

Saat pukul 15.01 - 06.59
![messageImage_1639067928444](https://user-images.githubusercontent.com/36225278/145459102-2c77d50d-8343-4a0b-9601-ce775f9c8dc1.jpg)

Saat selain pukul 15.01 - 06.59
![messageImage_1639067956156](https://user-images.githubusercontent.com/36225278/145459126-7f6c8580-cef2-43fd-9aa4-013d59dc0ed4.jpg)


## (6) Karena kita memiliki 2 Web Server, Luffy ingin Guanhao disetting sehingga setiap request dari client yang mengakses DNS Server akan didistribusikan secara bergantian pada Jorge dan Maingate

#### Doriki
- Membuat domain (DNS) yang mengarah ke IP random pada file `/etc/bind/named.conf`
```
zone "jarkomA09.com" {
        type master;
        file "/etc/bind/jarkom/jarkomA09.com";
};
```
- Buat folder jarkom dengan command:
`mkdir /etc/bind/jarkom`
- Copy `db.local` ke file `/etc/bind/jarkom/jarkomA09.com`
```
cp /etc/bind/db.local /etc/bind/jarkom/jarkomA09.com
```

- Edit file `/etc/bind/jarkom/jarkomA09.com`
```
$TTL    604800
@       IN      SOA     jarkomA09.com. root.jarkomA09.com. (
                        2021120705      ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      jarkomA09.com.
@       IN      A       192.173.8.1
```

#### Guanhao

Masukkan perintah:
```
iptables -A PREROUTING -t nat -p tcp -d 192.173.8.1 --dport 80 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 192.173.0.26:80
iptables -A PREROUTING -t nat -p tcp -d 192.173.8.1 --dport 80 -j DNAT --to-destination 192.173.0.27:80
iptables -t nat -A POSTROUTING -p tcp -d 192.173.0.26 --dport 80 -j SNAT --to-source 192.173.8.1:80
iptables -t nat -A POSTROUTING -p tcp -d 192.173.0.27 --dport 80 -j SNAT --to-source 192.173.8.1:80
```

#### Testing
- Pada Guanhao, Jorge, Maingate Elena dan fukurou `install apt-get install netcat`
- Pada Jorge ketikkan perintah: `nc -l -p 80`
- Pada Maingate ketikkan perintah: `nc -l -p 80`
- Pada client Elena dan fukurou ketikkan perintah: `nc 192.173.8.1 80`
- Ketikkan sembarang pada client Elena dan fukurou, nanti akan muncul bergantian

#### Elena
![image](https://user-images.githubusercontent.com/36225278/145459790-e52782dd-2221-49c9-97f3-aaf70450f7f7.png)

#### Fukurou
![image](https://user-images.githubusercontent.com/36225278/145459760-954a3319-12bd-40e0-aeb1-5070a4b09321.png)

#### Jorge
![image](https://user-images.githubusercontent.com/36225278/145459805-5b2e2973-1f1d-4e39-bda4-524b4a5771ee.png)

#### Maingate
![image](https://user-images.githubusercontent.com/36225278/145459822-0646a6fd-46f8-4474-9463-857ae8d6459e.png)

### Kendala:

- Kendala pada jaringan internet sehingga restart node dan menjalankan ulang scriptnya
- Nomor 1 ketika mencari IP nat pada source sempat kesulitan dan vlsm juga masih kagok
- Nomor 2 masih bingung ketika di bash, output port 80 udah filtered tapi ketika di jalankan kembali outputnya open
- Nomor 3 pada saat 4 node secara bersamaan semua ping menuju doriki atau jipangu mati
- Nomor 6 bingung ketika testingnya awal" karena masih awam
