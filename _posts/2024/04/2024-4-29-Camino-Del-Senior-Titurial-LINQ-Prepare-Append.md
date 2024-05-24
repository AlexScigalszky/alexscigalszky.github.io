---
layout: post
title: "Tutorial LINQ: Prepare y Append"
categories: [senior, csharp, coding
---

Agregan un nuevo elemento a una colección<!--more-->. La colleción original no se modifica,
Remueve todos los elementos duplicados de una colección. La función resultante tiene todos elementos únicos

# Append
Crea una nueva colección con el nuevo elemento al **final**.

```csharp
var numbers = new int[] { 1,1,2,1,5,3 };
var newNumbers = numbers.Append(9);// [1,1,2,1,5,3,9]
```

# Prepend
Crea una nueva colección con el nuevo elemento al **inicio**.

```csharp
var numbers = new int[] { 1,1,2,1,5,3 };
var newNumbers = numbers.Prepend(9);// [9,1,1,2,1,5,3]
```