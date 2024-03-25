---
layout: post
title: "Camino del Senior(.Net + Angular): Tutorial LINQ: Take"
---

Retorna una cantidad de elementos iniciales <!--more-->de una colección.

# Take
En este caso, devuelve los primeros 10 usuarios.

```csharp
var adults = users.Take(10);
```
> **Nota 1:** Si la colección es mas chica del valor dado, devuelve una colección igual.

# TakeLast
En este caso, devuelve los últimos 10 usuarios.

```csharp
var adults = users.TakeLast(10);
```

# TakeWhile
Tomará todos los elementos mientras que la condición se cumpla
En este caso, devuelve los primeros usuarios menores de edad.

```csharp
var minors = users.TakeWhile(x => x.Age < 18);
```
> **Nota 2:** `TakeWhile` es muy útil para largas colecciones ordenadas (el método `While` chequea todos los elementos). Hay que pensar en colecciones de 2 millones de items.