---
layout: post
title: "Antipatrones C#: Tipo de antipatrón: Asumir lo Peor"
categories: senior
---

Cuando el desarrollador se encuentra **siempre** a la defensiva <!--more-->. Esto hace que se agregan chequeos completamente innecesarios.
Por ejemplo, muchos manejadores de excepciones anidados para proteger código simple, sobre-ingeniería en arquitecturas (preparar el proyecto para todos los escenarios posibles desde el inicio), bloqueo de recursos por mucho tiempo, etc.

> **Nota 1:** A veces está bien obtener algunas excepciones.