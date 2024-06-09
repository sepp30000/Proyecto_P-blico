A partir de una imagen de ubuntu server instalada en nuestro servidor nos conectaremos por ssh

```bash
ssh sepp@[direccion-del-servidor]
```
Lo primero que haremos será instalar docker y docker-compose

```bash
sudo apt update
sudo apt upgrade
```

# añadimos docker al repositorio

```bash
# Add Docker's official GPG key:
sudo apt update
sudo apt install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
```

# Lo instalamos

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

arrancamos el servicio

```bash
sudo systemctl start docker
sudo systemctl enable docker
```

lo probamos

```bash
sudo docker run hello-world
```

para que no nos pida sudo

```bash
sudo usermod -aG docker sepp
newgrp docker
```

vamos a montar un docker-compose con apache para hacer el webdav

```yml

```