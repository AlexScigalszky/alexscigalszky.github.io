---
layout: post
title: "Tutorial LINQ: deferer execution con LINQ"
categories: [senior, csharp, coding
---

**deferer execution** significa que no se evalúa una expresión hasta <!--more-->necesitarse. Esto ayuda a la permormance del código evitando ejecuciones no necesarias

```csharp
var words = allWords.Where(x => x.Lenght < 3);// la expresión lamda no se ejecuta

foreach (var word in words){// se ejecuta aquí
    Console.WriteLine(word);
}

allWords.Add("ahí");

foreach (var word in words){// se ejecuta aquí también
    Console.WriteLine(word);
}
```

En este caso, se modificó la colleción inicial y la expresión lamda se ejecutó nuevamente con la colleción modificada.

Los métodos `ToList()`, `ToArray()`, `ToDictionary()`, etc fuerza la ejecución de la expresión lamda