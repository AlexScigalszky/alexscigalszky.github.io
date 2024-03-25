---
layout: post
title: "Camino del Senior(.Net + Angular): Tutorial LINQ: Contains"
---

Se utiliza para corroborar que al menos un elemento existe en la colleción<!--more-->. Devuelve un booleano.
En este caso, chequea si **existe** el número 10 en la colleción.

```csharp
bool is10Present = numbers.Contains(10);
```

> **NOTA 1:** tener en cuenta que utiliza el segundo parámetro `comparer`. Si ese parámetro no existe utiliza la comparación por referencia.

Ejemplo con comparer

```csharp
class Comparer: IEqualityComparer<Clazz> {
    public bool Equals(Clazz x, Clazz y) {
        return x.Id == y.Id; // condición por la que se van a comparar dos objetos
    }
    public int GetHashCode([DisallowNull] Clazz obj){
        throw new NotImplementedException(); // no es necesario en estos casos
    }
}
bool is10Present = numbers.Contains(10);
```

> **NOTA 2:** `string` implementa la interface `IEqualityComparer` lo que permite usarlo sin el **comparer**.

> **NOTA 3:** Los números son **value types** y no se comparar por referencia lo que permite usarlo sin el **comparer**.