---
layout: post
title: "Tutorial LINQ: Grupos"
categories: senior, csharp, coding
---

Permite agrupar los elemento a partir<!--more--> de un criterio.

Agrupa usuario según el estado en que se encuentren (PE: activos, inactivos, borrados)

```csharp
var listOfStates = users.GroupBy(
    x => x.State, //para elegir la clave que los distinguirá
    x => x //para elegir el elemento
    ); // lista de lista de usuarios
```
