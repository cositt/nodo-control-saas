# Nodo control de SaaS de Cositt

Este repositorio contiene información sobre como instalar el sistema de control de despliegue de SaaS de Cositt.
Es funcional en cualquier sistema operativo que soporte Docker y Docker Compose.

## Descripción

El Nodo de control de SaaS es un sistema en odoo que se ejecuta en docker y que permite el despliegue de clientes SAAS en nodos configurados para tal fin.

Utiliza una base de datos PostgreSQL, un nginx y un odoo.
Se utiliza un certificado ssl para la comunicación entre el cliente y el servidor generado mediante certbot.

## Requisitos

- Docker
- Docker Compose

## Certificado

Si disponemos de una clave ssh, la agregamos a github:

```bash
cat ~/.ssh/id_rsa.pub
```

Si no disponemos de clave ssh, generamos una:

```bash
ssh-keygen -t ed25519 -C "control@cositt.net"
```

Cuando se nos pida un nombre ponemos:

```bash
/root/.ssh/saas-control
```

copiamos la clave publica al portal de github:

```bash
cat /root/.ssh/saas-control.pub

```

Ahora clonamos el repositorio de github dentro del directorio creado anteriormente:

```bash
GIT_SSH_COMMAND="ssh -i ~/.ssh/saas-control" git clone git@github.com:cositt/nodo-control-saas.git /opt/saas
```

## Instalación

Se debe instalar el contenido en /opt/saas

Configuracion de los ficheros .env

Hay dos fichero .env requeridos, uno en el directorio saas y otro dentro de clientes, se pueden copiar de los ficheros .env.example que se encuentran en los mismos directorios.

## Creación certificado SSL

Para la creación del certificado SSL se debe ejecutar el siguiente comando desde el directorio saas, se recomienda el uso de un usuario y no de root

```bash
docker-compose run --rm -f docker-compose.certbot.yml certbot
```
