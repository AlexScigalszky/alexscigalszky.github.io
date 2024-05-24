---
layout: post
title: "Tutorial LINQ: Distinct"
categories: ["senior"]
---

Remueve todos los elementos duplicados <!--more-->de una colección. La función resultante tiene todos elementos únicos

# Distinct
En este caso, devuelve números no duplicados.

```csharp
var numbers = new int[] { 1,1,2,1,5,3 };
var unisquesNumbers = numbers.Distinct();// [1,2,5,3]
```
> **NOTA 1:** tener en cuenta que utiliza el segundo parámetro `comparer`. Si ese parámetro no existe utiliza la comparación por referencia.