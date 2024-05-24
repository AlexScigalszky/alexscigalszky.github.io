---
layout: post
title: "AZ-900 Curso de Azure: Compute"
categories: senior, cloud
---

Corresponse a todos los servicios que involucran computación en su uso<!--more-->:

# Virtual Machines (VM)

Es una computadora o server exclusiva. Puede correr en un hardware compartido. Se tiene completo control de lo que tiene instalado.
Existen muchas herramientas para manejar VMs.
Existen templates para crearlos con ciertas herramientas.
Se puede configurar la RAM, CPUs, Disco, etc. Azure maneja el hardward.

## Precio

Se calcula por hora y por cantidad de CPU y RAM se use.

## Casos de uso

### Pros

Se necesita total control
se necesita instalar una aplicación particular
Para infraestructuras ya existentes y se están migrando.

### Contras

No es para todo, a veces sirve pero otras veces no lo vale.
Mantener una VM es mucho más dificil que otros recursos.

# Scale Set

Es un servicio que permite crear grupos de máquinas virtuales idénticas balanceadas (con un load balancer).
Cuando una máquina virtual se encuentra en el límite de sus capacidades, azure toma automáticamente una nueva máquina virtual del Scale Set para distribuir la carga.

## Beneficios

Fácil de manejar muchas máquinas virtual (son todas iguales).
Alta disponibilidad del servicio.
Auto escalado (agrega o quita VM automáticamente)
Grandes escalas (hasta 1000 máquinas virtuales en un sólo set)
Sin costo extra.

# App Service

Servicio que permite manejar completamente toda la plataforma y enfocarse directamente en el negocio. Soportan muchos lenguajes.
Hay 3 tipos:

## Web Apps

Típicas aplicaciones online. Pueden correr en linux o windows. Se integran fácilmente para los deploys. Tienen autoescalado y balanceo de carga.

## Web App for Containers

Applicaciones online en contenedores.

## API App

forma eficiente para exponer una API del backend. Sin interfaz.

# Azure Container Instances (ACI)

Permite ejecutar contenedores sin preocuparse de las máquinas virtuales que lo corren. Se pueden crear bajo demanda desde el portal, cli o powershell. Últil para cosas rápidas, pruebas, trabajos tipo bulk y aplicaciones de microservicios.

# Azure Kubernetes Service (K8s)

Orquestador de contenedores open source. Para automatizar el deploy, el escalado y manejo de aplicaciones sobre containers.
Revisa la carga de los contenedores para autoescalarlos.
Duplica la arquitectura de contenedores lo que hace que la puesta en marcha sea mucho más agil, rápida y simple.
No hay que preocuparse de la infraestructura y accesos, etc ya que tiene incluido los servicios estándar de azure. Tiene alcance global para todas las regiones.

## Azure Container Registry (ACR)

Registro de las imagenes, archivos y paquetes para los contenedores. Provee imagenes de contenedores para ACI y AKS. Usa azure identity y sus sistemas de seguridad.

## AKS Cluster

Conjunto de máquinas tienen nodos que ejecutan aplicaciones contenerizadas manejadas por K8s

## Pod

Grupo de uno o más contenedores que comparten almacenamiento, red y especificaciones de cómo ejecutar el contenendor. Una aplicación y sus órdenes viven en un Pod. Cuando la carga es muy grande para un Pod, Kubernetes crea un Pod nuevo para balancear la carga.

# Windows Virutal Desktop

Crea máquinas virtuales con Windows accesibles desde la red. Previo uso del sistema de seguridad de Azure. Ideal para brindar acceso a los empleados de forma rápida. Se ejecuta 100% en la nube.

## Beneficios

- Reusar licencias.
- Muchos usuarios pueden usar la misma instancia a la vez.
- Acceso desde cualquier dispositivo.
- Información segura.
  .

# Functions

Permite ejecutar código sin preocuparse por la plataforma, máquina, procesos y nada relacionado. Es una simple función que hay que ejecutarse. Se ejecuta una vez (a partir de un evento) y se detiene totalmente. Puede comunicarse con otras funciones.

## Beneficiones

- Si no hay tráfico entonces se no se ejecuta, no hay costo extra.
- Si una función falla, no afecta el funcionamiento de las demás.
- Muy adaptable para sistemas de gran caudal no predecible.
