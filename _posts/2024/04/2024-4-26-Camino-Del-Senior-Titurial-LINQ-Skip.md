---
layout: post
title: "Camino del Senior(.Net + Angular): Tutorial LINQ: Skip"
categories: senior
---

Saltea los primeros elementos de <!--more-->una de una colección y devuelve el resto.

# Skip
En este caso, devuelve los usuarios desde la posición 10 hasta el final.

```csharp
var adults = users.Skip(10);
```
> **Nota 1:** Si la colección es mas chica del valor dado, devuelve una colección vacía.

# SkipLast
En este caso, devuelve todos los usuarios menos los últimos 10 usuarios.

```csharp
var adults = users.SkipLast(10);
```

# SkipWhile
Salteará todos los elementos mientras que la condición se cumpla y luego retorna el resto.
En este caso, saltea los primeros usuarios menores de edad.

```csharp
var minors = users.SkipWhile(x => x.Age < 18);
```
> **Nota 2:** `SkipWhile` es muy útil para largas colecciones ordenadas (el método `While` chequea todos los elementos). Hay que pensar en colecciones de 2 millones de items.