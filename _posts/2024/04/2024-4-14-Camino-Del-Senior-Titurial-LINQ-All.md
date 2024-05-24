---
layout: post
title: "Tutorial LINQ: All"
categories: ["senior", "csharp", "coding"]
---
Se utiliza para chequear una condición en una <!--more-->colleción en todos los elementos. Devuelve un booleano.
En este caso si **todos** los númerosson mayores a 100.

```csharp
bool areAllLargerThan100 = numbers.All(x => x > 100);
```