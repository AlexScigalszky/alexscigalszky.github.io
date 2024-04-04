---
layout: post
title: "Tutorial LINQ: Expresiones Lamda"
categories: senior
---

Son parte del lenguaje C#.<!--more-->Una lambda es una función anónima que puede definirse en línea. 

```csharp
int? isAnyLargerThan100 = numbers.Any(x => x > 100);
```

el código `x => x > 100` corresponde a una expresión lambda.