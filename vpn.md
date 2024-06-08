Enlace de interes: https://www.youtube.com/watch?v=vEecZXa3rYk
https://wireguard.how/client/macos
https://abcxperts.com/wireguard-en-mikrotik-routeros-una-solucion-segura-y-eficiente-para-vpn

Primer Paso: Actualizar Router

```bash
/tool wireguard key generate

/tool wireguard key print
```

Segundo paso: Crear interfaz WG0

```bash
/interface/wireguard add name=wg0 listen-port=51820
# Esto creará una private y public key del servidor, la usada ahora es de prueba
```

Configurar la interfaz

```bash
add address=192.168.23.2/24 network=192.168.23.0 interface=wg0
```

Configurar Firewall

```bash
/ip firewall filter add chain=forward action=drop comment="Block all forwarded traffic"
# Las reglas por defecto es que todas las conexiones estan cerradas abrimos tanto el puerto como las conexiones a la red de la vpn
/ip/firewall/filter
add chain=input action=accept protocol=udp dst-port=51820
add chain=input action=accept protocol=tcp dst-port=51820
add chain=input action=accept src-address=192.168.23.0/24
#Salir a internet
/ip/firewall/nat
add chain=srcnat action=masquerade out-interface=wg0
```

Creamos la peer

Nos descargamos el cliente de wireguard, en este caso en MAC, le damos a crear tunel vacio y le añadimos el nombre de la interfaz "wg0" copiamos la clave pública y nos vamos al mikrotik creamos nuevo peer en wireguard peers. Añadimos la clave pública y la dirección que va a utlizar el equipo.

Configuramos el cliente
Se puede exportar la configuración del cliente o leer el qr que te ofrece mikrotik. Pero lo vamos a configurar nosotros

```
#Respecto al equipo
[Interface]
PrivateKey = [Generada por el cliente]
# Direccion que ocupará el equipo
Address = 192.168.23.3/24
#DNS Será la puerta de enlace del router
DNS = 192.168.23.2
#Respecto al servidor
[Peer]
PublicKey = [Clave Pública del servidor]
# Lo dejamos así para que permita cualquier ip de donde esté conectado el equipo
AllowedIPs = 0.0.0.0/0
# Donde tiene que llegar el equipo, si hubiera un dns dinamico sería esa direccion más el puerto
Endpoint = 192.168.1.38:51820
# Manda paquetes para saber si sigue conectado
PersistentKeepalive = 10
```

ifconfig para ver que está configurado