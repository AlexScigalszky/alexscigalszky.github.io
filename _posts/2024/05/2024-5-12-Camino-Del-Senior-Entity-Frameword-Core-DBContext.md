---
layout: post
title: "Entity Frameword Core: DBContext"
categories: ["senior", "csharp", "coding"]
---

Para crer un contexto para la base de datos se <!--more--> debe heredar de la clase DbContext de EntityFrameworkCore.
y se aplica el connection string en em método `OnConfiguring`

```csharp
public class ApplicationDbContext : DbContext {
    public DbSet<Book> Books { get; set; } // la clase Book corresponde a una tabla en la base de datos

    protected override void OnConfiguring(DbContextOptionBuilder options) {
        options.UserSqlServer("Server=./SqlServer;Database=BookStore;TrustServerCertificate=True;Trusted_Connection=True");
    }
}
```

# Tables

Cada una de los DbSet deben tener una clave. Se puede hacer con **annotation**

```csharp
public class Book {

    [Key] // data annotation
    public int Id {get; set;}
    // otras propiedades
}
```
