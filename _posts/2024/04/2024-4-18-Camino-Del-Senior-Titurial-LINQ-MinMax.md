---
layout: post
title: "Camino del Senior(.Net + Angular): Tutorial LINQ: MinMax"
---

Devuelve el menor o mayor valor de <!--more-->una colleción usando el parámetro para seleccionar el criterio.

# Max
En este caso, obtiene el usuario con **mayor** edad

```csharp
int oldest = users.Max(x => x.Age);
```

# Min
En este caso, obtiene el usuario con **menor** edad

```csharp
int youngest = users.Max(x => x.Age);
```

# Sin parámetros
Se puede usar sin el selector pero la clase debe implementar la interfaz `IComparable<>`

```csharp
class User : IComparable<User> {
    public override int CompareTo(User other){
        return Age.CompareTo(other.Age); // compara por edad
    }
}
int oldest = users.Max();
int youngest = users.Max();
```

> **Nota 1:** Si la colección está vacía, disparará una excepción en tiempo de ejecución.