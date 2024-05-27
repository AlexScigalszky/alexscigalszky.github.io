---
layout: post
title: "Entity Frameword Core: Consultas"
categories: senior, csharp, coding
---

Para realizar consultas a la base de datos <!--more-->existen varias formas.

# Crear un contexto

Primero que todo, se debe crear un contexto, eso se puede hacer con Dependecy Injectio o directamente dentro de un bloque using (para asegurar la correcta limpieza de memoria y recursos)

```csharp
using(var context = new ApplicationDbContext() {
    // consultas a la base de datos
}
```

# Confirmar creación-migraciones

Se puede chequear si la base de datos fué creada y si existen migraciones que ejecutar.

```csharp
using(var context = new ApplicationDbContext() {
    // para asegurarse que la base de datos fué creada
    context.Database.EnsureCreated();
    // para chequear que no existen migraciones pendientes
    if (context.Database.GetPendingMigrations().Count() > 0)
         context.Database.Migrate();
}
```

# Consultas

## Listar todos los registros

```csharp
using var context = new ApplicationDbContext();
var result = context.Books.ToList();
```

## Crear un registro

```csharp
using var context = new ApplicationDbContext();
context.Books.Add(new Book() { Name = "El principito" });
context.SaveChanges();
```

## Listar un registro

```csharp
using var context = new ApplicationDbContext();
var result = context.Books.First(); // dispara una excepción en caso de no encontrar nada
var result = context.Books.FirstOrDefault(); // devuelve null si no lo encuentra
var result = context.Books.First(12); // busca por la clave primaria de la tabla
var result = context.Books.Single(); // dispara una excepción en caso de no encontrar nada o existen más de un elemento
var result = context.Books.SingleOrDefault(); // devuelve null si no lo encuentra o existen más de un elemento
```

## Filtrar

```csharp
using var context = new ApplicationDbContext();
var result = context.Books.Where(x => x.Id == 123).FirstOrDefault();
```

Se puede agregar una condición que siempre será agregada a cualquier insulta sobre una tabla. Por ejemplo, cuando queremos hacer un soft delete

```csharp
protected override void OnModelCreating(Model builder model builder) {
...
  modelBuilder.HasQueryFilter(a => !a.IsDeleted);

...
}
```

## Actualizar

```csharp
using var context = new ApplicationDbContext();
var books = context.Books.Where(x => x.Name.Contains("A")).ToList();
foreach(var book in books)
    book.Name = book.Name.Replace("A", "a");
context.SaveChanges();
```

## Eliminar

```csharp
using var context = new ApplicationDbContext();
var book = context.Books.First(12);
var result = context.Books.Delete(book);
context.SaveChanges();
```

# Log SQL

Para ver el código **sql** de una consulta

```csharp
public class ApplicationDbContext : DbContext {

    protected override void OnConfiguring(DbContextOptionBuilder options) {
        options.UserSqlServer("Server=./SqlServer;Database=BookStore;TrustServerCertificate=True;Trusted_Connection=True")
            .LogTo(Console.WriteLine, new []{ DbLoggerCategory.Database.Command.Name }, LogLevel.Information);
    }
}
```

# Async

Muchos métodos tienen su versión Async que permiten trabajar asincrónicamente.

# Ejecución diferida

Sólo se ejecuta la query a la base de datos cuando se necesitan los datos.
Por ejemplo:

- foreach
- ToList
- ToArray
- ToDictionary
- First
- FirstOrDefault
- Single
- SingleOrDefault

# Larga de datos relacionados

## Carga Explicita

Relacionando datos en consultas separadas.

## Carga Eager

Carga bajo demanda utilizando el método `.Include(x => x.Authors)` y `.IncludeThen(x => x.Addresses)` para cargar la tabla relacionada.

## Carga Lazy

Carga diferida utilizando los propiedades de navegación (referencias entre objetos). Por ej:`book.Authors.First().Name`.
