---
layout: post
title: "Camino del Senior(.Net + Angular): Tutorial LINQ: MinMax"
categories: senior
---

Devuelve el menor o mayor valor de <!--more-->una colleción usando el parámetro para seleccionar el criterio.

# Max
En este caso, obtiene la edad del usuario con **mayor** edad

```csharp
int oldestAge = users.Max(x => x.Age);
```

# MaxBy
En este caso, obtiene el usuario con **mayor** edad

```csharp
int oldestUser = users.MaxBy(x => x.Age);
```

# Min
En este caso, obtiene la edad del usuario con **menor** edad

```csharp
int youngestAge = users.Min(x => x.Age);
```

# MinBy
En este caso, obtiene el usuario con **menor** edad

```csharp
int youngestUser = users.MinBy(x => x.Age);
```

# Sin parámetros
Se puede usar sin el selector pero la clase debe implementar la interfaz `IComparable<>`

```csharp
class User : IComparable<User> {
    public override int CompareTo(User other){
        return Age.CompareTo(other.Age); // compara por edad
    }
}
int oldestAge = users.Max();
int youngestAge = users.Max();
```

> **Nota 1:** Si la colección está vacía, disparará una excepción en tiempo de ejecución.