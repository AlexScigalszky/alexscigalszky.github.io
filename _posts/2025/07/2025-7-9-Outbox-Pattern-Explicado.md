---
title: "Outbox Pattern Explicado"
date: 2025-07-09
categories: [patterns, architecture]
---

# Outbox Pattern

El Outbox Pattern es un patrón de arquitectura de software utilizado para asegurar la comunicación confiable entre servicios, especialmente en sistemas distribuidos. Es comúnmente aplicado cuando se necesita garantizar que los cambios en la base de datos y el envío de mensajes (como eventos o notificaciones) ocurran juntos, incluso ante fallos.

## Problema

Cuando un servicio actualiza su base de datos y necesita notificar a otros servicios (por ejemplo, a través de un message broker), existe el riesgo de que la actualización en la base de datos sea exitosa pero el mensaje no se envíe, o viceversa. Esto puede llevar a inconsistencias de datos y mensajes perdidos.

## Solución

El Outbox Pattern resuelve esto introduciendo una tabla "outbox" en la misma base de datos donde se almacena la información principal. El proceso funciona así:

1. **Transacción:** Al actualizar los datos principales, el servicio también escribe un mensaje en la tabla outbox dentro de la misma transacción de base de datos.
2. **Polling:** Un proceso o thread separado consulta periódicamente la tabla outbox buscando nuevos mensajes.
3. **Publishing:** El proceso de polling lee los mensajes y los publica en el message broker o sistema externo.
4. **Cleanup:** Tras publicarse exitosamente, los mensajes se marcan como enviados o se eliminan de la tabla outbox.

## Beneficios

- **Atomicidad:** Asegura que los cambios de datos y el envío de mensajes sean atómicos (todo o nada).
- **Confiabilidad:** Previene la pérdida de mensajes y la inconsistencia de datos.
- **Simplicidad:** No requiere transacciones distribuidas.

## Ejemplo

Supón que tienes un sistema de e-commerce. Cuando se realiza una orden, quieres guardar la orden y notificar al servicio de envíos. Usando el Outbox Pattern:

- La orden y el mensaje de notificación se guardan juntos en una sola transacción.
- Un background worker lee la tabla outbox y envía la notificación al servicio de envíos.

## Desventajas

- Requiere infraestructura adicional para el polling y la limpieza de la tabla outbox.
- Hay una pequeña demora entre la actualización de la base de datos y la entrega del mensaje (debido al intervalo de polling).

## Conclusión

El Outbox Pattern es una solución robusta para la publicación confiable de eventos en sistemas distribuidos, especialmente cuando se requiere atomicidad entre operaciones de base de datos y el envío de mensajes.
