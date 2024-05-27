---
layout: post
title: "Entity Frameword Core: Data Annotations"
categories: senior, csharp, coding
---

Para definir las propiedades de columnas o tablas en las clases se<!--more--> pueden usan los **Data Annotations**.

# Table

Para definir el nombre de una tabla.

```csharp
[Table("tb_book")]
public class Book {
    // properties
}
```

# Column

Para definir el nombre de una columna.

```csharp
public class Book {
    // properties
    [Column("cl_name")]
    public string Name { get; set; }

}
```

# Required

Para definir que una columna es requerida y si o sí debe completarse al momento de agregar o modificar registros en esa tabla.

```csharp
public class Book {
    // properties
    [Required]
    public string Name { get; set; }

}
```

# MaxLength

Para definir la longitud máxima de una propiedad del tipo string

```csharp
public class Book {
    // properties
    [MaxLength(50)]
    public string Name { get; set; }

}
```

# NotMapped

Para definir una propiedad que no va a ser mapeada a una columna en la tabla. Sólo tendrá la aplicación C# como alcance y no llegará a la base de datos

```csharp
public class Book {
    // properties
    [NotMapped(50)]
    public string Name { get; set; }

}
```
