---
layout: post
title: "Entity Frameword Core: Relaciones"
categories: senior
---

Existen diferentes formas de relacionar las tablas/clases<!--more--> en Entity Framework Core.

# One To One

Para definir una relación entre dos tablas dónde cada registro de una, corresponde otro registro en la otra.

```csharp
public class Book {
    public int Id {get; set;}

    [ForeignKey("Detail")]
    public int BookDetailId { get; set; }
    public BookDetail Detail { get; set; }
}
public class BookDetail {
    public int Id {get; set;}

    public Book Book { get; set; }
}
```

# One To Many

Para definir una relación entre dos tablas dónde cada registro de una, corresponde a varios de la otra.

```csharp
public class Book {
    public int Id {get; set;}

    public IEnumerable<Publisher> Publishers { get; set; }
}
public class Publisher {
    public int Id { get; set; }

    [ForeignKey("Book")]
    public int BookId { get; set; }
    public Book Book { get; set; }
}
```

# Many To Many (sin Mapping Table)

Para definir una relación entre dos tablas dónde muchos registros de una pueden tener varios en la otra sin crear una tabla explísitamente.

```csharp
public class Book {
    public int Id {get; set;}

    public IEnumerable<Author> Authors { get; set; }
}
public class Author {
    public int Id { get; set; }

    public IEnumerable<Book> Books { get; set; }
}
```

Esta configuración creará una tabla llamada `AuthorBook` con el BookBookId y AuthorAuthorId. Existe un problema, no existe control de la tabla creada (por ejemplo si queremos agregar una nueva columna).

# Many To Many (con Mapping Table)

Para definir una relación entre dos tablas dónde muchos registros de una pueden tener varios en la otra definiendo la tabla de mapping.

```csharp
public class Book {
    public int Id {get; set;}

    public IEnumerable<AuthorBook> AuthorBooks { get; set; }
}
public class AuthorBook {
    public int Id { get; set; }

    [ForeignKey("Book")]
    public int BookId { get; set; }
    public Book Book { get; set; }

    [ForeignKey("Author")]
    public int AuthorId { get; set; }
    public Author Author { get; set; }
}
public class Author {
    public int Id { get; set; }

    public IEnumerable<AuthorBook> AuthorBooks { get; set; }
}
```

> **Nota 1:** Tener en cuenta el Referencial Action y sus variantes (qué ocurre en caso de delete)

> **Nota 2:** Los IDs son del tipo `int` a modo de ejemplo, pero se debe considerar cada situación
