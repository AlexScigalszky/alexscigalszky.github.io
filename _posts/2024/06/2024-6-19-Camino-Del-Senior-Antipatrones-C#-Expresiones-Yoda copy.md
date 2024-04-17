---
layout: post
title: "Antipatrones C#: Expresiones Yoda"
categories: senior
---

Las expresiones Yoda son<!--more--> aquellas donde los valores se escriben de otra manera.
Por ejemplo:

```csharp
if (200 == GetHttpResponse()){
    ...
}
```

O

```csharp
if (GetHttpResponse().Equals(200)){
    ...
}
```

Se usaba para evitar asignaciones por error (usar `=` en vez de `==`).
