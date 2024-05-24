---
layout: post
title: "Estrategias de Change Detections"
categories: angular
---

Angular tiene dos estrategias para el Change Detection<!--more-->:

# Default

Actualiza la interfaz en cada ciclo de detección de cambios sin importar si los datos son diferentes o no.

# OnPush

Actualiza la interfaz si los datos de entrada cambian o si el componente recibe una nueva referencia.
Mejora el rendimiento.
