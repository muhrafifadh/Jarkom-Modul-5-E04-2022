# Jarkom-Modul-5-E04-2022
Laporan Resmi Praktikum Jarkom Modul 5

# Anggota Kelompok
Anggota  | NRP
---------|-------
Muhammad Afif Dwi Ardiansyah | 5025201212
Muhammad Rafif Fadhil Naufal | 5025201273
M Labib Alfaraby | 5025201083

## Soal Jarkom-Modul-5 2021
- [Soal] https://docs.google.com/document/d/1b-tRRx2BLu1RxCgXxnoI2lYJbG9E0C08adRppePfHxk/edit

### (A) Tugas pertama kalian yaitu membuat topologi jaringan sesuai dengan rancangan yang diberikan Loid dibawah ini:
![modul1](https://user-images.githubusercontent.com/81162174/206151572-c498b149-3f00-4c67-b29b-b97edb8e5c24.png)

Keterangan :	Eden adalah DNS Server
WISE adalah DHCP Server
		Garden dan SSS adalah Web Server
		Jumlah Host pada Forger adalah 62 host
		Jumlah Host pada Desmond adalah 700 host
		Jumlah Host pada Blackbell adalah 255 host
		Jumlah Host pada Briar adalah 200 host
### Untuk menjaga perdamaian dunia, Loid ingin meminta kalian untuk membuat topologi tersebut menggunakan teknik CIDR atau VLSM setelah melakukan subnetting.
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

### (C) Anya, putri pertama Loid, juga berpesan kepada anda agar melakukan Routing agar setiap perangkat pada jaringan tersebut dapat terhubung.

```
route add -net 192.173.1.0 netmask 255.255.255.0 gw 192.173.0.6                                     
route add -net 192.173.2.0 netmask 255.255.254.0 gw 192.173.0.6                                   
route add -net 192.173.0.24 netmask 255.255.255.248 gw 192.173.0.6                                    
route add -net 192.173.4.0 netmask 255.255.252.0 gw 192.173.0.2                                         
route add -net 192.173.0.128 netmask 255.255.255.128 gw 192.173.0.2                                 
route add -net 192.173.0.16 netmask 255.255.255.248 gw 192.173.0.2 
```

### (D) Tugas berikutnya adalah memberikan ip pada subnet Forger, Desmond, Blackbell, dan Briar secara dinamis menggunakan bantuan DHCP server. Kemudian kalian ingat bahwa kalian harus setting DHCP Relay pada router yang menghubungkannya.

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

## (1) Agar topologi yang kalian buat dapat mengakses keluar, kalian diminta untuk mengkonfigurasi Strix menggunakan iptables, tetapi Loid tidak ingin menggunakan MASQUERADE.

#### Strix 

Command yang digunakan `iptables -t nat -A POSTROUTING -s 192.194.0.0/21 -o eth0 -j SNAT --to-s` (ip eth0) yang menyesuaikan dari eth0 tersebut

Keterangan:

-> ip eth0 akan selalu berganti ketika restart node pada foosha atau restart GNS3 dengan rentang IP yang sudah dijelaskan
-> Cara mengetahui eth0, masukan command ip a pada Strix

Test ping google.com di Blackbell:

<img width="554" alt="image" src="https://user-images.githubusercontent.com/87472849/206823081-0263d992-3e16-47b9-9b89-fb73496b1397.png">

## (2) Kalian diminta untuk melakukan drop semua TCP dan UDP dari luar Topologi kalian pada server yang merupakan DHCP Server demi menjaga keamanan.

Command yang digunakan yaitu :

### Strix

`iptables -A FORWARD -p tcp --dport 80 -d 192.194.0.16/29 -i eth0 -j DROP` dan `iptables -A FORWARD -p udp --dport 80 -d 192.194.0.16/29 -i eth0 -j DROP`

Keterangan:
- `A FORWARD:` Menggunakan chain FORWARD
- `p tcp:` Mendefinisikan protokol yang digunakan, yaitu tcp
- `p udp:` Mendefinisikan protokol yang digunakan, yaitu udp
- `dport 80:` Mendefinisikan port yang digunakan, yaitu 80 (HTTP)
- `d 192.194.0.16/29:` Mendefinisikan alamat tujuan dari paket (DHCP dan DNS SERVER ) berada pada subnet 192.194.0.16/29
- `i eth0:` Paket masuk dari eth0 Strix
- `j DROP:` Paket di-drop

#### Testing

1. Install netcat di server Wise dan Eden: `apt-get install netcat`
2. Pada Wise dan Eden ketikkan: `nc -l -p 80`
3. Pada Strix ketikkan: `nmap -p 80 192.194.0.19` atau `nmap -p 80 192.194.0.18`

## (3) Loid meminta kalian untuk membatasi DHCP dan DNS Server hanya boleh menerima maksimal 2 koneksi ICMP secara bersamaan menggunakan iptables, selebihnya didrop.

#### Eden dan Wise
Diberikan komen:
```
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -p icmp -m connlimit --connlimit-above 2 --connlimit-mask 0 -j DROP
```

Keterangan:
- `A INPUT:` Menggunakan chain INPUT
- `p icmp:` Mendefinisikan protokol yang digunakan, yaitu ICMP (ping)
- `m connlimit:` Menggunakan rule connection limit
- `connlimit-above 2:` Limit yang ditangkap paket adalah di atas 2
- `connlimit-mask 0 :` Hanya memperbolehkan 3 koneksi setiap subnet dalam satu waktu
- `j DROP:` Paket di-drop

Lalu untuk mengecek bisa dilakukan dengan masuk ke 3 node berbeda
Lalu, ping ke arah WISE secara bersamaan.

### Testing
Kita ping ke WISE secara bersamaan,

#### Westalis
<img width="504" alt="image" src="https://user-images.githubusercontent.com/87472849/206823458-aa2c165f-837b-40af-ab8d-c8c7c1567759.png">

#### Strix
<img width="507" alt="image" src="https://user-images.githubusercontent.com/87472849/206823475-11d80c2e-7759-4bb4-ba43-0434e7264582.png">

#### Garden
Pada saat yang ke-3 mengakses node yang sama, maka ditolak </br>
<img width="498" alt="image" src="https://user-images.githubusercontent.com/87472849/206823498-8a0a432d-a55e-4258-810a-f170df3af675.png">

## (4) Akses menuju Web Server hanya diperbolehkan disaat jam kerja yaitu Senin sampai Jumat pada pukul 07.00 - 16.00.
#### Garden dan SSS
```
iptables -A INPUT -s 192.194.0.128/25 -m time --timestart 07:00 --timestop 16:00 --weekdays Mon,Tue,Wed,Thu,Fri -j ACCEPT
iptables -A INPUT -s 192.194.0.128/25 -j REJECT
```

Keterangan:

- `A INPUT :` Menggunakan chain INPUT
- `s 192.194.0.128/25 :` Mendifinisikan alamat asal dari paket yaitu IP dari subnet Forger
- `m time :` Menggunakan rule time
- `timestart 07:00 :` Mendefinisikan waktu mulai yaitu 07:00
- `timestop 16:00:` Mendefinisikan waktu berhenti yaitu 16:00
- `weekdays Mon,Tue,Wed,Thu,Fri :` Mendefinisikan hari yaitu Senin hingga Jumat
- `j ACCEPT :` Paket di-accept
- `j REJECT :` Paket ditolak

### Testing

Saat Hari Senin - Jumat antara jam 07.00 - 16.00
<img width="441" alt="image" src="https://user-images.githubusercontent.com/87472849/206823925-1225df63-5a28-4176-ad6e-b4474d2709fb.png">

## (5) Karena kita memiliki 2 Web Server, Loid ingin Ostania diatur sehingga setiap request dari client yang mengakses Garden dengan port 80 akan didistribusikan secara bergantian pada SSS dan Garden secara berurutan dan request dari client yang mengakses SSS dengan port 443 akan didistribusikan secara bergantian pada Garden dan SSS secara berurutan.

#### Eden
- Membuat domain (DNS) yang mengarah ke IP random pada file `/etc/bind/named.conf`
```
echo ‘
zone "jarkomE04.com" {
        type master;
        file "/etc/bind/jarkom/jarkomE04.com";
}; ‘ > /etc/bind/named.conf

mkdir /etc/bind/jarkom

cp /etc/bind/db.local /etc/bind/jarkom/jarkomE04.com

nano ‘
$TTL    604800
@       IN      SOA     jarkomE04.com. root.jarkomE04.com. (
                        2022120705      ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      jarkomE04.com.
@       IN      A       192.194.8.1
‘ > /etc/bind/jarkom/jarkomE04.com

service bind9 restart
```

#### Ostania

Masukkan perintah:
```
ptables -A PREROUTING -t nat -p tcp -d 192.194.8.1 --dport 80 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 192.194.0.27:80
iptables -A PREROUTING -t nat -p tcp -d 192.194.8.1 --dport 80 -j DNAT --to-destination 192.194.0.26:80
iptables -t nat -A POSTROUTING -p tcp -d 192.194.0.27 --dport 80 -j SNAT --to-source 192.194.8.1:80
iptables -t nat -A POSTROUTING -p tcp -d 192.194.0.26 --dport 80 -j SNAT --to-source 192.194.8.1:80

iptables -A PREROUTING -t nat -p tcp -d 192.194.8.1 --dport 443 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 192.194.0.26:443 
iptables -A PREROUTING -t nat -p tcp -d 192.194.8.1 --dport 443 -j DNAT --to-destination 192.194.0.27:443 
iptables -t nat -A POSTROUTING -p tcp -d 192.194.0.26 --dport 443 -j SNAT --to-source 192.194.8.1:443 
iptables -t nat -A POSTROUTING -p tcp -d 192.194.0.27 --dport 443 -j SNAT --to-source 192.194.8.1:443 
```

#### Testing
- Pada Garden, SSS, Blackbell, Briar `install apt-get install netcat`
- Pada Garden dan SSS ketikkan perintah: `nc -l -p 80`
- Pada client Blackbell dan Briar ketikkan perintah: `nc 192.194.8.1 80`
- Ketikkan sembarang pada clientBlackbell dan Briar, nanti akan muncul bergantian

#### Briar
<img width="215" alt="image" src="https://user-images.githubusercontent.com/87472849/206824305-b446d159-4dca-4ad4-ba14-5e6060cd9b09.png">

#### Garden
<img width="185" alt="image" src="https://user-images.githubusercontent.com/87472849/206824316-cd0dab67-064e-4c42-a07e-6af2ef232e52.png">


## (6) Karena Loid ingin tau paket apa saja yang di-drop, maka di setiap node server dan router ditambahkan logging paket yang di-drop dengan standard syslog level.



### Kendala:

- Kendala pada jaringan internet sehingga restart node dan menjalankan ulang scriptnya
- Nomor 2 masih kendala dalam memfilter paketnya
- Nomor 6 masih bingung cara mengerjakannya
