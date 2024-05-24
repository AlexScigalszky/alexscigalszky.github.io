---
layout: post
title: "AZ-900 Curso de Azure: Could Concepts"
categories: ["senior"]
---

Los sistemas Could computing se distinguen entre<!--more-->:

- Compute
- Networking
- Storage
  Los conceptos claves de la nube son:

# Lenguage

## High availablity

Es el Core de could computing. No tiene hardward pero e puden crear server facilmente
Si el hardward falla, es automaticamente reemplazado.

## Reliability

(aka Faul Tolerance/Disaster recovery)
El sistema se recupera rápidamente de fallos y continua funcionando.
Se deploya en muchas ubicaciones.
Cada vez que una computado falla, otra la reemplaza.

## Scalability

Se pueden crear nuevos recursos (maquinas virtuales, memoria, etc) a medida que los actuales no son suficientes a la cantidad de peticiones actuales. Se agregan y quitan muy rapidamente.
Existe escalabilidad:

- Vertical (más memoria, cpu, ram, etc)
- Horizontal (más copias de la misma máquina virtual)

## Security

Control total de la seguridad, mantenimiento, control de red y más dentro del ambiente cloud.

## Predictability

# Costos

No existen sorpresas inesperadas en la factura
Azure permite seguir y mantener los costoa en tiempo real.
Azure provee analitica para identificar patrones/tendencias para optimizar el uso.

## Performance

Se puede predecir cuándo se requiren más o menos recursos.
Esto brinda la misma experiencia sin verse afectado por el tráfico.

## Governance

- Entornos estandarizados
- Auditorías de conformidad

## Managebility

Se trata de la Manejabilidad:

### De la nube

- Auto escalamiento
- Monitorización
- Deploys basados en templates

### En la nube

- Portal
- CLI
- APIs

# Economía / Costos

Términos

## Capital Expenditure (CapEx)

Dinero gastado en edificios, tierras o equipamento. Grandes inversiones.

## Operationa Expenditure (OpEx)

Costos por ejecutar un sistema, costos anuales.
Existen dos modelos:

### Precio por hora

Se paga por hora que se usa un recurso. Por ejemplo Azure Functions (pagas por ejecución, segundo y su combinación).

### Precio por consumo

Se paga por los recursos utilizados

# Modelos de Cloud Service

Existen 3 modelos:

## Infraestructure as a Service (IaaS)

Servidores que se crean y destruyen. No se ve el Hardware, se tiene servidores a disposición sin el trabajo por detrás.

## Platform as a Service (PaaS)

IaaS con la infraestructura agregadas (middlewares, manejadores de bases de datos, herramientos, etc).
Está hecho para soportar el ciclo de vida de un desarrolo completo (desarrollo, test, deploy, prod).
Evita problemas de licencias.

## Software as a Service (SaaS)

Es PaaS con aplicaciones ya hechas. No se debe mantener nada por detrás. Por ejemplo Office 365.
Un ejemplo extremos son las Azure Functions.

> **Nota 1:** A medida que se pasa de IaaS, PaaS, SaaS la responsabilidad de mantener las aplicaciones se van pasando a Microsoft.

# Marketplace

Es un store con herramientas/sistemas para comprar/utilizar en el portal. Se puede tomar como Solutions as a Service.
Se accede desde el Azure App Store, algunos son pagos otros gratuitos. Se pueden crear los propies. Son componentes listos para utilizarse.

# Modelos de Arquitecturas Cloud

Existen tres modelos:

## Privado

Los servicios pueden utilizarlo sólamente los usuarios de la cuenta. Control completo de la infraestructura. mejor seguridad y privacidad.
IT es responsable de mantenerlo

## Publico

Cualquier puede conectarse. Hay que controlar la privacidad y seguridad. No se paga por el hardware. Tiene menos costo mensualmente. Se tiene control de las versiones

## Hibrido

Es una mezcla de ambos. Sirve para tener sistemas con partes privadas y publicas. Es mucho más compleja de mantener.

> **Nota 2:** Hay que elegir la arquitectura con mucho cuidado porque no se puede cambiar
