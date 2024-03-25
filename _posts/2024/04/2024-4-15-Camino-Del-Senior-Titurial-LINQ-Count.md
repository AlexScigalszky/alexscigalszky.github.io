---
layout: post
title: "Camino del Senior(.Net + Angular): Tutorial LINQ: Count"
---
Se utiliza para contar dentro de una colleción basandose en una condición <!--more--> data. Devuelve un booleano.
En este caso, cuenta **cuántos** de los números son mayores a 100.

```csharp
bool countOfLargerThan100 = numbers.Count(x => x > 100);
```