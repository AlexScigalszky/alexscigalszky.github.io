---
layout: post
title: "Antipatrones C#: Fechas en forma de string"
categories: senior
---

Reglas para utilizar las fechas <!--more-->.

* Usar ToString para fortear una fecha al estilo local.
* Los números de los meses empiezan con 0 (cero).
* Los días de semanas empiezan en Sunday (cero) hasta Sábado (seis).
* Usar DayOfWeek.