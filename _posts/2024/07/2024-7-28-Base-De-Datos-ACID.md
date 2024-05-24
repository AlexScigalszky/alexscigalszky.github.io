---
layout: post
title: "Base de datos: ACID"
categories: ["db"]
---

Las bases de datos deben cumplir con las reglas ACID para<!--more--> garantizar su integridad.

- **A**tomic.
- **C**onsist.
- **I**solated.
- **D**urable.

## Atomic.

Los cambios se deben hacer atómicamente sin problemas de multithreads.

## Consist.

Los cambios deben hacerse desde un estado consistente hacia otro estado también consistente.

## Isolated.

Cada cambio (transacción) debe realizarse de forma separada de todas las demás.

## Durable.

Los cambios deben permanecer en el tiempo aún cuando el servidor se apague.
