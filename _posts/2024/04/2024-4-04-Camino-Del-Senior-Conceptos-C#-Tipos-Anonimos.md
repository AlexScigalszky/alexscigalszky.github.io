---
layout: post
title: "Conceptos C#: Tipos Anónimos"
categories: ["senior", "csharp", "coding"]
---

Son tipos de data que no tienen nombre y que sólo <!--more-->almacenan datos.

```csharp
var instance = new  {
    FirstName = "Jonh",
    LastName = "King",
    Age = 33
};
```

Son considerados __inmutables__. No se pueden modificar una vez creados.
```csharp
var instance = new  {
    FirstName = "Jonh",
    LastName = "King",
    Age = 33
};
instance.Age = 34 ! ERROR
```