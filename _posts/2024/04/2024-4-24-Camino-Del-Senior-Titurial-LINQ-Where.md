---
layout: post
title: "Tutorial LINQ: Where"
categories: senior, csharp, coding
---

Filtra una colección en base a un <!--more-->predicado.

# Where
En este caso, devuelve una colección dónde todos los usuarios son adultos.

```csharp
var adults = users.Where(x => x.Age > 18);
```

# Where (con indice)
En este caso, devuelve una colección dónde todos los usuarios son adultos que se encuentren en una posición par.

```csharp
var evenAdults = users.Where((x, index) => index % 2 == 0 && x.Age > 18);
```

> **Nota 1: Si ningún elemente cumple la condición, entonces devuelve una colección vacía