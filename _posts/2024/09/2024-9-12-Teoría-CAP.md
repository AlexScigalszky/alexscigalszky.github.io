---
layout: post
title: "Teoría CAP"
categories: database, distributed
---

**CAP** es una teoría para sistemas distribuídos que significa:<!--more-->

|     |                     |
| :-- | :------------------ |
| C   | Consistency         |
| A   | Availability        |
| P   | Partition Tolerance |

# ¿Qué es?

Esta teoría dice que cualquier **sistema distribuído** sólo puede garantizar con dos de esos items al mismo tiempo. También se aplica a bases de datos distribuídas.

# Items

## Consistency

si tenemos dos bases de datos con los datos de una cuenta, se actualiza uno con un descuento, si inmediatamente se consulta a la segunda base de datos tendrá ese valor descontado.

## Availability

Un servidor no puede rechazar una petición.

## Partition Tolerance

Si la conexión entre dos servidor se interrumpe, los servidores tienen que seguir operando sin problemas.

# Teoría

En la práctica, los sistemas distribuidos suelen elegir entre dos de estos principios, sacrificando el tercero. Por ejemplo:

- **CA (Consistency y Availability)**: Sistemas que priorizan la consistencia y disponibilidad, pero no toleran particiones. Esto es común en entornos donde la red es confiable y las particiones son raras.
- **CP (Consistency y Partition Tolerance)**: Sistemas que garantizan consistencia y tolerancia a particiones, pero pueden sacrificar la disponibilidad durante fallos de red.
- **AP (Availability y Partition Tolerance)**: Sistemas que priorizan la disponibilidad y tolerancia a particiones, pero no garantizan consistencia inmediata.
