---
layout: post
title: "AZ-900 Curso de Azure: Azure Concepts"
categories: ["senior", "cloud"]
---

Los conceptos claves de azure son<!--more-->:

# Azure Portal

Es la página dónde se pueden acceder a las features de azure

## Personalización

Se puede acomodar el dashboard, workflos, colores, etc.

## Control de acceso

Se puede configurar el acceso a personas de la organzacion

## Manejo de costos

Seguimiento de costo actual y qué consume cada recurso de azure.

## On Stop Shop

Un sólo lugar para ver todas las cosas de Azure.

# Actualizaciones

Está constantemente actualizada.

## Multi-Plataforma

Se puede ver web, android y ios.

# Azure CLI

Es herramienta de la consola de comandos para realizar lo mismo que con el portal pero con comandos de textos. (crear maquinas virtuales).
Las ventajas son:

- Estable
- Structurado y siempre sigue el mismo patrón
- Cross platform
- Sirve para automatizar trabajos
- Puede servir para logear quién hace qué cosa
  .

# Azure PowerShell

Es una consola de comandos que sólo posee los comandos de Azure. Por ejemplo New-AzVm.

# Azure Cloud Shell

Es una consola accesible desde un browser para manejar recursos de azure.
Ventajas:

- Accesible y seguro
- Permite Bash o PowerShell
- Incluye herramientas de azure y permite Node, .Net y python
- Datos de session persistibles
- Tiene un editor de archivos

# Azure Mobile Shell

para trabajar desde cualquier lugar. Hay versiones en:

- iOS
- Android
  Usa AzureResourceManager para manejar los recursos de Azure.
  También tiene acceso a la terminal de Azure.

# ARM Template

Azure Resources Manager.
Los templateste ayudan a trabajar con los recursos más fácilmente:

- Describen lo que estás haciendo
- Tienen una sintaxis normalizada entre todos los templates.
- Son idempotentes.
  Se trata de un JSON descriptivo que tiene:
- $schema: describe las propiedades disponibles para ese template.
- contentVersion: version del template. Para indicar cambios.
- resources: Lista de recursos que se quieren manipular en el template.
- variables: se pueden usar variables que serán asignadas cuando se ejecute el template.

# Azure Advisor

Te da recomendaciones sobre un mejor manejo de los recursos. Ayuda a tener mejor seguridad.
