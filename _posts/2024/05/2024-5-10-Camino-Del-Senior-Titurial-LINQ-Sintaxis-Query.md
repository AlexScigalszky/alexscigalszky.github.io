---
layout: post
title: "Camino del Senior(.Net + Angular): Tutorial LINQ: Sintaxis Query"
categories: senior
---

SE una forma de escribir consultas expresivas y <!--more-->legibles sobre colecciones, usando palabras clave proporcionadas por LINQ (Language Integrated Query).

En este caso, los números mayores que 2:
```csharp
List<int> numbers = new List<int> { 1, 2, 3, 4, 5 };
var numbersGreaterThan2 = from num in numbers
                          where num > 2
                          select num;
```
> **Nota 1:** Las consultas complejas se hacen más legible de esta forma.