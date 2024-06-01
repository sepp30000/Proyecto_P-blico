imagen router mikrotik: chr 7.11.2 de gns3


RouterMikrotik
dhcp-client
add interface=ether1


ip internet: 192.168.1.0/24
ip dmz: 192.168.10.0/24
ip red interna: 192.168.20.0/22 (Haremos VLAN)
     vlan almacen: 22
     vlan tecnicos: 21
     vlan administración: 23

add address=192.168.10.0/24 interface=ether2