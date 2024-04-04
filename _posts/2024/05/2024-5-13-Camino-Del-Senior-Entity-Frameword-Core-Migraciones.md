---
layout: post
title: "Entity Frameword Core: Migraciones"
categories: senior
---

Una vez creado el contexto y vinculado a la base de datos, se deben manejar los cambios de estructura (y datos) a travéz de migraciones<!--more-->. Para eso se utiliza la herramienta: Tools > Nuget Package Manager > Nuget Package Console.

# Generar migración
Esta herramienta buscará los cambios nuevos en las clases involucradas en **ApplicationDbContext** para después generar un archivo Migration.

Para ejecutarla, hay que seleccionar la consola en el proyect dónde está el ApplicationDbContext y luego ejecutar
```bash
add-migration AddBookToDb
```
Este comando creará una nueva carpeta llamada `Migrations` y un archivo llamado `202405131201_AddBookToDb.cs` con la información necesaria para crear las tablas y columnas necesarias en la base de datos.

# Aplicar Migración
Para eso, en la consola usar el comando:
```bash
update-database
```
Esto va a aplicar los cambios en la base de datos

> **Nota 1:** Primero hay que crear la base de datos.

# ¿Cuándo agregar una Migración?
Cuando:
* Se agrega una nueva clase/tabla
* Se agrega una nueva propiedad/columna
* Se modifica una propiedad/columna
* Se eiminan una nueva clase/tabla
* Se eiminan una propiedad/columna

> **Nota 2:** Siempre intentar cambios chicos para que las migraciones sean simples y fáciles de seguir

# Agregar data
Para agregar datos una única vez y poder mantenerla, se puede usar la funcion de **Seed Data**.
Se agregan los datos en el método `OnModelCreating`.
```csharp
public class ApplicationDbContext : DbContext {
    public DbSet<Book> Books { get; set; } // la clase Book corresponde a una tabla en la base de datos

    protected override void OnModelCreating(ModelBuilder builder) {
        
        var books = new Book[]{
            new Book() { Id = 1, /*al propierties */},
            new Book() { Id = 2, /*al propierties */}
        };
        builder.Entity<Book>().HasData(books)
    }
}
```
Estos datos y futuros cambios de esa información serán incluidos en las migraciones.