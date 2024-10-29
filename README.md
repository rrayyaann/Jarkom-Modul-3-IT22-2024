# Lapres Pratikum Jarkom-Modul-3-IT22-2024

**KELOMPOK IT22**
| Nama | NRP |
|---------------------------|------------|
|Muhamad Arrayyan | 5027231014 |
|Fadlillah Cantika Sari Hermawan | 5027231042 |

<details>

<summary>Dokumentasi Gambar</summary>

![image](https://github.com/user-attachments/assets/530347e1-9621-43b2-9496-e004f948127c)
![image](https://github.com/user-attachments/assets/a4e95434-52b7-4933-b47e-084ed35477e6)
![image](https://github.com/user-attachments/assets/349ce330-d4f5-4f7f-8046-25723a2476df)
![image](https://github.com/user-attachments/assets/5ef5b72a-b32d-468f-9ea7-cab3c18604f2)
![image](https://github.com/user-attachments/assets/1c6ce56c-d3d9-44ed-b057-10620d2dca3a)
![image](https://github.com/user-attachments/assets/3b18793b-4ea0-4793-a4f3-3b8ee27bea21)

![image](https://github.com/user-attachments/assets/3d5ed48d-3e33-4064-af04-fad464968fad)

</details>

## Topologi 
<img width="1500" alt="image" src="https://github.com/user-attachments/assets/fc7efea8-81d8-47b8-8ccc-57cc84b05cf2">

<details>

<summary>Detail Gambar</summary>

</details>

## Tabel Network Config
| **Node**       | **Interface** | **IP Address**  | **Netmask**         | **Gateway**       | **Configuration** |
|----------------|---------------|-----------------|---------------------|-------------------|-------------------|
| Paradis (Router/DHCP Relay) | eth0 | DHCP            | -                   | -                 | DHCP              |
| Paradis (Router/DHCP Relay) | eth1 | 192.244.1.1     | 255.255.255.0       | -                 | Static            |
| Paradis (Router/DHCP Relay) | eth2 | 192.244.2.1     | 255.255.255.0       | -                 | Static            |
| Paradis (Router/DHCP Relay) | eth3 | 192.244.3.1     | 255.255.255.0       | -                 | Static            |
| Paradis (Router/DHCP Relay) | eth4 | 192.244.4.1     | 255.255.255.0       | -                 | Static            |
| Tybur (DHCP Server)         | eth0 | 192.244.4.2     | 255.255.255.0       | 192.244.4.1       | Static            |
| Fritz (DNS Server)          | eth0 | 192.244.4.3     | 255.255.255.0       | 192.244.4.1       | Static            |
| Warhammer (Database Server) | eth0 | 192.244.3.4     | 255.255.255.0       | 192.244.3.1       | Static            |
| Beast (Load Balancer Laravel)  | eth0 | 192.244.3.2  | 255.255.255.0       | 192.244.3.1       | Static            |
| Colossal (Load Balancer PHP)   | eth0 | 192.244.3.3  | 255.255.255.0       | 192.244.3.1       | Static            |
| Armin (PHP Worker)             | eth0 | 192.244.2.2  | 255.255.255.0       | 192.244.2.1       | Static            |
| Eren (PHP Worker)              | eth0 | 192.244.2.3  | 255.255.255.0       | 192.244.2.1       | Static            |
| Mikasa (PHP Worker)            | eth0 | 192.244.2.4  | 255.255.255.0       | 192.244.2.1       | Static            |
| Annie (Laravel Worker)         | eth0 | 192.244.1.2  | 255.255.255.0       | 192.244.1.1       | Static            |
| Bertholdt (Laravel Worker)     | eth0 | 192.244.1.3  | 255.255.255.0       | 192.244.1.1       | Static            |
| Reiner (Laravel Worker)        | eth0 | 192.244.1.4  | 255.255.255.0       | 192.244.1.1       | Static            |
| Zeke (Client)                  | eth0 | DHCP         | -                   | -                 | DHCP              |
| Erwin (Client)                 | eth0 | DHCP         | -                   | -                 | DHCP              

## Settingan Config
<details>

<summary>Detail Configure</summary>

## Konfigurasi
### Paradis
```jsx
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
	address 192.244.1.1
	netmask 255.255.255.0

auto eth2
iface eth2 inet static
	address 192.244.2.1
	netmask 255.255.255.0

auto eth3
iface eth3 inet static
	address 192.244.3.1
	netmask 255.255.255.0

auto eth4
iface eth4 inet static
	address 192.244.4.1
	netmask 255.255.255.0

up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 192.244.0.0/16
```

### Annie
```jsx
auto eth0
iface eth0 inet static
	address 192.244.1.2
	netmask 255.255.255.0
	gateway 192.244.1.1
```
### Berthold
```jsx
auto eth0
iface eth0 inet static
	address 192.244.1.3
	netmask 255.255.255.0
	gateway 192.244.1.1
```
### Reiner
```jsx
auto eth0
iface eth0 inet static
	address 192.244.1.4
	netmask 255.255.255.0
	gateway 192.244.1.1
```
### Armin
```jsx
auto eth0
iface eth0 inet static
	address 192.244.2.2
	netmask 255.255.255.0
	gateway 192.244.2.1
```
### Eren
```jsx
auto eth0
iface eth0 inet static
	address 192.244.2.3
	netmask 255.255.255.0
	gateway 192.244.2.1
```
### Mikasa
```jsx
auto eth0
iface eth0 inet static
	address 192.244.2.4
	netmask 255.255.255.0
	gateway 192.244.2.1
```
### Beast
```jsx
auto eth0
iface eth0 inet static
	address 192.244.3.2
	netmask 255.255.255.0
	gateway 192.244.3.1
```
### Colossal
```jsx
auto eth0
iface eth0 inet static
	address 192.244.3.3
	netmask 255.255.255.0
	gateway 192.244.3.1
```
### Warhammer
```jsx
iface eth0 inet static
	address 192.244.3.4
	netmask 255.255.255.0
	gateway 192.244.3.1
```
### Fritz
```jsx
auto eth0
iface eth0 inet static
	address 192.244.4.3
	netmask 255.255.255.0
	gateway 192.244.4.1
```
### Tybur
```jsx
auto eth0
iface eth0 inet static
	address 192.244.4.2
	netmask 255.255.255.0
	gateway 192.244.4.1
```
### Zeke dan Erwin
```jsx
auto eth0
iface eth0 inet dhcp
```
</details>

<details>

<summary>Instalasi Dependensi</summary>

### Paradis (DHCP Relay)
```jsx
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 192.244.0.0/16
apt-get update
apt-get install isc-dhcp-relay -y
```

### Tybur (DHCP Server)
```jsx
echo 'nameserver 192.244.4.3' > /etc/resolv.conf
apt-get update
apt-get install isc-dhcp-server -y
```

### Fritz (DNS Server)
```jsx
echo 'nameserver 192.168.122.1' > /etc/resolv.conf
apt-get update
apt-get install bind9 -y

echo 'options {
        directory "/var/cache/bind";

        forwarders {
                192.168.122.1;
        };

        // dnssec-validation auto;
        allow-query{any;};
        auth-nxdomain no;
        listen-on-v6 { any; };
}; ' >/etc/bind/named.conf.options

service bind9 restart
```

### Beast (Load Balancer)
```jsx
echo 'nameserver 192.244.4.3' > /etc/resolv.conf
apt-get update 
apt-get install apache2-utils -y
apt-get install nginx -y
apt-get install lynx -y
apt-get install php-fpm php-mbstring php-xml php-zip -y
service nginx start
```

### Colossal (Load Balancer)
```jsx
echo 'nameserver 192.244.4.3' > /etc/resolv.conf
apt-get update 
apt-get install bind9 -y
apt-get install apache2-utils -y
apt-get install nginx -y
apt-get install lynx -y
apt-get install php-fpm php-mbstring php-xml php-zip -y
service nginx start
```

### Warhammer (Database Server)
```jsx
echo 'nameserver 192.244.4.3' > /etc/resolv.conf
apt-get update
apt-get install mariadb-server -y
service mysql start
```

### Annie, Bertholdt, Reiner (Laravel Worker)
```jsx
echo 'nameserver 192.244.4.3' > /etc/resolv.conf
apt-get update
apt-get install lynx -y
apt-get install mariadb-client -y
apt-get install wget -y
apt-get install unzip -y
apt-get install -y lsb-release ca-certificates apt-transport-https software-properties-common gnupg2
apt install php7.3 -y
apt install php7.3-fpm -y
apt-get install nginx -y
apt-get install git -y
apt-get install htop -y
service nginx start
```

### Armin, Eren, Mikasa (PHP Worker)
```jsx
echo 'nameserver 192.244.4.3' > /etc/resolv.conf
apt-get update
apt-get install lynx -y
apt-get install nginx -y
apt-get install wget -y
apt-get install unzip -y
apt install software-properties-common -y
apt install php -y
apt install php php-fpm -y
```

### Zeke dan Erwin (Client)
```jsx
apt update
apt install lynx -y
apt install htop -y
apt install apache2-utils -y
apt-get install jq -y
```
</details>

## No.0
> Pulau Paradis telah menjadi tempat yang damai selama 1000 tahun, namun kedamaian tersebut tidak bertahan selamanya. Perang antara kaum Marley dan Eldia telah mencapai puncak. Kaum Marley yang dipimpin oleh Zeke, me-register domain name marley.yyy.com untuk worker Laravel mengarah pada Annie. Namun ternyata tidak hanya kaum Marley saja yang berinisiasi, kaum Eldia ternyata sudah mendaftarkan domain name eldia.yyy.com untuk worker PHP (0) mengarah pada Armin.


<details>

<summary>Detail Configure</summary>

> Membuat script di Fritz untuk memberikan domain marley.it25.com yang menyambung ke IP Annie, dan domain eldia.it25.com yang menyambung ke IP Armin

Fritz (warprepare.sh)
```bash
echo 'zone "marley.it22.com" { 
        type master; 
        file "/etc/bind/marley/marley.it22.com";
};

zone "eldia.it22.com" {
        type master;
        file "/etc/bind/eldia/eldia.it22.com";
}; ' >> /etc/bind/named.conf.local

mkdir /etc/bind/marley
mkdir /etc/bind/eldia

echo ';
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     marley.it22.com. root.marley.it22.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      marley.it22.com.
@       IN      A       192.244.1.2     ; IP Annie' > /etc/bind/marley/marley.it22.com

echo ';
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     eldia.it22.com. root.eldia.it22.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      eldia.it22.com.
@       IN      A       192.244.2.2     ; IP Armin' > /etc/bind/eldia/eldia.it22.com

service bind9 restart
```
</details>

### Test ping di client
<img width="1500" alt="image" src="https://github.com/user-attachments/assets/3b18793b-4ea0-4793-a4f3-3b8ee27bea21">

## No.1-5
Lakukan konfigurasi sesuai dengan peta yang sudah diberikan.

Jauh sebelum perang dimulai, ternyata para keluarga bangsawan, Tybur dan Fritz, telah membuat kesepakatan sebagai berikut:
1. Semua Client harus menggunakan konfigurasi ip address dari keluarga Tybur (dhcp).
2. Client yang melalui bangsa marley mendapatkan range IP dari [prefix IP].1.05 - [prefix IP].1.25 dan [prefix IP].1.50 - [prefix IP].1.100 (2)
3. Client yang melalui bangsa eldia mendapatkan range IP dari [prefix IP].2.09 - [prefix IP].2.27 dan [prefix IP].2 .81 - [prefix IP].2.243 (3)
4. Client mendapatkan DNS dari keluarga Fritz dan dapat terhubung dengan internet melalui DNS tersebut (4)
5. Dikarenakan keluarga Tybur tidak menyukai kaum eldia, maka mereka hanya meminjamkan ip address ke kaum eldia selama 6 menit. Namun untuk kaum marley, keluarga Tybur meminjamkan ip address selama 30 menit. Waktu maksimal dialokasikan untuk peminjaman alamat IP selama 87 menit. (5)

### Membuat script untuk menghubungkan DHCP Relay (Paradis) dengan DHCP Server (Tybur)
<details>

<summary>Instalasi Dependensi</summary>

Paradis (Soal 1-5.sh)
```
echo '# Defaults for isc-dhcp-relay initscript
# sourced by /etc/init.d/isc-dhcp-relay
# installed at /etc/default/isc-dhcp-relay by the maintainer scripts

#
# This is a POSIX shell fragment
#

# What servers should the DHCP relay forward requests to?
SERVERS="192.244.4.2"

# On what interfaces should the DHCP relay (dhrelay) serve DHCP requests?
INTERFACES="eth1 eth2 eth3 eth4"

# Additional options that are passed to the DHCP relay daemon?
OPTIONS=""' > /etc/default/isc-dhcp-relay

service isc-dhcp-relay start 
```

Tybur ((Soal 1-5.sh))
```
echo 'subnet 192.244.1.0 netmask 255.255.255.0 {
    range 192.244.1.05 192.244.1.25;
    range 192.244.1.50 192.244.1.100;
    option routers 192.244.1.1;
    option broadcast-address 192.244.1.255;
    option domain-name-servers 192.244.4.3;
    default-lease-time 1800;
    max-lease-time 5220;
}

subnet 192.244.2.0 netmask 255.255.255.0 {
    range 192.244.2.09 192.244.2.27;
    range 192.244.2.81 192.244.2.243;
    option routers 192.244.2.1;
    option broadcast-address 192.244.2.255;
    option domain-name-servers 192.244.4.3;
    default-lease-time 360;
    max-lease-time 5220;
}

subnet 192.244.3.0 netmask 255.255.255.0 {
}

subnet 192.244.4.0 netmask 255.255.255.0 {
}' > /etc/dhcp/dhcpd.conf

echo '# Defaults for isc-dhcp-server (sourced by /etc/init.d/isc-dhcp-server)

# Path to dhcpd'\''s config file (default: /etc/dhcp/dhcpd.conf).
DHCPDv4_CONF=/etc/dhcp/dhcpd.conf
DHCPDv6_CONF=/etc/dhcp/dhcpd6.conf

# Path to dhcpd'\''s PID file (default: /var/run/dhcpd.pid).
DHCPDv4_PID=/var/run/dhcpd.pid
DHCPDv6_PID=/var/run/dhcpd6.pid

# Additional options to start dhcpd with.
#<----->Don'\''t use options -cf or -pf here; use DHCPD_CONF/ DHCPD_PID instead
OPTIONS=""

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#<----->Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACESv4="eth0"
INTERFACESv6=""' > /etc/default/isc-dhcp-server

service isc-dhcp-server restart
```
</details>

### Test setelah client mendapat IP Dynamic dengan konfigurasi lease time yang sudah ditentukan
<img width="1500" alt="image" src="https://github.com/user-attachments/assets/1c6ce56c-d3d9-44ed-b057-10620d2dca3a">

### Test ping eldia.it22.com dan marley.it22.com setelah mendapat ip dynamic
<img width="1500" alt="image" src="https://github.com/user-attachments/assets/3b18793b-4ea0-4793-a4f3-3b8ee27bea21">

## No. 6
Armin berinisiasi untuk memerintahkan setiap worker PHP untuk melakukan konfigurasi virtual host untuk website berikut https://intip.in/BangsaEldia dengan menggunakan php 7.3 (6)
Setup PHP Worker (Armin, Eren, Mikasa)
```
#!/bin/bash

# Update package list and install necessary packages
apt-get update
apt-get install lynx nginx wget unzip php7.3 php-fpm -y

# Start PHP-FPM and Nginx services
service php7.3-fpm start
service nginx start

# Create download directory
mkdir -p /var/www/html/download/

# Download the ZIP file from Google Drive
wget --no-check-certificate 'https://drive.google.com/uc?export=download&id=1yliJkxu-3XmgJ6Xb37pGc2Jht5NTO9oj' -O /var/www/html/download/bangsa-eldia.zip

# Unzip the downloaded file
unzip /var/www/html/download/bangsa-eldia.zip -d /var/www/html/download

# Move extracted files to the web root
mv /var/www/html/download/bangsa-eldia/modul-3/* /var/www/html/

# Clean up by removing the download directory
rm -rf /var/www/html/download/

# Configure Nginx
cat <<EOL > /etc/nginx/sites-available/it19.conf
server {
    listen 80;

    root /var/www/html;

    index index.php index.html index.htm;

    server_name _;

    location / {
        try_files \$uri \$uri/ /index.php?\$query_string;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php7.3-fpm.sock;
    }

    error_log /var/log/nginx/it19_error.log;
    access_log /var/log/nginx/it19_access.log;
}
EOL

# Enable the site configuration
ln -s /etc/nginx/sites-available/it19.conf /etc/nginx/sites-enabled/

# Remove the default Nginx site
rm /etc/nginx/sites-enabled/default

# Restart Nginx and PHP-FPM services
service nginx restart
service php7.3-fpm restart
```

## No. 7
Pengujian dilakukan dengan mengirimkan 6000 request dan 200 request/second untuk mengevaluasi performa load balancer.

Langkah-langkah:

1. Pastikan server Colossal sudah dikonfigurasi untuk mendistribusikan beban ke beberapa server PHP Worker (Armin, Eren, Mikasa). Server ini harus sudah diatur agar siap menerima dan mengarahkan permintaan (request) ke worker.

2. Gunakan alat pengujian ab untuk mengirim 6000 permintaan ke server Colossal dengan 200 permintaan yang dikirimkan bersamaan. Tujuannya adalah melihat seberapa baik server dapat menangani beban.

```
ab -n 6000 -c 200 http://10.76.3.3/
```

