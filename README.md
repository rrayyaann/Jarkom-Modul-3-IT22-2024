# Lapres Pratikum Jarkom-Modul-2-IT22-2024

**KELOMPOK IT22**
| Nama | NRP |
|---------------------------|------------|
|Muhamad Arrayyan | 5027231014 |
|Fadlillah Cantika Sari Hermawan | 5027231042 |

## Topologi 
<img width="1500" alt="image" src="https://github.com/user-attachments/assets/fc7efea8-81d8-47b8-8ccc-57cc84b05cf2">

<details>

<summary>Detail Gambar</summary>

## Network Config
| **Node**       | **Interface** | **IP Address**  | **Netmask**         | **Gateway**       | **Configuration** |
|----------------|---------------|-----------------|---------------------|-------------------|-------------------|
| Arakis (Router/DHCP Relay) | eth0 | DHCP            | -                   | -                 | DHCP              |
| Arakis (Router/DHCP Relay) | eth1 | 192.244.1.1     | 255.255.255.0       | -                 | Static            |
| Arakis (Router/DHCP Relay) | eth2 | 192.244.2.1     | 255.255.255.0       | -                 | Static            |
| Arakis (Router/DHCP Relay) | eth3 | 192.244.3.1     | 255.255.255.0       | -                 | Static            |
| Arakis (Router/DHCP Relay) | eth4 | 192.244.4.1     | 255.255.255.0       | -                 | Static            |
| Mohiam (DHCP Server)       | eth0 | 192.244.3.2     | 255.255.255.0       | 192.244.3.1       | Static            |
| Irulan (DNS Server)        | eth0 | 192.244.3.3     | 255.255.255.0       | 192.244.3.1       | Static            |
| Chani (Database Server)    | eth0 | 192.244.4.2     | 255.255.255.0       | 192.244.4.1       | Static            |
| Stilgar (Load Balancer)    | eth0 | 192.244.4.3     | 255.255.255.0       | 192.244.4.1       | Static            |
| Leto (Laravel Worker)      | eth0 | 192.244.2.2     | 255.255.255.0       | 192.244.2.1       | Static            |
| Duncan (Laravel Worker)    | eth0 | 192.244.2.3     | 255.255.255.0       | 192.244.2.1       | Static            |
| Jessica (Laravel Worker)   | eth0 | 192.244.2.4     | 255.255.255.0       | 192.244.2.1       | Static            |
| Vladimir (PHP Worker)      | eth0 | 192.244.1.2     | 255.255.255.0       | 192.244.1.1       | Static            |
| Rabban (PHP Worker)        | eth0 | 192.244.1.3     | 255.255.255.0       | 192.244.1.1       | Static            |
| Feyd (PHP Worker)          | eth0 | 192.244.1.4     | 255.255.255.0       | 192.244.1.1       | Static            |
| Dmitri (Client)            | eth0 | DHCP            | -                   | -                 | DHCP              |
| Paul (Client)              | eth0 | DHCP            | -                   | -                 | DHCP              |
