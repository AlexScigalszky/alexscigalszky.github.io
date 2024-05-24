---
layout: post
title: "Tutorial LINQ: OrderBy"
categories: ["senior", "csharp", "coding"]
---

Ordena una colleción usando un criterio que <!--more--> es pasado como parámetro.

La función Lamda que recibe como parámetro se usa para seleccionar una propiedad, luego se utiliza la comparación por referencia entre objetos al menos que se defina un __comparer__

# OrderBY
En este caso, orderna por **Name**.

```csharp
bool shortUsers = users.OrderBy(x => x.Name);
```

> **NOTA 1:** OrderBy genera una nueva colleción ordenada. No modifica la original.

# OrderByDescending

Existe un método identico pero para ordernar **descendentemente**. El método es `OrderByDescending()`.

```csharp
bool shortUsers = users.OrderByDescending(x => x.Age);
```

# ThenBy
Para utilizar más de un criterio para ordernar se puede usar el método `ThenBy()` o `ThenByDescending()`

```csharp
bool shortUsers = users.OrderBy(x => x.Age).ThenByDescending(x => x.Name);
```

> **NOTA 2:** Se puede utilizar un comparer para ordenar por criterios muy complejos

# Reverse
Invierte el orden actual de la colleción

```csharp
bool usersFromZToA = usersFromAToZ.Reverse();
```