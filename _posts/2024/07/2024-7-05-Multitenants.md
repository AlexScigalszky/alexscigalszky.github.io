---
layout: post
title: "Multitenants"
---

Es el término que se utilizan para aplicaciones con múltiples clientes<!--more-->. Existen diferentes enfoques:

# Diferentes Bases de datos
Tablas de la misma estructura. También se podría hacer por separación de schema

## Ventajas
- No hay que preocuparse de distinguir el dato de un cliente al otro.
.

## Desventajas
- Mantener varias bases de datos
- Varios servidores

## Decidir la BD

### Un sistema cliente para cada uno
Se crea un cliente particular para cada cliente que se conecta a la base de datos particular.
Notas:
- Los bugs deben resolverse en varios servers
- Es muy común que cada cliente tenga su propia version y que los hotfix deban implementar de forma incorrecta..
.

> Algunas empresas exigen que los datos se encuentren en algún lugar particular.

### Un Administrador de conexiones
Un mismo código pero existe un connection multiplexer el cual selecciona la base de datos para cada cliente.
Notas: 
- El código es fácil de mantener
- Hay que sincronizar las bases de datos
- No se pueden usar migraciones
- Normalmente se tiene una aplicación extra para administrar las bases de datos

# Diferentes Identificadores
Cada tabla tiene una columna que identifique el cliente.

## Ventajas
- Fácil de mantener (un sólo lugar).
- Se pueden ver los datos fácilmente y distinguirlos.

## Desventajas
- Hay que agregar esa columna en muuuchas tablas.
- No se pueden tener versiones particulares para cada cliente.
- Con clientes restrictivos para los datos, no se puede utilizar (requieren datos en cierta zona geográfica).