---
layout: post
title: "Camino del Senior(.Net + Angular): Tutorial LINQ: Join"
---

Cómo unir dos colecciones de diferentes tipos<!--more-->. 

# Join
Permite unir elementos entre dos colecciones. 
Si se tienen dos colecciones: una para usuarios con la propiedad (CityId) y otra para ciudades.
Se pueden unir los usuarios con los datos de las ciudades de la siguiente manera:
```csharp

var inBoth = users.Join(
    // segunda colección
    cities,
    // selector de la primer colección
    u => u.CityId,
    // selector de la segunda colección
    c => c.CityId,
    // función que une los valores. En este caso devuelve un string (puede ser otro objeto)
    (user, city) => $"{user.Name} - {city.Name}"
);
```

> **Nota 1:** un elemento existirá en la colección resultante sí y sólo sí existen datos en ambas colecciones.


# GroupJoin
Igual que Join pero devuelve una agrupación por cada elemento de la primer colección, habrá una lista de elementos de la segunda
Si se tienen dos colecciones: una para usuarios con la propiedad (CityId) y otra para ciudades.
Se pueden unir los usuarios con los datos de las ciudades de la siguiente manera:
```csharp

var inBoth = users.Join(
    // segunda colección
    cities,
    // selector de la primer colección
    u => u.CityId,
    // selector de la segunda colección
    c => c.CityId,
    // función que une los valores. En este caso devuelve un string (puede ser otro objeto)
    (user, city) => $"{user.Name} - {city.Name}"
);
```

> **Nota 2:** permite realizar un left join.
