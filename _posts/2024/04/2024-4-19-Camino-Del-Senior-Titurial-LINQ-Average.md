---
layout: post
title: "Camino del Senior(.Net + Angular): Tutorial LINQ: Average"
---

Devuelve el valor promedio valor de <!--more-->una colleción usando el parámetro para seleccionar el criterio.

En este caso, obtiene la nota **promedio** de los estudiantes.

```csharp
int averageGrade = studends.Average(x => x.Grades);
```

> **Nota 1:** Siempre deben ser selecionadas propiedades del tipo **int**, **double**, **decimal**, **float**, **long**, y sus versiones nullables.

> **Nota 2:** Si la colección está vacía, disparará una excepción en tiempo de ejecución.