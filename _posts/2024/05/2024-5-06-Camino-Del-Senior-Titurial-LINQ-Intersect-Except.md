---
layout: post
title: "Tutorial LINQ: Intersect y Except"
categories: senior
---

Permiten buscar datos en común o diferente entre <!--more-->dos colecciones.

# Intersect

Crea una colección con los elementos que se encuentren en ambas colecciones

```csharp
var first = [1,2,3];
var second = [2,3,4,5];
var inBoth = first.Intersect(second); // [2,3]
```

# Except

Genera una nueva colección con los elementos que se encuentran en la primer colección pero no en la segunda.

```csharp
var first = [1,2,3];
var second = [2,3,4,5];
var inBoth = first.Intersect(second); // [1]
```

> **Nota 1:** Ambos métodos dependen de la definición de igualdad. Ver la implementación de `IEquatity<>`.
