---
layout: post
title: "Tutorial LINQ: Chunk"
categories: senior
---

Permite dividir una colección en <!--more-->colecciones del mismo tamaño

En este caso crea una colección de collecciones de tamañano 3, El último puede ser de mejor longitud.
```csharp
List<int> numbers = new List<int> { 1, 2, 3, 4, 5 };
var chunks = numbers.Chunk(2);// [[1,2,3], [4,5]]
```