---
layout: post
title: "Camino del Senior(.Net + Angular): Entity Frameword Core: Fluent API"
categories: senior
---

Permite definir usando *código* (sin annotations) las <!--more-->relaciones entre las clases, propiedades y valores de la base de datos. A veces hasta tiene mayor alcance.

# Ubicación

Entity Framework permite codificar las configuraciones del contexto usando código dentro del método del contexto `OnModelCreating`.
```csharp
public class ApplicationDbContext : DbContext {
    
    protected override void OnModelCreating(ModelBuilder modelBuilder) {
        // configuración del contexto - Fluent API
    }
}
```

# Métodos Cómunes
Los métodos más comunes son:
```csharp
public class ApplicationDbContext : DbContext {
    
    protected override void OnModelCreating(ModelBuilder modelBuilder) {
        // para especificar el nombre de la tabla
        modelBuilder.Entity<Book>().ToTable("tb_book"); 

        // para especificar el nombre de la columna
        modelBuilder.Entity<Book>().Property(x => x.Name).HasCollumnName("cl_name");

        // para definir una propiedad requerida
        modelBuilder.Entity<Book>().Property(x => x.Name).IsRequired(); 

        // para definir la longitud máxima
        modelBuilder.Entity<Book>().Property(x => x.Title).HasMaxLenght(50); 

        // para definir la clave
        modelBuilder.Entity<Book>().HasKey(x => x.Id);

        // para no mapear la propiedad en la base de datos
        modelBuilder.Entity<Book>().Ignore(x => x.NotMapped);

        // para una relación One to One
        modelBuilder.Entity<BookDetail>()
            .HasOne(x => x.Detail)
            .WithOne(x => x.Book)
            .HasForeingKey<BookDetail>(x => x.BookId);

        // para una relación One To Many
        modelBuilder.Entity<Book>()
            .HasOne(x => x.Publishers)
            .WithMany(x => x.Book)
            .HasForeingKey(x => x.PublisherId);

        // para una relación Many To Many (sin Mapping Table)
        // nada para hacer, sólo las relaciones

        // para una relación Many To Many (con Mapping Table)
        modelBuilder.Entity<BookAuthor>()
            .HasOne(x => x.Book)
            .WithMany(x => x.BookAuthor)
            .HasForeingKey(x => x.BookId);

        modelBuilder.Entity<BookAuthor>()
            .HasOne(x => x.Author)
            .WithMany(x => x.BookAuthor)
            .HasForeingKey(x => x.AuthorId);
    }
}
```

# Prioridades
EntityFramework sigue una serie de prioridades para configurar un contexto (y crear migrations):
1. FluentAPI
2. Annotations
3. Reglas Internas

> **Nota 1:** Las  reglas internas siguen estándares como por ejemplo la propiedad "Id" corresponde a la clave de la clase.

# Separar en archivos

Se pueden separar las configuraciones en diferentes clases heredando de `IEntityTypeConfiguration<>`
```csharp
public class BookConfig : IEntityTypeConfiguration<Book> {
    
}
```


