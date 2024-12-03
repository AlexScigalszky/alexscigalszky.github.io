---
layout: post
title: "Cómo migrar un monolito a microservicios"
categories: devops, coding
---

A tener en cuenta durante la migración<!--more-->.

## Cuando un código está duplicado

Cuando hay código que es igual:

- se mueve para una librería compartida.
- se abstrae la funcionalidad en común para que, al modificarlo se actualice todos los microservicios (por ejemplo startup, logs, conexiones a base de datos).

## Miración de forma gradual

Se puede dejar el monolito sin modificar y nuevas funcionalidades con microservicios. También se puede usar un load-balancer y feature-flags para habilitar las faeturas de un lado al otro. Una vez estabilizado en microservicios, se elimina el código del monolito.

