---
layout: post
title: "Tutorial LINQ: Sum"
categories: ["senior"]
---

Devuelve la suma de todos los valores de <!--more-->una colleción usando el parámetro para seleccionar el criterio.

En este caso, obtiene la **suma** de horas de todas las materias.

```csharp
int totalHoursStuding = subjects.Sum(x => x.HoursCount);
```

> **Nota 1:** Siempre deben ser selecionadas propiedades del tipo **int**, **double**, **decimal**, **float**, **long**, y sus versiones nullables.

> **Nota 2:** Si la colección está vacía, devuelve **0 (cero)**.