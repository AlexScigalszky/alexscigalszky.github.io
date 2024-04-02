---
layout: post
title: "Camino del Senior(.Net + Angular): Tutorial LINQ: Aggregate"
categories: senior
---

Permite realizar una operación sobre cada <!--more-->elemento y obtener un valor resultante (de cualquier tipo). Recibe una función de 2 parámetros: `accumulator` que tiene el resultado temporal de la operación y el segundo el `current` que es el elemento actual en la iteración.

En este caso, calcula la suma de todos los valores de la colección.
```csharp
var numbers = [1,2,3,4,5];
var sum = numbers.Aggreate((acc, el) => sum + el); // 15
```

> **Nota 1:** el resultado de la función parámetro se asignará en la variable `accumulator` para el siguiente elemento.

> **Nota 2:** tiene un parámetro para definir el valor **inicial** del `accumulator`

En este caso, devuelve la palabra más larga de un string


```csharp
var text = "un texto con palabras que pueden ser largas o cortas";
var longestWord = text.Split(" ")
    .Aggregate(
        // valor inicial
        "",
        // función para calcular la palabra más larga
        (longestWordSoFar, word) => word.Length > longestWordSoFar.Length ? word : longestWordSoFar 
    );
```
.
> **Nota 3:** es la función equivalente al `reduce` de javascript