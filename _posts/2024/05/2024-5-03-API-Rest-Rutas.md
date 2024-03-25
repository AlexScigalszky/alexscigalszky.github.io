---
layout: post
title: "API Rest: Rutas"
---
Convensión de los endpoints es que sean en **plural** que representen recursos. Separara las palabras con guión medio `-` y letras en **minúscula**.

Por ejemplo:

```csharp
GET /products
GET /products/{id}
```