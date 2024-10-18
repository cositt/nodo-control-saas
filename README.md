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

## Instalación

Se debe instalar el contenido en /opt/saas

```bash
git clone https://github.com/cositt/nodo-control-saas.git /opt/saas
```

## Configuracion de los ficheros .env

Hay dos fichero .env requeridos, uno en el directorio saas y otro dentro de clientes, se pueden copiar de los ficheros .env.example que se encuentran en los mismos directorios.

## Creación certificado SSL

Para la creación del certificado SSL se debe ejecutar el siguiente comando desde el directorio saas, se recomienda el uso de un usuario y no de root

```bash
docker-compose run --rm -f docker-compose.certbot.yml certbot
```
