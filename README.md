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
SERVERS="192.186.0.19"

# On what interfaces should the DHCP relay (dhrelay) serve DHCP requests?
INTERFACES=""

# Additional options that are passed to the DHCP relay daemon?
OPTIONS="" '> /etc/default/isc-dhcp-relay
```
5. Pada Jipangu edit file `/etc/default/isc-dhcp-server` dengan menambahkan:
`INTERFACES="eth0"`
6. Pada dhcp-server isikan data pada `/etc/dhcp/dhcpd.conf` di Jipangu, lalu lakukan `service isc-dhcp-server restart`
```
subnet 192.186.1.0 netmask 255.255.255.0 {
    range 192.186.1.2 192.186.1.254;
    option routers 192.186.1.1;
    option broadcast-address 192.186.1.255;
    option domain-name-servers 192.186.0.18;
    default-lease-time 600;
    max-lease-time 7200;
}
subnet 192.186.0.128 netmask 255.255.255.128 {
    range 192.186.0.130 192.186.0.254;
    option routers 192.186.0.129;
    option broadcast-address 192.186.0.255;
    option domain-name-servers 192.186.0.18;
    default-lease-time 600;
    max-lease-time 7200;
}
subnet 192.186.4.0 netmask 255.255.252.0 {
    range 192.186.4.2 192.186.4.254;
    option routers 192.186.4.1;
    option broadcast-address 192.186.4.255;
    option domain-name-servers 192.186.0.18;
    default-lease-time 600;
    max-lease-time 7200;
}
subnet 192.186.2.0 netmask 255.255.254.0 {
    range 192.186.2.2 192.186.2.254;
    option routers 192.186.2.1;
    option broadcast-address 192.186.2.255;
    option domain-name-servers 192.186.0.18;
    default-lease-time 600;
    max-lease-time 7200;
}
subnet 192.186.0.16 netmask 255.255.255.248{
}
```
7. Buka file `/etc/network/interfaces`. Command konfigurasi lama (static) dan ubah ip Blueno, Cipher, Fukurou, dan Elena dengan command
8. Lakukan restart di node yang dijadikan ip dhcp

## (1) Agar topologi yang kalian buat dapat mengakses keluar, kalian diminta untuk mengkonfigurasi Foosha menggunakan iptables, tetapi Luffy tidak ingin menggunakan MASQUERADE.

#### Foosha 

Command yang digunakan `iptables -t nat -A POSTROUTING -s 192.186.0.0/16 -o eth0 -j SNAT --to-s` (ip eth0) yang menyesuaikan dari eth0 tersebut

Lalu, pada semua node yang terkait dilakukan echo nameserver `192.168.122.1 > /etc/resolv.conf`

Keterangan:

-> ip eth0 akan selalu berganti ketika restart node pada foosha atau restart GNS3 dengan rentang IP yang sudah dijelaskan
-> Cara mengetahui eth0, masukan command ip a pada foosha

## (2) Kalian diminta untuk mendrop semua akses HTTP dari luar Topologi kalian pada server yang memiliki ip DHCP dan DNS Server demi menjaga keamanan.
#### Foosha

Command yang digunakan yaitu `iptables -A FORWARD -p tcp --dport 80 -d 192.186.0.16/29 -i eth0 -j DROP`

Keterangan:
-`A FORWARD:` Menggunakan chain FORWARD
-`p tcp:` Mendefinisikan protokol yang digunakan, yaitu tcp
-`dport 80:` Mendefinisikan port yang digunakan, yaitu 80 (HTTP)
-`d 192.186.0.16/29:` Mendefinisikan alamat tujuan dari paket (DHCP dan DNS SERVER ) berada pada subnet 192.186.0.16/29
-`i eth0:` Paket masuk dari eth0 Foosha
-`j DROP:` Paket di-drop

#### Testing

1. Install netcat di server Jipangu dan Doriki: `apt-get install netcat`
2. Pada Jipangu dan Doriki ketikkan: `nc -l -p 80`
3. Pada foosha ketikkan: `nmap -p 80 192.173.0.19` atau `nmap -p 80 192.173.0.18`

## (3) Karena kelompok kalian maksimal terdiri dari 3 orang. Luffy meminta kalian untuk membatasi DHCP dan DNS Server hanya boleh menerima maksimal 3 koneksi ICMP secara bersamaan menggunakan iptables, selebihnya didrop.

#### Jipangu dan Doriki
Diberikan komen:
```
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -p icmp -m connlimit --connlimit-above 3 --connlimit-mask 0 -j DROP
```

Keterangan:
```
-`A INPUT:` Menggunakan chain INPUT
-`p icmp:` Mendefinisikan protokol yang digunakan, yaitu ICMP (ping)
-`m connlimit:` Menggunakan rule connection limit
-`connlimit-above 3:` Limit yang ditangkap paket adalah di atas 3
-`connlimit-mask 0 :` Hanya memperbolehkan 3 koneksi setiap subnet dalam satu waktu
-`j DROP:` Paket di-drop
```

Lalu untuk mengecek bisa dilakukan dengan masuk ke 4 node berbeda
Lalu, ping ke arah Jipangu secara bersamaan.

## (4) Kemudian kalian diminta untuk membatasi akses ke Doriki yang berasal dari subnet Blueno, Cipher, Elena dan Fukuro dengan beraturan sebagai berikut :Akses dari subnet Blueno dan Cipher hanya diperbolehkan pada pukul 07.00 - 15.00 pada hari Senin sampai Kamis.

#### Doriki
```
iptables -A INPUT -s 192.186.0.128/25 -m time --timestart 07:00 --timestop 15:00 --weekdays Mon,Tue,Wed,Thu -j ACCEPT
iptables -A INPUT -s 192.186.0.128/25 -j REJECT
```

#### Chiper
```
iptables -A INPUT -s 192.186.4.0/22 -m time --timestart 07:00 --timestop 15:00 --weekdays Mon,Tue,Wed,Thu -j ACCEPT
iptables -A INPUT -s 192.186.4.0/22 -j REJECT
```

Keterangan:

-`A INPUT :` Menggunakan chain INPUT
-`s 192.173.0.128/25 :` Mendifinisikan alamat asal dari paket yaitu IP dari subnet Blueno
-`s 192.173.4.0/22 :` Mendifinisikan alamat asal dari paket yaitu IP dari subnet Chiper
-`m time :` Menggunakan rule time
-`timestart 07:00 :` Mendefinisikan waktu mulai yaitu 07:00
-`timestop 15:00:` Mendefinisikan waktu berhenti yaitu 15:00
-`weekdays Mon,Tue,Wed,Thu :` Mendefinisikan hari yaitu Senin hingga Kamis
-`j ACCEPT :` Paket di-accept
-`j REJECT :` Paket ditolak

### Testing
