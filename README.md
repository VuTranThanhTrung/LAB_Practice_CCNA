# Lab 1 – VLAN, Routing, DHCP, NAT, STP

## 🎯 Mục tiêu
- Cấu hình VLAN, trunk, và access port.
- Triển khai Router-on-a-stick cho Inter-VLAN Routing.
- Định tuyến OSPF đơn vùng giữa các router.
- DHCP Server cấp phát IP cho VLAN 10, 20, 30.
- NAT cho phép các mạng nội bộ truy cập Internet.
- STP với đường dự phòng theo yêu cầu.

- 
## 📋 Bảng địa chỉ IP chi tiết

| Thiết bị       | Interface   | Địa chỉ IP         | Subnet Mask       | VLAN / Mạng liên quan           |
|----------------|-------------|--------------------|-------------------|-------------------------------|
| **Router1**    | Fa0/0       | 192.168.1.254      | 255.255.255.0     | Mạng LAN PC1 (192.168.1.0/24) |
|                | Se0/0/1     | 10.10.68.1         | 255.255.255.0     | Liên kết Router1-Router3       |
| **Router2**    | Se0/0/0     | 1.1.1.2            | 255.255.255.252   | Liên kết Router2-Router3       |
|                | Fa0/1       | 2.2.2.1            | 255.255.255.252   | Liên kết Router2-ISP           |
| **Router3**    | Se0/0/1     | 10.10.68.2         | 255.255.255.0     | Liên kết Router1-Router3       |
|                | Se0/0/0     | 1.1.1.1            | 255.255.255.252   | Liên kết Router2-Router3       |
|                | G0/1.10     | 10.10.64.254       | 255.255.255.0     | VLAN 10                       |
|                | G0/1.20     | 10.10.65.254       | 255.255.255.0     | VLAN 20                       |
|                | G0/1.30     | 10.10.66.254       | 255.255.255.0     | VLAN 30                       |
|                | G0/1.40     | 10.10.67.254       | 255.255.255.0     | VLAN 40                       |
| **ISP**        | Fa0/0       | 3.3.3.254          | 255.255.255.0     | Mạng Internet                 |
|                | Fa0/1       | 2.2.2.2            | 255.255.255.252   | Liên kết Router2-ISP          |
| **DNS Server** | Fa0         | 3.3.3.1            | 255.255.255.0     | Mạng Internet                 |
| **PC1**        | Fa0         | 192.168.1.1        | 255.255.255.0     | Mạng LAN 192.168.1.0/24       |
| **PC4**        | Fa0         | DHCP (10.10.64.x)  | 255.255.255.0     | VLAN 10                      |
| **PC5**        | Fa0         | DHCP (10.10.65.x)  | 255.255.255.0     | VLAN 20                      |
| **PC6**        | Fa0         | DHCP (10.10.66.x)  | 255.255.255.0     | VLAN 30                      |
| **PC7**        | Fa0         | 3.3.3.2            | 255.255.255.0     | Mạng Internet                 |
| **Mail Server**| Fa0         | 10.10.67.1         | 255.255.255.0     | VLAN 40                      |
| **Web Server** | Fa0         | 10.10.67.2         | 255.255.255.0     | VLAN 40                      |
| **FTP Server** | Fa0         | 10.10.67.3         | 255.255.255.0     | VLAN 40                      |
