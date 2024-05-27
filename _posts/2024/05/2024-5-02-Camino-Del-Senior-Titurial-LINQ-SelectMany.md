---
layout: post
title: "Tutorial LINQ: SelectMany"
categories: senior, csharp, coding
---

Genera una colección a partir de las colecciones "hijas" de cada elemento<!--more-->. Es decir, crea una colección de **una** dimensión a partir de otra de **dos** dimensiones.

En este caso, devuelve los nietos.

```csharp
var grandchildrens = childrens.Select(x => x.childrens);// hijos de los hijos.
```
