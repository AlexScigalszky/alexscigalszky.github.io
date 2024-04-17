---
layout: post
title: "AZ-900 Curso de Azure: Networking"
categories: senior
---

El manejo de las redes en azure se realiza<!--more-->:

# Virtual Network (VNet)

Son redes privadas entre los servicios de Azure. Cada red tiene su propio espacio de red y cada servicio una IP propia dentro de la VNet. Cada virtual network se encuentra en una sola región y a una sóla subscripción. Se pueden aislar servicios utilizando las VNets. Todas las conecciones entre servicios se realizan dentro de la red virtual.

## Sub red

Se puede dividir el espacio de red de una red virtual se hace creando subredes, es la forma más común para separar recursos.

# Load Balancer

Sirve para balancear la carga entre varios servicios para alivar la carga y que cada uno tenga el mismo (o parecido) trabajo.
Redirige el tráfico a cada servicio acorde a ciertas reglas. Se puede utilizar para port fordwarding.

## Inbound Flows

Trafico desde internet

## Fronted

Punto de acceso al load balancer. Todo el tráfico llega a este punto.

## Backend Pool

Instancias disponibles para procesar una petición.

## Reglas

Reglas para decidir hacia donde redirigir

## Health Probes

Dice el estado actual de un servicio.

# VPN Gateway

Es una verión especial de VPN para comunicarse entre los servicios de azure y servicios externos que pasan por internet de forma segura (encriptado).
Un VPN Gateway es cada uno de los puntos que se conectan a una VPN de azure.

# Application Gateway

Se pueden aplicar custom reglas de redirección. Trabaja sobre el protocolo HTTP en vez de IP/Port

## Beneficios

- Se puede escalar
- Está encriptado end to end
- Redundancia en la zona
- Se puede usar el mismo Aplication gateway para más de 1000 aplicaciones.
- Funciona con casi todos los servicios de Azure
  .

# ExpressRoute

Se utiliza para tener conexiones muy muy rápidas. Son conexiones especiales entre centros de datos privados y Azure sin utilizar internet.

# Content Delivery Network (CDN)

Es una red distribuida de servidores que tienen copias de los datos que se pueden entregar datos a los clientes rápidamente (porque están distribuídos en todos lados del mundo). Se utiliza para minimizar la latencia.

## Beneficios

- Mejor performance
- Escalable
- Distribución de datos
  .
