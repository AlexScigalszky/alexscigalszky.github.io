---
layout: post
title: "Entity Frameword Core: Vistas y Stored Procedures"
categories: senior
---

Se pueden utilizar **vistas** o **stored procedures** <!--more-->desde EntityFramework. Ambas consultas se ejecutan en el servidor de base de datos. 

# Vistas
Las vistas pueden ser mapeadas como tablas directamente en el contexto especificandolo con FluentAPI

```csharp
public class ApplicationDbContext : DbContext {
    
    protected override void OnModelCreating(ModelBuilder modelBuilder) {
        modelBuilder.Entity<BookView>().HasNoKey().ToView("GetBooksDetails");
    }
}
```
Para consultar esa vista se realiza de la misma manera que cualquier DbSet.
```csharp
using var context = new ApplicationDbContext();
// ejecuta la vista completa y devuelve todos los datos
var trackedEntities = context.BooksView.ToList();
// ejecuta la vista completa y devuelve todos los datos pero EF sólo toma el primero
var trackedEntities = context.BooksView.FirstOrDefault();
// ejecuta la vista completa y devuelve todos los datos pero EF filtra el resultado y toma el primero
var trackedEntities = context.BooksView.Where(x => x.Price > 2).FirstOrDefault();
```

> **Nota 1:** Entidades obtenidas con vistas, no serán trackeadas porque son sólo de lectura.

# Raw Queries
Se pueden ejecutar consultas directamente a la base de datos:
```csharp
using var context = new ApplicationDbContext();
var id = 1;
// ejecuta una consulta en el parámetro string directamente
var trackedEntities = context.FromSQLRaw("select Id from Books Where Id = " + id);
var trackedEntities = await context.FromSQLRawAsync("select Id from Books Where Id = " + id);

// ejecuta una consulta en el parámetro string directamente
var trackedEntities = context.FromSQLInterpolated("select Id from Books Where Id = {0}", id);
var trackedEntities = await context.FromSQLInterpolatedAsync("select Id from Books Where Id = {0}", id);
```

# Stored Procedures
```csharp
using var context = new ApplicationDbContext();

// ejecuta una consulta en el parámetro string directamente
var trackedEntities = context.FromSQLInterpolated("exec SP_Book_By_Id {0}", id);
var trackedEntities = await context.FromSQLInterpolatedAsync("exec SP_Book_By_Id {0}", id);
```

Cuando devuelven datos complejos requiren implementar una clase con propiedades con los mismo nombres que las columnas de la query para mapear los result sets.