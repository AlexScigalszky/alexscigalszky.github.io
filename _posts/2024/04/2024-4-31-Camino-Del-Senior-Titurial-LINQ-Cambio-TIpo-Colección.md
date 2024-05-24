---
layout: post
title: "Tutorial LINQ: Cambio de tipo de colección"
categories: [senior, csharp, coding
---

Existe toda una familia de métodos que <!--more-->pueden usarse para cambiar el tipo de colección.


# ToArray
Cambia de un `IEnumerable<T>` al tipo `T[]`

# ToList
Cambia de un `IEnumerable<T>` al tipo `List<T>`

# ToHashSet
Cambia de un `IEnumerable<T>` al tipo `HashSet<T>` dónde todos los elementos son únicos. Elimina duplicados.

# ToDictionary
Cambia de un `IEnumerable<T>` al tipo `Dictionary<Tkey, T>`. Se debe especificar un selector para identificar la key.

```csharp
var usersDictionary = users.ToDictionary(
    x => x.ID, // la clave será el ID del usuario
    x => x // el valor es el usuario mismo
); // diccionario de id, usuario
```

> **Nota 1:** Se puede evitar usar el selector para el valor. Esto utilizará el elemento como valor.
> **Nota 2:** Si el selector de clave devuelve dos valores iguales, disparará una exceptión en tiempo de ejecución.

# ToLookup
Permite obtener un diccionario pero con multiples valores para una clave.
Cambia de un `IEnumerable<T>` al tipo `ILookup<Tkey, T>`. Se debe especificar un selector para identificar la key y otro para los valores.

```csharp
var usersDictionary = users.ToLookup(
    x => x.Age, // la clave será el ID del usuario
    x => x // el valor es el usuario mismo
); // diccionario de edad, usuarios
```
> **Nota 3:** Se puede evitar usar el selector para el valor. Esto utilizará el elemento como valor.

# AsEnumerable
Cambia de un `IEnumerable<T>` al tipo `IEnumerable<T>`.
Por ejemplo, cuando se tiene una implementación de una lista muy particular que no permita filtrados, pero permite convertirse a un enumerable que sí lo hace

```csharp
var specificList = new ListWithoutWhereCondition<User>();
var userFiltered = specificList.Where(x => x.Age > 20); // dispara una excepción
var userFiltered = specificList.AsEnumerable().Where(x => x.Age > 20); // retorna una colleción
```

# Cast
Cambia de un `IEnumerable<T>` al tipo `IEnumerable<R>`.
Permite cast cada elemento de la colección y devolver una nueva,

```csharp
var decimals = new decimal[]{1.3,2.1,3.9};
var integers = decimals.Cast<int>(); // colección de ints (los números redondeados)
```