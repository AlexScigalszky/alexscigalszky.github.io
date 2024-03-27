---
layout: post
title: "Camino del Senior(.Net + Angular): Tutorial LINQ: Any"
---

Se utiliza para chequear una condición en una <!--more-->colleción al menos una vez. Devuelve un booleano.
En este caso si existe **algún** número que sea mayor a 100

```csharp
bool isAnyLargerThan100 = numbers.Any(x => x > 100);
```