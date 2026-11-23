# Router-on-a-stick-Network
The Star Model

The Star Model Configuration

Devices Included:
- 1 Router
- 1 Switch
- 3 PCs

Interfaces on Router:
Interface G0/0.10 - 192.168.10.1/24
Interface G0/0.20 - 192.168.20.1/24

VLAN Assigment on Switch:
VLAN 10 - Covers PC 1 and PC 2 via interfaces ()
VLAN 20 - Covers PC 3 via interface ()

*network segmentation = controlled communication - prevents PCs from VLAN 1O from communicating with PCs in VLAN 20

Configuration to make the router act like a dhcp server:

MOST IMPORTANT - *excluding these host addresses below prevents the dhcp server from assigning any of these addresses as the dhcp server address

1. "Configure terminal" - to enter global configuration mode
2. ip dhcp excluded-address 192.168.10.1 192.168.10.10
3. ip dhcp excluded-address 192.168.20.1 192.168.20.10

DHCP Pool Configuration

1. Configure terminal 
2. int vlan 10
3. ip dhcp VLAN10_Pool
4. network 192.168.10.0 255.255.255.0 
5. default-router 192.168.10.1
6. dns-server 8.8.8.8
7. int vlan 20
8. ip dhcp VLAN20_Pool
9. network 192.168.20.0 255.255.255.0
10. default-router 192.168.20.1
11. dns-server 8.8.8.8
