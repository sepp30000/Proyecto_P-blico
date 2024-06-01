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




añadir vlan
add name=tecnicos vlan-id=10 interface=ether3 
add name=almacen vlan-id=20 interface=ether3 
add name=administracion vlan-id=30 interface=ether3 

interfaces
add address=192.168.21.1/24 interface=tecnicos  
add address=192.168.22.1/24 interface=almacen    
add address=192.168.23.1/24 interface=administracion 

dhcp server setup
Press F1 for general console usage help
[admin@MikroTik] /ip/dhcp-server> setup 
Select interface to run DHCP server on 

dhcp server interface:  
administracion     almacen     ether1     ether2     ether3     ether4     ether5     ether6     ether7     ether8     tecnicos   
dhcp server interface: tecnicos 
Select network for DHCP addresses 

dhcp address space: 192.168.21.0/24  
Select gateway for given network 

gateway for dhcp network: 192.168.21.1 
Select pool of ip addresses given out by DHCP server 

addresses to give out: 192.168.21.2-192.168.21.254, 
Select DNS servers 

dns servers: 8.8.8.8,1.1.1.1            
Select lease time 

lease time: 1800 


[admin@MikroTik] /ip/dhcp-server> setup 
Select interface to run DHCP server on 

dhcp server interface: almacen 
Select network for DHCP addresses 

dhcp address space: 192.168.22.0/24 
Select gateway for given network 

gateway for dhcp network: 192.168.22.1 
Select pool of ip addresses given out by DHCP server 

addresses to give out: 192.168.22.2-192.168.22.254, 
Select DNS servers 

dns servers: 8.8.8.8,1.1.1.1            
Select lease time 

lease time: 1800


[admin@MikroTik] /ip/dhcp-server> setup 
Select interface to run DHCP server on 

dhcp server interface:  
administracion     almacen     ether1     ether2     ether3     ether4     ether5     ether6     ether7     ether8     tecnicos   
dhcp server interface: administracion 
Select network for DHCP addresses 

dhcp address space: 192.168.23.0/24 
Select gateway for given network 

gateway for dhcp network: 192.168.23.1 
Select pool of ip addresses given out by DHCP server 

addresses to give out: 192.168.23.2-192.168.23.254, 
Select DNS servers 

dns servers: 8.8.8.8,1,1,1,1            
value of dns-servers should have no more than 2 elements
dns servers: 8.8.8.8,1.1.1.1           
Select lease time 

lease time: 1800 

Salida internet
[admin@MikroTik] /ip/firewall/nat> add action=masquerade chain=srcnat out-interface=ether1 


## Conectar routers

R-entrada
[admin@MikroTik] /ip/address> add address=192.168.10.1/24 interface=ether2

R-DMZ
[admin@MikroTik] /ip/address> add address=192.168.10.2/24 interface=ether1

Red DMZ

ip address/add address=192.168.11.1/24 interface=ether2
salida dmz
[admin@MikroTik] /ip/firewall/nat> add action=masquerade chain=srcnat out-interface=ether1


En el router dmz
[admin@MikroTik] /ip/route> add gateway=192.168.10.1
[admin@MikroTik] /ip/dns> set servers=8.8.8.8,1.1.1.1

Configurar vpc internos para comprobar
ip 192.168.11.100 255.255.255.0 192.168.11.1
