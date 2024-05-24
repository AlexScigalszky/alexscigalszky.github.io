---
layout: post
title: "Tutorial LINQ: Nuevas colleciones"
categories: ["senior", "csharp", "coding"]
---

Existen varios métodos para generar colecciones<!--more-->.

# Empty

Para crear una colección vacía. En este caso una colección vacía de numeros

```csharp
var empty = Enumerable.Empty<int>(); // colección vacía
```

# Repeat

Para crear una colección de un tamaño dado y con el valor duplicado en cada posición. En este caso una colección de 100 elementos 10

```csharp
var tens = Enumerable.Repeat(10,100); // 100 veces 10
```

# Range

Para crear una colección a partir de un rango de valores dado. El primer parámetro es el valor inicial, el segundo es la cantidad de items.

```csharp
var tens = Enumerable.Range(10,5); // [11,12,13,14,15]
```

# DefaultIfEmpty

Devuelve una colección con al menos un elemento. Si está vacía crea un elemento del tipo `default()` sino devuelve una copia de la colleción original.

```csharp
var ints = new int[0]; // colección vacía
var tens = Enumerable.DefaultIfEmpty(); // [0] cero es el default de int
```

> **Nota 1:** también puede recibir el valor por defecto como parámetro.
