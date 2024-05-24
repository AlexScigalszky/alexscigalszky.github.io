---
layout: post
title: "Tutorial LINQ: Single"
categories: ["senior"]
---

Devuelve el único elemento que cumple la<!--more--> condición dada de una colección. Si existe más de un elemento, entonces dispara una excepción

# Single
En este caso, obtiene el **único** usuario de la colección mayor de edad.

```csharp
var users = new List<User> {new { Age = 10 }, new { Age = 19 }new { Age = 10 }, new { Age = 11 }}
var adult = users.First(x => x.Age > 18);
var adult = users.First(x => x.Age > 10);// ERROR
```

> **Nota 1:** Si la colección está vacía, disparará una excepción en tiempo de ejecución.

> **Nota 2:** Si la colección tiene un sólo elemento se puede llamar al método Single sin parámetros. Es una forma de convertir una colección a un elemento.

# SingleOrDefault
En este caso, intenta obtener el último usuario que cumpla la condición, haya más de un elemento que cumple la condición o no exista elemento que cumpla. En este caso devuelve el valor default

```csharp
var users = new List<User> {new { Age = 10 }, new { Age = 19 }new { Age = 10 }, new { Age = 11 }}
User firstAdult = users.SingleOrDefault(x => x.Age > 18);
User firstAdult = users.SingleOrDefault(x => x.Age > 10);// null
```
