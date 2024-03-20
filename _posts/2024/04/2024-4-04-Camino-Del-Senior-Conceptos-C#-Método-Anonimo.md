---
layout: post
title: "Camino del Senior(.Net + Angular): Conceptos C#: Métodos Anónimos"
---

Métodos Anónimos son métodos que no tienen<!--more--> nombre, ya sea porque se pasan como parámetro a una función o se registran en una variable.
Los **delegates** están muy relacionados ya que se tratan de un puntero a una función que muchas veces es anónima (aunque no siempre es así)

# Ejemplos
Con delegate
```csharp
Func<int, int, int> suma = delegate(int x, int y) { return x + y; };
```
Sin delegate, utilizando expresiones lambda
```csharp
Func<int, int, int> suma = (x, y) => x + y;
```