+++
title = "Instalar"
weight = 1
+++

## Instalar Docker

Linux (Ubuntu)

### Añadir y configurar el repositorio de docker:

1. Actualizar el repositorio

``bash
sudo apt-get update
```


2. Instalar los paquetes para permitir usar un repositorio sobre https

```bash
sudo apt-get install \
apt-transport-https \
ca-certificates \
curl \
gnupg-agent \
software-properties-common
```

3. Añadir la clave GPG oficial de Docker

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

 - Comprobar que ha funcionado:
    sudo apt-key fingerprint 0EBFCD88

4. Añadir el repositorio para la última verisón disponible

```bash
sudo add-apt-repository \
"deb [arch=amd64] https://download.docker.com/linux/ubuntu \
$(lsb_release -cs) \
stable"
```

### Instalar Docker CE(Community Edition)

1. Actualizar el índice de paquetes apt

```bash
sudo apt-get update
```

2. Instalar Docker CE y containerd

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

3. Comprobar que se ha instalado

```bash
docker --version
```

4. Comprobar que funciona correctamente ejecutando la imagen hello-world

```bash
sudo docker run hellow-world
```

La información aquí indicada ha sido traducida y simplificada de la web oficial: [Docker docs - DockerCE - Linux - Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/#install-docker-ce-1)