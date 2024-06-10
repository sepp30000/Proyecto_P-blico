# Del primer al segundo router
# 192.168.21.1
/ip firewall nat
# Apache
add chain=dstnat dst-address=192.168.21.1 protocol=tcp dst-port=80 action=dst-nat \
  to-addresses=192.168.10.2 to-ports=80
add chain=dstnat dst-address=192.168.21.1 protocol=tcp dst-port=443 action=dst-nat \
  to-addresses=192.168.10.2 to-ports=443
# Postgre
add chain=dstnat dst-address=192.168.21.1 protocol=tcp dst-port=5432 action=dst-nat \
  to-addresses=192.168.10.2 to-ports=5432
# FTP
add chain=dstnat dst-address=192.168.21.1 protocol=tcp dst-port=21 action=dst-nat \
  to-addresses=192.168.10.2 to-ports=21
# Puertos dinamicos
add chain=dstnat dst-address=192.168.21.1 protocol=tcp dst-port=50000-51000 action=dst-nat \
  to-addresses=192.168.10.2 to-ports=30000-31000
# Teamvierwer
add chain=dstnat dst-address=192.168.21.1 protocol=tcp dst-port=5938 action=dst-nat \
  to-addresses=192.168.10.2 to-ports=5938
# ssh
add chain=dstnat dst-address=192.168.21.1 protocol=tcp dst-port=22 action=dst-nat \
  to-addresses=192.168.10.2 to-ports=22
# Pgadmin
add chain=dstnat dst-address=192.168.21.1 protocol=tcp dst-port=5938 action=dst-nat \
  to-addresses=192.168.10.2 to-ports=5050
# PHP
add chain=dstnat dst-address=192.168.21.1 protocol=tcp dst-port=5938 action=dst-nat \
  to-addresses=192.168.10.2 to-ports=8080

# 192.168.22.1
/ip firewall nat
add chain=dstnat dst-address=192.168.22.1 protocol=tcp dst-port=80 action=dst-nat \
  to-addresses=192.168.10.2 to-ports=80

add chain=dstnat dst-address=192.168.22.1 protocol=tcp dst-port=443 action=dst-nat \
  to-addresses=192.168.10.2 to-ports=443

add chain=dstnat dst-address=192.168.22.1 protocol=tcp dst-port=5432 action=dst-nat \
  to-addresses=192.168.10.2 to-ports=5432

add chain=dstnat dst-address=192.168.22.1 protocol=tcp dst-port=8080 action=dst-nat \
  to-addresses=192.168.10.2 to-ports=8080

add chain=dstnat dst-address=192.168.22.1 protocol=tcp dst-port=50000 action=dst-nat \
  to-addresses=192.168.10.2 to-ports=50000

add chain=dstnat dst-address=192.168.22.1 protocol=tcp dst-port=21 action=dst-nat \
  to-addresses=192.168.10.2 to-ports=21

add chain=dstnat dst-address=192.168.22.1 protocol=tcp dst-port=50000-51000 action=dst-nat \
  to-addresses=192.168.10.2 to-ports=50000-51000

add chain=dstnat dst-address=192.168.22.1 protocol=tcp dst-port=5938 action=dst-nat \
  to-addresses=192.168.10.2 to-ports=5938

add chain=dstnat dst-address=192.168.22.1 protocol=tcp dst-port=5938 action=dst-nat \
  to-addresses=192.168.10.2 to-ports=5938

# Pgadmin
add chain=dstnat dst-address=192.168.22.1 protocol=tcp dst-port=5938 action=dst-nat \
  to-addresses=192.168.10.2 to-ports=8000


# 192.168.23.1
/ip firewall nat
add chain=dstnat dst-address=192.168.23.1 protocol=tcp dst-port=80 action=dst-nat \
  to-addresses=192.168.10.2 to-ports=80

add chain=dstnat dst-address=192.168.23.1 protocol=tcp dst-port=443 action=dst-nat \
  to-addresses=192.168.10.2 to-ports=443

add chain=dstnat dst-address=192.168.23.1 protocol=tcp dst-port=5432 action=dst-nat \
  to-addresses=192.168.10.2 to-ports=5432

add chain=dstnat dst-address=192.168.23.1 protocol=tcp dst-port=8080 action=dst-nat \
  to-addresses=192.168.10.2 to-ports=8080

add chain=dstnat dst-address=192.168.23.1 protocol=tcp dst-port=50000 action=dst-nat \
  to-addresses=192.168.10.2 to-ports=50000

add chain=dstnat dst-address=192.168.23.1 protocol=tcp dst-port=21 action=dst-nat \
  to-addresses=192.168.10.2 to-ports=21

add chain=dstnat dst-address=192.168.23.1 protocol=tcp dst-port=50000-51000 action=dst-nat \
  to-addresses=192.168.10.2 to-ports=50000-51000

add chain=dstnat dst-address=192.168.23.1 protocol=tcp dst-port=5938 action=dst-nat \
  to-addresses=192.168.10.2 to-ports=5938
add chain=dstnat dst-address=192.168.23.1 protocol=tcp dst-port=5938 action=dst-nat \
  to-addresses=192.168.10.2 to-ports=22
# Pgadmin
add chain=dstnat dst-address=192.168.23.1 protocol=tcp dst-port=5938 action=dst-nat \
  to-addresses=192.168.10.2 to-ports=8000


# Del segundo router al servidor
/ip firewall nat
add chain=dstnat dst-address=192.168.10.2 protocol=tcp dst-port=80 action=dst-nat \
  to-addresses=192.168.11.11 to-ports=80

add chain=dstnat dst-address=192.168.10.2 protocol=tcp dst-port=443 action=dst-nat \
  to-addresses=192.168.11.11 to-ports=443

add chain=dstnat dst-address=192.168.10.2 protocol=tcp dst-port=5432 action=dst-nat \
  to-addresses=192.168.11.11 to-ports=5432

add chain=dstnat dst-address=192.168.10.2 protocol=tcp dst-port=8080 action=dst-nat \
  to-addresses=192.168.11.11 to-ports=8080

add chain=dstnat dst-address=192.168.10.2 protocol=tcp dst-port=50000 action=dst-nat \
  to-addresses=192.168.11.11 to-ports=50000

add chain=dstnat dst-address=192.168.10.2 protocol=tcp dst-port=21 action=dst-nat \
  to-addresses=192.168.11.11 to-ports=21

add chain=dstnat dst-address=192.168.10.2 protocol=tcp dst-port=50000-51000 action=dst-nat \
  to-addresses=192.168.11.11 to-ports=50000-51000

add chain=dstnat dst-address=192.168.10.2 protocol=tcp dst-port=5938 action=dst-nat \
  to-addresses=192.168.11.11 to-ports=5938

add chain=dstnat dst-address=192.168.10.2 protocol=tcp dst-port=5938 action=dst-nat \
  to-addresses=192.168.11.11 to-ports=22

add chain=dstnat dst-address=192.168.10.2 protocol=tcp dst-port=5938 action=dst-nat \
  to-addresses=192.168.11.11 to-ports=8000
