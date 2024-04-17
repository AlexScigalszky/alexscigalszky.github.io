---
layout: post
title: "Normalización de una base de datos"
---

Una base de datos sana corresponde a aquella que está <!--more-->normalizada.

# ¿Por qué normalizar?

- Evitar la redundancia de los datos.
- Disminuir problemas de actualización de los datos en las tablas.
- Proteger la integridad de los datos.
- Facilitar el acceso e interpretación de los datos.
- Reducir el tiempo y complejidad de revisión de las bases de datos.
- Optimizar el espacio de almacenamiento.
- Prevenir borrados indeseados de datos.

# Niveles

## 1FN

1. Eliminar los grupos repetitivos de la tablas individuales.
2. Crear una tabla separada por cada grupo de datos relacionados.
3. Identificar cada grupo de datos relacionados con una clave primaria.

## 2FN

1. Tener la 1° forma normal.
2. Crear tablas separadas para aquellos grupos de datos que se aplican a varios registros.
3. Relacionar estas tablas mediante una clave externa.

## 3FN

1. Tener la 2° forma normal.
2. Eliminar aquellos campos que no dependan de la clave.
3. Ninguna columna puede depender de una columna que no tenga una clave.
4. No puede haber datos derivados.
