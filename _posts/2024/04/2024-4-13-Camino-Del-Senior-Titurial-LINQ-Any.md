---
layout: post
title: "Tutorial LINQ: Any"
categories: ["senior"]
---

Se utiliza para chequear una condición en una <!--more-->colleción al menos una vez. Devuelve un booleano.
En este caso si existe **algún** número que sea mayor a 100

```csharp
bool isAnyLargerThan100 = numbers.Any(x => x > 100);
```