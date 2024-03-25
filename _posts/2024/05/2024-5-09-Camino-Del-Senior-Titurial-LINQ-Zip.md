---
layout: post
title: "Camino del Senior(.Net + Angular): Tutorial LINQ: Zip"
---

Aplica una función a cada elemento de dos colecciones<!--more--> a la vez para obtener un valor resultante (de cualquier tipo).


> **Nota 1:** si se omite la función `resultSelector` entonces devolverá una colecció de `Tuple<T, R>` con un elemento de cada colección.

En este caso, calcula la distancia entre cada uno de los puntos de un mapa. 
```csharp
var points = new []{
    new Point(10, 10),
    new Point(10, 11),
    new Point(11, 13),
    new Point(12, 14),
    new Point(14, 11),
}
var distances = points
    .Zip(points.Skip(1)) // uno cada punto con el siguiente (saltea el primero)
    .Select((first, second) => GetDisance(first, second));
```