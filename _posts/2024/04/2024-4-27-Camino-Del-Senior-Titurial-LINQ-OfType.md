---
layout: post
title: "Camino del Senior(.Net + Angular): Tutorial LINQ: OfType"
---

Filtra los elementos que <!--more--> son de un tipo específico. La colección puede ser una combinación de muchos tipos de datos o clases.
La collección que devuelve está tipificada, devuelve todos los elementos del tipo definido.

# OfType
En este caso, devuelve sólos los elementos del tipo **User**.

```csharp
var adults = users.OfType<User>();
```
> **Nota 1:** Un ejemplo claro es cuando se tiene una colección de una interfaz pero querés sólo aquellos que son de cierta clase.