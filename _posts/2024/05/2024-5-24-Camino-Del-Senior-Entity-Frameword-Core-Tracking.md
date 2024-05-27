---
layout: post
title: "Entity Frameword Core: Tracking vs No Tracking"
categories: senior, csharp, coding
---

Entity Framework nos deja decirle cuándo<!--more--> queremos trackear o cuándo no las entidades. Entity Framework trackea todos los objetos que obtiene y mantiene sus cambios para aplicarlos en la base de datos. A veces no queremos eso, por eso existen herramientas para poder controlar ese comportamiento.

# Tracking

Por defecto, todos los objetos son trackeado.

# AsNoTracking

El método `AsNoTracking()` permite evitar que los objetos resultante de la query sean trackeados.

```csharp
using var context = new ApplicationDbContext();
var trackedEntities = context.Books.AsNoTracking().ToList();
```

> **Nota 1:** Es muy útil para consultas de lectura unicamente.
