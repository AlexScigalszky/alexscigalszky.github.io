---
layout: post
title: "Camino del Senior(.Net + Angular): Entity Frameword Core: Data Annotations"
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
Pra definir el nombre de una columna.
```csharp
public class Book {
    // properties
    [Column("cl_name")]
    public string Name { get; set; }

}
```