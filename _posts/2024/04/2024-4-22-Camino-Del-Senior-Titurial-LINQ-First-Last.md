---
layout: post
title: "Tutorial LINQ: First y Last"
categories: senior, csharp, coding
---

Devuelve el primer y el último elemento <!--more-->de una colleción. O sea, el elemento en el indice **0 (cero)**.
También se puede pasar una condición para obtener el primer elemento que cumpla esa condición.

# First
En este caso, obtiene el primer usuario de la colección y el primer usuario mayor de edad.

```csharp
var firstUser = users.First();
var firstAdult = users.First(x => x.Age > 18);
```
> **Nota 1:** Si la colleción está vacía, disparará una excepción en tiempo de ejecución.

# Last
En este caso, obtiene el último usuario de la colección y el último usuario mayor de edad.

```csharp
var lastUser = users.Last();
var lastAdult = users.Last(x => x.Age > 18);
```
> **Nota 2:** Si la colleción está vacía, disparará una excepción en tiempo de ejecución.

# FirstAtDefault
En este caso, intenta obtene el primer usuario que cumpla la condición o null (default).

```csharp
User? firstUser = users.FirstAtDefault();
User? firstAdult = users.FirstAtDefault(x => x.Age > 18);
```

# LastAtDefault
En este caso, intenta obtene el último usuario que cumpla la condición o null (default).

```csharp
User? lastUser = users.LastAtDefault();
User? lastAdult = users.LastAtDefault(x => x.Age > 18);
```