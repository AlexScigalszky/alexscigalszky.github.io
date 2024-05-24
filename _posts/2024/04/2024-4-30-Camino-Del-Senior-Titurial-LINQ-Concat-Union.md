---
layout: post
title: "Tutorial LINQ: Concat y Union"
categories: [senior, csharp, coding
---

Combina dos colecciones del<!--more--> mismo tipo.

# Concat
Concatena dos colecciones del mismo tipo.

```csharp
var numbers1 = new int[] { 1,1,2 };
var numbers2 = new int[] { 1,5,3 };
var newNumbers = numbers1.Append(numbers2);// [1,1,2,1,5,3]
```

# Union
Concatena dos colecciones del mismo tipo y remueve **duplicados**.

```csharp
var numbers1 = new int[] { 1,1,2 };
var numbers2 = new int[] { 1,5,3 };
var newNumbers = numbers1.Union(numbers2);// [1,2,5,3]
```

> **Nota 1:** También admiten un segundo parámetro **comparer** para comparar si los objetos son iguales